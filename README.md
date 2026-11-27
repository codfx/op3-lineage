# OnePlus 3 LineageOS 22.2 (unofficial)

Project site for an unofficial LineageOS 22.2 (Android 15) port to the OnePlus 3, on a Linux 4.4
kernel: https://codfx.github.io/op3-lineage/

In development, not released. The text of this site is licensed under CC BY-SA 4.0 (see LICENSE).

## Project site

The project site is live, and M3e is frozen.

Site: https://codfx.github.io/op3-lineage/ (repo codfx/op3-lineage, public; Pages status "built")
- Pages: Home (status table), Known issues (Investigating / Parked / Fixed, not yet in a build / In the current build), Changelog (M1 → M3e), Porting notes. Plus README.md and LICENSE (CC BY-SA 4.0, as on the tablet site).
- Calls row: I changed it to "2G (circuit-switched fallback from LTE)", since our test calls actually ran on GSM.
- Privacy check: site-scan.sh runs as a pre-commit and pre-push hook. It covers your exact values, IPv4/IPv6/MAC, IMSI/ICCID/phone-number/IMEI shapes, the serials and the private repo names, in ASCII and UTF-16. I tested that it blocks a test file containing an IP, an IMEI and a private repo name. The first push scanned clean.
- Author: codfx <1727424+codfx@users.noreply.github.com>.
- Update rule: saved as a standing rule. The site gets updated in the same step as HANDOFF whenever a fix is tested or goes into a build.
