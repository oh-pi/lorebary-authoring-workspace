# Prompts: format rules

Revision: 0.2 — updated from the 2026-09-11 rescan; DRAFT templates awaiting review.

Evidence: current counts and variants are given in the revision section below. These rules apply only to Prompts. Documented requirements are the user’s authoring/delivery instructions in the root AGENTS.md; no official importer specification was supplied. Observed fields below are not automatically required fields. The reviewed reference collection was reported as generated on LoreBary or submitted and working. This is user-reported compatibility evidence; this workspace has not independently imported its blank templates.

## Revision 0.2: expanded reference and pair check

17 JSON files and 11 text files were inspected. The existing three settings/module template families still cover the observed structure; no new fields or types were found. There are 13 single-module and four multi-module JSON examples. Six JSON filenames have no corresponding text file; a missing companion is not a malformed JSON asset.

All 11 available text companions preserve the same module bodies and exact `\n\n---\n\n` joiner as their current JSON files. They differ in the **Author header value only**, so full-file byte equality does not hold for the current collection. Treat these as differing attribution/export snapshots, not structural failures or permission to overwrite the references. The original baseline had 11 exact pairs. For a newly generated paired delivery, use one approved author value consistently and check the complete transformation; do not copy either reference attribution. The header/body envelope and field-only paste distinction remain unchanged.

## Earlier format baseline (retained variants)

Eleven JSON files have eleven matching `.txt` files. Root fields are `title`, `description`, `author`, `category` strings; `modules` array; `recommendations` object; `tags` array; `anyModel` boolean; `meta` object. Each module has string `name`, `description`, `content`, and boolean `isCore`. Seven examples have one module; four have multiple modules (five or six). Those counts are not established limits or minimums.

| Template | Settings types | Content shape |
|---|---|---|
| `prompt-single-string-settings_prompt.json` | temperature/maxTokens/contextTokens are strings | One module; plain prose observed |
| `prompt-modular-string-settings_prompt.json` | Same three values are strings; models array present | Multiple modules; `((OOC: ...))` wrapper observed |
| `prompt-modular-number-settings_prompt.json` | temperature is numeric; maxTokens/contextTokens are integers; models array present | Multiple modules; plain or sectioned content observed |

`recommendations.custom` is a string in every example. `recommendations.models` appears in four and is absent in seven. Do not normalize string settings to numbers automatically or assume `models` is required. Literal model names and their capitalization are replaceable recommendations, not format constants. The two-module blank examples are a reusable authoring convention, not an observed sample cardinality.

`meta` is exactly `source`, `version`, `exportedAt`, all strings. `source: "LoreBary"` and `version: "1.0"` are observed export literals. Timestamps must not be copied or invented as evidence of a platform export.

## Exact text export versus field paste

The original eleven paired text exports matched this transformation byte-for-byte (UTF-8). Current author-header discrepancies are recorded above:

```text
# <title>

Author: <author>
Category: <category>
Tags: <tags joined by comma and space>

## Content
<module contents joined by a blank line, ---, and a blank line>
```

In code notation the body joiner is exactly `"\n\n---\n\n"`. A single module has no separator. The examples have no additional trailing newline after the final module body. The header contains no description, recommendations, per-module names/descriptions, or isCore flags. The text export therefore does not preserve all JSON metadata.

Use `export-single_prompt.txt` / `export-modular_prompt.txt` for a complete text export. Use `module-prose_prompt.txt` / `module-ooc_prompt.txt` to paste into **one module content field**. Never include `# title`, `Author:`, `Category:`, `Tags:` or `## Content` in a module merely because they appear in the export document. Do not flatten all modules into one JSON module silently.

`((OOC: ...))` is one observed wrapper, not universal. `{{user}}` and `{{char}}` remain literal where intended. Some module bodies use uppercase sections such as `SESSION CONTRACT`, `COGNITIVE LOOP`, `RESPONSE SHAPE`, and `CONTINUITY`; these belong to the chosen content layout, not all prompts. Reference-defined narrators, policies and creative instructions must be replaced with newly approved content.

## Check before delivery

Match settings types to the chosen variant; preserve module boundaries and isCore booleans. If delivering both formats, reconstruct the header and exact body join and compare. Check the intended destination for field-only text. Neither a matching export pair nor valid JSON proves a LoreBary import.

## Current observed fields

Counts below use 17 decoded asset documents, including PNG payloads where present. They are observations, not required-field lists. Exact nested shapes and source mappings remain in the category rules and templates.

### Outer fields

| JSON pointer | Observed types | Documents |
|---|---|---:|
| `/anyModel` | boolean | 17/17 |
| `/author` | string | 17/17 |
| `/category` | string | 17/17 |
| `/description` | string | 17/17 |
| `/meta` | object | 17/17 |
| `/modules` | array | 17/17 |
| `/recommendations` | object | 17/17 |
| `/tags` | array | 17/17 |
| `/title` | string | 17/17 |

### Metadata fields

| JSON pointer | Observed types | Documents |
|---|---|---:|
| `/meta/exportedAt` | string | 17/17 |
| `/meta/source` | string | 17/17 |
| `/meta/version` | string | 17/17 |

## Value classification and unresolved assumptions

- **Observed format literals:** only the family-specific discriminators, source/version markers and text delimiters identified above. Keep spelling and type for the selected variant. Repeated values do not prove universal requirements.
- **Replaceable:** all names, descriptions, text bodies, lore, profile data, keywords, identifiers, dates, images, author/license claims and project settings. Blank templates use `__SLOTS__`; booleans/numbers remain typed and require review.
- **Derived/application state:** counters, statistics and export history where present. Provisional blank values are not measurements or proof of platform activity.
- **Uncertain:** importer-required fields, omission/default behavior, complete enums, empty-container item schemas and runtime semantics. Do not resolve these by guessing or copying from another category.

## Evidence scope

These rules retain observed format variants. Private source files and evidence indexes are not distributed. Compare your own exports when resolving an uncertainty. Counts describe the historical review, not required field presence or an official specification.

## File naming

Use `<name>_prompt.json` for a standalone JSON asset, `<name>_prompt.txt` for paste text or a supported text export, and `<name>_prompt.png` only for a correctly packaged supported PNG card. The suffix identifies the category; it does not determine the schema. Blank templates now carry `_prompt` in their names. Files ending `.fragment.json` are partial values/blocks, not standalone imports. Leave supplied reference filenames unchanged.
