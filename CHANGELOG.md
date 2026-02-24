# Changelog

All notable changes to the OVN License for Digital Resources will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [2.0] - 2025-02-24

### Changed

- **Standalone license framing.** Removed the claim that the license "builds on GPLv3." The preamble now acknowledges GPLv3, the Peer Production License, and CAL-1.0 as philosophical inspirations only, explicitly stating the license is legally independent from all three. (Resolves v1.0 Known Issue 1.)

- **Protocol-level economic reciprocity.** Replaced the percentage-based honor system (0.5% non-commercial, 2% commercial) with a protocol-enforcement model. The license now describes a Contribution Distribution Mechanism built into the software that captures value during Transactional Activity automatically. The license protects this mechanism from circumvention rather than imposing external payment obligations. (Resolves v1.0 Known Issue 3.)

- **Anti-circumvention as core legal mechanism.** Added Section 5 (Anti-Circumvention) prohibiting removal, disabling, or bypassing of the Contribution Distribution Mechanism. Modeled on CAL-1.0 Section 4.2.2 but applied to economic distribution rather than user autonomy.

- **Tightened definitions.** Replaced "Material Benefits" (too vague) with "Transactional Activity" (exchange of economic value in a market context). Added definitions for Contribution Distribution Mechanism, Source Code, Recipient, You/Your, and Modify/Modified Version. Removed "Non-Commercial Entities," "Commercial Entities," and "Material Benefits." (Resolves v1.0 Known Issue 2.)

- **Removed commercial/non-commercial distinction.** When the Contribution Distribution Mechanism applies uniformly to all Transactional Activity, the organizational form of the user is irrelevant. The PPL-inspired entity classification has been removed entirely.

- **Explicit copyleft.** Section 3 now explicitly requires Modified Versions to be distributed under the same License (v1.0 implied but did not state this clearly). Added source code access requirement. Added protection against removal of existing Contributors from the Contribution Pie-Chart without consent.

- **Fixed SPDX identifier.** Changed from `OVN Digital-1.0` (invalid, contains space) to `LicenseRef-OVN-Digital-2.0` (valid per SPDX specification for non-registered licenses). (Resolves v1.0 Known Issue 5.)

- **Expanded warranty and liability section.** Section 9 now includes full warranty disclaimer, limitation of liability, and a mechanism-specific disclaimer stating the Contribution Distribution Mechanism carries no warranty of error-free operation.

- **Updated section structure.** Expanded from 7 sections (numbered 0-6) to 12 sections (numbered 1-11 with preamble). Section numbering now starts at 1 per standard convention.

### Added

- **Section 4: Protocol Economics.** Describes the three-layer enforcement model (protocol mechanics, network validation, legal backstop). Includes a "soft launch" provision for projects that adopt the license before implementing the mechanism.

- **Section 5: Anti-Circumvention.** Five subsections: no removal, no disabling, no bypassing, no contractual override, and parameter modification rules. This is the core legal innovation of v2.0.

- **Section 6: Scope Exclusions.** Explicitly states that development and improvement (including grant-funded work), non-transactional internal use, education and research, personal use, and interoperability testing are all excluded from economic obligations.

- **Section 7: Good Faith and Safe Harbor.** Good faith presumption for unintentional errors; 30-day cure period (retained from v1.0); notification requirement before enforcement; technical safe harbor for mechanism failures; de minimis threshold for low-value Transactional Activity.

- **"Or any later version" provision.** Section 10 allows licensors to specify "v2.0 or any later version" for forward compatibility.

- **CAL-1.0 reference in inspirations.** Section 11 now acknowledges CAL-1.0's contribution to the protocol-level enforcement concept.

### Removed

- **Fixed percentage tiers.** The 0.5% non-commercial and 2% commercial rates are no longer in the license text. Distribution parameters are now determined by the Work's implementation and governed through the Contribution Pie-Chart governance process.

- **Commercial/non-commercial entity definitions.** These entity classifications have been removed from the license entirely.

- **"Material Benefits" definition.** Replaced by "Transactional Activity" which provides a clearer trigger for when economic obligations apply.

- **GPLv3 derivation language.** The phrase "builds on the GNU General Public License v3" has been removed.

### Known Issues

1. **Enforceability of anti-circumvention across jurisdictions.** The anti-circumvention clause is modeled on copyright license conditions. Enforceability may vary across jurisdictions, particularly between common-law and civil-law systems. This is a shared challenge with all copyleft licenses and is not unique to this license.

2. **"Functionally equivalent to zero" boundary.** Section 5(e) prohibits setting the distribution to zero or "a value so low as to be functionally equivalent to zero." The exact boundary of this phrase will require case-by-case judgment and may benefit from interpretive guidance.

3. **Transactional Activity boundary cases.** Some activities (freemium models with mixed free/paid transactions, advertising-supported use, speculative token systems) may be ambiguous. The definition focuses on "exchange of economic value in a market context" but edge cases exist.

4. **Projects without a mechanism.** The "soft launch" provision (Section 4(d)) allows adoption before the mechanism is built, but a bad-faith actor could adopt the license and never implement the mechanism. This is a governance challenge, not a legal one.

5. **Pie-Chart Specification version.** The pie-chart specification (draft v0.1) references v1.0 section numbers. It should be updated to reference v2.0 sections.

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

### Known Issues (v1.0, resolved in v2.0)

1. **GPLv3 Framing Ambiguity** -- Resolved in v2.0: license is now explicitly standalone with inspirations acknowledged.
2. **Definition Precision** -- Resolved in v2.0: "Material Benefits" replaced by "Transactional Activity"; entity classifications removed.
3. **Reciprocity Mechanism Gaps** -- Resolved in v2.0: replaced honor-system percentages with protocol-level enforcement and anti-circumvention.
4. **Unspecified Pie-Chart Format** -- Addressed separately: draft specification at spec/contribution-pie-chart.md.
5. **Invalid SPDX Syntax** -- Resolved in v2.0: corrected to `LicenseRef-OVN-Digital-2.0`.
