# Phenix Android SDK

## Integration
The Phenix SDK is provided as a standard Android library module in form of an .aar file.
Please check [official Android documentation](https://developer.android.com/studio/projects/android-library#AddDependency) for integration.

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
### Package `com.phenixrts.*` doesn't exist
`phenix-sdk.aar` should be more than 80MB, in other cases please check git-lfs installation.
Try `#> git lfs pull`.

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
