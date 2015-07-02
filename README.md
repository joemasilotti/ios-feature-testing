# iOS Feature Testing

A comparison of the current iOS feature testing frameworks available.

## Features

Comparison overview of each of the frameworks' features such as `UIControl` interaction, remote processes, and the ability to be run from the command line.

### Essential

| Feature 	| Frank 	| UIAutomation 	| Subliminal 	| KIF 	| Appium
|---------	|-------	|--------------	|------------	|-----	| ------
| iOS 8+ support          	| 💚 	| 💚 	| 💚 	| 💚 	| 💚  |
| Run from CI             	| 💚 	| 💚 	| 💚 	| 💚 	| 💚  |
| Animation waiting       	| 💛[¹](#footnotes)	|    	| 💚  	| 💚  	| 💛[¹](#footnotes)  |

### UIKit Interactions

| Feature 	| Frank 	| UIAutomation 	| Subliminal 	| KIF 	| Appium  |
|---------	|-------	|--------------	|------------	|-----	| ------  |
| Reading UILabels         	| 💚	| 💚  	| 💚 	| 💚 	| 💚  |
| UITableView interaction   	| 💚   	| 💚 	| ❌ 	| 💚 	| 💚  |
| Scrolling UIScrollViews  	| 💚   	| 💚 	| 💚 	| 💚 	| 💚  |
| Standard UIAlertViews     	| 💚   	| 💚 	| ❌ 	| 💚 	| 💚  |
| Typing into UITextFields   	| 💛[²](#footnotes) 	| 💚  	| 💚	| 💚	| 💚  |
| Tapping UIControls        	| 💚  	| 💚	| 💚	| 💚	| 💚  |
| Sliding UISliders         	| 💚 	| ❌	| 💛[³](#footnotes)	| 💚 	| 💛[¹⁰](#footnotes)  |
| UIKit visibility          	| 💚 	| 💚	| 💚	| 💚	| 💚  |
| UIActionSheet interaction 	| 💚 	| 💚 	| 💚 	| 💚 	| 💚  |
| UIPickerView interaction  	| 💚 	| 💛[⁴](#footnotes)	| 💚 	| 💚 	| 💛[⁴](#footnotes)  |
| Swipe to delete           	| ❌ 	| ❌ 	| ❌ 	| 💚 	| 💚  |

### Hybrid Apps

| Feature 	| Frank 	| UIAutomation 	| Subliminal 	| KIF 	| Appium  |
|---------	|-------	|--------------	|------------	|-----	| ------  |
| UIWebView interaction   	| ❌ 	| 💚 	| 💚 	| 💚 	| 💚  |
| WKWebView interaction   	| ❌ 	| 💚 	| ❌[⁵](#footnotes) 	| ❌ 	| 💚  |

### External to App

| Feature 	| Frank 	| UIAutomation 	| Subliminal 	| KIF 	| Appium  |
|---------	|-------	|--------------	|------------	|-----	| ------  |
| Remote controllers          	| ❌ 	| 💚 	| ❌[⁵](#footnotes)	| ❌ 	| 💚  |
| System UIAlertViews        	| ❌ 	| 💚 	| ❌	| 💚 	| 💚  |
| Backgrounding/foregrounding 	| ❌ 	| ❌ 	| ❌	| ❌ 	| ❌  |

### Developer Niceties

| Feature 	| Frank 	| UIAutomation 	| Subliminal 	| KIF 	| Appium  |
|---------	|-------	|--------------	|------------	|-----	| ------  |
| Objective-C                                 	| ❌ 	| ❌ 	| 💚 	| 💚 	| 💚  |
| BDD-style                                   	| 💚 	| ❌  	| ❌ 	| 💛[⁶](#footnotes) 	| 💚  |
| Can be debugged                            	| 💚 	| ❌  	| 💛[⁷](#footnotes)	| 💚 	| 💚  |
| Does not require Instruments.app            	| 💚 	| ❌  	| ❌ 	| 💚 	| ❌  |
| Focus tests                                 	| 💚 	| ❌    	| 💚 	| 💚[⁸](#footnotes) 	| ❌  |
| Cocoapods support                           	| 💚 	| n/a 	| 💚 	| 💚 	| ❌ |
| Inspect view hierarchy from framework’s PoV 	| 💚 	| 💚  	| 💚 	| 💛[⁹](#footnotes) 	| 💚  |

💚 = Full support
💛 = Support with caveats

## Rubric

A more detailed look into the pros and cons of each framework.

1. How easy it is to write tests *first*
1. Familiarity with language tests are written in
1. Ability to be run via the command line and on CI
1. Reliability
1. Coverage
1. How close to real interaction it is
1. Documentation
1. Community
1. Framework maintenance
1. Ability to run on physical devices (nice to have)

### Frank

1. Developer can target UI elements via css-like selectors. This frees the developer from having to know ahead of time the implementation of the view hierarchy.
1. Tests are written in Ruby with lots of Cucumber helper steps optionally available.
1. There is a single command to "Frankify" the app, but CI setup takes more custom work.
1. Some tests can become flaky if written poorly. Asynchronous behavior quickly becomes unreliable, especially with animations and chaining events.
1. Most user interactions are able to be reproduced. The exceptions are `MFMailComposeViewController`, `ABPeoplePickerNavigationController`, and other controllers that aren't actually handled *inside* the app (eg. asking for location permissions and access to the address book). There are workarounds for some but not all of these issues.
1. The framework uses UIAutomation when possible but some interactions are not as "true" as they could be. Lot's of Frank's magic comes from `UIKit` objects being extended. For example, swiping views is all done in Objective-C to workaround it not being available in UIAutomation.
1. There is a decent amount of setup and implementation details on the website but lots of the functionality isn't documented or explained.
1. [frank-discuss](https://groups.google.com/forum/#!forum/frank-discuss) Google group is more of a knowledge base than an active discussion forum. Stack Overflow is lacking information on Frank.
1. Frank is maintained so poorly we have considered forking it and maintaining it on our own. This, however, has improved since iOS 8 has launched.
1. Frank claims to be able to run on devices but I haven't gotten it to work.

### UIAutomation

1. UIAutomation requires that each level of the view hierarchy be explicitly referenced. For example, to access a button in a scroll view your syntax would look something like `UIATarget.localTarget().frontMostApp().mainWindow().scrollViews[0].buttons()[0]`. This makes your feature tests tied to the implementation of your view hierarchy.
1. UIAutomation is written in JavaScript. There are a number of wrappers built on top of it to help make it less verbose, such as [bwoken](https://github.com/bendyworks/bwoken) and [tuneup_js](https://github.com/alexvollmer/tuneup_js).
1. It is possible to run UIAutomation scripts via the command line with the some custom build scripts. The main idea is to inject the JavaScript into the app and then run it via Instruments.
1. While reliable when running via the GUI and command line, there is a race condition bug in Instruments that occurs on lower-end machines. This makes it particularly difficult to use when running as CI on a Mac Mini.
1. UIAutomation should be able to cover 99% of all use cases when running on a mobile device. However, a portion of these are broken with the introduction of iOS 7 (and continue to remain broken in iOS 8). These range from basic features such as scrolling views to very complex interactions like putting the app to sleep for five seconds.
1. Being UIAutomation is from Apple it should be as close to “real” user interaction as possible.
1. Most of Apple’s documentation exists in the [UI Automation JavaScript Reference](https://developer.apple.com/library/ios/documentation/DeveloperTools/Reference/UIAutomationRef/UIAutomationRef.pdf) pdf.
1. There is a fair amount of talk online regarding UIAutomation and even a book from Pragmatic Bookshelf, [Test iOS Apps with UI Automation: Bug Hunting Made Easy](https://pragprog.com/book/jptios/test-ios-apps-with-ui-automation), covering how best to use.
1. Apple owns it and it’s closed source. It doesn’t appear that any updates have occurred since iOS 6.
1. Works but takes an extra couple of seconds to get installed on the device.

### Subliminal

1. Similar to KIF, all views are interacted with via their accessibility labels. Subliminal traverses the view hierarchy looking for each match, no knowledge the way the views are laid out is needed.
1. Tests are written in Objective-C as subclasses of XCTest.
1. While no issues are apparent in Subliminal itself, the tests are run through Instruments which carries its own slew of problems. See UIAutomation’s notes on Reliability for more information.
1. Subliminal has the best coverage off all the frameworks, even better than UIAutomation itself. Most of the broken parts of UIAutomation have been patched (either in Objective-C or JavaScript directly) and work well. One of the few remaining limitations is lack of interaction with WKWebView.
1. Beings it runs UIAutomation scrips under the hood, interaction should be as close to “real” user interaction as possible.
1. Every public method is documented with expectations and parameters with full integration into Dash.
1. Despite its shortcomings Subliminal seems to have the largest community of users. Twitter even [publicly acknowledged using it](https://twitter.com/JoinTheFlock/status/484163665336098816).
1. There haven’t been many recent commits to master and the [Xcode 6 / iOS 8 branch](https://github.com/inkling/Subliminal/pull/259) has been open for almost six months.
1. Subliminal claims to be able to run on devices but I haven't gotten it to work.

### KIF

1. All views are interacted with via their accessibility labels. Since KIF traverses the view hierarchy looking for each match, no knowledge the way the views are laid out is needed.
1. Tests are written in Objective-C as subclasses of XCTest.
1. Tests are run with the standard `xcodebuild test` command.
1. KIF is the most reliable of all the frameworks tested.
1. Similar to Frank, most user interactions are able to be reproduced. KIF still suffers from the same issues that plague Frank (e.g. it can’t interact with views outside of the app’s control). However, with recent additions it now can interact with system alerts (e.g. location services and photo authorization dialogs).
1. Most (if not all) of KIF’s interaction boils down to create `UITouch` events at the right point and sending them to the app.
1. Every public method is documented with expectations and parameters with full integration into Dash.
1. There is a [Google Group](https://groups.google.com/forum/#!forum/kif-framework) which only gets about one post per week. The same goes for the official StackOverflow tag, [kif-framework](http://stackoverflow.com/questions/tagged/kif-framework).
1. Framework is actively maintained with PRs being addressed within a few days of submission.
1. Works for all cases except interacting with system alerts.

### Appium
1. Tests are written the same way as selenium tests, and are designed to provide the same wrapper for iOS and Android so users do not need to know about platform-specific details. Tests can be written using any testRunner or methodology.
1. Tests can be written in *any* language (clients exist for Java, Swift, Python, Javascript, C#, Perl, PHP).
1. Tests can be run programmatically and from the command line. Easy to integrate with CI.
1. As of version 1.4.0 server is pretty reliable. Sometimes needs to be restarted if left running over hundreds of tests. Built on Instruments it comes will the bugs present in that tool.
1. Coverage is a bit better than that of UIAutomation, since Appium adds functionality and also implements workarounds over known bugs.
1. It's right there, as close as UIAutomation. Apps are not repackaged or wrapped for testing. Touch actions are actually simulated on the device.
1. Documentation is currently very verbose and explanatory, but disorganized.
1. Community is huge. Github issues are replied to usually same-day, and the www.discuss.appium.io forum has hundreds of users who are active daily.
1. Appium releases happen about once a month. Github issues are tracked and critical bugs fixed right away. Users are encouraged to write pull requests to add features they request.
1. Runs on physical devices (uses Instruments) with a few limitations, most notably:
 - There is an Instruments-enforced one second delay between user commands.
 - geolocation mocking doesn't work
 - files cannot be pushed to and from the device
 - safari alerts cannot be dismissed
 - cannot set the locale/language

#### Footnotes

* ¹ Some animations are handled without interaction, while others require manual waiting.
* ² Sometimes Frank is so eager to type, he doesn’t wait for the UITextField to fully focus, leading to dropped characters. Workarounds are possible.
* ³ Subliminal can slide a slider and successfully call delegate methods, but the computation of the physical nub offsets are left to you.
* ⁴ UIAutomation makes each UIPicker selection on value at a time, making selection very slow. Also, if the date is not selectable UIAutomation will silently fail.
* ⁵ Subliminal cannot interact with these elements directly, but can call into UIAutomation’s JavaScripts via `SLTerminal -eval:`.
* ⁶ Kif itself isn't a BDD framework, but integrates seamlessly with BDD frameworks such as [Quick](https://github.com/Quick/Quick).
* ⁷ Subliminal loops over Objective-C code which calls JavaScript asynchronously via Instruments making debugging possible, but quite difficult.
* ⁸ Tests can be focused in Xcode via tapping the gutter (ala XCTest) but not via the command line.
* ⁹ You can use the [Accessibility Inspector](https://developer.apple.com/library/ios/technotes/TestingAccessibilityOfiOSApps/TestAccessibilityiniOSSimulatorwithAccessibilityInspector/TestAccessibilityiniOSSimulatorwithAccessibilityInspector.html) to identify elements for KIF to interact with, but there isn’t a direct way to view the hierarchy or identify elements which KIF ignores because they are accessibility containers.
* ¹⁰ You can get the location of UISlider elements and create touch actions which manipulate them.

## Versions

* Xcode 6.1
* iOS 8.1
* Frank 1.2.3
* Subliminal 1.1.0 - [shared/Xcode6 branch - d99fef4 commit](https://github.com/inkling/Subliminal/commit/d99fef42529589373adc1948aede98aed0fbe9de)
* KIF - 3.0.8
* Appium - 1.4.6
