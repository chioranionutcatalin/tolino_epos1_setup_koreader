# After wasting like 2 days, I'm making a resume for my koreader setup on Tolino epos1

## Tolino Epos 1: Nova Launcher and KOReader via ADB

I used Android Platform Tools from Google and a USB cable to connect my Tolino Epos 1 to my PC.

The device was running an  Tolino firmware 16 on Android 4.4.2, so I used the Tolino debug menu code for that firmware generation to enable debug mode from the search field.

I installed the APKs through ADB,  (run in cmd, you need to be in the platform-tools root with the apks, example: C:\Users\.....\platform-tools-latest-windows\platform-tools):
[https://developer.android.com/tools/releases/platform-tools](url)
[https://github.com/koreader/koreader](url)

```bash
adb devices
adb install "com.teslacoilsw.launcher_4.2.2-42200_minAPI16(nodpi).apk" (seached on the web)
adb install "koreader-android-arm-v2026.03.apk" (I used latest)
```

Once the APKs were installed, I rebooted the Tolino and selected Nova Launcher as the default Home app.

To start KOReader directly without going through Nova Launcher, I used a delayed start command:

```bash
adb shell "(sleep 10 && am start -n org.koreader.launcher/org.koreader.launcher.MainActivity) &"
```

Important: this only worked reliably for me if I unplugged the USB cable a few seconds after running the command (within the delay window). If I kept the cable connected, Tolino often stayed stuck in its stubborn USB/stock flow.

This gave me the setup I wanted: Nova Launcher as the home screen and KOReader available as a normal app.

Debug menu codes for Tolino devices vary by firmware generation:

- Firmware 14: `124816`
- Firmware 15: `1123581321`
- Firmware 16: `112358132fb`

Use the code that matches your device firmware.
