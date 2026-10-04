# Maclean-Voice
Maclean Voice is a versatile voice recording app AGPLv3 licensed for Android devices
# Maclean Recorder

**Maclean Recorder** is a privacy-focused, open-source Android audio recorder designed for local recording without cloud services, accounts, or Internet access.

It supports microphone recording, Android device-audio capture, and simultaneous device + microphone recording, with MP3 as the default audio format.

## Features

- MP3 recording by default
- WAV, FLAC, M4A, and Opus/Ogg support where supported by the device
- Three recording-source modes:
  - Microphone
  - Device audio
  - Device + microphone
- Simultaneous device and microphone capture with balanced audio mixing
- Android background/foreground recording
- Stop-and-save notification while recording
- Live recording amplitude meter
- Microphone/input-device selection
- Recording library
- Folders and tags
- Favorites
- Recording metadata
- Select and delete recordings
- Share and export recordings
- 16-bit PCM WAV trimming
- Background photos
- Adjustable background opacity
- Adjustable text scaling
- High-contrast accessibility mode
- Keep-screen-on option
- Fully customizable interface colors
- Continuous color wheel for background, buttons, lines, and text
- Persistent appearance settings
- Offline license and third-party notices

## Device Audio Recording

On Android 10 and later, Maclean Recorder can capture audio being played by other applications using Android's MediaProjection system.

Android displays a system consent prompt before device-audio recording begins. Applications can restrict whether their audio is capturable, so some protected or restricted audio cannot be recorded.

**Device + microphone** mode captures both sources concurrently and mixes them into a single recording.

## Privacy

Maclean Recorder is designed as a **local-first application**.

The application has **no Internet permission** and does not require an online account, cloud service, AI service, or external recording server.

Recordings remain under the user's control on the Android device unless the user chooses to share or export them.

## MP3 Support

MP3 is the default recording format.

MP3 encoding uses the bundled pure-Java Java LAME implementation rather than relying on a device-specific MP3 encoder or native library.

## Application Information

**Version:** 1.2.2  
**Package:** `com.macleanofduartenterprises.macleanrecorder`  
**Minimum Android:** Android 8.0 / API 26  
**Target:** Android 15 / API 35  
**Developer:** Maclean Of Duart Enterprises

## License

Maclean Recorder is free and open-source software licensed under the **GNU Affero General Public License v3.0 (AGPL-3.0-only)**.

The complete AGPLv3 license, LGPLv3 text, and applicable third-party notices are available offline inside the application under:

**Settings → Licenses**

Third-party components remain subject to their respective licenses.

Copyright © Maclean Of Duart Enterprises.
