## 3.1.2
* Example(Android): Added android.suppressUnsupportedCompileSdk=35 for compileSdk 35 builds.

## 3.1.1
* Android: Updated plugin `compileSdkVersion` to 35 for Android SDK 35 compatibility
* Example: Use `flutter.compileSdkVersion` and `flutter.targetSdkVersion` for automatic SDK updates
* Fix: UPI merchant code parameter now correctly uses `&mc=` (was missing `=`)
* Android 11+: Refined package visibility `<queries>` to specify `upi://pay` with `android:host="pay"`
* Build: Replaced deprecated `jcenter()` with `mavenCentral()` repository
* Example: Disabled Jetifier (not needed with v2 embedding) and increased Gradle heap to 2GB

## 3.1.0
* Migrated Android plugin to v2 embedding (declarative Gradle plugin system)
* Updated to AGP 8.3.0 and Gradle 8.4 for modern Flutter compatibility
* Added namespace configuration for Android (required for AGP 8.0+)
* Fixed build compatibility with Flutter 3.0+ and Android 12+
* Added explicit `android:exported` attribute for MainActivity

## 3.0.1
* `getAllUpiApps()` now supports Android 11+ 
* Updated Readme

## 3.0.0
Migrated to Null Safety

## 2.2.0+1
Added Warning about "Maximum limit exceeded" and "Risk threshold exceeded" in Readme.

## 2.2.0
**Breaking Change**
* `startTransaction` now does not return **UpiResponse** on error, rather throws error.
* Names of predefined apps now use camelCase as they are no longer constants.
* `app` parameter of **UpiApp** has been renamed to `packageName` to avoid confusion.
* `app` parameter passed in `startTransaction` now directly takes UpiApp instead of String.
* New Custom error classes have been added.
* `getAllUpiApps` now has three new parameters: `mandatoryTransactionId`, `allowNonVerifiedApps`, `includeOnly`.
* Airtel Thanks (My Airtel) has been moved to incompatible app group as it was not returning any response.
* New UPI Apps included.
* Now only the supported apps will be returned by `getAllUpiApps`.
* Migrated to use Android plugin APIs Embedding v2.

## 2.1.2
**Breaking Change** Names of classes have been changed to make them more concise.

* **UpiIndiaApp** has been renamed to **UpiApp**
* **UpiIndiaResponse** has been renamed to **UpiResponse**
* **UpiIndiaResponseStatus** has been renamed to **UpiPaymentStatus**
* **UpiIndiaResponseError** has been renamed to **UpiError**
* Modified Readme.


## 2.0.0
**Breaking Change** Whole way to use this plugin has changed. Some major changes are:

* Now pass transaction details in `startTransaction()` method instead of `UpiIndia` constructor.
* Renamed `UpiIndiaApps` to `UpiIndiaApp` and made it a model class containing app name, package name and app icon (only for apps returned by the below method).
* Added `getAllUpiApps()` method which returns `List<UpiIndiaApp>`.
* Now `startTransaction()` returns `Future<UpiIndiaResponse>` instead of `Future<String>`
* Now you get the error from the `error` parameter of `UpiIndiaResponse`
* Some new UPI Apps have been added too.
* **upi_india.dart** has been divided into three files to increase readability.
* **UpiIndiaPlugin.java** has been formatted to make it easy to understand.

## 1.1.2
* Removed **UpiIndiaResponseStatus.FAILED**.
* Removed **MI Pay** because of conflicting package name in  Play Store and GetApps(MI Apps).
* Added **Mobikwik** and **FreeCharge**
* Now look for **UPI_INDIA_FINAL_RESPONSE** in your terminal window to see the actual response string from your requested app.

## 1.1.1
* Changed **UpiIndiaResponseStatus.FAILED** to **UpiIndiaResponseStatus.FAILURE**.
* **UpiIndiaResponseStatus.FAILED** has been deprecated.

## 1.1.0

* Prevented app to crash in case requested app wasn't ready to proceed payment
* Did some changes in response status because PhonePe was returning **FAILED** instead of **FAILURE** as specified.

## 1.0.0

* Plugin to implement UPI in Android
