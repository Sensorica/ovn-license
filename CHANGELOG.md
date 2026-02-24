# Changelog

All notable changes to the OVN License for Digital Resources will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [1.0] - 2025-01-01

### Added
- Initial release of the OVN License for Digital Resources.
- Definitions for Work, Contributor, Contribution Pie-Chart, Use, Non-Commercial Entities, Commercial Entities, and Material Benefits (Section 0).
- License grant for any purpose subject to conditions (Section 1).
- Redistribution obligations requiring license and pie-chart inclusion (Section 2).
- Economic reciprocity tiers: 0.5% minimum for non-commercial entities, 2% minimum for commercial entities (Section 3).
- Automatic termination on violation with 30-day cure period (Section 4).
- No warranty disclaimer (Section 5).
- Application instructions with header template (Section 6).
- Reference materials linking to GPLv3, Peer Production License, and OVN Wiki.

### Known Issues

The following issues are documented for transparency and will be addressed in future versions:

1. **GPLv3 Framing Ambiguity** -- The preamble states the license "builds on the GNU General Public License v3 (GPLv3)" but does not incorporate GPLv3 terms by reference, does not include GPLv3 section numbering, and adds obligations (economic reciprocity) that conflict with GPLv3 Section 7. This creates confusion about whether works under this license are GPLv3-compatible. Clarification: this license is standalone and GPLv3-inspired, not a GPLv3 extension. See [RATIONALE.md](RATIONALE.md) for details.

2. **Definition Precision** -- Several definitions would benefit from greater precision:
   - "Material Benefits" includes "monetizable advantage" which is broad and difficult to measure.
   - "Non-Commercial Entities" lists specific organizational types but the boundary between non-commercial and commercial use is not always clear (e.g., a cooperative selling software).
   - "Use" covers a broad range of activities; not all should trigger economic reciprocity (e.g., personal use with no material benefit).

3. **Reciprocity Mechanism Gaps** -- The license requires benefit allocation but does not specify:
   - How "Material Benefits" are calculated or reported.
   - What "transparently and in good faith" means in practice.
   - Who verifies compliance or adjudicates disputes.
   - Payment frequency, methods, or minimum thresholds for triggering payment.

4. **Unspecified Pie-Chart Format** -- The license references a "Contribution Pie-Chart" but v1.0 does not define its format, required fields, or validation rules. A draft specification is provided separately in [spec/contribution-pie-chart.md](spec/contribution-pie-chart.md).

5. **Invalid SPDX Syntax** -- The SPDX identifier `OVN Digital-1.0` contains a space, which is not valid SPDX syntax. The correct format for a custom identifier would be `LicenseRef-OVN-Digital-1.0`. This will be corrected in a future version; the v1.0 text is preserved as-is for the initial release.
