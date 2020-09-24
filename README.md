# Flutter Firebase Starter

This project is a guide to properly configure any flutter project using Firebase on iOS and Android.

## Documentation
* [Prerequisites](#prerequisites)
* [Setup Android app for Firebase](#setupAndroid)
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
