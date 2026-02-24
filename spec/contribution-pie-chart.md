# Contribution Pie-Chart Specification

**Version:** Draft v0.1
**Status:** Draft -- seeking review

## Overview

The Contribution Pie-Chart is a machine-readable file that accompanies software licensed under the OVN License for Digital Resources. It records the proportional contributions of each contributor to the project and serves as the basis for distributing value through the Contribution Distribution Mechanism under the license's protocol economics and anti-circumvention provisions (Sections 4 and 5).

This specification defines the format, required fields, validation rules, and governance for pie-chart files.

## Relationship to the License

The OVN License v2.0 requires:

- **Section 2:** A copy of the Contribution Pie-Chart must be included in all copies or substantial portions of the Work.
- **Section 3:** The pie-chart must be maintained in all redistributions. Modified Versions may update the pie-chart to reflect new contributions, but must not remove existing Contributors without consent.
- **Section 4:** The Contribution Distribution Mechanism distributes value to Contributors "according to the Contribution Pie-Chart."
- **Section 5:** The governance process for modifying distribution parameters is recorded in the Contribution Pie-Chart.

This specification defines what a valid Contribution Pie-Chart looks like and how it should be maintained.

## File Format

### Canonical Format: JSON

JSON is the canonical format for Contribution Pie-Charts. All tooling, validation, and on-chain verification should target JSON.

The canonical filename is `pie-chart.json`, placed in the project root directory.

### Alternative Authoring Formats

Projects may author pie-charts in YAML or TOML for readability, provided that:

1. A JSON version is generated and included in distributions.
2. The JSON version is the authoritative copy for validation and benefit distribution.
3. The conversion process is documented and reproducible.

## Schema

### Top-Level Structure

```json
{
  "schema_version": "0.1",
  "project": { ... },
  "contributors": [ ... ],
  "metadata": { ... },
  "organization": { ... },
  "history": [ ... ],
  "extensions": { ... }
}
```

### Required Fields

#### `schema_version` (string, required)

The version of this specification that the file conforms to. For this draft, the value must be `"0.1"`.

#### `project` (object, required)

Information about the project this pie-chart belongs to.

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `name` | string | yes | The project name. |
| `repository` | string | yes | URL of the project's source repository. |
| `license_version` | string | yes | The OVN License version (e.g., `"1.0"`). |

#### `contributors` (array, required)

An array of contributor objects. Must contain at least one entry.

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `name` | string | yes | The contributor's display name. |
| `identifier` | string | yes | A unique, stable identifier for the contributor. This may be an email address, a URL (e.g., a personal website or profile), a DID, or a platform-specific ID. The identifier must be unique within the pie-chart. |
| `share` | number | yes | The contributor's share as a percentage (0 < share <= 100). |
| `roles` | array of strings | no | Descriptions of the contributor's roles (e.g., `["core developer", "documentation"]`). |

#### `metadata` (object, required)

Administrative information about the pie-chart.

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `created` | string (ISO 8601 date) | yes | The date the pie-chart was created (e.g., `"2025-01-15"`). |
| `last_updated` | string (ISO 8601 date) | yes | The date of the most recent update. |
| `governance` | string | yes | A brief description of how pie-chart updates are governed (e.g., `"Consensus among active contributors"`, `"Maintainer discretion"`, `"DAO vote"`). |
| `dispute_resolution` | string | yes | A reference to the dispute resolution process. May be a description or a URL. |

### Optional Fields

#### `organization` (object, optional)

Information about the organization or network that governs the project.

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `name` | string | yes (if object present) | Organization name. |
| `url` | string | no | Organization website. |
| `type` | string | no | Organization type (e.g., `"cooperative"`, `"association"`, `"value network"`, `"informal collective"`). |

#### `history` (array, optional)

An array of change records documenting modifications to the pie-chart over time.

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `date` | string (ISO 8601 date) | yes (if entry present) | Date of the change. |
| `description` | string | yes (if entry present) | What changed and why. |
| `shares_snapshot` | object | no | A snapshot of `{ identifier: share }` at the time of the change. |

### Extensions

#### `extensions` (object, optional)

The `extensions` object provides a namespace for platform-specific or application-specific fields that are not part of the core specification. This allows the pie-chart format to be extended without modifying the core schema.

