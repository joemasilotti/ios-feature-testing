# Features

## Essential
 
| Feature 	| Frank 	| UIAutomation 	| Subliminal 	| KIF 	| Calabash 	|
|---------	|-------	|--------------	|------------	|-----	|----------	|
| iOS 8+ support          	| 💚 	| 💚 	| 💚 	| 💚 	|   	|
| Run from CI             	| 💚 	| 💚 	| 💚 	| 💚 	|   	|
| Animation waiting       	| 💛¹	|    	| 💚  	| 💚  	|   	|

## UIKit Interactions

| Feature 	| Frank 	| UIAutomation 	| Subliminal 	| KIF 	| Calabash 	|
|---------	|-------	|--------------	|------------	|-----	|----------	|
| Reading UILabels         	| 💚	| 💚  	| 💚 	| 💚 	|  	|
| UITableView interaction   	| 💚   	| 💚 	| ❌ 	| 💚 	|  	|
| Scrolling UIScrollViews  	| 💚   	| 💚 	| 💚 	| 💚 	|  	|
| Standard UIAlertViews     	| 💚   	| 💚 	| ❌ 	| 💚 	|  	|
| Typing into UITextFields   	| 💛² 	| 💚  	| 💚	| 💚	|  	|
| Tapping UIControls        	| 💚  	| 💚	| 💚	| 💚	|  	|
| Sliding UISliders         	| 💚 	| ❌	| 💛⁴	| 💚 	|  	|
| UIKit visibility          	| 💚 	| 💚	| 💚	| 💚	|  	|
| UIActionSheet interaction 	| 💚 	| 💚 	| 💚 	| 💚 	|  	|
| UIPickerView interaction  	| 💚 	| 💛⁵	| 💚 	| 💚 	|  	|
| Swipe to delete           	| ❌ 	| ❌ 	| ❌ 	| 💚 	|  	|

## Hybrid Apps

| Feature 	| Frank 	| UIAutomation 	| Subliminal 	| KIF 	| Calabash 	|
|---------	|-------	|--------------	|------------	|-----	|----------	|
| UIWebView interaction   	| ❌ 	| 💚 	| 💚 	| 💚 	|  	|
| WKWebView interaction   	| ❌ 	| 💚 	|    	| ❌ 	|  	|

## External to App

| Feature 	| Frank 	| UIAutomation 	| Subliminal 	| KIF 	| Calabash 	|
|---------	|-------	|--------------	|------------	|-----	|----------	|
| Remote controllers          	| ❌ 	| 💚 	|  	| ❌ 	|  	|
| System UIAlertViews        	| ❌ 	| 💚 	|  	| ❌ 	|  	|
| Backgrounding/foregrounding 	| ❌ 	| 💚 	|  	| 💚 	|  	|


## Developer Niceties

| Feature 	| Frank 	| UIAutomation 	| Subliminal 	| KIF 	| Calabash 	|
|---------	|-------	|--------------	|------------	|-----	|----------	|
| Objective-C                                 	| ❌ 	| ❌ 	| 💚 	| 💚 	|  	|
| BDD-style                                   	| 💚 	| ❌  	| ❌ 	| ❌ 	|  	|
| Can be debugged                            	| 💚 	| ❌  	| 💛³	| 💚 	|  	|
| Does not require Instruments.app            	| 💚 	| ❌  	| ❌ 	| 💚 	|  	|
| Focus tests                                 	| 💚 	| ❌    	| 💚 	| ❌ 	|  	|
| Cocoapods support                           	| 💚 	| n/a 	| 💚 	| 💚 	|  	|
| Inspect view hierarchy from framework’s PoV 	| 💚 	| 💚  	| 💚 	| 💛⁶ 	|  	|




💚 = Full support
💛 = Support with caveats

* ¹ Some animations are handled without interaction, while others require manual waiting.
* ² Sometimes Frank is so eager to type, he doesn’t wait for the UITextField to fully focus, leading to dropped characters. Workarounds are possible.
* ³ Subliminal loops over Objective-C code which calls JavaScript asynchronously via Instruments making debugging possible, but quite difficult.
* ⁴ Subliminal can slide a slider and successfully call delegate methods, but the computation of the physical nub offsets are left to you.
* ⁵ UIAutomation makes each UIPicker selection on value at a time, making selection very slow. Also, if the date is not selectable UIAutomation will silently fail.
* ⁶ You can use the [Accessibility Inspector](https://developer.apple.com/library/ios/technotes/TestingAccessibilityOfiOSApps/TestAccessibilityiniOSSimulatorwithAccessibilityInspector/TestAccessibilityiniOSSimulatorwithAccessibilityInspector.html) to identify elements for KIF to interact with, but there isn’t a direct way to view the hierarchy or identify elements which KIF ignores because they are accessibility containers.
