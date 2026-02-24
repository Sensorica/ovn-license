# Applying the OVN License to a Python Service

This guide shows how to apply the OVN License for Digital Resources v2.0 to a Python project (library, CLI tool, or web service).

## Step 1: Add License and Pie-Chart Files

```
your-python-project/
  LICENSE.md                OVN License v2.0
  pie-chart.json            Contribution Pie-Chart
  pyproject.toml            Project metadata (reference license)
  src/
    your_package/
      __init__.py           License header
      module.py             License header
  tests/
    ...
```

## Step 2: Create the Pie-Chart

Create a `pie-chart.json` in your project root. See [pie-chart.json](pie-chart.json) for an example.

## Step 3: Add Source File Headers

Add a license header to each Python source file:

```python
# This work is licensed under the OVN License for Digital Resources v2.0.
# Use of this work is subject to contribution distribution and anti-circumvention terms.
# See LICENSE file and accompanying Contribution Pie-Chart.
# SPDX-License-Identifier: LicenseRef-OVN-Digital-2.0
# Copyright (c) [year] Your Name or Organization
```

For the package `__init__.py`, you may also include:

```python
"""
your_package - Description of your package.

Licensed under the OVN License for Digital Resources v2.0.
See LICENSE file and accompanying Contribution Pie-Chart.
"""
```

## Step 4: Configure pyproject.toml

Reference the license in your `pyproject.toml`:

```toml
[project]
name = "your-package"
version = "1.0.0"
description = "Your package description"
license = {file = "LICENSE.md"}
readme = "README.md"

# Note: The SPDX identifier for the OVN License is not yet registered.
# Use "LicenseRef-OVN-Digital-2.0" as the custom identifier.
# license = {text = "LicenseRef-OVN-Digital-2.0"}

[project.urls]
Repository = "https://github.com/your-org/your-package"
License = "https://github.com/your-org/your-package/blob/main/LICENSE.md"
"Contribution Pie-Chart" = "https://github.com/your-org/your-package/blob/main/pie-chart.json"
```

## Step 5: Include in Distributions

When distributing your package (via PyPI or other means), ensure both `LICENSE.md` and `pie-chart.json` are included in the source distribution:

```toml
[tool.setuptools]
# If using setuptools
[tool.setuptools.package-data]
"*" = ["LICENSE.md", "pie-chart.json"]
```

Or add a `MANIFEST.in` for sdist:

```
include LICENSE.md
include pie-chart.json
```

## Step 6: Implement the Contribution Distribution Mechanism

For Python services that process transactions, the Contribution Distribution Mechanism might be implemented as:

- **Middleware** that captures a percentage of transaction value.
- **A billing module** that allocates contributor shares per the pie-chart.
- **An API layer** that deducts contribution shares from service fees.

If the mechanism is not yet implemented, you can still adopt the license. The anti-circumvention obligations in Section 5 activate when the mechanism is added (see License Section 4(d)).

## Checklist

- [ ] `LICENSE.md` file present with full OVN License v2.0 text
- [ ] `pie-chart.json` with valid contributor data
- [ ] License headers in all `.py` source files (with SPDX identifier)
- [ ] `pyproject.toml` references the license
- [ ] `LICENSE.md` and `pie-chart.json` included in package distributions
- [ ] Pie-chart validates against the JSON Schema
- [ ] README mentions the license and links to the pie-chart
- [ ] Contribution Distribution Mechanism implemented (or noted as planned)
