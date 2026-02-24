# OVN License for Digital Resources

> **Status:** v2.0. This license is seeking community review from legal experts, open-source practitioners, and commons-oriented organizations. It has not been reviewed by a lawyer and is not OSI-approved. See [CHANGELOG.md](CHANGELOG.md) for version history and known issues.

## What Is This?

The OVN License for Digital Resources is a copyleft license designed for commons-based peer production. It ensures that software remains free and open while protecting a built-in Contribution Distribution Mechanism that directs value from transactional activity back to contributors, proportional to their contributions as recorded in a Contribution Pie-Chart.

Unlike traditional reciprocity models that rely on voluntary compliance, the OVN License is designed for software that includes its own economic distribution mechanism. The license provides legal protection against circumvention of that mechanism.

## Quick Start

To apply this license to your project:

1. **Copy `LICENSE.md`** into your project root.
2. **Create a `pie-chart.json`** file listing contributors, their shares, and roles. See [spec/contribution-pie-chart.md](spec/contribution-pie-chart.md) for the format and [spec/examples/](spec/examples/) for templates.
3. **Add a header** to each source file (or your README):
   ```
   This work is licensed under the OVN License for Digital Resources v2.0.
   Use of this work is subject to contribution distribution and anti-circumvention terms.
   See LICENSE and the accompanying Contribution Pie-Chart.
   SPDX-License-Identifier: LicenseRef-OVN-Digital-2.0
   Copyright (c) [year] [your name or organization]
   ```
4. **Implement the Contribution Distribution Mechanism** in your software. If the mechanism is not yet implemented, you can still adopt the license (see Section 4(d) of the license text). The anti-circumvention obligations in Section 5 activate when the mechanism is added.

## Key Concepts

- **Contribution Pie-Chart.** A machine-readable file that records each contributor's share of the project. It travels with the source code and governs value distribution. See the [specification](spec/contribution-pie-chart.md).

- **Contribution Distribution Mechanism.** A software component built into the Work that automatically captures a portion of value generated through transactional activity and distributes it to contributors per the pie-chart. This is a feature of the software, not a separate payment obligation.

- **Anti-Circumvention.** The core legal obligation: you may not remove, disable, or bypass the Contribution Distribution Mechanism. This is modeled on CAL-1.0's approach to protocol-level enforcement.

- **Scope Exclusions.** Development grants, internal non-transactional use, education, personal use, and interoperability testing are all excluded from economic obligations.

- **Good Faith and Safe Harbor.** 30-day cure period for non-compliance, good faith presumption for honest errors, technical safe harbor for mechanism failures, and a de minimis threshold for low-value transactions.

## Repository Contents

```
LICENSE.md                   The license text (v2.0)
README.md                    This file
CHANGELOG.md                 Version history and known issues
RATIONALE.md                 Design choices and legal context
CONTRIBUTING.md              How to propose changes

spec/
  contribution-pie-chart.md          Pie-Chart specification (draft v0.1)
  contribution-pie-chart.schema.json JSON Schema for validation
  examples/                          Example pie-chart files

compatibility/
  README.md                  Compatibility overview
  CAL-1.0.md                 Cryptographic Autonomy License analysis
  AGPLv3.md                  AGPL v3 interaction analysis
  GPLv3.md                   GPL v3 relationship clarification
  MIT-Apache2.md             Permissive license interactions

examples/
  holochain-happ/            Applying the license to a Holochain hApp
  python-service/            Applying the license to a Python service
  documentation/             Applying the license to documentation
```

## Related Projects

- **[Sensorica](https://www.sensorica.co/)** -- The Open Value Network that originated the principles behind this license.
- **[OVN Wiki](https://ovn.world/)** -- Documentation on OVN governance, contribution accounting, and the pie-chart concept.
- **[NRP-CAS](https://wiki.p2pfoundation.net/NRP-CAS)** -- Network Resource Planning / Contribution Accounting System, the software that pioneered contribution tracking in value networks.

## Contributing

We welcome contributions, especially from legal professionals, open-source license experts, and practitioners of commons-based peer production. See [CONTRIBUTING.md](CONTRIBUTING.md) for the process.

## License for This Repository

The contents of this repository (documentation, specification, examples) are licensed under [CC-BY-SA-4.0](https://creativecommons.org/licenses/by-sa/4.0/). The license text itself (`LICENSE.md`) may be freely copied and applied to your projects as described in Section 10 of the license.
