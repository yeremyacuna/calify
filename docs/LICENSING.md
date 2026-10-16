# ⚖️ Calify — Licensing Decision

**Status:** Decision pending. This document does not grant any license to use or redistribute unreleased software.

## The Two Requirements

1. Allow other students to use a safe, individually configured edition of Calify.
2. Determine whether third parties should be allowed to redistribute copies, publish derivatives, or create competing services.

These requirements must be resolved before selecting an open-source license.

## Common Options

| License Model | Use | Copy & Redistribution | Warranty / Liability |
|:------------:|:---:|:---------------------:|:--------------------:|
| MIT | Broad permission | Allowed, including commercial derivatives | Includes disclaimer and limitation |
| GPLv3 | Broad permission with copyleft | Allowed; distributed modified code generally remains open under GPL | Includes disclaimer and limitation |
| Source-available or proprietary terms | Defined by the author | Can be restricted in a custom agreement | Requires carefully reviewed terms |
| No license yet | No general software permission granted | Not generally permitted beyond legal exceptions/platform terms | No standard license disclaimer |

**Critical:** MIT and GPLv3 cannot be used to prohibit forks or redistribution. Open-source licenses generally permit both.

A limitation-of-liability clause reduces certain legal exposure but does not guarantee immunity from every claim, in every jurisdiction.

## Scope

Future choices should explicitly define coverage of source code, documentation, art/logo/trademarks, sample academic data, and distribution artifacts. Unpublished personal Production code must not be assumed licensed merely because project documentation is visible.

## Decision Needed

Choose between:

- **Open source:** permission to inspect, copy, modify and redistribute under conditions (MIT or GPLv3).
- **Restricted distribution:** students may use Calify but third-party redistribution or cloning requires permission (would need appropriately drafted terms).

See [GitHub's license selection guidance](https://choosealicense.com/) and consult a qualified legal professional if strong enforceable restrictions or particular liability protections are essential.
