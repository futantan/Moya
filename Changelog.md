# Next

- Changes `Moya.Error.Underlying` to have `NSError` instead of `ErrorType`. *Breaking change*

# 6.4.0

- Makes `convertResponseToResult` public to make use of this method when dealing with Alamofire directly
- Updates to ReactiveCocoa 4.1
- Updates to Result 2.0

# 6.3.1

- Updates for Swift 2.2 / Xcode 7.3 compatibility.

# 6.3.0

- Fixed endpoint setup when adding `parameters` or `headers` when `parameters` or `headers` or nil.
- Adds StructTarget for using Moya with structs.

# 6.2.0

- Adds `response` computed property to `Error` type, which yields a Response object if available.
- Added URLEncodedInURL to ParameterEncoding.
- Adds convenience `endpointByAdding` method.
- Remove our own implementation of `ParameterEncoding` and make it a `public typealias` of `Alamofire.ParameterEncoding`.

# 6.1.3

- Updated to ReactiveCocoa 4.0 final.
- Added formatter parameter to plugin for pretty-printing response data. See #392.

# 6.1.2

- Compatibility with RxSwift 2.x.

# 6.1.1

- Compatibility with RxSwift 2.1.x.

# 6.1.0

- The built-in `DefaultAlamofireManager` as parameter's default value instead of the singleton `Alamofire.Manager.sharedinstance` is now used when instantiating `ReactiveCocoaMoyaProvider` and `RxMoyaProvider` as well.

# 6.0.1

- Updates to ReactiveCocoa 4 RC 2.

# 6.0.0

- **Breaking Change** pass a built-in `DefaultAlamofireManager` as parameter's default value instead of passing the singleton `Alamofire.Manager.sharedinstance` when initialize a `provider`
- Fixes issue that stubbed responses still call the network.

# 5.3.0

- Updates to RXSwift 2.0.0
- Moves to use Antitypical/Result

# 5.2.1

- Update to ReactiveCocoa v4.0.0-RC.1
- Fixes cases where underlying network errors were not properly propagated.
- Moves to antitypical Result type

# 5.2.0

- Updated to RxSwift 2.0.0-beta.4

# 5.1.0

- Update to ReactiveCocoa v4.0.0-alpha.4

# 5.0.0

