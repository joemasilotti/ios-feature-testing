# Features

## Essential
 
| Feature 	| Frank 	| UIAutomation 	| Subliminal 	| KIF 	| Calabash 	|
|---------	|-------	|--------------	|------------	|-----	|----------	|
| iOS 8+ support          	| 💚 	| 💚 	| 💚 	| 💚 	|   	|
| Run from CI             	| 💚 	| 💚 	| 💚 	|    	|   	|
| Animation waiting       	| 💛*	|    	|    	|    	|   	|

## UIKit Interactions

| Feature 	| Frank 	| UIAutomation 	| Subliminal 	| KIF 	| Calabash 	|
|---------	|-------	|--------------	|------------	|-----	|----------	|
| Reading UILabels         	| 💚	| 💚  	|    	|    	|  	|
| UITableView interaction   	| 💚   	| 💚 	| ❌ 	| 💚 	|  	|
| Scrolling UIScrollViews  	| 💚   	| 💚 	| 💚 	| 💚 	|  	|
| Standard UIAlertViews     	| 💚   	| 💚 	| ❌ 	| 💚 	|  	|
| Typing into UITextFields   	| 💛** 	| 💚  	|  	|  	|  	|
| Tapping UIControls        	| 💚  	| 💚	|  	| 	|  	|
| Sliding UISliders         	| 💚 	|  	|  	|  	|  	|
| UIKit visibility          	| 💚 	| 💚	| 💚	| 💚	|  	|
| UIActionSheet interaction 	| 💚 	| 💚 	| 💚 	| 💚 	|  	|
| UIPickerView interaction  	| 💚 	|  	| 💚 	| 💚 	|  	|
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
| Can be debugged                            	| 💚 	| ❌  	| 💛***	| 💚 	|  	|
| Does not require Instruments.app            	| 💚 	| ❌  	| ❌ 	| 💚 	|  	|
| Focus tests                                 	| 💚 	|     	| 💚 	| ❌ 	|  	|
| Cocoapods support                           	| 💚 	| n/a 	| 💚 	| 💚 	|  	|
| Inspect view hierarchy from framework’s PoV 	| 💚 	| 💚  	| 💚 	|    	|  	|




💚 = Full support
💛 = Support with caveats

* `*` Some animations are handled without interaction, while others require manual waiting.
* `**` Sometimes Frank is so eager to type, he doesn’t wait for the UITextField to fully focus, leading to dropped characters. Workarounds are possible.
* `***` Subliminal loops over Objective-C code which calls JavaScript asynchronously via Instruments making debugging possible, but quite difficult.
