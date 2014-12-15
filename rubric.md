# iOS Feature Testing

## Rubric

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

## Frameworks

1. [Frank](http://www.testingwithfrank.com)
1. [UIAutomation](https://developer.apple.com/library/ios/documentation/DeveloperTools/Conceptual/InstrumentsUserGuide/UsingtheAutomationInstrument/UsingtheAutomationInstrument.html)
1. [KIF](https://github.com/kif-framework/KIF)
1. [Subliminal](https://github.com/inkling/Subliminal)
1. [Zucchini](http://www.zucchiniframework.org)

### Frank

1. Developer can target UI elements via css-like selectors. This frees the developer from having to know ahead of time the implementation of the view heirarchy.
1. Tests are written in Ruby with lots of Cucumber helper steps optionally available.
1. There is a single command to "Frankify" the app, but CI setup takes more custom work.
1. Some tests can become flaky if written poorly. Asyncronous behavior quickly becomes unreliable, especially with animations and chaining events.
1. Most user interactions are able to be reproduced. The exceptions are `MFMailComposeViewController`, `ABPeoplePickerNavigationController`, and other controllers that aren't actually handled *inside* the app (eg. asking for location permissions and access to the address book). There are workarounds for some but not all of these issues.
1. The framework uses UIAutomation when possible but some interactions are not as "true" as they could be. Lot's of Frank's magic comes from `UIKit` objects being extended. For example, swiping views is all done in Objective-C to workaround it not being available in UIAutomation.
1. There is a decent amount of setup and implementation details on the website but lots of the functionality isn't documented or explained.
1. [frank-discuss](https://groups.google.com/forum/#!forum/frank-discuss) Google group is more of a knowledge base than an active discussion forum. Stack Overflow is lacking information on Frank.
1. Frank is maintained so poorly we have considered forking it and maintaining it on our own. This, however, has improved since iOS 8 has launched.
1. Frank claims to be able to run on devices but I haven't gotten it to work.

### KIF

### Subliminal

### Zucchini
