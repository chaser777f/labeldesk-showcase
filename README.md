# LabelDesk

**Compare saved label text, explain differences, and keep the evidence traceable.**

An AI-assisted personal Python project exploring data verification and review workflows for public drug-label records. It compares saved DailyMed label versions and checks selected wording against saved generic-label text. Its outputs are review leads, not regulatory or medical conclusions.

## Start with the sample

- [Readable sample report](SAMPLE-REPORT.md)
- [Formatted HTML report](sample/glenmark-case.html) — download and open locally; GitHub displays HTML source.
- [Focused evidence JSON](sample/glenmark-evidence.json) — versions, acquisition timestamps, public source URLs and SHA-256 hashes.

To view the formatted report, choose **Code → Download ZIP** on this repository, extract the entire ZIP, and open `sample/glenmark-case.html` in your browser. Keep the extracted folder structure intact so the report's link to `glenmark-evidence.json` works. No installation is needed.

Evidence was acquired October 2, 2026. This showcase does not claim those saved records describe today's labels or distribution.

## What the project demonstrates

| Problem | How the comparison handles it |
| --- | --- |
| Formatting looks like a substantive change | Normalizes sentence splits, reordered parts, abbreviations and equivalent range formatting. |
| Similar wording hides an important edit | Distinguishes changed numbers, units and negation from minor editorial differences. |
| A section contains images instead of readable text | Marks it not checked and requests manual review rather than reporting a missing sentence. |
| Old records distort a summary | Separates publication timing and discontinued records; unknown or mixed status prevents automatic exclusion. |
| A product match looks more certain than it is | Labels Orange Book matches as inferred, explains the matching fields and calls for expert confirmation. |
| A result cannot be traced back | Retains source responses by SHA-256 and links findings to exact versions and acquisition records. |

The audit also corrected a section-selection bug: summary text outside Recent Major Changes could be treated as a comparison source. Regression coverage was added around these reporting and comparison cases.

## Verification

On October 3, 2026, automated checks run with AI assistance against the local project produced:

- **82 tests passed** with `python -m unittest discover -s tests -t . -q`.
- **721 saved source-object hashes verified**, plus report totals, match references, HTML links and evidence hashes, using the retained-report verifier.

The first sandboxed test attempt hit Windows temporary-directory permissions; the unrestricted offline rerun passed. These checks establish tested software behavior and retained-data consistency, not clinical accuracy, expert approval or customer adoption. They are not represented as Chase independently performing 82 manual tests.

## Workflow and implementation

The Python application separates network acquisition from offline comparison. Acquisition retains DailyMed XML and FDA Orange Book evidence with manifests. Offline report building compares sections, groups review cases and produces self-contained HTML and structured JSON. A labeling specialist would then assess whether a match and the apparent difference are meaningful.

## Current limits

- Product relationships are inferred from ingredient, dosage form, route and strength, with a documented fallback when an exact strength match is unavailable.
- Image-only material requires manual review; authorized generics are outside the checked scope.
- A publication date or retained wording does not establish a late submission, noncompliance, or current distribution.
- No independent labeling-specialist validation or customer traction is claimed here.

## Project credit and repository scope

Chase's personal project, developed with AI assistance. This repository contains selected documentation and a dated sample based on public records. Application source, the full evidence store, local paths, outreach drafts and credentials are not included. No open-source license for the application is granted by this showcase.
