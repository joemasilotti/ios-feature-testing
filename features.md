# Features

## Essential
 
| Feature 	| Frank 	| UIAutomation 	| Subliminal 	| KIF 	| Calabash 	|
|---------	|-------	|--------------	|------------	|-----	|----------	|
| iOS 8+ support          	| 💚 	| 💚 	| 💚 	| 💚 	|   	|
| Run from CI             	| 💚 	| 💚 	| 💚 	| 💚 	|   	|
| Animation waiting       	| 💛[¹](#footnotes)	|    	| 💚  	| 💚  	|   	|

## UIKit Interactions

| Feature 	| Frank 	| UIAutomation 	| Subliminal 	| KIF 	| Calabash 	|
|---------	|-------	|--------------	|------------	|-----	|----------	|
| Reading UILabels         	| 💚	| 💚  	| 💚 	| 💚 	|  	|
| UITableView interaction   	| 💚   	| 💚 	| ❌ 	| 💚 	|  	|
| Scrolling UIScrollViews  	| 💚   	| 💚 	| 💚 	| 💚 	|  	|
| Standard UIAlertViews     	| 💚   	| 💚 	| ❌ 	| 💚 	|  	|
| Typing into UITextFields   	| 💛[²](#Footnotes) 	| 💚  	| 💚	| 💚	|  	|
| Tapping UIControls        	| 💚  	| 💚	| 💚	| 💚	|  	|
| Sliding UISliders         	| 💚 	| ❌	| 💛[³](#Footnotes)	| 💚 	|  	|
| UIKit visibility          	| 💚 	| 💚	| 💚	| 💚	|  	|
| UIActionSheet interaction 	| 💚 	| 💚 	| 💚 	| 💚 	|  	|
| UIPickerView interaction  	| 💚 	| 💛[⁴](#Footnotes)	| 💚 	| 💚 	|  	|
| Swipe to delete           	| ❌ 	| ❌ 	| ❌ 	| 💚 	|  	|

## Hybrid Apps

| Feature 	| Frank 	| UIAutomation 	| Subliminal 	| KIF 	| Calabash 	|
|---------	|-------	|--------------	|------------	|-----	|----------	|
| UIWebView interaction   	| ❌ 	| 💚 	| 💚 	| 💚 	|  	|
| WKWebView interaction   	| ❌ 	| 💚 	| ❌[⁵](#Footnotes) 	| ❌ 	|  	|

## External to App

| Feature 	| Frank 	| UIAutomation 	| Subliminal 	| KIF 	| Calabash 	|
|---------	|-------	|--------------	|------------	|-----	|----------	|
| Remote controllers          	| ❌ 	| 💚 	| ❌[⁵](#Footnotes)	| ❌ 	|  	|
| System UIAlertViews        	| ❌ 	| 💚 	| ❌	| ❌ 	|  	|
| Backgrounding/foregrounding 	| ❌ 	| ❌ 	| ❌	| ❌ 	|  	|


## Developer Niceties

| Feature 	| Frank 	| UIAutomation 	| Subliminal 	| KIF 	| Calabash 	|
|---------	|-------	|--------------	|------------	|-----	|----------	|
| Objective-C                                 	| ❌ 	| ❌ 	| 💚 	| 💚 	|  	|
| BDD-style                                   	| 💚 	| ❌  	| ❌ 	| ❌ 	|  	|
| Can be debugged                            	| 💚 	| ❌  	| 💛[⁶](#Footnotes)	| 💚 	|  	|
| Does not require Instruments.app            	| 💚 	| ❌  	| ❌ 	| 💚 	|  	|
| Focus tests                                 	| 💚 	| ❌    	| 💚 	| ❌ 	|  	|
| Cocoapods support                           	| 💚 	| n/a 	| 💚 	| 💚 	|  	|
| Inspect view hierarchy from framework’s PoV 	| 💚 	| 💚  	| 💚 	| 💛[⁷](#Footnotes) 	|  	|

💚 = Full support
💛 = Support with caveats

### Versions

* Xcode 6.1
* iOS 8.1
* Frank 1.2.3
* Subliminal 1.1.0 - [shared/Xcode6 branch - d99fef4 commit](https://github.com/inkling/Subliminal/commit/d99fef42529589373adc1948aede98aed0fbe9de)
* KIF - 3.0.8

### Footnotes

* ¹ Some animations are handled without interaction, while others require manual waiting.
* ² Sometimes Frank is so eager to type, he doesn’t wait for the UITextField to fully focus, leading to dropped characters. Workarounds are possible.
* ³ Subliminal can slide a slider and successfully call delegate methods, but the computation of the physical nub offsets are left to you.
* ⁴ UIAutomation makes each UIPicker selection on value at a time, making selection very slow. Also, if the date is not selectable UIAutomation will silently fail.\
* ⁵ Subliminal cannot interact with these elements directly, but can call into UIAutomation’s JavaScripts via `SLTerminal -eval:`.
* ⁶ Subliminal loops over Objective-C code which calls JavaScript asynchronously via Instruments making debugging possible, but quite difficult.
* ⁷ You can use the [Accessibility Inspector](https://developer.apple.com/library/ios/technotes/TestingAccessibilityOfiOSApps/TestAccessibilityiniOSSimulatorwithAccessibilityInspector/TestAccessibilityiniOSSimulatorwithAccessibilityInspector.html) to identify elements for KIF to interact with, but there isn’t a direct way to view the hierarchy or identify elements which KIF ignores because they are accessibility containers.
