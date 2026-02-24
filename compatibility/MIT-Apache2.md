# Compatibility: OVN License v2.0 + Permissive Licenses (MIT, Apache-2.0)

## Overview

Permissive licenses like the [MIT License](https://opensource.org/license/mit) and [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0) impose minimal restrictions on downstream use. They allow code to be incorporated into projects under different licenses, including copyleft licenses.

This document explains how permissively-licensed code interacts with OVN-licensed projects.

## Compatibility Analysis

### Inbound: Permissive Code in OVN Projects

**This is allowed and straightforward.** MIT and Apache-2.0 licensed code can be used as dependencies in OVN-licensed projects without conflict.

| Requirement | MIT | Apache-2.0 | Conflict with OVN? |
|-------------|-----|------------|---------------------|
| Include copyright notice | Yes | Yes | No -- OVN also requires notice inclusion |
| Include license text | Yes (in copies) | Yes | No -- both can coexist in a NOTICES file |
| State changes | No | Yes | No -- OVN requires marking Modified Versions |
| Patent grant | No | Yes | No -- OVN does not address patents |
| Trademark restrictions | No | Yes | No -- independent concerns |

**How to handle permissive dependencies:**

1. Include the dependency's license in a `NOTICES` or `THIRD-PARTY-LICENSES` file.
2. The OVN License's anti-circumvention clause applies to the Contribution Distribution Mechanism in the OVN-licensed project, not to individual permissive dependencies. The mechanism captures value from Transactional Activity performed through the overall Work.
3. The permissive dependencies' original authors are not automatically pie-chart contributors (unless they also contribute to the OVN-licensed project directly).

### Outbound: OVN Code in Permissive Projects

**This is NOT allowed without relicensing.** You cannot take OVN-licensed code and include it in an MIT or Apache-2.0 project, because the OVN License's anti-circumvention clause and copyleft requirements (Section 3) would be lost. The OVN License requires that its terms be maintained in all redistributions.

| Scenario | Allowed? | Reason |
|----------|----------|--------|
| MIT library used in OVN project | Yes | Permissive code flows into copyleft |
| OVN code copied into MIT project | No | Would strip anti-circumvention and copyleft obligations |
| OVN project depending on MIT library | Yes | Dependency, not incorporation |
| MIT project depending on OVN library | Complex -- see below | Depends on linking model |

### Mixed Dependency Chains

When an MIT or Apache-2.0 project uses an OVN-licensed library as a dependency:

- **If the OVN code is incorporated** (copied, vendored, statically linked): The combined work must comply with the OVN License, including maintaining the Contribution Distribution Mechanism and the Contribution Pie-Chart. The permissive license of the outer project does not override the OVN License on the OVN-licensed component.

- **If the OVN code is a separate dependency** (dynamic linking, package manager dependency, network service): The outer project's license governs its own code. Users who also use the OVN-licensed dependency must comply with the OVN License for that dependency's use.

## Anti-Circumvention Scope

A common concern: "If I use one OVN-licensed package in my otherwise MIT project, does the anti-circumvention clause apply to my entire project?"

**The anti-circumvention clause (Section 5) applies to the Contribution Distribution Mechanism** in the OVN-licensed component. If the OVN-licensed component includes a mechanism, you must not remove or disable it. The clause does not require you to add a mechanism to your own code or to the permissive components.

However, if the OVN-licensed component is incorporated into a larger work (not just used as a separate dependency), the copyleft provision (Section 3(b)) requires Modified Versions to be distributed under the OVN License. This means incorporating OVN-licensed code into a permissive project effectively converts the combined work to OVN-licensed.

**Practical advice for downstream users:**

1. Evaluate whether the OVN-licensed component is central to your product or peripheral.
2. If peripheral, keep it as a separate dependency rather than incorporating it.
3. When in doubt, contact the project's contributors to discuss the appropriate approach.
4. Consider contributing improvements back to the OVN-licensed component, which may be reflected in the pie-chart.

## Practical Guidance for OVN Project Maintainers

### Managing Permissive Dependencies

1. **Track third-party licenses** in a `NOTICES` file alongside your `pie-chart.json`.
2. **Do not add permissive dependency authors** to the pie-chart unless they contribute directly to your project.
3. **Document the dependency relationship** so users understand which components are under which license.

### Example Project Structure

```
your-ovn-project/
  LICENSE.md               OVN License v2.0
  pie-chart.json           Contribution Pie-Chart
  NOTICES                  Third-party license notices
  src/
    core/                  OVN-licensed code
    vendor/                MIT/Apache-2.0 dependencies (or managed via package manager)
```

### NOTICES File Template

```
This project includes the following third-party software:

---
library-name v1.2.3
License: MIT
Copyright (c) 2024 Library Author
[Full MIT license text]

---
another-library v4.5.6
License: Apache-2.0
Copyright (c) 2024 Another Author
[Full Apache-2.0 license text or reference]
```

## Summary

| Direction | Compatibility | Notes |
|-----------|--------------|-------|
| Permissive code INTO OVN project | Compatible | Include notices; anti-circumvention applies to OVN project's mechanism |
| OVN code INTO permissive project | Not compatible | Anti-circumvention and copyleft cannot be stripped |
| Permissive project DEPENDING ON OVN library | Case-by-case | Depends on incorporation vs. separate dependency |
| OVN anti-circumvention propagation upstream | Does not propagate | MIT/Apache-2.0 authors not affected |
