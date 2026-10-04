# Maclean Recorder 1.2.2 — build and verification report

Built and publisher-signed on 2026-10-02 from the updated 1.2.2 source. Static and JVM evidence
passes; no Android device or emulator was connected for runtime UI or capture testing.

| Check | Result |
| --- | --- |
| Application ID | `com.macleanofduartenterprises.macleanrecorder` |
| Version | `1.2.2` / versionCode `10202` |
| Android versions | minSdk 26; target/compile SDK 35 |
| Clean release build and R8 shrinking | PASS |
| Release lint | PASS: 0 errors, 4 warnings |
| Unit tests | PASS: 15 tests, 0 failures, 0 errors, 0 skipped |
| Independent MP3 probe/decode | PASS: MP3, 44.1 kHz, mono, 192 kbps; FFmpeg decode completed without an error |
| Publisher signing | PASS: supplied publisher key; APK Signature Schemes v2 and v3 |
| APK alignment | PASS |
| Package and launcher identity | PASS |
| Supplied launcher artwork | PASS: embedded byte-for-byte; adaptive and themed resources present |
| Debuggable release | No |
| Bundled native libraries | None; zero `.so` files and zero `lib/` entries |
| AI models or signing keys in APK | None |
| Internet permission | Absent |
| Offline licenses | AGPLv3, notices, and LGPLv3 match the source texts |
| APK size | 1,354,461 bytes |

Signed APK SHA-256:
`bda6d90016c9c96ab6ecefd1c0e7506b9d112bb7990dbda7c7702a9e4e84d7b7`

Publisher certificate SHA-256:
`62ebb3c5d7d722b2e1174a4622f7593926204579084f94e11151ef606b32d136`

## Changes in 1.2.2

- Replaced the launcher artwork with the supplied 1536×1536 green evergreen, sound-wave, and
  microphone image. Its bytes and SHA-256 are unchanged inside the optimized APK.
- Sized the artwork within Android's adaptive-icon layers and added a dark-green edge fill so
  circular, rounded-square, and manufacturer-defined masks do not expose the source canvas.
- Added a matching single-color evergreen/microphone resource for Android 13+ themed icons and
  declared the adaptive icon for both standard and round launcher presentation.
- Retained default MP3 capture; Device audio, Microphone, and Device + microphone sources; the
  background, button, line, and letter color wheels; metadata, sharing, WAV trimming, and offline
  license features.

## Tests performed

- Six WAV tests cover exact stereo frame boundaries, copy and replacement behavior, invalid
  selections, truncated input, odd-sized RIFF chunks, and overflow-safe end-time clamping.
- Four encoding tests cover signed 16-bit peak calculation, FLAC STREAMINFO construction,
  duplicate codec configuration, and rejection of headerless FLAC.
- Two PCM/MP3 tests verify exact sample-by-sample 50/50 device/microphone mixing and MP3 output
  from the bundled pure-Java encoder.
- Three appearance tests verify the four interface defaults, case-normalized six-digit colors,
  and rejection of malformed, shorthand, and alpha-bearing values.
- A separate release-evidence step generated a one-second MP3 through the compiled app sink.
  FFprobe identified the expected codec, sample rate, channel count, and bitrate; FFmpeg decoded
  it without errors.

## Lint warnings

Two `DefaultLocale` warnings are inside the vendored, unmodified Java LAME ID3 implementation;
automatic ID3 writing is disabled by the app. `IconLauncherShape` identifies the supplied artwork
as a filled square, while Android displays it through the declared adaptive mask. One
`MonochromeLauncherIcon` warning concerns the base adaptive icon; the API 33 resource variant
supplies the monochrome layer. No lint error was disabled or baselined.

## Physical-device checks still required

- Install over 1.2.1 and cold-launch the signed APK; verify existing recording and appearance
  preferences migrate without data loss.
- Inspect the icon on home screens and app drawers using circle, squircle, and rounded-square
  launcher masks. On Android 13+, enable themed icons and verify the evergreen/microphone silhouette.
- Open each of the four color wheels, tap and drag across hue/saturation, change brightness,
  apply a color, restart, and verify persistence. Confirm button fills/accents, outlines/dividers
  and the recording-level line, and text/icons respond independently.
- Exercise very light, dark, and similar foreground/background choices, background photos, large
  text, Reset interface colors, and the high-contrast override on small and large displays.
- Record, stop, reopen, and share MP3 from the microphone at the available rates, mono/stereo
  choices, and bitrates. Include very short and extended sessions.
- On Android 10+, test consent approval, denial, and revocation for Device audio; record
  Device + microphone and confirm both sources are audible and balanced.
- Repeat MP3, WAV, FLAC, M4A, and Opus/Ogg capture where supported, including built-in,
  Bluetooth, wired, and USB microphones, screen-off recording, and notification stop behavior.
- Recheck metadata, favorites, folders, tags, selected deletion, sharing, and WAV trim
  copy/replace.

Static inspection and host-side decoding do not substitute for these device tests. Device audio
capture also cannot bypass another app's playback-capture policy.

## Evidence

`verification/` contains the successful clean-build log, all JUnit XML results, lint text/XML,
independent MP3 probe/decode results, APK manifest and badging, publisher-signature output,
structured verification metadata, and the R8 mapping for this exact APK. The private keystore and
passwords are excluded.
