# PennyPlate – Android build

## Option A: no installs (GitHub)
1. Create a free GitHub repo, upload everything in this folder (keep the `.github` folder).
2. Repo > Actions > "Build APK" > Run workflow.
3. When it finishes, download `PennyPlate-debug-apk` from the run page, unzip, install `app-debug.apk`.

## Option B: your computer (Node 20 + JDK 17 + Android SDK)
    npm install
    npx cap add android
    # add to android/app/src/main/AndroidManifest.xml, inside <manifest>:
    #   <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
    #   <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    npx cap sync android
    cd android && ./gradlew assembleDebug
APK: android/app/build/outputs/apk/debug/app-debug.apk

## What changed in index.html
- GPS now goes through the native Capacitor Geolocation plugin (permission prompt + real GPS).
- Map/store links open via the native Browser plugin, so Google Maps opens.
Edit `www/index.html`, then run `npx cap sync android` and rebuild.
