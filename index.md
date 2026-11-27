---
layout: home
title: Home
---

Unofficial **LineageOS 22.2 (Android 15)** for the **OnePlus 3** (`oneplus3`, A3003,
Snapdragon 820 / msm8996), on a **Linux 4.4** kernel.

> **Status: in development, not released.** There is no download. This site documents the
> port, its fixes and what still needs work.

The OnePlus 3 last had official LineageOS up to 18.1 (Android 11, kernel 3.18). This port
moves it to LineageOS 22.2 with a 4.4 kernel, using the LineageOS msm8996 device trees of the
Xiaomi Mi 5 family and the LG G5 as references, plus OnePlus-specific drivers and firmware
blobs from the OnePlus 3's own 18.1 release.

## Status

| Area | Status | Notes |
|---|---|---|
| Boot, UI, display, touch | ✅ Works | |
| Loudspeaker (TFA9890 smart amp) | ✅ Works | With continuous speaker protection monitoring (coil resistance, temperature, alarms) |
| Earpiece, microphone | ✅ Works | Tested in calls |
| Headphones (3.5 mm) | ✅ Works | Including the headset volume buttons |
| Mobile data (LTE) | ✅ Works | IPv4 and IPv6 |
| Calls | ⚠️ Partly | Work over 2G (circuit-switched fallback from LTE); VoLTE does not register yet |
| SMS | ✅ Works | Send and receive (multi-part too); a slow-send state is being verified |
| IMEI, baseband, dual SIM | ✅ Works | Both SIM slots detected |
| Wi-Fi | ✅ Works | |
| Wi-Fi hotspot | ✅ Works | |
| Bluetooth | ❔ Not tested yet | |
| USB (adb) | ✅ Works | adb may need a cable re-plug after a restart |
| Charging | ⚠️ Partly | Wall charger works; a PC USB port does not charge |
| Standby (deep sleep) | ✅ Works | About 94 % of idle time asleep with Wi-Fi on; no measurable drain in a 27-minute test (M3e) |
| GPS, sensors | ❔ Not tested yet | |
| Camera | ⏸ Parked | Disabled until the camera stage |
| Fingerprint, NFC | ⏸ Parked | Disabled until their stages |
| DRM (Widevine) | ⏸ Parked | Needs a newer Widevine HAL (Android 15 requirement) |
| USB OTG | ❔ Not tested yet | The USB-C controller driver is not ported yet |
| SELinux | ⚠️ Permissive | Enforcing planned before release |
| Recovery | ✅ Works | LineageOS 22.2 recovery, adb sideload |

See [Known issues](known-issues.html) for details and the [Changelog](changelog.html) for
progress.
