# Design Rationale

This document explains why the OVN License for Digital Resources is structured the way it is, what problems it attempts to solve, and where it sits in relation to existing licenses. It is intended for reviewers evaluating the license and for downstream adopters deciding whether the license fits their needs.

## Purpose of This License

Traditional open-source licenses guarantee freedoms to use, study, modify, and distribute software. They do not address the economic reality that contributors to commons-based projects often receive no material return for their work, while downstream users -- particularly commercial entities -- may derive significant value.

The OVN License attempts to bridge this gap by adding an economic reciprocity layer to a copyleft foundation. Its goal is not to restrict use but to ensure that material benefits flow back to contributors in proportion to their contributions.

## Design Goals

1. **Copyleft + Reciprocity** -- Maintain the four freedoms (use, study, modify, distribute) while adding an obligation to share material benefits. The copyleft ensures the code remains open; the reciprocity ensures contributors are compensated.

2. **Tiered Obligations** -- Recognize that different types of users have different capacities. A community cooperative and a multinational corporation should not bear the same reciprocity burden. The tiered structure (0.5% non-commercial, 2% commercial) reflects this.

3. **Transparent Contribution Tracking** -- The Contribution Pie-Chart provides a verifiable, machine-readable record of who contributed what. This removes ambiguity about benefit distribution and enables automation.

4. **Cure-First Enforcement** -- The 30-day cure period encourages good-faith compliance over adversarial enforcement. This reflects the cooperative values of the communities the license serves.

## What This License Is NOT

- **Not a GPLv3 extension.** Despite the preamble's language about "building on" GPLv3, this license is a standalone document. It does not incorporate GPLv3 terms by reference and adds obligations (economic reciprocity) that are incompatible with GPLv3 Section 7's restrictions on additional terms. See "Relationship to GPLv3" below.

- **Not anti-commercial.** Commercial use is explicitly permitted. The license only requires that commercial users share a portion of material benefits with contributors. This is analogous to a royalty, not a prohibition.

- **Not a Contributor License Agreement (CLA).** The pie-chart records contributions for benefit distribution purposes. It does not transfer copyright, grant additional patent rights, or change the licensing terms. Contributors retain their copyright.

- **Not OSI-approved.** The economic reciprocity clauses likely conflict with the Open Source Definition, specifically OSD criteria 1 (Free Redistribution) and 6 (No Discrimination Against Fields of Endeavor). See "OSI Compatibility" below.

## Relationship to GPLv3

The license preamble states it "builds on the GNU General Public License v3 (GPLv3)." This language was chosen to signal the license's philosophical lineage -- it shares GPLv3's commitment to software freedom and copyleft. However, the relationship is one of inspiration, not incorporation.

**Key differences from GPLv3:**

- **Economic reciprocity** -- GPLv3 has no mechanism for requiring payment or benefit-sharing. GPLv3 Section 7 explicitly limits the additional terms that can be added, and an economic reciprocity clause would not fit within those limits.
- **Tiered user classes** -- GPLv3 does not distinguish between commercial and non-commercial users. All users have the same rights and obligations.
- **Contribution tracking** -- GPLv3 has no equivalent of the Contribution Pie-Chart. Copyright notices serve a different purpose.
- **Simplified structure** -- The OVN License has 7 sections compared to GPLv3's 17. It omits GPLv3's detailed provisions on patents, anti-circumvention, installation information, and network interaction.

**Why this matters:** A work licensed under the OVN License cannot be combined with GPLv3-licensed code in a single derivative work, because the economic reciprocity clause would constitute an "additional restriction" under GPLv3 Section 7. See [compatibility/GPLv3.md](compatibility/GPLv3.md) for details.

**Future direction:** The preamble language should be revised in a future version to clarify that the license is inspired by, not built on, GPLv3.

## Relationship to the Peer Production License

