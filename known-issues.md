---
layout: page
title: Known issues
permalink: /known-issues.html
---

Status of open issues and recent fixes. Items move from **Investigating** to **Fixed, not yet
in a build** when a fix is tested on the test phone, and to **In the current build** once a test
build contains it. Every fix is also listed in the [Changelog](changelog.html).

## Investigating

- **VoLTE does not register.** Calls fall back to 2G and work normally; the IMS stack is running
  but not yet registering with the network.
- **A PC USB port does not charge the phone.** The charger sees the cable but never switches
  charging on from a computer port; a wall charger works. The charger/USB handshake changed in
  the 4.4 kernel and is being compared with the 3.18 one.
- **adb may need a cable re-plug after a restart or after deep sleep** (the computer shows the phone as
  "offline" or not at all).
## Parked (disabled on purpose until their stage)

- **Camera**, **fingerprint**, **NFC**: disabled until their porting stages.
- **DRM (Widevine):** Android 15 needs a newer Widevine HAL than the one from the OnePlus 18.1
  release; disabled until then (it was restarting every few seconds).

## Fixed, not yet in a build

- (none)

## In the current build

- **Deep sleep works.** The camera service waited forever (uninterruptibly) for the camera daemon,
  which is parked for now, so the phone could never be frozen for suspend and drained about 2-4 % per
  hour with the screen off. The wait is now bounded and freezable, as in the OnePlus 3.18 kernel. In a
  27-minute screen-off test on Wi-Fi the phone slept about 94 % of the time with no measurable battery
  drop. (M3e)
- **Wi-Fi no longer wakes the phone for every broadcast packet.** The Wi-Fi driver registered a
  wake-up for each received packet (about 3 per second on a home network), which stopped any
  deep sleep. (M3d)
- **The radio daemon can take wake locks again.** On Android 15 its wake-lock requests went to
  the wrong service manager and all failed. A slow-send state seen once before this fix did not
  return: an SMS sent after deep sleep goes out in under a second. (M3c, verified on M3e)
- **The radio starts.** Libraries of the radio stack picked up Android 15's own copies of shared
  libraries and failed to load; IMEI, baseband, LTE data, calls and SMS now work. (M3b)
