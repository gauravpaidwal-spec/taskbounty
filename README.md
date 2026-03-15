# TaskBounty Android App (WebView Wrapping)

This is the Android wrapper for the TaskBounty micro-tasking platform. It converts the responsive mobile web UI into a fully-fledged native app experience featuring standard Android components (Bottom Navigation, Swipe to refresh, Native Push Notifications via Firebase).

## Prerequisites
- Android Studio Iguana (or newer)
- Java Development Kit (JDK) 17+
- An emulator or physical Android device

## Changing the Web App Target URL
Before releasing, you must link the Android app to your live production Flask URL (e.g. deployed on Render.com or PythonAnywhere).

1. Open `app/src/main/java/com/taskbounty/app/MainActivity.kt`
2. Find the constant `BASE_URL` on line 28.
3. Replace the `http://10.0.2.2:5000` (Localhost emulator mapping) to your actual remote URL. Example:
   ```kotlin
   private val BASE_URL = "https://taskbounty.yourdomain.com"
   ```

## Configuring Firebase Push Notifications
Push notifications run via Firebase Cloud Messaging (FCM). To make it work in production:
1. Go to the [Firebase Console](https://console.firebase.google.com).
2. Create a new project or select an existing one.
3. Add an Android App with the package name: `com.taskbounty.app`
4. Download the actual `google-services.json` file.
5. Replace the placeholder file `app/google-services.json` inside this repository with your real downloaded file.

## How to Build the APK
Building the Android application package allows you to install it manually on devices or distribute it off-store.

1. Open **Android Studio** and click **Open**. Select the `TaskBountyApp` folder.
2. Wait for Gradle Sync to finish. Check the Build sidebar at the bottom to ensure no dependency errors occur.
3. In the top toolbar, go to **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
4. Android Studio will compile the app.
5. Once complete, a toast notification in the bottom right corner will appear saying "APK(s) generated successfully".
6. Click **Locate**. This opens your file explorer highlighting `app-debug.apk`. 

## How to Build for Play Store (AAB)
1. Go to **Build > Generate Signed Bundle / APK...**
2. Select **Android App Bundle** (AAB) and click **Next**.
3. Create a Key store path and fill out the password credentials. Keep this file safe!
4. Select the `release` Build Variant and click **Create**. This will generate the signed `.aab` file required by the Google Play Developer Console.

## Installing the APK on a physical device
1. Connect your Android device via USB.
2. Ensure **Developer Options** and **USB Debugging** are enabled on your device.
3. Transfer the `app-debug.apk` file to your device's internal storage.
4. Open your device's File Manager, tap on the APK, and grant permission to "Install Unknown Apps" if prompted.
5. Install and launch the app!
