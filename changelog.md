---
layout: page
title: Changelog
permalink: /changelog.html
---

Test builds, newest first. None of them is released.

## M3e (built, not yet tested)

- Deep sleep: the camera service's wait for the (parked) camera daemon is now bounded and
  freezable, as in the OnePlus 3.18 kernel; it blocked every suspend.
- Fuel-gauge update intervals back to stock (an earlier change in M3d turned out not to matter).

## M3d

- Wi-Fi: no wake-up event for every received packet.
- Widevine DRM parked until a suitable HAL is available.

## M3c

- Radio: the radio daemon can take wake locks again.

## M3b

- Radio: the radio stack loads its own protobuf libraries instead of Android 15's, so it starts:
  IMEI, baseband, SIM, LTE data, calls (2G fallback) and SMS work.
- The same fix for the DRM library.

## M3

- Radio stack switched to the Qualcomm RIL used by the LineageOS 22.2 msm8996 devices (Android 15
  needs a newer radio interface than the OnePlus 18.1 one); modem firmware and modem configuration
  stay the OnePlus 3's own.
- Audio service waits for the sound card at boot.

## M1f

- Loudspeaker in normal use, with continuous speaker protection monitoring.
- Much less log noise; fingerprint, NFC and camera parked until their stages.

## M1 - M1e

- First boots of LineageOS 22.2 on the 4.4 kernel: display, touch, adb, recovery.
- Sound card and audio (earpiece, headphones, microphone); bring-up of the TFA9890 speaker
  amplifier with its factory calibration and speaker protection.
