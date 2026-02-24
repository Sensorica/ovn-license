# Compatibility: OVN License v2.0 + GNU General Public License v3

## Overview

This document clarifies the relationship between the OVN License for Digital Resources v2.0 and the [GNU General Public License v3](https://www.gnu.org/licenses/gpl-3.0.html) (GPLv3).

## Clarification: Standalone License

**The OVN License is a standalone license.** v2.0 explicitly states it is "legally independent" from GPLv3 (Preamble and Section 11). The v1.0 language about "building on" GPLv3 has been removed. The OVN License:

- Does not incorporate GPLv3 terms by reference.
- Does not use GPLv3 section numbering.
- Does not include GPLv3's detailed provisions on patents, installation information, or network interaction.
- Adds an anti-circumvention clause (Section 5) protecting the Contribution Distribution Mechanism, which GPLv3 does not permit as an additional term.

The relationship is one of philosophical inspiration: both licenses share a commitment to software freedom and copyleft.

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

The OVN License's anti-circumvention clause (Section 5), which prohibits removing the Contribution Distribution Mechanism, does not fit any of these categories. Under GPLv3 Section 7, it would be classified as an "additional restriction" which GPLv3 states "you may remove."

Additionally, the requirement to maintain the Contribution Pie-Chart (Section 3) and the scope exclusion provisions (Section 6) introduce obligations not contemplated by GPLv3.

### What This Means in Practice

| Scenario | Allowed? | Reason |
|----------|----------|--------|
| Using GPLv3 library in OVN project | No (combined work) | GPLv3 would require removing OVN's anti-circumvention clause |
| Using GPLv3 tool to build OVN project | Yes | Tool output is not a derivative of the tool |
| Side-by-side in same repository | Yes (aggregate) | Separate works distributed together |
| Linking GPLv3 and OVN code | No | Creates derivative work subject to GPLv3 |
| GPLv3 code as a separate service | Yes | Network communication, not linking |

### Bridge Component Approach

If your project must use GPLv3 dependencies, the same bridge component strategy described in [AGPLv3.md](AGPLv3.md) applies: separate the GPLv3 and OVN components with defined interfaces so they remain independent works.

## Frequently Asked Questions

### "Can I treat OVN-licensed code as GPLv3?"

No. The OVN License is not GPLv3 and does not grant GPLv3 rights. Treating OVN-licensed code as GPLv3 would ignore the anti-circumvention obligations and the Contribution Pie-Chart requirement.

### "Can I relicense OVN-licensed code under GPLv3?"

Only if you are the sole copyright holder (or have permission from all copyright holders). The OVN License does not include a GPLv3 compatibility clause or a relicensing provision.

### "I have a GPLv3 project and want to add economic reciprocity. Can I just add the OVN License?"

No. You cannot add additional restrictions to GPLv3 code. You would need to either:

1. Relicense the entire project under the OVN License (requires consent of all copyright holders), or
2. Write new OVN-licensed components that interact with the GPLv3 code through a defined API (bridge component approach).

### "Will a future version of the OVN License be GPLv3-compatible?"

This is an open question. GPLv3 compatibility would require removing or fundamentally restructuring the anti-circumvention clause, which is the license's core innovation. The authors consider protocol-level economic reciprocity more important than GPLv3 compatibility. See [RATIONALE.md](../RATIONALE.md) for the design philosophy.

## Summary

The OVN License and GPLv3 are philosophically aligned but legally incompatible. The anti-circumvention clause and Contribution Pie-Chart requirement are "additional restrictions" that GPLv3 does not permit. Projects must keep OVN-licensed and GPLv3-licensed code in separate components if both licenses are present.
