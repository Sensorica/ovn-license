# Compatibility: OVN License + GNU Affero General Public License v3

## Overview

The [GNU Affero General Public License v3](https://www.gnu.org/licenses/agpl-3.0.html) (AGPLv3) is a copyleft license that extends GPLv3's provisions to cover network interaction. If you run modified AGPLv3 software as a network service, you must make the source code available to users who interact with it over the network.

The OVN License and AGPLv3 are **not directly compatible** -- they cannot be applied to the same codebase as a combined work. However, they can coexist in a project through careful component separation.

## Compatibility Analysis

### Key Conflicts

| AGPLv3 Provision | OVN License Provision | Conflict |
|-----------------|----------------------|----------|
| Section 7: No additional restrictions | Section 3: Economic reciprocity (0.5% / 2%) | **Direct conflict** -- AGPLv3 does not allow requiring payment or benefit-sharing as an additional term |
| Section 10: Automatic licensing | Section 1: License grant with conditions | **Tension** -- AGPLv3 grants automatic downstream licenses without additional conditions |
| Section 5c: Modified source must be licensed under AGPL | Section 2: Must maintain OVN License + pie-chart | **Conflict** -- derivative works cannot satisfy both requirements simultaneously |

### Why They Conflict

The AGPLv3 follows the GPLv3 framework of permitted additional terms (Section 7). The economic reciprocity clause of the OVN License does not fit within any of the categories of permitted additional terms listed in AGPLv3 Section 7(a)-(f). Specifically, requiring a percentage of material benefits is an "additional restriction" under AGPLv3 Section 7, which means it would be stripped from any combined work.

## Bridge Component Strategy

While the licenses cannot apply to the same code, a project can use both by separating components with defined interfaces:

```
┌─────────────────────────────────────────┐
│              Your Project                │
│                                         │
│  ┌─────────────────┐ ┌───────────────┐  │
│  │  AGPLv3 Component│ │ OVN Component │  │
│  │  (e.g., server   │ │ (e.g., core   │  │
│  │   framework)     │ │  algorithms)  │  │
│  └────────┬────────┘ └──────┬────────┘  │
│           │   Defined API    │           │
│           └──────────────────┘           │
└─────────────────────────────────────────┘
```

### Requirements for Bridge Components

1. **Clear separation** -- Each component must be a separate work, not a derivative of the other. They communicate through a defined API (function calls, network protocols, file I/O, etc.).

2. **Independent licensing** -- Each component carries its own license. The AGPLv3 component does not include OVN-licensed code, and vice versa.

3. **Interface documentation** -- The API between components must be documented so that either component could be replaced independently.

4. **Separate distribution** -- Components may be distributed together as an "aggregate" (AGPLv3 Section 5, final paragraph) but must remain independently identifiable.

### What "Separate Work" Means in Practice

The AGPLv3 defines a combined work broadly. To maintain separation:

- **Do not** copy code between AGPLv3 and OVN components.
- **Do not** share header files or type definitions that would create a derivative work.
- **Do** communicate through well-defined interfaces (REST APIs, message queues, shared file formats, CLI invocations).
- **Do** keep the components in separate directories with separate license files.

## Practical Guidance

### When to Use This Pattern

This bridge pattern is appropriate when:

- Your project depends on an AGPLv3 library or framework (e.g., an AGPLv3 database driver or web framework).
- You want your core application logic to be under the OVN License for contribution tracking and economic reciprocity.
- The components have a natural architectural boundary.

### When NOT to Use This Pattern

- If the components are tightly coupled and cannot be separated at an API boundary.
- If you need to modify AGPLv3 code to add OVN-specific functionality (the modification would be AGPLv3-only).
- If the licensing complexity would confuse your users or contributors.

### Example: Web Service Architecture

```
AGPLv3 layer:
  - Web framework (e.g., an AGPLv3 framework)
  - Database adapters
  - Network infrastructure

  Communicates via REST API or function interface

OVN License layer:
  - Business logic and algorithms
  - Contribution tracking integration
  - Benefit distribution logic
  - pie-chart.json
```

## Summary

| Approach | Feasibility | Recommendation |
|----------|-------------|----------------|
| Single codebase, both licenses | Not possible | Do not attempt |
| Dual-license (user chooses) | Legally possible but defeats OVN purpose | Not recommended |
| Bridge components | Feasible with careful architecture | Recommended when AGPLv3 dependencies exist |
| Replace AGPLv3 dependency | Simplest solution | Recommended when alternatives exist |
