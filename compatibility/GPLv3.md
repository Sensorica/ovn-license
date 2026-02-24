# Compatibility: OVN License + GNU General Public License v3

## Overview

This document clarifies the relationship between the OVN License for Digital Resources and the [GNU General Public License v3](https://www.gnu.org/licenses/gpl-3.0.html) (GPLv3). This is important because the OVN License preamble states it "builds on the GNU General Public License v3 (GPLv3)," which may create confusion about compatibility.

## Clarification: Standalone License, Not a GPLv3 Extension

**The OVN License is a standalone license.** Despite the preamble language, it:

- Does not incorporate GPLv3 terms by reference.
- Does not use GPLv3 section numbering.
- Does not include GPLv3's detailed provisions on patents, anti-circumvention, installation information, or network interaction.
- Adds economic reciprocity obligations that GPLv3 does not permit as additional terms.

The phrase "builds on" should be understood as "draws inspiration from" -- the OVN License shares GPLv3's philosophical commitment to software freedom and copyleft, but is structurally and legally independent.

This ambiguity is documented as a known issue in [CHANGELOG.md](../CHANGELOG.md) and will be addressed in a future revision.

## Compatibility Analysis

### The OVN License and GPLv3 are NOT Compatible

OVN-licensed code and GPLv3-licensed code **cannot be combined** into a single derivative work. The reason is straightforward:

**GPLv3 Section 7** lists the only additional terms that may be applied to GPLv3-covered code:

- (a) Warranty disclaimers
- (b) Liability limitations
- (c) Attribution requirements (limited)
- (d) Naming/trademark restrictions
- (e) Declining to grant patent rights
- (f) Indemnification requirements

The OVN License's economic reciprocity clause (Section 3) does not fit any of these categories. Under GPLv3 Section 7, paragraph 4: "If the Program as you received it [...] specifies that a certain numbered version of the GNU General Public License 'or any later version' applies to it, you have the option of following the terms and conditions either of that numbered version or of any later version published by the Free Software Foundation."

An economic reciprocity requirement would be classified as an "additional restriction" under GPLv3, which GPLv3 Section 7 states "you may remove."

### What This Means in Practice

| Scenario | Allowed? | Reason |
|----------|----------|--------|
| Using GPLv3 library in OVN project | No (combined work) | GPLv3 would require removing OVN's reciprocity clause |
| Using GPLv3 tool to build OVN project | Yes | Tool output is not a derivative of the tool |
| Side-by-side in same repository | Yes (aggregate) | Separate works distributed together |
| Linking GPLv3 and OVN code | No | Creates derivative work subject to GPLv3 |
| GPLv3 code as a separate service | Yes | Network communication, not linking |

### Bridge Component Approach

If your project must use GPLv3 dependencies, the same bridge component strategy described in [AGPLv3.md](AGPLv3.md) applies: separate the GPLv3 and OVN components with defined interfaces so they remain independent works.

## Frequently Asked Questions

### "If the OVN License builds on GPLv3, can I treat OVN-licensed code as GPLv3?"

No. The OVN License is not GPLv3 and does not grant GPLv3 rights. The "builds on" language describes philosophical inspiration, not legal derivation. Treating OVN-licensed code as GPLv3 would ignore the economic reciprocity obligations.

### "Can I relicense OVN-licensed code under GPLv3?"

Only if you are the sole copyright holder (or have permission from all copyright holders). The OVN License does not include a GPLv3 compatibility clause or a relicensing provision.

### "I have a GPLv3 project and want to add economic reciprocity. Can I just add the OVN License?"

No. You cannot add additional restrictions to GPLv3 code. You would need to either:

1. Relicense the entire project under the OVN License (requires consent of all copyright holders), or
2. Write new OVN-licensed components that interact with the GPLv3 code through a defined API (bridge component approach).

### "Will a future version of the OVN License be GPLv3-compatible?"

This is an open question. GPLv3 compatibility would require removing or fundamentally restructuring the economic reciprocity clause, which is the license's core feature. The authors consider economic reciprocity more important than GPLv3 compatibility. See [RATIONALE.md](../RATIONALE.md) for the design philosophy.

## Summary

The OVN License and GPLv3 are philosophically aligned but legally incompatible. The economic reciprocity clause is an "additional restriction" that GPLv3 does not permit. Projects must keep OVN-licensed and GPLv3-licensed code in separate components if both licenses are present.
