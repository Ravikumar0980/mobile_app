# Quote & Invoice Manager – Android project

Needs: Node.js 22+, Android Studio (latest, installs SDK + JDK).

## Debug APK (for testing)
1. `npm install`
2. `npm run apk`   (or: `npm run open`, then Build > Build APK(s) in Android Studio)
3. APK: android/app/build/outputs/apk/debug/app-debug.apk  -> copy to phone and install

First build downloads Gradle, so it needs internet and a few minutes.
If `gradlew` errors about JAVA_HOME, set it to Android Studio's JBR folder (Android Studio > Settings > Build Tools > Gradle > Gradle JDK).

## Signed release (Play Store .aab / release APK)
Android Studio: Build > Generate Signed Bundle / APK. Create a keystore ONCE and keep it + passwords safe;
every future update must use the same one. Increase versionCode in android/app/build.gradle for each update.

## Change app id / name
Edit capacitor.config.json (appId must be unique, e.g. com.yourcompany.quotes), then `npx cap sync android`.
Do this BEFORE the first Play Store upload; it cannot change afterwards.

## Editing the app
Edit www/index.html, then `npm run sync` and rebuild.

## Moving your data
The APK stores data separately from the browser. In your old version: Settings > Download backup.
In the APK: Settings > Restore backup (pick the file). Also download backups regularly.
