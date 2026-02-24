# OVN License for Digital Resources

> **Status:** v1.0 -- Early development. This license is a working draft seeking community review from legal experts, open-source practitioners, and commons-oriented organizations. It has not been reviewed by a lawyer and is not OSI-approved. See [CHANGELOG.md](CHANGELOG.md) for known issues.

## What Is This?

The OVN License for Digital Resources is a copyleft license designed for commons-based peer production. It ensures that software remains free and open while requiring users who derive material benefits to share a portion of those benefits with contributors, proportional to their contributions as recorded in a Contribution Pie-Chart.

## Quick Start

To apply this license to your project:

1. **Copy `LICENSE.md`** into your project root.
2. **Create a `pie-chart.json`** file listing contributors, their shares, and roles. See [spec/contribution-pie-chart.md](spec/contribution-pie-chart.md) for the format and [spec/examples/](spec/examples/) for templates.
3. **Add a header** to each source file (or your README):
   ```
   This work is licensed under the OVN License For Digital Resources v1.0
   Redistribution and Use require compliance with reciprocity terms.
   See LICENSE file and accompanying Contribution Pie-Chart.
   Copyright (c) [year] [your name or organization]
   ```

## Key Concepts

- **Contribution Pie-Chart** -- A machine-readable file that records each contributor's share of the project. It travels with the source code and governs benefit distribution. See the [specification](spec/contribution-pie-chart.md).

- **Reciprocity Tiers** -- The license distinguishes between non-commercial entities (cooperatives, nonprofits, commoners) who owe a minimum of 0.5% of material benefits, and commercial entities who owe at least 2%. Both tiers distribute according to the pie-chart.

- **Cure Period** -- If you violate the license terms, you have 30 days to cure the violation and have your rights reinstated by the contributor community. This encourages good-faith compliance over punitive enforcement.

## Repository Contents

```
LICENSE.md                   The license text (v1.0)
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
- **[NRP-CAS](https://speakerdeck.com/mikorizal/open-value-network-nrp-accounting)** -- Network Resource Planning / Contribution Accounting System, the software that pioneered contribution tracking in value networks.

## Contributing

We welcome contributions, especially from legal professionals, open-source license experts, and practitioners of commons-based peer production. See [CONTRIBUTING.md](CONTRIBUTING.md) for the process.

## License for This Repository

The contents of this repository (documentation, specification, examples) are licensed under [CC-BY-SA-4.0](https://creativecommons.org/licenses/by-sa/4.0/). The license text itself (`LICENSE.md`) may be freely copied and applied to your projects as described in Section 6 of the license.
