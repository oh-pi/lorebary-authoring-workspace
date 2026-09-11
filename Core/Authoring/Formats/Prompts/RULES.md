# Prompts: format rules

Revision: 0.1 — DRAFT, awaiting review.

Evidence: 11 supplied JSON files. These rules apply only to Prompts. Documented requirements are the user’s authoring/delivery instructions in the root AGENTS.md; no official importer specification was supplied. Observed fields below are not automatically required fields. Actual LoreBary import: **not tested**.

## Choose a format

Eleven JSON files have eleven matching `.txt` files. Root fields are `title`, `description`, `author`, `category` strings; `modules` array; `recommendations` object; `tags` array; `anyModel` boolean; `meta` object. Each module has string `name`, `description`, `content`, and boolean `isCore`. Seven examples have one module; four have multiple modules (five or six). Those counts are not established limits or minimums.

| Template | Settings types | Content shape |
|---|---|---|
| `prompt-single-string-settings.json` | temperature/maxTokens/contextTokens are strings | One module; plain prose observed |
| `prompt-modular-string-settings.json` | Same three values are strings; models array present | Multiple modules; `((OOC: ...))` wrapper observed |
| `prompt-modular-number-settings.json` | temperature is numeric; maxTokens/contextTokens are integers; models array present | Multiple modules; plain or sectioned content observed |

`recommendations.custom` is a string in every example. `recommendations.models` appears in four and is absent in seven. Do not normalize string settings to numbers automatically or assume `models` is required. Literal model names and their capitalization are replaceable recommendations, not format constants. The two-module blank examples are a reusable authoring convention, not an observed sample cardinality.

`meta` is exactly `source`, `version`, `exportedAt`, all strings. `source: "LoreBary"` and `version: "1.0"` are observed export literals. Timestamps must not be copied or invented as evidence of a platform export.

## Exact text export versus field paste

All eleven paired text exports match this transformation byte-for-byte (UTF-8):

```text
# <title>

Author: <author>
Category: <category>
Tags: <tags joined by comma and space>

## Content
<module contents joined by a blank line, ---, and a blank line>
```

In code notation the body joiner is exactly `"\n\n---\n\n"`. A single module has no separator. The examples have no additional trailing newline after the final module body. The header contains no description, recommendations, per-module names/descriptions, or isCore flags. The text export therefore does not preserve all JSON metadata.

Use `export-single.txt` / `export-modular.txt` for a complete text export. Use `module-prose.txt` / `module-ooc.txt` to paste into **one module content field**. Never include `# title`, `Author:`, `Category:`, `Tags:` or `## Content` in a module merely because they appear in the export document. Do not flatten all modules into one JSON module silently.

`((OOC: ...))` is one observed wrapper, not universal. `{{user}}` and `{{char}}` remain literal where intended. Some module bodies use uppercase sections such as `SESSION CONTRACT`, `COGNITIVE LOOP`, `RESPONSE SHAPE`, and `CONTINUITY`; these belong to the chosen content layout, not all prompts. Reference-defined narrators, policies and creative instructions must be replaced with newly approved content.

## Check before delivery

Match settings types to the chosen variant; preserve module boundaries and isCore booleans. If delivering both formats, reconstruct the header and exact body join and compare. Check the intended destination for field-only text. Neither a matching export pair nor valid JSON proves a LoreBary import.

## Observed outer fields

| JSON pointer | Observed types | Files containing field |
|---|---|---:|
| `/anyModel` | boolean | 11/11 |
| `/author` | string | 11/11 |
| `/category` | string | 11/11 |
| `/description` | string | 11/11 |
| `/meta` | object | 11/11 |
| `/modules` | array | 11/11 |
| `/recommendations` | object | 11/11 |
| `/tags` | array | 11/11 |
| `/title` | string | 11/11 |

## Observed metadata fields

These counts preserve variation; they are not a proposed required-field list. Detailed nested keys, types and per-file shapes are in your own local structure notes.

| JSON pointer | Observed types | Files containing field |
|---|---|---:|
| `/meta/exportedAt` | string | 11/11 |
| `/meta/source` | string | 11/11 |
| `/meta/version` | string | 11/11 |

## Value classification and unresolved assumptions

- **Observed format literals:** only the family-specific discriminators, source/version markers and text delimiters identified above. Keep spelling and type for the selected variant. Repeated values do not prove universal requirements.
- **Replaceable:** all names, descriptions, text bodies, lore, profile data, keywords, identifiers, dates, images, author/license claims and project settings. Blank templates use `__SLOTS__`; booleans/numbers remain typed and require review.
- **Derived/application state:** counters, statistics and export history where present. Provisional blank values are not measurements or proof of platform activity.
- **Uncertain:** importer-required fields, omission/default behavior, complete enums, empty-container item schemas and runtime semantics. Do not resolve these by guessing or copying from another category.

## Provenance and independent verification

These rules summarize observed export structures; no original reference files, personal metadata, source-filename indexes, or original creative material are distributed. Historic sample counts are context, not a claim about the contents of your Reference folders. No importer certification is implied.

Use the blank templates and this rule set as a starting baseline. To verify or extend a variant, create your own content in LoreBary, download it into this category’s Reference folder, compare its structure and text formatting, and record your own decisions. Examples are formatting evidence only. Keep any local evidence notes private unless intentionally sanitized for sharing.
