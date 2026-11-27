---
layout: page
title: Known issues
permalink: /known-issues.html
---

Status of open issues and recent fixes. Items move from **Investigating** to **Fixed, not yet
in a build** when a fix is tested on the test phone, and to **In the current build** once a test
build contains it. Every fix is also listed in the [Changelog](changelog.html).

## Investigating

- **No deep sleep (standby battery drain).** The phone never completes a system suspend, so it
  drains about 2-4 % per hour with the screen off. Cause found: the camera service waits forever
  for a camera daemon that is parked for now, and a task in that state cannot be frozen, so every
  suspend attempt stalls until something wakes the phone. A fix (a bounded, freezable wait, as in
  the OnePlus 3.18 kernel) is in the next build and still has to be tested.
- **VoLTE does not register.** Calls fall back to 2G and work normally; the IMS stack is running
  but not yet registering with the network.
- **A PC USB port does not charge the phone.** The charger sees the cable but never switches
  charging on from a computer port; a wall charger works. The charger/USB handshake changed in
  the 4.4 kernel and is being compared with the 3.18 one.
- **adb may need a cable re-plug after a restart** (the computer shows the phone as "offline").
- **Slow SMS sending (being verified).** Once, after many hours of uptime, sending an SMS took
  minutes or needed retries; after a radio restart it was instant. The radio daemon could not take
  wake locks at the time (fixed in M3c); this is being re-checked once deep sleep works.

## Parked (disabled on purpose until their stage)

- **Camera**, **fingerprint**, **NFC**: disabled until their porting stages.
- **DRM (Widevine):** Android 15 needs a newer Widevine HAL than the one from the OnePlus 18.1
  release; disabled until then (it was restarting every few seconds).

## Fixed, not yet in a build

- (none)

## In the current build

- **Wi-Fi no longer wakes the phone for every broadcast packet.** The Wi-Fi driver registered a
  wake-up for each received packet (about 3 per second on a home network), which stopped any
  deep sleep. (M3d)
- **The radio daemon can take wake locks again.** On Android 15 its wake-lock requests went to
  the wrong service manager and all failed. (M3c)
- **The radio starts.** Libraries of the radio stack picked up Android 15's own copies of shared
  libraries and failed to load; IMEI, baseband, LTE data, calls and SMS now work. (M3b)
