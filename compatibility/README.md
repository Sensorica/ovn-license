# License Compatibility Analysis

This directory contains analyses of how the OVN License for Digital Resources v2.0 interacts with other software licenses. Each document examines a specific license, identifies compatibility issues, and provides practical guidance for projects that need to work with code under multiple licenses.

## Overview

| License | Compatible? | Strategy | Document |
|---------|-------------|----------|----------|
| **CAL-1.0** (Cryptographic Autonomy License) | Dual-license | CAL for code autonomy + OVN for reciprocity | [CAL-1.0.md](CAL-1.0.md) |
| **AGPLv3** (GNU Affero GPL) | No -- bridge components | Separate components with defined interfaces | [AGPLv3.md](AGPLv3.md) |
| **GPLv3** (GNU GPL) | No | Standalone license, not a GPLv3 extension | [GPLv3.md](GPLv3.md) |
| **MIT / Apache-2.0** | Inbound only | Permissive dependencies allowed in OVN projects | [MIT-Apache2.md](MIT-Apache2.md) |

## How to Read These Analyses

Each document follows a consistent structure:

1. **Overview** -- What the other license requires and how it relates to the OVN License.
2. **Compatibility Analysis** -- Specific clause-by-clause interactions and conflicts.
3. **Practical Guidance** -- What project maintainers should actually do.
4. **Examples** -- Concrete scenarios showing how the analysis applies in practice.

## Important Caveats

- **This is not legal advice.** These analyses reflect the authors' understanding of the license texts. Consult a lawyer before making licensing decisions for your project.
- **The OVN License is not OSI-approved.** Compatibility analysis is based on the license texts, not on any certification body's determination.
- **These analyses are for v2.0 of the OVN License.** The v2.0 license uses an anti-circumvention model (protecting the Contribution Distribution Mechanism) rather than the v1.0 percentage-based model. This changes the compatibility landscape in some cases.

## Contributing

If you identify errors in these analyses or want to add analysis for additional licenses, see [CONTRIBUTING.md](../CONTRIBUTING.md).
