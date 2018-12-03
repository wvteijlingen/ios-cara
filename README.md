![](./Images/CaraShield.jpg)

[![CI Status](http://img.shields.io/travis/icapps/ios-cara.svg?style=flat)](https://travis-ci.org/icapps/ios-cara)
[![Language Swift 4.0](https://img.shields.io/badge/Language-Swift%204.2-orange.svg?style=flat)](https://swift.org)

> Cara is the webservice layer that is (or should be) most commonly used throughout our apps.

## TOC

- [Installation](#installation)
- [Features](#features)
    - [Configuration](#configuration)
- [Contribute](#contribute)
  - [How to contribute?](#howtocontribute)
  - [Contributors](#contributors)
- [License](#license)

## Installation 💾

Cara is available through [CocoaPods](http://cocoapods.org). To install it, simply add the following line to your `Podfile`:

```ruby
pod 'Cara', git: 'https://github.com/icapps/ios-cara.git', commit: '...'
```

_Pass the correct commit reference to make sure your code doesn't break in future updates._

## Features

### Configuration

In order to use the service layer you have to configure it. This can be done by implementing the `Configuration` protocol and passing it to the `Service` init function.

```swift
let configuration: Configuration = SomeConfiguration()
let service = Service(configuration: configuration)
```

Once this is done you are good to go. For more information on what configuration options are available, take a look at the documentation inside the `Configuration.swift` file.

### Trigger a Request

In order to trigger a request you have to do 2 things:
- Create a request that conforms to `Request`.
    
    _The request configuration will be done in this instance. For more information on what options are available, take a look at the documentation inside the `Request.swift` file._

- Create a serializer  that conforms to `Serializer`.

    _The serialization of the response will be done here. You have to implement the `serialize(data:error:response:)` function and this will be called when the response completes._

Once both instances are created and you `Service` is configured, you can execute the request.

```swift
let request: Request = SomeRequest()
let serializer: Serializer = JSONSerializer()
service.execute(request, with: serializer) { response in
    ...
}
```

The `response` returned by the completion block is the same as result of the serializer's `serialize(data:error:response:)` function.

## Contribute

### How to contribute ❓

1. Add a Github issue describing the missing functionality or bug.
2. Implement the changes according to the `Swiftlint` coding guidelines.
3. Make sure your changes don't break the current version. (`deprecate` is needed)
4. Fully test the added changes.
5. Send a pull-request.

### Contributors 🤙

- Jelle Vandebeeck, [@fousa](https://github.com/fousa)

## License

Cara is available under the MIT license. See the LICENSE file for more info.