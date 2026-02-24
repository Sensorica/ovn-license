# Applying the OVN License to a Holochain hApp

This guide shows how to apply the OVN License for Digital Resources v1.0 to a Holochain hApp project, including dual-licensing with CAL-1.0 (recommended).

## Prerequisites

- A Holochain hApp project with a standard directory structure.
- Familiarity with the OVN License terms (see [LICENSE.md](../../LICENSE.md)).
- Review the [CAL-1.0 compatibility analysis](../../compatibility/CAL-1.0.md) for dual-licensing guidance.

## Step 1: Add License Files

Place license files in your hApp project root:

```
your-happ/
  LICENSE-CAL-1.0           Full text of CAL-1.0
  LICENSE-OVN-1.0           Full text of OVN License v1.0 (copy of LICENSE.md)
  LICENSE                   Dual-license notice (see below)
  pie-chart.json            Contribution Pie-Chart
  happ.yaml                 hApp manifest (reference license)
  dnas/
    your-dna/
      zomes/
        your-zome/
          src/
            lib.rs          Source files with license headers
```

## Step 2: Create the Dual-License Notice

Create a `LICENSE` file in your project root:

```
This software is dual-licensed:

1. Cryptographic Autonomy License 1.0 (CAL-1.0)
   Governs: source code availability, user data rights, and
   distribution requirements.
   Full text: LICENSE-CAL-1.0

2. OVN License for Digital Resources v1.0
   Governs: economic reciprocity, contribution tracking, and
   benefit distribution among contributors.
   Full text: LICENSE-OVN-1.0
   Contribution Pie-Chart: pie-chart.json

Both licenses apply. Use of this software constitutes acceptance
of both licenses.
```

## Step 3: Create the Pie-Chart

Create a `pie-chart.json` in your project root. See [pie-chart.json](pie-chart.json) in this directory for a complete example with Holochain extensions.

Key points for Holochain hApps:

- Use the `extensions.holochain` object to map contributor identifiers to Holochain agent IDs.
- Include the DNA hash for on-chain verification.
- Reference the validation zome name if using on-chain pie-chart validation.

## Step 4: Add Source File Headers

Add a license header to each Rust source file in your zomes:

```rust
// This work is dual-licensed under:
// - Cryptographic Autonomy License 1.0 (CAL-1.0)
// - OVN License for Digital Resources v1.0
// See LICENSE files and accompanying Contribution Pie-Chart.
// Copyright (c) 2025 Your Name or Organization
```

For `happ.yaml` and other YAML files:

```yaml
# This work is dual-licensed under:
# - Cryptographic Autonomy License 1.0 (CAL-1.0)
# - OVN License for Digital Resources v1.0
# See LICENSE files and accompanying Contribution Pie-Chart.
# Copyright (c) 2025 Your Name or Organization
```

## Step 5: Reference in hApp Manifest

In your `happ.yaml`, add a metadata section referencing the license:

```yaml
---
manifest_version: "1"
name: your-happ
description: Your hApp description
roles:
  - name: your-role
    provisioning:
      strategy: create
      deferred: false
    dna:
      bundled: "dnas/your-dna.dna"

# License metadata (informational, not part of Holochain spec)
# license:
#   type: "dual: CAL-1.0 + OVN-Digital-1.0"
#   pie_chart: "pie-chart.json"
```

Note: The `license` field is not part of the official Holochain hApp manifest specification. It is included as a comment for human reference. Formal license metadata support in hApp manifests may be proposed to the Holochain community.

## On-Chain Verification

For projects that want to verify pie-chart integrity on-chain:

1. **Store the pie-chart** as an entry in a dedicated zome.
2. **Validate on commit** that shares sum to 100 and identifiers are unique.
3. **Link to DNA entry** for discoverability.
4. **Verify agent signatures** by checking that `extensions.holochain.agent_ids` match the agents signing the entry.

A reference implementation of the validation zome is planned. See the [pie-chart specification](../../spec/contribution-pie-chart.md) for validation rules.

## Checklist

- [ ] `LICENSE-CAL-1.0` file present with full CAL-1.0 text
- [ ] `LICENSE-OVN-1.0` file present with full OVN License text
- [ ] `LICENSE` file with dual-license notice
- [ ] `pie-chart.json` with valid contributor data and Holochain extensions
- [ ] License headers in all `.rs` source files
- [ ] License headers in YAML configuration files
- [ ] `happ.yaml` references license (as comment)
- [ ] Pie-chart validates against the JSON Schema