The [Peer Production License](https://wiki.p2pfoundation.net/Peer_Production_License) (PPL), created by Dmytri Kleiner, introduced the concept of differentiated licensing based on the user's organizational form. The PPL permits free use by worker-owned cooperatives, nonprofits, and commoners, while requiring commercial entities to negotiate a separate license.

The OVN License adopts the PPL's core principle -- that commons-produced resources should benefit their producers -- but differs in several ways:

- **Graduated instead of binary.** The PPL draws a sharp line: non-commercial use is free, commercial use requires negotiation. The OVN License uses a graduated approach with specific percentage thresholds (0.5% and 2%), allowing commercial use without negotiation while still ensuring reciprocity.
- **Quantified obligations.** The PPL leaves commercial terms to negotiation. The OVN License specifies minimum percentages, reducing uncertainty for adopters and users.
- **Contribution tracking.** The PPL does not address how benefits are distributed among contributors. The OVN License requires a Contribution Pie-Chart that makes distribution transparent and verifiable.
- **Cure period.** The PPL does not include a cure mechanism. The OVN License provides 30 days to remedy violations, reflecting a preference for compliance over punishment.

## Relationship to the Cryptographic Autonomy License (CAL-1.0)

The [Cryptographic Autonomy License](https://opensource.org/license/cal-1-0) (CAL-1.0) is an OSI-approved license designed for distributed and cryptographic applications, particularly Holochain. It addresses a gap that traditional copyleft licenses miss: user data autonomy in peer-to-peer systems.

The OVN License and CAL-1.0 are complementary, not competing:

- **CAL-1.0 covers code autonomy and user data rights** -- ensuring users can access their own data and run the software independently.
- **OVN License covers contribution tracking and economic reciprocity** -- ensuring contributors receive a share of material benefits.

For Holochain hApp projects, dual-licensing under both CAL-1.0 and the OVN License is the recommended approach. See [compatibility/CAL-1.0.md](compatibility/CAL-1.0.md) for practical guidance.

## Why 0.5% and 2% Thresholds

The reciprocity percentages are among the most scrutinized aspects of the license. Here is the reasoning behind each:

### 0.5% for Non-Commercial Entities

- **Low enough to be affordable.** A 0.5% allocation from a cooperative's revenue derived from the software is unlikely to create financial hardship. For a cooperative earning $10,000/year from a product using the software, this is $50/year.
- **High enough to be meaningful.** At scale, even small percentages create a sustainable funding stream for contributors. If 100 cooperatives each contribute $50/year, that is $5,000/year flowing to contributors.
- **Acknowledges solidarity.** Non-commercial entities often operate within the same commons ecosystem as contributors. The lower rate reflects their alignment with commons values while still establishing the principle of reciprocity.

### 2% for Commercial Entities

- **Proportional to capacity.** Commercial entities deriving profit from commons-produced software have greater capacity to contribute back. A 2% allocation is modest compared to typical software licensing costs or SaaS margins.
- **Competitive with alternatives.** Many commercial open-source models involve dual licensing where commercial use requires a paid license. A 2% reciprocity rate is likely lower than what most commercial licenses would charge.
- **Not punitive.** The rate is designed to be sustainable, not prohibitive. A commercial entity earning $1,000,000/year from a product using the software would owe $20,000/year -- meaningful for contributors but not burdensome for the business.

### Why Not Higher or Lower?

- **Higher rates** risk discouraging adoption, particularly for early-stage commercial products where margins are thin. The goal is widespread use with sustainable reciprocity, not maximum extraction.
- **Lower rates** risk being negligible -- not worth the administrative overhead to track and distribute. The current rates are the minimum that can create meaningful contributor income at moderate scale.
- **These rates are starting points.** Community feedback may lead to adjustments in future versions. The important principle is that rates exist and are explicit, not that these specific numbers are optimal.

## Why the Pie-Chart Requirement

The Contribution Pie-Chart is the mechanism that distinguishes the OVN License from other reciprocity-oriented licenses. It draws on two sources:

### OVN Principles

Open Value Networks use contribution accounting as a foundational governance mechanism. The principle is that value flows should be transparent, verifiable, and proportional to contribution. The pie-chart makes this principle enforceable at the license level.

### NRP-CAS Precedent

The Network Resource Planning / Contribution Accounting System (NRP-CAS), developed by Sensorica and the Mikorizal Software collective, demonstrated that contribution tracking in open networks is technically feasible. NRP-CAS tracked contributions across multiple value streams with granular accounting. The pie-chart is a simplified, portable version of this concept -- one that can travel with source code rather than depending on a centralized platform.

### Why Machine-Readable?

A machine-readable format (JSON as canonical, with YAML/TOML as authoring alternatives) enables:

- **Automated validation** -- CI/CD pipelines can verify pie-chart integrity.
- **Automated distribution** -- Payment systems can read the pie-chart and distribute benefits without manual intervention.
- **On-chain verification** -- For Holochain and other distributed systems, the pie-chart can be validated by smart contracts or zome functions.
- **Tooling ecosystem** -- Editors, visualizers, and auditing tools can work with a standardized format.

## OSI Compatibility

The OVN License is likely incompatible with the [Open Source Definition](https://opensource.org/osd) (OSD) as maintained by the Open Source Initiative. Specifically:

- **OSD Criterion 1 (Free Redistribution)** -- The OSD requires that the license "shall not require a royalty or other fee for such sale." The economic reciprocity clause requires a percentage of material benefits, which could be interpreted as a royalty.

- **OSD Criterion 6 (No Discrimination Against Fields of Endeavor)** -- The OSD requires that the license "must not restrict anyone from making use of the program in a specific field of endeavor." The different rates for commercial vs. non-commercial entities could be seen as discriminatory, although the license permits all uses -- it only differentiates the reciprocity obligation.

**This is an intentional design choice.** The OVN License prioritizes contributor sustainability over OSI compliance. The authors believe that the open-source ecosystem's failure to address contributor compensation is a systemic problem, and that licenses must evolve to address it. OSI compatibility is desirable but not at the cost of the license's core purpose.

**Practical impact:** Projects using the OVN License cannot claim to be "OSI-approved open source." They can accurately describe themselves as "free software with economic reciprocity" or "commons-licensed."

## Open Questions for Community Review

The following questions remain open and would benefit from community input:

1. **Material Benefits calculation** -- How should "Material Benefits" be calculated in practice? Is gross revenue the right base, or should it be net profit, or something else? What about indirect benefits like increased customer acquisition?

2. **Compliance verification** -- Who verifies that users are meeting their reciprocity obligations? Should there be an audit mechanism, or is good-faith self-reporting sufficient?

3. **Threshold triggers** -- Should there be a minimum revenue threshold below which the reciprocity obligation does not apply (a de minimis exception)? This would reduce the burden on very small users.

4. **Pie-chart governance** -- Who has authority to update the pie-chart? What happens when contributors disagree about shares? The current spec proposes a dispute resolution process, but should this be part of the license itself?

5. **Interaction with employment** -- If a contributor is employed and contributes as part of their job, does their employer receive their share? Or does the individual contributor receive it?

6. **International enforcement** -- How does the license interact with different legal jurisdictions? Is the economic reciprocity clause enforceable in jurisdictions that do not recognize software licenses as contracts?

7. **Preamble revision** -- Should the GPLv3 reference in the preamble be revised to "inspired by" rather than "builds on" to eliminate compatibility confusion?
