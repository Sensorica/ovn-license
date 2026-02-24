# Design Rationale

This document explains why the OVN License for Digital Resources v2.0 is structured the way it is, what problems it attempts to solve, and where it sits in relation to existing licenses. It is intended for reviewers evaluating the license and for downstream adopters deciding whether the license fits their needs.

## Purpose of This License

Traditional open-source licenses guarantee freedoms to use, study, modify, and distribute software. They do not address the economic reality that contributors to commons-based projects often receive no material return for their work, while downstream users may derive significant value.

The OVN License attempts to bridge this gap by combining a copyleft foundation with protocol-level economic reciprocity. Its goal is not to restrict use but to ensure that value generated through the Work flows back to contributors in proportion to their contributions.

## Evolution from v1.0 to v2.0

### What Changed and Why

v1.0 used an honor-system model: the license stated that non-commercial users owed 0.5% of "Material Benefits" and commercial users owed 2%. This approach had several problems:

1. **Unenforceable.** There was no practical way to verify that users were calculating and paying the correct amounts. Self-reporting without verification is not a reliable mechanism.

2. **Vague trigger.** "Material Benefits" included "monetizable advantage," which is too broad to measure. It was unclear what triggered the obligation and what did not.

3. **Commercial/non-commercial distinction was fragile.** The boundary between commercial and non-commercial entities is often blurry (e.g., a cooperative selling software, a nonprofit with consulting revenue). Requiring users to self-classify creates disputes.

4. **GPLv3 derivation confusion.** The v1.0 preamble claimed to "build on" GPLv3, but the license was structurally and legally independent. This created confusion about compatibility.

