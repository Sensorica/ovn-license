# Compatibility: OVN License + Cryptographic Autonomy License 1.0

## Overview

The [Cryptographic Autonomy License 1.0](https://opensource.org/license/cal-1-0) (CAL-1.0) is an OSI-approved copyleft license designed for distributed and cryptographic applications, particularly Holochain hApps. It addresses two concerns that traditional copyleft licenses miss:

1. **Code autonomy** -- Users must be able to run the software independently, without depending on a third party's infrastructure.
2. **User data rights** -- Users must be able to access, possess, and move their own data processed by the software.

The OVN License addresses a different concern: **economic reciprocity** for contributors. These concerns are complementary, making dual-licensing a natural strategy.

## Compatibility Analysis

### Why Not a Single License?

Neither license alone covers both concerns:

- **CAL-1.0 alone** ensures code autonomy and user data rights but provides no mechanism for contributor compensation or benefit-sharing.
- **OVN License alone** ensures economic reciprocity but does not address user data autonomy or the specific needs of distributed applications.

### Dual-Licensing Strategy

A project can be offered under both licenses simultaneously, with each license governing different aspects:

- **CAL-1.0 governs:** Source code availability, user data rights, modification and distribution requirements, performance of the software as a service.
- **OVN License governs:** Economic reciprocity obligations, contribution tracking via the pie-chart, benefit distribution among contributors.

This is not an "OR" dual license (where users choose one). It is an "AND" dual license (where both apply, each to its domain).

### Potential Conflicts

| CAL-1.0 Requirement | OVN License Requirement | Conflict? |
|---------------------|------------------------|-----------|
| Source code availability | Source code + pie-chart availability | No -- OVN adds the pie-chart requirement |
| User data rights | No equivalent provision | No -- independent requirements |
| No additional restrictions (copyleft) | Economic reciprocity (0.5% / 2%) | Possible -- see below |

The main tension is that CAL-1.0's copyleft provision (derived from the concept of "no additional restrictions") could conflict with the OVN License's economic reciprocity clause. However, since the dual license explicitly states that both licenses apply, users accept both sets of obligations when they use the software. This is analogous to how software can be subject to both a license and a separate service agreement.

### Resolution

The recommended approach is to:

1. **State both licenses clearly** in the project's LICENSE file.
2. **Specify which license governs what** in a dual-license notice.
3. **Use the OVN pie-chart** as the mechanism for tracking contributions and distributing benefits.
4. **Rely on CAL-1.0** for code availability and user data rights.

## Practical Guidance for hApp Projects

### File Setup

```
your-happ/
  LICENSE-CAL-1.0            Full text of CAL-1.0
  LICENSE-OVN-1.0            Full text of OVN License v1.0
  LICENSE                    Dual-license notice (see template below)
  pie-chart.json             Contribution Pie-Chart
  ...
```

### Dual-License Notice Template

Include this in your `LICENSE` file or `README.md`:

```
This software is dual-licensed:

1. Cryptographic Autonomy License 1.0 (CAL-1.0)
   Governs: source code availability, user data rights, and
   distribution requirements.
   Full text: LICENSE-CAL-1.0

2. OVN License for Digital Resources v1.0
   Governs: economic reciprocity, contribution tracking, and
   benefit distribution among contributors.
   Full text: LICENSE-OVN-1.0
   Contribution Pie-Chart: pie-chart.json

Both licenses apply. Use of this software constitutes acceptance
of both licenses.
```

### Source File Headers

```rust
// This work is dual-licensed under:
// - Cryptographic Autonomy License 1.0 (CAL-1.0)
// - OVN License for Digital Resources v1.0
// See LICENSE files and accompanying Contribution Pie-Chart.
// Copyright (c) 2025 [Your Name or Organization]
```

## Examples

### Scenario: Commercial Platform Using a hApp

A company builds a marketplace platform using a CAL-1.0 + OVN dual-licensed hApp.

**CAL-1.0 obligations:**
- Provide source code to all users.
- Ensure users can export their data.
- Ensure users can run the hApp independently.

**OVN License obligations:**
- As a commercial entity, allocate at least 2% of material benefits derived from the hApp to contributors.
- Distribute according to the pie-chart.
- Maintain the pie-chart in any redistributions.

**Result:** The company can use the hApp commercially, provided it shares source code, respects user data rights, and shares 2% of derived benefits with contributors.

### Scenario: Community Fork

A community cooperative forks the hApp to add features for their members.

**CAL-1.0 obligations:**
- Release their modifications under CAL-1.0.
- Maintain user data rights.

**OVN License obligations:**
- Update the pie-chart to include new contributors.
- As a non-commercial entity, allocate at least 0.5% of any material benefits to contributors (original + new) per the updated pie-chart.

**Result:** The fork remains open, the original contributors continue to receive their share of benefits, and new contributors are recognized.
