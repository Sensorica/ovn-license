# Applying the OVN License to a Python Service

This guide shows how to apply the OVN License for Digital Resources v1.0 to a Python project (library, CLI tool, or web service).

## Step 1: Add License and Pie-Chart Files

```
your-python-project/
  LICENSE.md                OVN License v1.0
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
# This work is licensed under the OVN License for Digital Resources v1.0
# Redistribution and Use require compliance with reciprocity terms.
# See LICENSE file and accompanying Contribution Pie-Chart.
# Copyright (c) 2025 Your Name or Organization
```

For the package `__init__.py`, you may also include:

```python
"""
your_package - Description of your package.

Licensed under the OVN License for Digital Resources v1.0.
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

# Note: The SPDX identifier for the OVN License is not yet standardized.
# Use "LicenseRef-OVN-Digital-1.0" as the custom identifier.
# license = {text = "LicenseRef-OVN-Digital-1.0"}

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

## Checklist

- [ ] `LICENSE.md` file present with full OVN License text
- [ ] `pie-chart.json` with valid contributor data
- [ ] License headers in all `.py` source files
- [ ] `pyproject.toml` references the license
- [ ] `LICENSE.md` and `pie-chart.json` included in package distributions
- [ ] Pie-chart validates against the JSON Schema
- [ ] README mentions the license and links to the pie-chart
