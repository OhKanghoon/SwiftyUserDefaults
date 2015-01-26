# SwiftyUserDefaults

SwiftyUserDefaults is a set of extensions to make the `NSUserDefaults` API cleaner, nicer, and at home with Swift's syntax.

Read [Swifty APIs: NSUserDefaults](http://radex.io/swift/nsuserdefaults/) for more information about this project.

### Fetching data

```swift
Defaults["color"].string            // returns String?
Defaults["launchCount"].int         // returns Int?
Defaults["chimeVolume"].double      // returns Double?
Defaults["loggingEnabled"].bool     // returns Bool?
Defaults["lastPaths"].array         // returns NSArray?
Defaults["credentials"].dictionary  // returns NSDictionary?
Defaults["hotkey"].data             // returns NSData?
Defaults["firstLaunchAt"].date      // returns NSDate?
Defaults["anything"].object         // returns NSObject?
Defaults["anything"].number         // returns NSNumber?
```

SwiftyUserDefaults always returns `nil` for non-existing values, also for numbers and booleans.

### Setting data

```swift
Defaults["color"] = "red"
Defaults["launchCount"] = 0
```

SwiftyUserDefaults infers the right type when setting values.

### Optional assignment

```swift
Defaults["color"]            // => nil
Defaults["color"] ?= "white" // => "white"
Defaults["color"] ?= "red"   // => "white"
```

Works like `||=` in other languages — sets value only if the left-hand side value is `nil`.

### Arithmetic

```swift
Defaults["launchCount"] += 1
Defaults["launchCount"]++
```

You can use the `+=` and `++` operators to easily work on integer values in the user defaults. If the key didn't exist before operation, the operators assume it was `0`.

### Existence

```swift
if !Defaults.hasKey("hotkey") {
    Defaults.remove("hotkeyOptions")
}
```

You can use the `hasKey` method to check for key's existence in the user defaults. `remove()` is an alias for `removeObjectForKey()`.

### Author and license

Radek Pietruszewski

* [github.com/radex](http://github.com/radex)
* [twitter.com/radexp](http://twitter.com/radexp)
* [radex.io](http://radex.io)
* this.is@radex.io

SwiftyUserDefaults is available under the MIT license. See the LICENSE file for more info.

### Contributing

If you have comments, complaints or ideas for improvements, feel free to open an issue or a pull request.

### How to install

The recommended way is to install this library via CocoaPods as a private pod. Just add this line to your 'Podfile':

```ruby
pod 'SwiftyUserDefaults', :git => "https://github.com/radex/SwiftyUserDefaults.git"
```

### How to link to your project

Just import module "SwiftyUserDefaults" like this:

```swift
import SwiftyUserDefaults
```