- **Breaking Change** rename `MoyaTarget` protocol to `TargetType`
- **Breaking Change** rename `MoyaRequest` protocol to `RequestType`
- **Breaking Change** rename `Plugin` protocol to `PluginType`
- Removes conversion from `Moya.Method` to `Alamofire.Method` since it was unused
- Changes `NetworkLoggingPlugin`'s initializer to also take a function that has the same signature as `print` to simplify testing
- **Breaking Change** renames `ParameterEncoding`'s `parameterEncoding` method to `toAlamofire` and makes it internal only
- **Breaking Change** `Plugin<Target>` is now a protocol and as such no longer sends a typed `MoyaProvider`. - @swizzlr
- **Breaking Change** The types that were subtypes of `Moya` are now defined at the top level; you should find no compatibility issues since they are still invoked by `Moya.X` – @swizzlr
- **Breaking Change** `Completion` closure now returns a `Result` instead of multiple optional parameters.
- **Breaking Change** `MoyaResponse` is now `Response`, and also `final`. It will be changed to a `struct` in a future release. - @swizzlr
- **Breaking Change** `ReactiveCocoaMoyaProvider` can now be supplied with an optional `stubScheduler` – @swizzlr (sponsored by [Network Locum](https://networklocum.com))
- **Breaking Change** Introduce `Error` type for use with reactive extensions - [@tomburns](http://github.com/tomburns)
- **Breaking Change** Deprecate ReactiveCocoa 2 support

# 4.5.0

- Adds mapping methods to `MoyaResponse`

# 4.4.0

- Adds tvOS and watchOS support
- Fixes carthage OS X target not having source files
- Makes base OS X target 10.9 instead of 10.10

# 4.3.1

- Updates to latest ReactiveCocoa alpha. Again.

# 4.3.0

- Updates to latest ReactiveCocoa alpha.

# 4.2.0

- Removed extraneous `SignalProducer` from ReactiveCocoa extension – @JRHeaton
- Removed extraneous `deferred()` from RxSwift extension
- Moved to new RxSwift syntax – @wouterw
- Updated RxSwift to latest beta – @wouterw

# 4.1.0

- OS X support.

# 4.0.3

- Fixes Carthage integration problem.

# 4.0.2

- CancellableTokens can now debug print the requests cURL.

# 4.0.1

- Plugins now subclasses NSObject for custom subclasses.
- Plugins' methods are now public, allowing custom subclasses to override.

# 4.0.0

- Updates Alamofire dependency to `~> 3.0`

# 3.0.1

- Changes `mapImage()` RxSwift function to use `UIImage!` instead of `UIImage`.

# 3.0.0

- Makes `parameters` on `MoyaTarget` an optional `[String: AnyObject]` dictionary.
- Makes `parameters` and `httpHeaderFields` on `Endpoint` to be optionals.
- Renamed stubbing identifiers: **Breaking Change**
  - `Moya.StubbedBehavior` renamed to `Moya.StubBehavior`
  - `Moya.MoyaStubbedBehavior` renamed to `Moya.StubClosure`
  - `Moya.NoStubbingBehavior` -> `Moya.NeverStub`
  - `Moya.ImmediateStubbingBehaviour` -> `Moya.NeverStub`
  - `Moya.DelayedStubbingBehaviour` -> `Moya.DelayedStub`
- Default class functions have been moved to extensions to prevent inadvertent subclassing.
- Renamed other identifiers: **Breaking Change**
  - `MoyaProvider.MoyaEndpointsClosure` to `MoyaProvider.EndpointClosure`
  - `MoyaProvider.MoyaEndpointResolution` to `MoyaProvider.RequestClosure`
  - `MoyaProvider.endpointResolver` to `MoyaProvider.requestClosure`
  - `MoyaProvider.stubBehavior` to `MoyaProvider.stubClosure`
  - `MoyaCredentialClosure` to `CredentialClosure`
  - `MoyaProvider` initializer parameter names
  - `MoyaCompletion` to `Moya.Completion`
  - `DefaultEndpointResolution` to `DefaultRequestMapping`
- Renamed `T` generic types of `MoyaProvider` and `Endpoint` classes to `Target`.
- Removed errantly named `DefaultEndpointResolution`
- Changes the closure to map `Endpoint`s to `NSURLRequest`s asynchonous.
- Removes inflight request tracking for ReactiveCocoa and RxSwift providers. **Breaking Change**
- Adds support for ReactiveCocoa 4 by moving `ReactiveCocoaMoyaProvider` to use `SignalProducer` instead of `RACSignal`
- Renamed `EndpointSampleResponse` cases: **Breaking Change**
  - `Success` to `NetworkResponse`, now contains `NSData` instead of `() -> NSData`.
  - `Error` to `NetworkError`
  - Additionally, `NetworkError` no longer has a status code or data associated with it. This represents an error from the underlying iOS network stack, like an inability to connect. See [#200](https://github.com/Moya/Moya/issues/200) for more details.
  - Also additionally, removed `Closure` case (see below).
- Changed `Endpoint` to use a `sampleResponseClosure` instead of a `sampleResponse`, making all sample responses lazily executed. **Breaking Change**
- New plugin architecture **Breaking Change**
  - This replaces `networkActivityClosure` with a plugin.
- ReactiveCocoa provider no longer replaces errors that contain status codes (an unlikely situation) with its own errors. It passes all errors directly through.
- Renames `token` to `target` (it was usually `target` anyway, just made it consistent).

# 2.4.1

- Corrects problem with ignoring the specified Alamofire manager

# 2.4.0

- Adds HTTP basic auth support.

# 2.3.0

- Adds data processing functions for use with `RxMoyaProvider`

# 2.2.2

- Adds convenience `endpointByAddingParameterEncoding` method.

# 2.2.1

- Adds Moya files as members of RxMoya and ReactiveMoya frameworks.

# 2.2.0

- Add backward-compatible call from `DefaultEnpointResolution` to `DefaultEndpointResolution` on `MoyaProvider` class. `DefaultEndpointResolution` is now used internally as the default resolver. `DefaultEnpointResolution` can be removed in a future major release.
- Carthage support.

# 2.1.0

- Add option to pass an `Alamofire.Manager` to `MoyaProvider` initializer

# 2.0.2

- Updates Demo directory's RxSwift version.

# 2.0.1

- Updates Demo directory's Moya version for `pod try` compatbility.

# 2.0.0

- **Breaking change** Combines `MoyaPath` and `MoyaTarget` protocols.
- **Breaking change** Renames `Moya/Reactive` subspec to `Moya/ReactiveCocoa`.
- **Breaking change** Removes `stubResponses` from initializer; replaced with new stubbing behavior `.NoStubbing`. Added class methods to `MoyaProvider` to provide defaults, while allowing users to still change stubbing behaviour on a per-request basis.
- **Breaking change** Redefines types of `DefaultEndpointMapping` and `DefaultEnpointResolution` class functions on `MoyaProvider`. You no longer invoke these functions to return a closure, rather, you reference the functions themselves _as_ closures.
- **Breaking change** Renames `endpointsClosure` parameter and property of `MoyaProvider` to `endpointClosure`.
- **Breaking change** Renames `ReactiveMoyaProvider` to `ReactiveCocoaMoyaProvider` for consistency.
- Fixes problem that the `ReactiveMoyaProvider` initializer would not respect the stubbing behaviour it was passed.
- Adds official Carthage support – [@neonichu](http://github.com/neonichu)
- Relaxes version dependency on RxSwift - [@alcarvalho](http://github.com/alcarvalho)
- Fixes possible concurrency bugs with reactive providers - [@alcarvalho](http://github.com/alcarvalho)

# 1.1.1

- Fixes problem where `RxMoyaProvider` would not respect customized stubbing behaviour (delays).

# 1.1.0

- Adds support for RxSwift – [@alcarvalho](http://github.com/alcarvalho)

# 1.0.0

- **Breaking change** Changes `EndpointSampleResponse` to require closures that return `NSData`, not `NSData` instances themselves. This prevents sample data from being loaded during the normal, non-unit test app lifecycle.
- **Breaking change** Adds `method` to `MoyaTarget` protocol and removes `method` parameter from `request()` functions. Targets now specify GET, POST, etc on a per-target level, instead of per-request.
- **Breaking change** Adds `parameters` to `MoyaTarget` protocol and removes ability to pass parameters into `request()` functions. Targets now specify the parameters directly on a per-target level, instead of per-request.
- Adds a sane default implementation of the `MoyaProvider` initializer's `endpointsClosure` parameter.

# 0.8.0

- Updates to Swift 1.2.

# 0.7.1

- Adds cancellable requests -[@MichaelMcGuire](http://github.com/MichaelMcGuire)

# 0.7.0

- Adds network activity closure to provider.

# 0.6.1

- Updates podspec to refer to `3.0.0-aplha.1` of ReactiveCocoa. -[@ashfurrow](http://github.com/ashfurrow)

# 0.6

- First release on CocoaPods trunk.
- Add data support for [stubbed error responses](https://github.com/ashfurrow/Moya/pull/92). – [@steam](http://github.com.steam)
- Fixes [#66](https://github.com/AshFurrow/Moya/issues/66), a problem with outdated Alamofire dependency and it's serializer type signature. -[@garnett](http://github.com/garnett)
- Delete note about ReactiveCocoa installation -[@garnett](http://github.com/garnett)

# 0.5

- Fixes [#52](https://github.com/AshFurrow/Moya/issues/52) to change submodules to use http instead of ssh. -[@ashfurrow)](http://github.com/AshFurrow)
- Migrate to support Xcode beta 6.1 -[@orta)](http://github.com/orta)
- Adds the original NSURLResponse to a MoyaResponse -[@orta)](http://github.com/orta)
- Fixes [#63](https://github.com/AshFurrow/Moya/issues/63), a problem where stale inflight requests were kept around if they error'd down the pipline (discussed [here](https://github.com/ReactiveCocoa/ReactiveCocoa/issues/1525#issuecomment-58559734)) -[@ashfurrow](http://github.com/AshFurrow)

# 0.4

- Implements [#46](https://github.com/AshFurrow/Moya/issues/46), the code property of the NSError sent through by ReactiveMoyaProvider will now match the failing http status code. -[@powerje](http://github.com/powerje)

# 0.3

- Fixes [#48](https://github.com/AshFurrow/Moya/issues/48) that modifies Moya to execute completion blocks of stubbed responses *immediately*, instead of using `dispatch_async` to defer it to the next invocation of the run loop. **This is a breaking change**. Because of this change, the ReactiveCocoa extensions had to be modified slightly to deduplicate inflight stubbed requests. Reactive providers now vend `RACSignal` instances that start the network request *when subscribed to*. -[@ashfurrow](http://github.com/AshFurrow)

# 0.2

- Fixes [#44](https://github.com/AshFurrow/Moya/issues/44) where status codes weren't being pass through to completion blocks. This also modified the behaviour of the ReactiveCocoa extensions significantly but sending MoyaResponse objects instead of just NSData ones. —[@ashfurrow](http://github.com/AshFurrow)

# 0.1

- Initial release.
