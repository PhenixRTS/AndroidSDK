# Phenix Android SDK

## Integration
The Phenix SDK is provided as a standard Android library module in form of an .aar file.
Please check [official Android documentation](https://developer.android.com/studio/projects/android-library#AddDependency) for integration.

### As Gradle dependency (recommended)
1) Add to your `~/.gradle/gradle.properties`
```
github.user=<Github user name>
github.token=<Github personal token with read:packages permission>
```
Token can be created in: https://github.com/settings/tokens
See official page for details: https://help.github.com/en/articles/creating-a-personal-access-token-for-the-command-line

2) Add repository to your `app/build.gradle` or `project/build.gradle/allProjects`
```
repositories {
   mavenCentral()
   maven {
       credentials {
           username project.findProperty("github.user") as String
           password project.findProperty("github.token") as String
       }
       url "https://maven.pkg.github.com/PhenixRTS/AndroidSDK"
   }
}
```
3) Add to your project `app/build.gradle`
```
dependencies {
   // For the latest version please check https://github.com/PhenixRTS/AndroidSDK/packages/23358
   implementation "com.phenixrts.android:phenix-sdk-android:2022.0.1"
}
```

 Note: Unfortunately "com.phenixrts.sdk:phenix-sdk:2019.+" won’t work due to Android Studio restrictions for 3p libraries.

### As GIT submodule
You may add our library as git submodule to your project.
1. Add Phenix SDK as git submodule to you Android project root:
	1. [Install git-lfs](https://github.com/git-lfs/git-lfs/wiki/Installation)
	2. clone library to your project as submodule:
	```console
	git submodule add <git@github ...> [path to Android project]```
2. Add module name (same as directory), to your **settings.gradle** (ex ':phenix-sdk')
3. Don't forget to add it as dependency to your *app/build.gradle*:
```
dependencies {
    implementation project(':phenix-sdk')
    ...
}
```

## Known issues

### ERROR: Unable to resolve dependency for ':app@debug/compileClasspath': Could not resolve com.phenixrts.android:phenix-sdk-android:*.

1) Check Phenix SDK version
2) Check that your account has access to Phenix private repository (https://github.com/PhenixRTS/AndroidSDK)
3) Check that token has `read:packages` permission
4) Check that you are using the correct token

### Package `com.phenixrts.*` doesn't exist
Verify that `phenix-sdk.aar` has a reasonably large size (> 80MB), otherwise check your `git-lfs` installation.
Try `#> git lfs install` and then cloning the AndroidSDK repository again.

### Build crash: java.io.IOException: Failed to find byte code for …
Android Studio issue: https://issuetracker.google.com/issues/76403146
**Solution:**
1) Upgrade : _gradle-wrapper.properties_ - **gradle-4.6-all.zip or later**
2) Upgrade gradle plugin in project _build.gradle_ - 'com.android.tools.build:gradle:**3.2.+' or later**

Or Disable instant run - Android Studio -> Settings -> Search Instant run -> Disable

### IDE error: .GroovyFileImpl because: different providers: SingleRootFileViewProvider
Android Studio issue: https://issuetracker.google.com/issues/77939622
**Solution:** If directory for module was created (e.g. `/phenix-sdk`), just add direcory name to _settings.gradle_ file.
```gradle
include ':app', ':phenix-sdk'
```
