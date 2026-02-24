# Applying the OVN License to Documentation

This guide shows how to apply the OVN License for Digital Resources v2.0 to documentation projects (technical writing, guides, educational materials, wikis).

## When to Use the OVN License for Docs

The OVN License is designed primarily for software, but its provisions apply to any "digital resource" (per the license title). Documentation projects that benefit from contribution tracking and reciprocity (such as collaboratively written technical guides, course materials, or knowledge bases) can use this license.

Note that the Contribution Distribution Mechanism and anti-circumvention provisions (Sections 4 and 5) are most relevant to software that processes transactions. For documentation without a built-in economic mechanism, the license still provides copyleft protection and contribution tracking via the pie-chart. The anti-circumvention obligations activate only when a mechanism is present (Section 4(d)).

For documentation that accompanies OVN-licensed software, using the same license simplifies compliance. Alternatively, consider CC-BY-SA-4.0 for documentation if contribution tracking and economic reciprocity are not needed.

## Step 1: Add License and Pie-Chart Files

```
your-docs-project/
  LICENSE.md                OVN License v2.0
  pie-chart.json            Contribution Pie-Chart
  docs/
    index.md
    guide.md
    reference.md
```

## Step 2: Create the Pie-Chart

Create a `pie-chart.json` in your project root. See [pie-chart.json](pie-chart.json) for an example.

For documentation projects, contributor roles might include: `"author"`, `"editor"`, `"reviewer"`, `"illustrator"`, `"translator"`.

## Step 3: Add a License Footer

Add a license notice to the footer or colophon of each document. For Markdown files:

```markdown
---

This work is licensed under the [OVN License for Digital Resources v2.0](LICENSE.md).
Use of this work is subject to contribution distribution and anti-circumvention terms.
See the [Contribution Pie-Chart](pie-chart.json) for contributor information.
Copyright (c) [year] Your Name or Organization
```

For HTML docs (e.g., in a static site generator):

```html
<footer>
  <p>This work is licensed under the
    <a href="LICENSE.md">OVN License for Digital Resources v2.0</a>.
    See the <a href="pie-chart.json">Contribution Pie-Chart</a> for
    contributor information.</p>
  <p>Copyright &copy; [year] Your Name or Organization</p>
</footer>
```

## Multi-Author Handling

Documentation projects often have many contributors with varying levels of involvement. Strategies for the pie-chart:

- **Per-project pie-chart**: One pie-chart for the entire documentation set, with shares reflecting overall contribution across all documents.
- **Per-document pie-charts**: Separate pie-charts for major documents (e.g., a book with chapters by different authors). Reference the specific pie-chart in each document's footer.
- **Algorithmic shares**: Calculate shares from version control metrics (commits, words added, reviews). Document the formula in the `metadata.governance` field.

## Step 4: Reference in Repository

In your project README:

```markdown
## License

This documentation is licensed under the
[OVN License for Digital Resources v2.0](LICENSE.md).
See [pie-chart.json](pie-chart.json) for contributor shares.

Redistribution and use require compliance with the license terms.
```

## Checklist

- [ ] `LICENSE.md` file present with full OVN License v2.0 text
- [ ] `pie-chart.json` with valid contributor data
- [ ] License footer in all documentation files
- [ ] README references the license and pie-chart
- [ ] Pie-chart validates against the JSON Schema
- [ ] Multi-author handling strategy documented (if applicable)
