# ⚖️ Calify — Licensing Decision

**Status:** Decision pending. This document does not grant any license to use or redistribute unreleased software.

## The Two Requirements

1. Allow other students to use a safe, individually configured edition of Calify.
2. Determine whether third parties should be allowed to redistribute copies, publish derivatives, or create competing services.

These requirements must be resolved before selecting an open-source license.

## Common Options

<div align="center">
<table align="center">
<thead><tr><th align="center">License Model</th><th align="center">Use</th><th align="center">Copy &amp; Redistribution</th><th align="center">Warranty / Liability</th></tr></thead>
<tbody>
<tr><td align="center">MIT</td><td align="center">Broad permission</td><td align="center">Allowed, including commercial derivatives</td><td align="center">Includes disclaimer and limitation</td></tr>
<tr><td align="center">GPLv3</td><td align="center">Broad permission with copyleft</td><td align="center">Allowed; distributed modified code generally remains open under GPL</td><td align="center">Includes disclaimer and limitation</td></tr>
<tr><td align="center">Source-available or proprietary terms</td><td align="center">Defined by the author</td><td align="center">Can be restricted in a custom agreement</td><td align="center">Requires carefully reviewed terms</td></tr>
<tr><td align="center">No license yet</td><td align="center">No general software permission granted</td><td align="center">Not generally permitted beyond legal exceptions/platform terms</td><td align="center">No standard license disclaimer</td></tr>
</tbody>
</table>
</div>


**Critical:** MIT and GPLv3 cannot be used to prohibit forks or redistribution. Open-source licenses generally permit both.

A limitation-of-liability clause reduces certain legal exposure but does not guarantee immunity from every claim, in every jurisdiction.

## Scope

Future choices should explicitly define coverage of source code, documentation, art/logo/trademarks, sample academic data, and distribution artifacts. Unpublished personal Production code must not be assumed licensed merely because project documentation is visible.

## Decision Needed

Choose between:

- **Open source:** permission to inspect, copy, modify and redistribute under conditions (MIT or GPLv3).
- **Restricted distribution:** students may use Calify but third-party redistribution or cloning requires permission (would need appropriately drafted terms).

See [GitHub's license selection guidance](https://choosealicense.com/) and consult a qualified legal professional if strong enforceable restrictions or particular liability protections are essential.
