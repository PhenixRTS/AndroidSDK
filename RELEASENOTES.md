# Release notes

### 2018.10.19 ###
+ Fixes
    + Fixes for various crashes that could occur when shutting down or stopping the Phenix SDK
    + Fixed sporadic loss of audio on viewer side
    + Fixed exception when unsupported resolution is requested
    + Fixed crashes when running SDK in simulator
    + Fixed exception when activity gets destroyed while renderer is still active

+ Features
    + SDK is organized as an AAR package for easier integration
    + First version of telemetry, providing better visibility into device performance
    + Room and channel publish APIs now provide RoomService instance in callback
    + Improved connections times when initializing Phenix SDK
    + Allow passing of custom HTTP headers for authentication and stream token requests
