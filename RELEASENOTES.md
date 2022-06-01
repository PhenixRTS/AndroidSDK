# Release notes

### 2022.0.2 ###
#### Features/Improvements

#### Fixes

### 2022.0.1 ###
#### Features/Improvements

- Added support for CDN domains.
- Improved PhenixPCastExpressFactory: it is not necessary anymore to provide a PCastUri if it is included in the token.
- Reduced network usage when downloading stream replay segments.
- Improved channel joining: it is not necessary anymore to provide a channel alias or ID if it is included in the token.

#### Fixes

- Fixed chat room’s messages loss in case of network issues.
- Fixed late PhenixChannelExpress.joinChannel callback call in case of network issues.
- Fixed media sometimes not starting on some devices

### 2021.0.15 ###
#### Features/Improvements
- Timeshift API
- Viewport based HLS layer selection for timeshifts
- Timeshift prefetch window is updated based on layer bitrate for faster switching from very low bitrate layers
- Support for "click and seek" into a timeshift segment
- Timeshift observable playback head reports position in UTC time
- Timeshift pause and play options
- Timeshift observable failure report
- `LimitBanwdith` API for `TimeShift`
- Added observable in `RoomChatService` that fires individually for each chat message as they come in
- Automatic stream restart on change in network type
- Camera auto reconnection logic
- Add support for Automatic Gain Control
- Support for configurable sampling rate for BlueTooth SCO capability
- Adds support for MIME types to chat messages
- `Member.commitChanges` callback is guaranteed to be called, with a timeout status if need be
- VOD asset playback support via TimeShift
- Observable session id on `PCastExpress`
- Support for stereo audio output
- `TimeShiftOptions` via `RendererOptions` allows customization of rendition selection behavior
- `ChannelExpress.joinChannel` will now return with an "unauthorized" status (subscriber callback) when the stream token that was provided when the channel was joined is either invalid or has expired. The recourse for the app is to leave the channel (`RoomService.leaveRoom`) and then re-join the channel with an updated stream token.
- Improved error handling when attempting to start subscribers and publishers with capabilities and edge stream tokens
- When no Admin API (e.g. backend) is provided, channel publisher wildcard tokens are now automatically disabled to avoid failures
- `UserMediaStream` instances will no longer get stopped because of network disruptions or switches so they can be retained for as long as needed by an app
- Increased internal timeout when connecting to PCast platform to avoid SDK initialization failures on clients with lossy network connections
- Support for new `replay` subscriber capability

#### Fixes
- Fix for inconsistent self member updates
- Fix for occasional failures when creating `RoomChatService`. Extra delay before creating service is no longer needed.
- Fixed missing callback invocation for `RoomExpress.subscribeToMemberStream` if member stream has ended already
- Removed embedded private key and certificate


### 2020.0.0 ###
#### Features/Improvements
- Introduced stream ended observables to MediaStream and Publisher, allowing for multiple subscribers
- The Publisher will now stop itself and forward the reason to the stream ended observables when the underlying stream ends
- `PCastExpress.publish` will now accept publish options with both a user media stream and constraints specified

#### Fixes
- Fixed video failing to render as a result of `Surface` lifecycle changes
- Fixed crash when network type changes during SDK initialization
- Fixed crash when calling `getUserMedia()` with both audio and video disabled
- The SDK will more reliably reconnect when a network connection is reestablished
- `Observable.subscribe()` now takes an `OnChangedHandler<T>` instead of `OnChangedHandler<Object>`. As a result, callback handlers need to implement `onEvent(T change)` instead of `onEvent(Object change)`.


### 2019.2.3 ###
#### Features/Improvements
- Support for edge authentication tokens
- Added playout delay override API
- Argument-less `withRenderer` API on various options builders has been deprecated. Use `withAudioOnlyRenderer` instead
- `close()` API on SDK objects has been deprecated. Use `dispose()` instead, which does not declare an explicit exception, and is, therefore, easier to use
- MIPS architectures are removed
- Now available as Gradle dependency. See Readme.md for details

#### Fixes
- Room or channel service automatically re-joins after a network disruption
- Fix ScreenGrabber crashes on SecurityException on Android 6+


### 2019.2.2 ###
#### Fixes
- Room participants will no longer leave zombie sessions around when reauthenticating
- Fixed `audio-only` for cases where wildcard tokens are present for channel viewers


### 2019.2.1 ###
#### Features/Improvements
- Lag render statistic via `Renderer.getStats`/`PhenixRenderer.stats`
- Reduced SDK initialization times
- Improved layer switching strategy for MBR streams
- Improved reconnection logic for clients with network outages

#### Fixes
- Fixed memory leak on stop publishing
- Fixed rebuffering telemetry metric
- Fixed rare crash when backgrounding app
- Fixed crash when attempting to subscribe while SDK is being shut down
- Fixed horn-like sound artifact when app returns to foreground
- Fixed resource leak in video rendering code


### 2019.2.0 ###
#### Fixes
- Fix crash during ICE server registration
- Safe creation of an empty renderer from an already stopped ExpressSubscriber 
- Publisher side frame-ready API: Drops frames when overloaded instead of falling behind

#### Features/Improvements
- Audio Echo Cancelation is now available on Android. 

**Note:** AEC needs to be enabled in the RendererOptions in addition to UserMediaOptions. See documentation for more details.


### 2019.0.0 ###
#### Fixes
- Publisher bitrate limitation reason will remain “None” and no longer be set to “PublisherLimited” while recovering from bitrate override
- Normal app termination/exit will no longer trigger sporadic exceptions
- App will no longer crash if we are unable to leave a room while the RoomService is being finalized

### 2018.4.3 ###
#### Features/Improvements
- URIs passed to SDK can now accept leading and trailing whitespaces without causing failures
- Improved chat message observable behavior to ensure that initial callback will always contain most recent chat history

#### Fixes
- Fixed detached functionality when publishing remote streams via express API
- Fixed sporadic DTLS connection issues
- Properly release all resources when stopping an express publisher


### 2018.4.2 ###
#### Features/Improvements
- Improved connection time during SDK initialization.  Results in shorter time-to-first-frame.
- WiFi connected clients are no longer automatically forced through TURN/TCP
- New limitBandwidth API method to limit the maximum bandwidth a client should use for streams

#### Fixes
- Fixed reconnection issues which could occur when devices switch networks or are moved to background and back
- Fixed occasional 5 second hang when SDK is shut down
- Fix for dropping video or audio when consuming streams where one is arriving later than the other
- Fixed automatic resubscription logic when streams are ended with a recoverable reason


### 2018.4.1 ###
#### Features
- SDK is organized as an AAR package for easier integration
- First version of telemetry, providing better visibility into device performance
- Room and channel publish APIs now provide RoomService instance in callback
- Improved connections times when initializing Phenix SDK
- Allow passing of custom HTTP headers for authentication and stream token requests

#### Fixes
- Fixes for various crashes that could occur when shutting down or stopping the Phenix SDK
- Fixed sporadic loss of audio on viewer side
- Fixed exception when unsupported resolution is requested
- Fixed crashes when running SDK in simulator
- Fixed exception when activity gets destroyed while renderer is still active
