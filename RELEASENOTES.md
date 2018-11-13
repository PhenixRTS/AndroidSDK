# Release notes

### 2018.11.13 ###
#### Features/Improvements
- Improved connection time during SDK initialization.  Results in shorter time-to-first-frame.
- WiFi connected clients are no longer automatically forced through TURN/TCP
- New limitBandwidth API method to limit the maximum bandwidth a client should use for streams

#### Fixes
- Fixed reconnection issues which could occur when devices switch networks or are moved to background and back
- Fixed occasional 5 second hang when SDK is shut down
- Fix for dropping video or audio when consuming streams where one is arriving later than the other
- Fixed automatic resubscription logic when streams are ended with a recoverable reason

### 2018.10.19 ###
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