Through developing [Nondominium](https://github.com/Sensorica/nondominium) (a Holochain-based distributed resource management application), we discovered that the economic mechanism should be enforced by the software itself, similar to how blockchain gas fees operate. The software captures a contribution percentage automatically from transactional activity, and the license's job is to prevent circumvention of that mechanism.

### The Three-Layer Enforcement Model

v2.0 is built on three reinforcing layers:

1. **Protocol Mechanics (automatic).** The software includes a Contribution Distribution Mechanism that captures a portion of value generated through Transactional Activity and distributes it to Contributors per the Contribution Pie-Chart. This is how the software functions, not a separate legal obligation.

2. **Network Validation (architectural).** In Holochain's architecture, validation rules are enforced by the DHT. A fork that removes the economic mechanism creates data that is incompatible with the network. This is architectural enforcement: the fork becomes a separate, incompatible network.

3. **Legal Terms (backstop).** The license provides legal recourse against circumvention. If someone forks the software, strips the mechanism, and runs a separate network, the anti-circumvention clause (Section 5) makes this a license violation with legal consequences.

## Design Goals

1. **Protocol-Level Enforcement.** Make economic reciprocity a property of the running system rather than a contractual obligation that requires voluntary compliance and external verification.

2. **Anti-Circumvention as the Core Legal Mechanism.** Rather than "you must pay X%," the key legal obligation is: "you may not modify, disable, or bypass the Contribution Distribution Mechanism." This is modeled on CAL-1.0 Section 4.2.2 but applied to economic distribution.

3. **Transparent Contribution Tracking.** The Contribution Pie-Chart provides a verifiable, machine-readable record of who contributed what. This enables automated distribution and removes ambiguity.

4. **Clear Scope Boundaries.** Explicitly state what triggers economic obligations (Transactional Activity) and what does not (development grants, internal use, education, personal use). This encourages ecosystem growth.

5. **Good Faith Compliance.** The cure period, good faith presumption, technical safe harbor, and de minimis threshold all reflect a preference for compliance over punishment. The license serves communities, not litigators.

## What This License Is NOT

- **Not a GPLv3 extension.** The license is standalone and legally independent from GPLv3. It acknowledges GPLv3 as philosophical inspiration only.

- **Not anti-commercial.** Commercial use is explicitly permitted. The Contribution Distribution Mechanism applies equally to all parties engaged in Transactional Activity, regardless of organizational form.

- **Not a Contributor License Agreement (CLA).** The pie-chart records contributions for benefit distribution purposes. It does not transfer copyright, grant additional patent rights, or change the licensing terms. Contributors retain their copyright.

- **Not OSI-approved.** The anti-circumvention clause and the requirement to maintain the Contribution Distribution Mechanism likely conflict with the Open Source Definition. This is an intentional design choice. See "OSI Compatibility" below.

- **Not a royalty.** The license is technically royalty-free. The Contribution Distribution Mechanism is a feature of the software that distributes value as part of its operation. The license does not impose a payment obligation; it prevents removal of a software feature. This distinction matters for legal interpretation.

## Relationship to GPLv3

The v1.0 preamble stated the license "builds on the GNU General Public License v3." This language has been removed in v2.0. The license now clearly states it is "inspired by" GPLv3 and "legally independent from" it.

**Key differences from GPLv3:**

- **Anti-circumvention of economic mechanism.** GPLv3 has no concept of protecting a built-in economic distribution feature. GPLv3 Section 7 explicitly limits additional terms, and an anti-circumvention clause protecting an economic mechanism would not fit within those limits.
- **Contribution tracking.** GPLv3 has no equivalent of the Contribution Pie-Chart.
- **Scope exclusions.** GPLv3 does not distinguish between types of use; all uses have the same obligations. The OVN License explicitly excludes non-transactional use from economic obligations.

**Compatibility:** OVN-licensed code and GPLv3-licensed code cannot be combined in a single derivative work. See [compatibility/GPLv3.md](compatibility/GPLv3.md) for details.

## Relationship to the Peer Production License

The [Peer Production License](https://wiki.p2pfoundation.net/Peer_Production_License) (PPL) introduced differentiated licensing based on the user's organizational form. The OVN License adopts the PPL's core principle (commons-produced resources should benefit their producers) but departs from its approach:

- **Protocol enforcement instead of entity classification.** The PPL draws a sharp line between commercial and non-commercial use. The OVN License v2.0 removes this distinction entirely. When the Contribution Distribution Mechanism applies uniformly to all Transactional Activity, the software does not need to know whether the user is a cooperative or a corporation.
- **Anti-circumvention instead of negotiation.** The PPL requires commercial users to negotiate a separate license. The OVN License allows all use under the same terms, with the mechanism handling distribution automatically.
- **Contribution tracking.** The PPL does not address how benefits are distributed among contributors. The OVN License requires a Contribution Pie-Chart.
- **Cure period.** The PPL does not include a cure mechanism. The OVN License provides 30 days plus good faith protections.

## Relationship to the Cryptographic Autonomy License (CAL-1.0)

The [Cryptographic Autonomy License](https://opensource.org/license/cal-1-0) (CAL-1.0) is the most direct technical influence on v2.0. CAL-1.0 introduced the concept of protocol-level enforcement of user rights in distributed systems. Specifically, CAL-1.0 Section 4.2.2 prohibits cryptographic measures that limit user autonomy.

The OVN License v2.0 applies the same pattern in reverse: instead of prohibiting measures that limit user access, it prohibits measures that remove economic distribution. Both licenses protect a feature of the software from being stripped by redistributors.

For Holochain hApp projects, dual-licensing under both CAL-1.0 and the OVN License is recommended:
- CAL-1.0 covers code autonomy and user data rights
- OVN License covers economic reciprocity and contribution tracking

The anti-circumvention clauses are complementary: CAL-1.0 ensures Recipients can access the mechanism; OVN ensures the mechanism cannot be stripped from redistributed versions.

See [compatibility/CAL-1.0.md](compatibility/CAL-1.0.md) for practical guidance.

## Why No Fixed Percentages in v2.0

v1.0 specified 0.5% for non-commercial and 2% for commercial use. v2.0 removes these numbers from the license text. The reasons:

1. **Parameters belong in the software, not the license.** The Contribution Distribution Mechanism has configurable parameters (distribution percentage, timing, methods). These are part of the Work's implementation, governed by the pie-chart governance process. Different projects can set different rates appropriate to their context.

2. **One size does not fit all.** A Holochain hApp processing micro-transactions might set a 1% rate. A SaaS platform might set 3%. A data marketplace might use a different structure entirely. The license should not prescribe what the mechanism captures, only that the mechanism must not be removed.

3. **Removes the commercial/non-commercial problem.** When percentages are in the software and apply uniformly, the license does not need to classify users.

4. **Governance flexibility.** The Contributor community can adjust rates through their governance process without needing a new license version.

## Why the Anti-Circumvention Approach

The shift from "you owe X%" to "you must not remove the mechanism" has several advantages:

1. **Verifiable.** Did the defendant remove the mechanism? This is a binary question answerable by code inspection. Did the defendant calculate Material Benefits correctly? This requires financial auditing and is practically unverifiable for most commons projects.

2. **Self-enforcing at the protocol level.** In distributed systems like Holochain, the mechanism is enforced by network validation. The legal clause is a backstop for cases the protocol cannot reach (e.g., a fork running a separate network).

3. **Modeled on established precedent.** CAL-1.0's anti-circumvention clause has been accepted by OSI. The DMCA contains anti-circumvention provisions for copy protection. The concept of prohibiting tampering with a software mechanism is well-established legally.

4. **Separates the license from the implementation.** The license defines the legal framework. The software defines the economic parameters. This separation makes both more maintainable.

## Scope Exclusions Rationale

v2.0 explicitly excludes five categories of activity from economic obligations:

1. **Development and Improvement** (Section 6(a)). Grant funding, donations, and volunteer labor directed at improving the commons are inputs to the system, not extractions from it. Taxing these would discourage contribution.

2. **Non-Transactional Internal Use** (Section 6(b)). An organization using the software for internal operations (project management, research tools) without market-based transactions should not trigger economic obligations. Taxing productivity gains would conflict with open source freedom of use.

3. **Education and Research** (Section 6(c)). Academic and educational use should be unrestricted to encourage adoption and knowledge sharing.

4. **Personal Use** (Section 6(d)). Individual non-commercial use should not trigger obligations. v1.0 technically required even personal users to pay 0.5% of any "Material Benefits."

5. **Interoperability Testing** (Section 6(e)). Testing compatibility should be encouraged, not penalized.

## Why the Pie-Chart Requirement

The Contribution Pie-Chart is the mechanism that distinguishes the OVN License from other reciprocity-oriented licenses. It draws on two sources:

### OVN Principles

Open Value Networks use contribution accounting as a foundational governance mechanism. The principle is that value flows should be transparent, verifiable, and proportional to contribution. The pie-chart makes this principle enforceable at the license level.

### NRP-CAS Precedent

The Network Resource Planning / Contribution Accounting System (NRP-CAS), developed by Sensorica and the Mikorizal Software collective, demonstrated that contribution tracking in open networks is technically feasible. The pie-chart is a simplified, portable version of this concept that travels with source code.

### Why Machine-Readable?

A machine-readable format (JSON as canonical, with YAML/TOML as authoring alternatives) enables:

- **Automated validation.** CI/CD pipelines can verify pie-chart integrity.
- **Automated distribution.** The Contribution Distribution Mechanism can read the pie-chart and distribute value without manual intervention.
- **On-chain verification.** For Holochain and other distributed systems, the pie-chart can be validated by smart contracts or zome functions.
- **Tooling ecosystem.** Editors, visualizers, and auditing tools can work with a standardized format.

## OSI Compatibility

The OVN License is likely incompatible with the [Open Source Definition](https://opensource.org/osd) (OSD). The anti-circumvention clause (Section 5) requires maintaining a specific software feature (the Contribution Distribution Mechanism) in all redistributions. This could be interpreted as an additional restriction beyond standard copyleft.

Additionally, the requirement to maintain the Contribution Pie-Chart and the contributor protection (no removal of contributors without consent) go beyond what the OSD envisions for copyleft licenses.

**This is an intentional design choice.** The OVN License prioritizes contributor sustainability over OSI compliance. The authors believe that the open-source ecosystem's failure to address contributor compensation is a systemic problem, and that licenses must evolve to address it.

**Practical impact:** Projects using the OVN License cannot claim to be "OSI-approved open source." They can accurately describe themselves as "free software with economic reciprocity" or "commons-licensed." Dual-licensing with CAL-1.0 (which is OSI-approved) provides an OSI-compatible layer for code autonomy and user data rights.

## Open Questions for Community Review

The following questions remain open and would benefit from community input:

1. **"Functionally equivalent to zero" threshold.** Section 5(e) prohibits reducing the distribution to zero or functionally equivalent to zero. What constitutes "functionally equivalent"? Should the license or companion documents provide more specific guidance?

2. **De minimis threshold default.** Section 7(e) allows the Contributor community to set a de minimis threshold. What is a reasonable default for projects that do not specify one?

3. **Pie-chart governance.** Who has authority to update the pie-chart? What happens when contributors disagree about shares? The current spec proposes a dispute resolution process, but should this be part of the license itself?

4. **Interaction with employment.** If a contributor is employed and contributes as part of their job, does their employer receive their share? Or does the individual contributor receive it?

5. **International enforcement.** How does the anti-circumvention clause interact with different legal jurisdictions? Is it enforceable in jurisdictions that do not recognize software licenses as contracts?

6. **Advertising and indirect revenue models.** If a party hosts the Work and generates revenue through advertising (not direct transactions through the Work), does this constitute Transactional Activity? The current definition focuses on operations "performed by or through the Work" in a market context, but advertising-supported models may be a gray area.