Each key in the `extensions` object is a namespace identifier (e.g., `"holochain"`, `"ethereum"`, `"did"`). The value is an object whose structure is defined by the extension.

**Example: Holochain extension**

```json
{
  "extensions": {
    "holochain": {
      "dna_hash": "uhC0k...",
      "agent_ids": {
        "alice@example.com": "uhCAk...",
        "bob@example.com": "uhCAk..."
      },
      "zome_name": "contribution_tracker"
    }
  }
}
```

The core specification does not validate the contents of extension objects -- validation is the responsibility of extension-specific tooling.

**Known extension namespaces:**

| Namespace | Purpose | Status |
|-----------|---------|--------|
| `holochain` | Holochain agent IDs, DNA hashes, zome references | Proposed |
| `ethereum` | Ethereum addresses, contract references | Proposed |
| `did` | Decentralized Identifier mappings | Proposed |

Extension specifications should be contributed to this repository. See [CONTRIBUTING.md](../CONTRIBUTING.md).

## Validation Rules

A pie-chart file is valid if and only if:

1. **Schema version** -- `schema_version` is present and matches a known version string.
2. **Required fields** -- All required fields at all levels are present and non-empty.
3. **Shares sum to 100** -- The sum of all `contributors[].share` values equals exactly 100. Floating-point tolerance: the sum must be within 0.01 of 100 (i.e., 99.99 <= sum <= 100.01).
4. **Positive shares** -- Every `contributors[].share` is greater than 0.
5. **Unique identifiers** -- Every `contributors[].identifier` is unique within the array.
6. **At least one contributor** -- The `contributors` array is non-empty.
7. **Valid dates** -- All date fields conform to ISO 8601 format (YYYY-MM-DD).
8. **Type conformance** -- All fields match their declared types.

A JSON Schema implementing these rules is provided at [contribution-pie-chart.schema.json](contribution-pie-chart.schema.json).

## Governance and Updates

### Who Can Update the Pie-Chart?

The `metadata.governance` field declares the update mechanism for the project. Common models include:

- **Maintainer discretion** -- The project maintainer(s) update the pie-chart based on contribution data.
- **Contributor consensus** -- All active contributors must agree on updates.
- **Algorithmic** -- Shares are computed from version control metrics (commits, lines, reviews) using a defined formula.
- **DAO governance** -- A decentralized autonomous organization votes on updates.

The license does not mandate a specific governance model. Projects should choose a model that fits their community structure and document it in the `governance` field.

### Dispute Resolution Process

When contributors disagree about share allocations, the following process applies (unless overridden by the project's `dispute_resolution` field):

1. **Discussion period (30 days)** -- Contributors attempt to resolve the dispute through direct communication. This may occur in the project's issue tracker, mailing list, or other public forum.

2. **Mediation** -- If discussion fails, contributors may engage a neutral mediator acceptable to all parties. The mediator may be an individual, an organization (e.g., the Sensorica network), or an automated system.

3. **Equal-shares fallback** -- If mediation fails or no mediator is available, the disputed shares are temporarily divided equally among the disputing contributors until resolution is reached.

The goal of this process is to keep benefit distribution flowing even during disputes, rather than allowing disagreements to freeze all payments.

## Holochain Integration Notes

For Holochain hApp projects, the pie-chart can be validated on-chain using a zome function. A minimal validation zome would:

1. **Accept** a pie-chart JSON entry.
2. **Validate** against the schema (shares sum to 100, unique identifiers, required fields).
3. **Link** to the hApp DNA entry for discoverability.
4. **Verify agent signatures** if the `holochain` extension maps identifiers to agent IDs.

A reference implementation of the validation zome is planned but not yet available.

## Migration from NRP-CAS

Projects currently using NRP-CAS (Network Resource Planning / Contribution Accounting System) for contribution tracking can migrate to the pie-chart format by:

1. **Exporting** contribution data from NRP-CAS as percentages per contributor.
2. **Mapping** NRP-CAS user accounts to pie-chart identifiers (email, URL, or DID).
3. **Creating** an initial pie-chart with the exported shares.
4. **Recording** the migration in the `history` array.

The migration preserves the contribution data while enabling the portability and tooling benefits of the standardized pie-chart format.
