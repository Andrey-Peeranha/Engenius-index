# Accessibility Testing on Mobile Apps: A Critical Component for App Development

What is the most crucial consideration to have when developing a mobile app? Many will argue about this point until the end of time, and each will have a different take on the answer. Some may say it’s technical superiority while others might say it’s user-friendliness. However, something to consider is this: wouldn’t you want to allow for as many people as possible to use your app? Enter accessibility, which aims to set your app up to be used by just about everyone.

## What is accessibility testing?
To the mobile app development community, accessibility (a.k.a “A11y”) is the practice of making products, devices, services, or environments to be usable by as many people as possible. In essence, developers design apps to have functionality that will work for people with or without disabilities. For mobile apps, accessibility typically adds features that cater to people who require alternate means of interaction with apps through visuals, sounds, and tactile responsiveness. Accessibility testing for mobile apps ensures that each function designed to help someone with an impairment use the app does its job well. Testing automation comes into play here and can greatly expedite the process with fewer mistakes with a shorter turnaround time.

Some examples of accessibility functionality for mobile apps include, but are not limited to, the following:

Higher contrast text and imagery options
Speak to text functionality
Text can be read aloud
Detailed descriptions of images
Tactile feedback and vibrations for certain activities
Color palettes that are friendly to color blindness
## Why is accessibility testing important to app development?
Since there is a wide variety of accessibility functions mobile app developers can utilize, choosing the right ones is critical to an app’s success with its target audience. Likewise, ensuring accessibility functionality is on par is just as critical so the app works for everyone and your development team does not get in trouble. Depending on the app, mistakes made during the accessibility testing phase can have dire consequences, sometimes resulting in lawsuits for millions of dollars. If you need more specific reasons for the importance of accessibility testing, try these on for size:

### Inclusivity
Not just a buzz word in the workplace, inclusivity means giving equity to people so that they can succeed when faced with physical or mental adversities. Most companies want to be able to reach out to as many people as possible who fall under the umbrella of their target audience. Some of these people within a target audience may have difficulties with using mobile apps, so designing an app to function for them also helps the brand appear more empathetic to its user base.  

### Legal and Regulatory Compliance 
Depending on the industry and country in which the app will operate, government regulation may mandate that mobile apps be user-friendly to everyone, including those with certain disabilities. Such legal compliance is typical for most government agency apps that allow payment processing, scheduling, documentation, etc. Other industries in which legal regulations may mandate accessibility include the medical, finance, civic, and security industries.

### Expanding the User Base 
In being inclusive, companies that utilize accessible apps increase their ability to expand the number of users as well as diversifying the kind of people that use their app. Adding accessibility functionality creates a broader appeal to a wider audience, inviting more users to be drawn to an app that satisfies their needs despite their need for accommodation.

### Ethical Considerations 
Think of it this way: is it fair to deny a person who needs a wheelchair access to a place simply because they are in a wheelchair? Most, including governments, consider such treatment as discrimination and generally unfair to those such action affects. Instead of denying wheelchair-bound customers, businesses provide a ramp along with stairs to promote accessibility. In the case of accessibility for mobile apps, promoting fair treatment and accommodation for all abilities puts the brand’s ethics on display. Accessibility is not just a function of usage, but an ethical consideration as well, so ensure customers see the app in a positive light.

### Improved User Experience 
By providing accessibility to all customers, the app becomes much more useful in general. Consider the current phenomenon in watching TV via streaming with the subtitles on, even if you do not have a hearing impairment. People want clarity on what is being said more often than not, so people whose hearing is just fine find the addition of accurate subtitles while watching helpful in understanding the scene. For mobile apps, adding accessibility features can provide additional functionality for those who may not necessarily need it, but find it helpful nonetheless.

### Competitive Advantage 
This notion may seem like a no-brainer, but making your app much more accessible to all types of users grants a tremendous competitive advantage over those who do not. Customers will naturally gravitate towards an app that accommodates their needs and the needs of those close to them (co-workers, family, friends, etc.) Even if your app does its task well, you may lose out to a competitor who follows accessibility best practices due to users not suggesting you to their circles who require accommodations.

