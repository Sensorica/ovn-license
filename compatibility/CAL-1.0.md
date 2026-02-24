# Compatibility: OVN License v2.0 + Cryptographic Autonomy License 1.0

## Overview

The [Cryptographic Autonomy License 1.0](https://opensource.org/license/cal-1-0) (CAL-1.0) is an OSI-approved copyleft license designed for distributed and cryptographic applications, particularly Holochain hApps. It addresses two concerns that traditional copyleft licenses miss:

1. **Code autonomy** -- Users must be able to run the software independently, without depending on a third party's infrastructure.
2. **User data rights** -- Users must be able to access, possess, and move their own data processed by the software.

The OVN License v2.0 addresses a different concern: **economic reciprocity** for contributors, enforced through an anti-circumvention clause protecting the Contribution Distribution Mechanism. These concerns are complementary, making dual-licensing a natural strategy.

## Compatibility Analysis

### Why Not a Single License?

Neither license alone covers both concerns:

- **CAL-1.0 alone** ensures code autonomy and user data rights but provides no mechanism for contributor compensation or benefit-sharing.
- **OVN License alone** ensures economic reciprocity but does not address user data autonomy or the specific needs of distributed applications.

### Dual-Licensing Strategy

A project can be offered under both licenses simultaneously, with each license governing different aspects:

- **CAL-1.0 governs:** Source code availability, user data rights, modification and distribution requirements, performance of the software as a service.
- **OVN License governs:** Anti-circumvention of the Contribution Distribution Mechanism, contribution tracking via the pie-chart, value distribution among contributors.

This is not an "OR" dual license (where users choose one). It is an "AND" dual license (where both apply, each to its domain).

### Anti-Circumvention Complementarity

The v2.0 anti-circumvention clause (Section 5) and CAL-1.0 Section 4.2.2 operate in complementary directions:

- **CAL-1.0 Section 4.2.2** prohibits cryptographic measures that limit a Recipient's ability to access functionality. This ensures Recipients can access the Contribution Distribution Mechanism.
- **OVN License Section 5** prohibits removing, disabling, or bypassing the Contribution Distribution Mechanism. This ensures the mechanism cannot be stripped from redistributed versions.

Together, they create a strong pairing: CAL-1.0 guarantees access to the mechanism, and the OVN License guarantees the mechanism's presence. Neither contradicts the other.

### Potential Conflicts

| CAL-1.0 Requirement | OVN License v2.0 Requirement | Conflict? |
|---------------------|------------------------------|-----------|
| Source code availability | Source code + pie-chart availability | No -- OVN adds the pie-chart requirement |
| User data rights | No equivalent provision | No -- independent requirements |
| No additional restrictions (copyleft) | Anti-circumvention of distribution mechanism | See below |

The main tension is that CAL-1.0's copyleft provision could conflict with the OVN License's anti-circumvention clause. However, since the dual license explicitly states that both licenses apply, users accept both sets of obligations when they use the software. The anti-circumvention clause protects a software feature (the mechanism) rather than imposing an external payment obligation, which makes it structurally closer to copyleft (maintaining a feature in redistributions) than to a royalty.

### Resolution

The recommended approach is to:

1. **State both licenses clearly** in the project's LICENSE file.
2. **Specify which license governs what** in a dual-license notice.
3. **Use the OVN pie-chart** as the mechanism for tracking contributions and distributing value.
4. **Rely on CAL-1.0** for code availability and user data rights.

## Practical Guidance for hApp Projects

### File Setup

```
your-happ/
  LICENSE-CAL-1.0            Full text of CAL-1.0
  LICENSE-OVN-2.0            Full text of OVN License v2.0
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

2. OVN License for Digital Resources v2.0
   Governs: contribution distribution mechanism protection,
   contribution tracking, and value distribution among contributors.
   Full text: LICENSE-OVN-2.0
   Contribution Pie-Chart: pie-chart.json

Both licenses apply. Use of this software constitutes acceptance
of both licenses.
```

### Source File Headers

```rust
// This work is dual-licensed under:
// - Cryptographic Autonomy License 1.0 (CAL-1.0)
// - OVN License for Digital Resources v2.0
// See LICENSE files and accompanying Contribution Pie-Chart.
// SPDX-License-Identifier: CAL-1.0 AND LicenseRef-OVN-Digital-2.0
// Copyright (c) [year] [Your Name or Organization]
```

## Examples

### Scenario: Commercial Platform Using a hApp

A company builds a marketplace platform using a CAL-1.0 + OVN dual-licensed hApp that includes a Contribution Distribution Mechanism.

**CAL-1.0 obligations:**
- Provide source code to all users.
- Ensure users can export their data.
- Ensure users can run the hApp independently.

**OVN License obligations:**
- Do not remove, disable, or bypass the Contribution Distribution Mechanism.
- Maintain the pie-chart in any redistributions.
- Any parameter modifications must go through the authorized governance process.

**Result:** The company can use the hApp commercially. The Contribution Distribution Mechanism captures and distributes value automatically during transactions. The company must not tamper with this mechanism.

### Scenario: Community Fork

A community cooperative forks the hApp to add features for their members.

**CAL-1.0 obligations:**
- Release their modifications under CAL-1.0.
- Maintain user data rights.

**OVN License obligations:**
- Keep the Contribution Distribution Mechanism intact (Section 5).
- Update the pie-chart to include new contributors (Section 3(d)).
- Distribution parameters may be adjusted through the governance process, but the mechanism itself must remain functional (Section 5(e)).

**Result:** The fork remains open, the mechanism continues to operate, original contributors continue to receive their share, and new contributors are recognized in the updated pie-chart.
