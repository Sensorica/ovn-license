# Contributing to the OVN License

Thank you for your interest in improving the OVN License for Digital Resources. This project benefits from contributions across several domains, and we welcome input from legal professionals, open-source practitioners, software developers, and commons-oriented communities.

## What Contributions Are Needed

### High Priority

- **Legal review** -- The license text has not been reviewed by a lawyer. We need feedback on enforceability, jurisdictional issues, and interaction with existing legal frameworks.
- **Definition precision** -- Several definitions (Material Benefits, Non-Commercial Entities, Use) need tightening. See [CHANGELOG.md](CHANGELOG.md) Known Issue 2.
- **Reciprocity mechanism design** -- How should Material Benefits be calculated and reported? What compliance verification is appropriate? See [CHANGELOG.md](CHANGELOG.md) Known Issue 3.

### Medium Priority

- **Compatibility analysis** -- Additional analysis for licenses not yet covered (e.g., MPL-2.0, EUPL, LGPL). See [compatibility/](compatibility/).
- **Pie-chart tooling** -- Validators, editors, visualizers, and CI/CD integrations for the pie-chart format.
- **Application examples** -- Guides for applying the license to additional project types (e.g., mobile apps, hardware designs, datasets).
- **Holochain integration** -- Reference implementation of the pie-chart validation zome.

### Lower Priority

- **Translation** -- Translations of the license text and documentation into other languages.
- **Branding and communication** -- Clear explanations of the license for non-technical audiences.
- **SPDX registration** -- Working toward a proper SPDX identifier. See [CHANGELOG.md](CHANGELOG.md) Known Issue 5.

## Process

### For All Contributions

1. **Open an issue first.** Describe what you want to change and why. This allows discussion before you invest time in a pull request.
2. **One concern per issue.** Keep issues focused on a single topic.
3. **Reference existing documentation.** If your contribution relates to a known issue, link to the relevant CHANGELOG entry, RATIONALE section, or compatibility document.

### For License Text Changes

Changes to the license text (`LICENSE.md`) require a longer review cycle because they affect all downstream adopters.

1. Open an issue describing the proposed change and its motivation.
2. Allow at least 30 days for community discussion.
3. Changes require rough consensus among active contributors before merging.
4. Version the change: any modification to `LICENSE.md` creates a new version (e.g., v1.1).
5. Update `CHANGELOG.md` with the change and any new known issues.

### For Specification Changes

Changes to the pie-chart specification (`spec/`) follow a similar but shorter cycle:

1. Open an issue describing the proposed change.
2. Allow at least 14 days for community discussion.
3. Ensure backward compatibility where possible. Breaking changes require a new schema version.
4. Update examples to reflect specification changes.
5. Update the JSON Schema to match.

### For Documentation and Examples

Changes to documentation, compatibility analysis, and examples can follow a standard pull request workflow:

1. Open an issue or pull request.
2. Ensure cross-references remain consistent (e.g., links between README, RATIONALE, CHANGELOG, spec).
3. Review typically completes within 7 days.

## Style Guidelines

- **Prose style** -- Clear, direct, and professional. Avoid marketing language. State trade-offs honestly.
- **Document structure** -- Follow the existing structure of similar documents in the repository.
- **Cross-references** -- Use relative links to other documents in the repository.
- **Examples** -- Include concrete examples where possible. Abstract principles are more useful when illustrated.

## Code of Conduct

This project follows the principles of respectful, constructive collaboration. We expect contributors to:

- Engage with ideas on their merits, not on the identity of the person presenting them.
- Assume good faith in discussions.
- Accept that disagreement is productive when conducted respectfully.
- Recognize that legal and ethical questions rarely have simple answers.

## License for Contributions

Contributions to this repository (documentation, specification, examples) are licensed under [CC-BY-SA-4.0](https://creativecommons.org/licenses/by-sa/4.0/), consistent with the repository's license. By submitting a contribution, you agree to license it under these terms.

## Contact

For questions about contributing, open an issue in this repository or contact the Sensorica network through [sensorica.co](https://www.sensorica.co/).
