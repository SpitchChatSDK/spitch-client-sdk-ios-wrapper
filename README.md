# SpitchClientLibraryWrapper

Objective-C-friendly wrapper around SpitchClientLibrary 3.

## Installation

For the first you should have _SpitchClientLibrary_ inside your project.

Then just copy .swift-files from **SpitchClientLibraryWrapper** directory to your Objective-C-based project (in alphabetical order):
* **Department.swift**
* **FatalErrorHandler.swift**,
* **Message.swift**,
* **MessageListener.swift**,
* **MessageStream.swift**,
* **MessageTracker.swit**,
* **Operator.swift**,
* **ProvidedAuthorizationTokenStateListener.swift**
* **Webim.swift**,
* **WebimError.swift**,
* **WebimLogger.swift**,
* **WebimRemoteNotification.swift**,
* **WebimSession.swift**.

If your project doesn't contain any .swift-files yet Xcode (or another IDE you use) may offer to create a bridging header file. Do not hesitate to agree.
More details about "Swift and Objective-C in the Same Project" can be found at [Apple Developer portal](https://developer.apple.com/library/content/documentation/Swift/Conceptual/BuildingCocoaApps/MixandMatch.html).

Inside an Objective-C-file in which you are intended to use _SpitchClientLibrary_ you have to import just "<Your_Project_Name>-Swift.h" (do not try to import nor _SpitchClientLibrary_, neither _SpitchClientLibraryWrapper_ files!).

That's it! You are ready to start using _SpitchClientLibrary_ inside your Objective-C code!

## Example

Provided example is not a working application. It's just a basic sample project to show how _SpitchClientLibraryWrapper_ can be integrated into your app.

## Version

Every version of _SpitchClientLibraryWrapper_ matches with appropriate _SpitchClientLibrary_ version.
Different versions may have differences in classes and methods naming or do not have some of functionality.

## Usage

Basically there's no need to take a look inside _SpitchClientLibraryWrapper_ files. In the most cases it is sufficient to work just with _SpitchClientLibrary_ APIs.

Class and methods names that should be used are similar to API names. E.g. to create session this code may be used:
```
WebimSession *webimSession = [[[[Webim newSessionBuilder]
    setAccountName:@"ACCOUNT_NAME"]
    setLocation:@"LOCATION"]
    build:&error];
```
Original API version is:
```
let webimSession = try Webim.newSessionBuilder()
    .set(accountName: "ACCOUNT_NAME")
    .set(location: "LOCATION_NAME")
    .build()
```

Another example is resuming session:
```
[webimSession resume:&error];
```
Instead of this Swift synthax:
```
try webimSession.resume()
```

And one more:
```
MessageStream *messageStream = [webimSession getStream];
```
Instead of:
```
let messageStream = webimSession.getStream()
```

Simple! And obvious.

> Of course there're many differences between Swift and Objective-C languages, so some of the features are presented differently. The most notable othernesses in this context are optionals and error handling.

> If this wrapper implementation seems not comfortable to you, go on, feel free to change wrapper files at your decision. This code is just an instrument.

## License

_SpitchClientLibraryWrapper_ is available under the MIT license. See the LICENSE file for more info.

