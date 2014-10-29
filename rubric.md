# iOS Feature Testing

## Rubric

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
1. [Calabash](https://github.com/calabash/calabash-ios)
1. [KIF](https://github.com/kif-framework/KIF)
1. [Subliminal](https://github.com/inkling/Subliminal)
1. [Zucchini](http://www.zucchiniframework.org)

### Frank

1. Written in Objective-C, Ruby, and Cucumber. Cucumber wraps the Ruby steps.
1. There is a single command to "Frankify" the app, but CI setup takes more custom work.
1. Some tests can become flaky if written poorly. But interacting with some Apple frameworks (eg. MapKit) always cause issues.
1. Most user interactions are able to be reproduced. The exceptions are `MFMailComposeViewController`, `ABPeoplePickerNavigationController`, and other controllers that aren't actually handled *inside* the app (eg. asking for location permissions and access to the address book). There are workarounds but they require extra configuration and aren't straightforward.
1. The framework uses UIAutomation when possible but some interactions are not as "true" as they could be. Lot's of Frank's magic comes from `UIKit` objects being extended. For example, swiping views is all done in Objective-C to workaround it not being available in UIAutomation.
1. 
1. Frank claims to be able to run on devices but I haven't gotten it to work.

### Calabash

### KIF

### Subliminal

### Zucchini