### User Loyalty
As with any branding tactic, presenting an app that is accessible to all will breed a loyal following in those that you convert. An accessible app is also likely to inspire loyal users to bring along their friends, family, and co-workers, further growing your base of app evangelists. 

## How to perform your own accessibility testing
### Method 1: XCUITest
If you are already performing XCUITests, you have the capability for performing accessibility tests for your mobile app. Xcode products include a tool called Accessibility Inspector that can perform app audits to find and fix issues with accessibility functions. 

To perform an accessibility audit on your app, launch the Accessibility Inspector when viewing your app in Admin mode. Within the main dashboard, you can see a list of previous audits you have performed along with any issues the audit tool found to be corrected.

Before you perform your accessibility audit, click on Options in the upper right corner and ensure the following elements are checked:

Element Description
Contrast
Hit Region
Element Detection
Clipped Text
Traits
Dynamic Type
These elements are some of the most common that help to facilitate accessible features within a mobile app, so make sure you are checking them for functionality. 

You can make this entire process automated by using the following code shown below within your XCUIApplication:

No assertions are needed when performing this automated test. If any accessibility issues are discovered, the test will automatically fail and you will be able to fix the issues much more quickly. 

There are some additional accessibility test you can perform by adding these codes to your audit:

Ensuring minimum text size

Removing redundant elements

Uppercase button labels

### Uppercase button labels

[AccessibilitySnapshot](https://github.com/cashapp/AccessibilitySnapshot) allows you to create snapshots of accessibility hierarchy within your app as part of running regression tests. Before starting an accessibility snapshot test, you want to ensure that the app project is set up to run such tests. AccessibilitySnapshot uses the [SnapshotTesting](https://github.com/pointfreeco/swift-snapshot-testing) tool by default to record and compare snapshots. [iOSSnapshotTestCase](https://github.com/uber/ios-snapshot-test-case) is also available to use as a framework. 

SnapshotTesting:

import SnapshotTesting

import XCTest

class MyViewControllerTests: XCTestCase {

  func testMyViewController() {

    let vc = MyViewController()

    assertSnapshot(of: vc, as: .image)

  }

}

iOSSnapshotTestCase:

func testAccessibility() {

    let view = MyView()

    // Configure the view…

    SnapshotVerifyAccessibility(view)

}

Below is a list of alternate snapshot tools you can utilize for these tests:

[CocoaPods](https://cocoapods.org/)
pod ‘AccessibilitySnapshot’
pod ‘AccessibilitySnapshot/Core’
pod ‘AccessibilitySnapshot/iOSSnapshotTestCase’
[Swift Package Manager](https://www.swift.org/documentation/package-manager/)
dependencies: [

    .package(name: “AccessibilitySnapshot”, url: “https://github.com/cashapp/AccessibilitySnapshot.git”, from: “0.4.1”),

]

[Carthage](https://github.com/Carthage/Carthage)
github “cashapp/AccessibilitySnapshot”

Bazel
bazel_dep(

    name = “accessibility_snapshot”,

    version = “x.x.x”,

)

### Method 3: A11yUITests
Using this method, you can either use AccessibilitySnapshot like before, or [Reveal](https://revealapp.com/) to run your accessibility audit test. Also, A11yUITests works within the Xcode platform.

A11yUITests (All Elements):

func test_allTests() {

    XCUIApplication().launch()

    a11yCheckAllOnScreen()

}

A11yUITests (Specified Elements):

func test_buttons() {

    let buttons = XCUIApplication().buttons.allElementsBoundByIndex

    a11y(tests: a11yTestSuiteInteractive, on: buttons)

}

A11yUITests (Individual Element):

func test_individualTest_individualButton() {

    let button = XCUIApplication().buttons[“My Button”]

    a11y(tests: [.buttonLabel], on: [button])

}

Test Suite Shortcuts:

a11yTestSuiteAll: Runs all tests.
a11yTestSuiteImages: Runs tests suitable for images.
a11yTestSuiteInteractive: Runs tests suitable for interactive elements.
a11yTestSuiteLabels: Runs tests suitable for static text elements.
Want to learn more about accessibility testing, or have your own insight to share? Join our Discord to get in on the conversation!

[Link to Engenious Discord community](https://discord.gg/uXZdZjFcjB)
