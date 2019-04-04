# Release notes

### 2019.2.0 ###
#### Features/Improvements
- AEC integration
#### Fixes
- Fix crash during ICE server registration
- Safe creation of an empty renderer from an already stopped ExpressSubscriber 
- Publisher side frame-ready API: Drops frames when overloaded instead of falling behind


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
