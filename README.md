# US Carrier Call-Forwarding Codes

A maintained dataset of call-forwarding activation and deactivation codes for US phone carriers: no-answer forwarding, busy forwarding, forward-all, and the portal paths for carriers that have no self-serve dial codes.

Small businesses use these codes to send missed calls to an answering service, a receptionist, a co-worker's cell, or a call center. The information is scattered across carrier support sites, often outdated, and sometimes wrong for a specific line type (wireless vs copper landline vs digital voice vs VoIP). This repo keeps it in one machine-readable place.

## Data

- [`data/forwarding-codes.json`](data/forwarding-codes.json): structured entries per carrier: codes by forwarding type, portal paths, and caveats.

`NUMBER10` in a code means the 10-digit destination number (digits only). `NUMBER11` means the 11-digit form starting with 1.

## Quick reference

| Carrier | Forward missed calls (no answer) | Forward every call | Turn off |
|---|---|---|---|
| Verizon wireless | `*71` + number | `*72` + number | `*73` |
| AT&T wireless | `**004*1` + number + `#` (no answer, busy, unreachable); `*61*1` + number + `#` (no answer only) | `*21*1` + number + `#` | `##004#` / `#61#` / `#21#` |
| T-Mobile | `**004*1` + number + `#` (no answer, busy, unreachable); `**61*1` + number + `#` (no answer only) | `**21*1` + number + `#` | `##004#` / `##61#` / `##21#` |
| Verizon landline | `*92` | n/a | `*93` (`*91` for busy) |
| AT&T U-verse | `*92` + number + `#` | `*72` + number + `#` | `*93#` / `*73#` |
| AT&T landline | agent-enabled (800.288.2020) | `*72` + number | `*73` |
| Xfinity Voice (home) | portal only | `*72` | `*73` |
| Comcast Business Voice / VoiceEdge | `*92`, number at the second dial tone | `*72` + number | `*93` / `*73` |
| Blue Ridge | not offered | `*72`, press `1`, 11-digit number, `#` | `*72`, press `1` again (toggle) |
| Spectrum (home) | portal only | `*72` + number | `*73` |
| Spectrum Business | `*92` + number + `#` (`*90` busy) | `*72` + number | `*93` (`*91` busy) / `*73` |
| CenturyLink (Lumen) business | `*92`, number at the dial tone (feature must be on the line) | `*72` + number | `*93` / `*73` |
| Vonage | portal only | `*72` | `*73` |

VoIP services (Google Voice, RingCentral, Grasshopper/OpenPhone/Dialpad and other hosted systems) configure forwarding in their app instead of dial codes; see the JSON for exact paths and caveats. Google Voice specifically does not support forwarding to automated systems; the supported route is via the linked cell's carrier code.

## Why forward missed calls

On the contractor lines OnCrew answers, 33.4% of conversations arrive outside weekday business hours (16.5% on weekday evenings and early mornings, 16.9% on weekends), 15.1% are emergencies, and 29.7% end with the caller asking to be called back. That is 910 inbound conversations of 12 seconds or longer over the 120 days to October 2, 2026, on the lines of the five contractors who have paid for OnCrew (HVAC, plumbing and roofing); on the two HVAC-and-plumbing shops, 36.9% arrived after hours and 20.9% were emergencies. Method and exclusions: [oncrew.ai/resources/missed-call-statistics](https://oncrew.ai/resources/missed-call-statistics#first-party). One vendor's lines, not a market sample.

## Verification

Each entry names its source in the JSON; most are the carrier's own published support documentation (CenturyLink's comes from answering-service onboarding guides). Last full review: 2026-10-03. Corrections welcome by issue or PR, ideally with a link to the carrier doc.

## License and attribution

Data is released under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Attribute "OnCrew" with a link to this repo or to [oncrew.ai](https://oncrew.ai).

Maintained by [OnCrew](https://oncrew.ai), the AI receptionist for HVAC, plumbing, and electrical companies. These codes power OnCrew's carrier-specific setup guides, and this dataset is published so nobody has to re-research them.
