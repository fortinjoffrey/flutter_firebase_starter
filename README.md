# Flutter Firebase Starter

This project is a guide to properly configure any flutter project using Firebase on iOS and Android.

## Documentation
* [Prerequisites](#prerequisites)
* [Setup Android app for Firebase](#setupAndroid)
* [Setup iOS app for Firebase](#setupIOS)
* [Update Android app display name](#updateAndroidappDisplayName)
* [Update iOS app display name](#updateIOSappDisplayName)
* [Troubleshooting](#troubleshooting)

<a name="prerequisites"/>

## ⚙ Prerequisites
* *flutter master*
* Create a new Flutter project
* Create a new [Firebase console]([https://console.firebase.google.com/) project (disable Firebase Analytics)

<a name="setupAndroid"/>

## Setup Android app for Firebase

In Firebase console, go to Add app > Android

### Register app

* Fill the **Android package name** following this format : `com.yourcompany.appname`

* Fill the **App nickname**

* To fill the **Debug signing certificate SHA-1**

* Open up **terminal** or **powershell**

```shell
cd projectName/android
./gradlew signinReport
```

* When running `./gradlew signinReport` you might encounter an error, please report to troubleshooting [section](#troubleshootingSigninReport)

* Scroll through the end of result to get the SHA1, copy/paste it to console

* Click **next**

### Download config file

* Download **google-services.json**

* Move the google-services.json file you just downloaded into your Android app module root directory

### Add Firebase SDK

* Follow the **Project-level build.gradle** and **App-level build.gradle** instructions

* In **App-level build.gradle**, update the `applicationId` (the same as you previously entered in Firebase console) and `minSdkVersion`

```json
applicationId "com.yourcompany.appname"
minSdkVersion 21
```

When `applicationId` changes in build.gradle, you need to update other files. Follow this [guide](https://medium.com/@skyblazar.cc/how-to-change-the-package-name-of-your-flutter-app-4529e6e6e6fc)

***Quick tip***

If your code is under version-control system (like Git), please add the **google-services.json** to a **.gitignore** file

To know [more](https://stackoverflow.com/questions/44937175/firebase-should-i-add-googleservice-info-plist-to-gitignore) about

<a name="setupIOS"/>

## Setup iOS app for Firebase

### Xcode manipulation

* Open with Xcode **Runner.xcworkspace** file in ios/ folder

* In Xcode click on the parent .xcworkspace file

* Update the **Bundle Identifier** following this format : `com.yourcompany.app_name`

* Go to **Signing & Capabilities** tab

* Select your team account. Make sure you have a valid certificate for Apple Development

### Register app

In Firebase console, go to Add app > iOS

* Fill the **iOS bundle ID** following this format : `com.yourcompany.app_name`

* Fill the **App nickname**

* Click **next**

### Download config file

* Download **GoogleService-Info.plist**

* Move the GoogleService-Info.plist file you just downloaded into ios > Runner directory

### Add Firebase SDK

Skip this step. Flutter will handle future installation of Firebase products

### Add initialization code

Skip this step. Firebase initialization will be written in Dart files

***Quick tip***

If your code is under version-control system (like Git), please add the **GoogleService-Info.plist** to a **.gitignore** file

To know [more](https://stackoverflow.com/questions/44937175/firebase-should-i-add-googleservice-info-plist-to-gitignore) about





<a name="updateAndroidappDisplayName"/>

## Update Android app display name

Open the **android/app/src/main/AndroidManifest.xml** file

Edit the **android:label** property : 
```xml
android:label="yourAppName"
```

<a name="updateIOSappDisplayName"/>

## Update iOS app display name

Open the **ios/Runner/Info.plist** file

Edit the **CFBundleName** key :  
```xml
<key>CFBundleName</key>
<string>yourAppName</string>
```

<a name="troubleshooting"/>

## ⚠️ Troubleshooting

<a name="troubleshootingSigninReport"/>

**Problem**

When running `./gradlew signinReport` you might encounter this error 
```diff
- FAILURE: Build failed with an exception.
```

**Solution**

* Open up the project with Android Studio

* Edit the `android/gradle.properties` file

* Replace the **org.gradle.jvmargs line** with `org.gradle.jvmargs=-Xmx1024M`

* Then go to **File>Invalidate Caches/Restart > Invalidate and Restart**

To know [more](https://stackoverflow.com/a/39680977) about
