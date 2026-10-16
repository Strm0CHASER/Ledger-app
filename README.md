# Ledger APK project

Full illustrated-style guide: see the "Turn Ledger into an Android APK" document you were sent with this zip. Short version below.

## Route A: build online with GitHub (nothing to install)
1. Unzip this file on a computer.
2. Create a free account at github.com and make a new empty repository (default branch: main).
3. Click "uploading an existing file" and drag in EVERYTHING from inside the ledger-app folder, including the hidden .github folder, the www folder and the signing folder. Commit to main.
   - Can't upload .github? Use Add file > Create new file, name it .github/workflows/build-apk.yml and paste in the contents of the file from this zip.
4. Open the Actions tab. If asked, enable workflows. Pick "Build APK" and press Run workflow if it has not started. Wait 5 to 10 minutes for the green tick.
5. Open the finished run, download the "ledger-apk" artifact and unzip it to get app-debug.apk.
6. Send app-debug.apk to your phone and tap it. Allow installs from that app when asked. If Play Protect warns, choose More details > Install anyway.

## Route B: Android Studio on your computer
Install Node.js 20 and Android Studio, then in this folder run:
  npm install
  npx cap add android
  npx cap sync android
  npx cap open android
In Android Studio choose Build > Build Bundle(s) / APK(s) > Build APK(s). The file is at android/app/build/outputs/apk/debug/app-debug.apk

## Updating the app later
Edit www/index.html (on GitHub: open the file, press the pencil, paste the new code, commit). Route A rebuilds automatically. Install the new APK over the old one. The fixed key in the signing folder keeps your data. If you ever get "App not installed", export a backup (Setup > Backup > Export json), uninstall the old app, install the new one, then Import json.

## Your data
Stored on the phone only. Uninstalling erases it, so export a backup now and then.
This is a debug build for your own phone. It is not for the Play Store.
