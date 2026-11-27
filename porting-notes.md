---
layout: page
title: Porting notes
permalink: /porting-notes.html
---

Short technical notes for people porting other msm8996 devices.

**Kernel.** The OnePlus 3 shipped with a 3.18 kernel; this port uses a 4.4 msm8996 kernel with the
OnePlus drivers moved over (touch, display, audio amplifier and more). Several drivers behave
differently on 4.4 than on 3.18 and need attention.

**Vendor inside system.** The phone has no separate vendor partition, and the device uses the
legacy linker configuration: libraries are looked up in `/system` before `/vendor`. Any vendor
blob that needs a library whose name also exists in `/system` gets the system copy. Two cases
broke here: protobuf (the radio stack failed to start) and libhardware_legacy (wake locks failed).
Both are solved with uniquely named compatibility copies of the older libraries, as the LG G5 port
does.

**Radio.** Android 15 only accepts radio interface 1.4 or newer, which the OnePlus 18.1 radio stack
does not provide. The Qualcomm radio stack used by other msm8996 LineageOS 22.2 devices works
with the OnePlus 3's modem firmware; files that read or write the modem's storage partitions are
kept from the OnePlus 3's own release.

**Speaker amplifier.** The TFA9890 needs its OnePlus container converted for the newer driver, and
the driver checks the factory calibration, never writes it, and monitors the speaker continuously
(resistance window, temperature limit, alarms).

**Deep sleep.** A task stuck in an uninterruptible wait can't be frozen, so suspend never completes;
other wake-ups (fuel gauge, Wi-Fi) then only show up as the abort reason. Lowering
`/sys/power/pm_freeze_timeout` at runtime makes the kernel name the task that refuses to freeze.
