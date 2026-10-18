# The Idiot Audiobook — Android Studio project

The audiobook **HTML interface is bundled inside the APK** at `app/src/main/assets/index.html`. The app does not navigate to GitHub Pages to download the page itself; Android loads the bundled HTML directly.

## Current asset arrangement

- `app/src/main/assets/index.html`: bundled copy of `index_apple_music_player_v5.html`.
- Audio and read-along JSON paths in this HTML currently resolve against `https://0xdsaini.github.io/dostoevsky/`, so chapter MP3s and read-along timing JSON are still hosted online. This project bundle did not include those large media files.
- Playback progress and settings are stored in the WebView's local storage on this Android device.
- An internet connection is currently required for chapter audio and read-along JSON.

If you later want a fully offline app, put the chapter MP3s under `app/src/main/assets/build/audio_in/merged_chapters/` and the timing JSON files under `app/src/main/assets/readalong/`, then update the HTML paths and WebView loading/origin strategy accordingly.

## Build an APK

1. Install Android Studio, JDK 17, and Android SDK Platform 35.
2. Open this project folder in Android Studio.
3. Allow Gradle sync and install any requested SDK components.
4. Choose **Build → Build Bundle(s) / APK(s) → Build APK(s)**.
5. Android Studio will show the APK location, usually `app/build/outputs/apk/debug/app-debug.apk`.

The app uses an immersive full-screen window, enables JavaScript and DOM storage, supports the website's fullscreen API, and opens external web links in the device browser.

## Updating the bundled interface

Replace `app/src/main/assets/index.html` with the updated HTML file, then rebuild the APK. Changes to the website's `index.html` alone will not change the HTML already packaged in an installed APK.
