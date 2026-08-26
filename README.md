# US Carrier Call-Forwarding Codes

A maintained dataset of call-forwarding activation and deactivation codes for US phone carriers: no-answer forwarding, busy forwarding, forward-all, and the portal paths for carriers that have no self-serve dial codes.

Small businesses use these codes to send missed calls to an answering service, a receptionist, a co-worker's cell, or a call center. The information is scattered across carrier support sites, often outdated, and sometimes wrong for a specific line type (wireless vs copper landline vs digital voice vs VoIP). This repo keeps it in one machine-readable place.

## Data

- [`data/forwarding-codes.json`](data/forwarding-codes.json) — structured entries per carrier: codes by forwarding type, portal paths, and caveats.

`NUMBER10` in a code means the 10-digit destination number (digits only). `NUMBER11` means the 11-digit form starting with 1.

## Quick reference

| Carrier | Forward missed calls (no answer) | Forward every call | Turn off |
|---|---|---|---|
| Verizon wireless | `*71` + number | `*72` + number | `*73` |
| AT&T wireless | `*61*1` + number + `#` | `*21*1` + number + `#` | `#61#` / `#21#` |
| T-Mobile | `**61*1` + number + `#` | — | `##61#` (or `##004#` reset) |
| Verizon landline | `*92` | — | `*93` (`*91` for busy) |
| AT&T U-verse | `*92` + number + `#` | `*72` + number + `#` | `*93#` / `*73#` |
| AT&T landline | agent-enabled (800.288.2020) | `*72` + number | `*73` |
| Xfinity Voice | portal only | `*72` | `*73` |
| Blue Ridge | not offered | `*72`, press `1`, 11-digit number, `#` | `*72`, press `1` again (toggle) |
| Spectrum | portal only | `*72` + number | `*73` |
| Vonage | portal only | `*72` | `*73` |

VoIP services (Google Voice, RingCentral, Grasshopper/OpenPhone/Dialpad and other hosted systems) configure forwarding in their app instead of dial codes; see the JSON for exact paths and caveats. Google Voice specifically does not support forwarding to automated systems; the supported route is via the linked cell's carrier code.

## Verification

Every entry is checked against the carrier's own published support documentation. Last full review: 2026-08-25. Corrections welcome by issue or PR, ideally with a link to the carrier doc.

## License and attribution

Data is released under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Attribute "OnCrew" with a link to this repo or to [oncrew.ai](https://oncrew.ai).

Maintained by [OnCrew](https://oncrew.ai), the AI receptionist for HVAC, plumbing, and electrical companies. These codes power OnCrew's carrier-specific setup guides, and this dataset is published so nobody has to re-research them.
