# Lorebooks: format rules

Revision: 0.2 — updated from the 2026-09-11 rescan; DRAFT templates awaiting review.

Evidence: current counts and variants are given in the revision section below. These rules apply only to Lorebooks. Documented requirements are the user’s authoring/delivery instructions in the root AGENTS.md; no official importer specification was supplied. Observed fields below are not automatically required fields. The reviewed reference collection was reported as generated on LoreBary or submitted and working. This is user-reported compatibility evidence; this workspace has not independently imported its blank templates.

## Revision 0.2: expanded reference check

27 JSON files retain the existing map envelope and the compact/extended entry variants. Seventeen PNG images were also inventoried recursively; none contains a supported embedded asset JSON payload (one has XMP image metadata). Image pixels are not evidence of an import schema.

`meta.creatorUsername` is newly observed as an optional string. Use `creator-username_lorebook.fragment.json` as that metadata value only when matching this variant; do not copy an example account name. No new entry-field type or populated chapter reference schema was established. Some description strings now contain `<p>...</p>` markup; preserve markup when selected, replacing the prose. Existing text-section fragments remain category-specific options.

## Earlier format baseline (retained variants)

The original 17 examples used an object with `name` (string), `description` (string), `entries` (object map), `extensions` (object), and `meta` (object). Entries are keyed by numeric strings such as `"1"`; their `uid` is an integer. Do not turn this map into an array.

| Template | Difference |
|---|---|
| `entry-map-extended_lorebook.json` / `entry-01_lorebook.fragment.json` | Includes `instructions` string and `chapterId` null |
| `entry-map-compact_lorebook.json` / `entry-02_lorebook.fragment.json` | Those two fields are absent |

Entry fields in both shapes: `uid` integer; `key` and `keysecondary` arrays of strings; `comment` and `content` strings; `constant`, `selective`, `disable` booleans; `order` and `position` integers; `category` and `keyMatchMode` strings. Dictionary key order differs between samples and has not been established as semantically significant. Keep a chosen template's order for readable, stable output.

`chapterId` is only observed as null; the shape and resolution of a populated chapter reference are not established. `keyMatchMode` occurs as `partial` and `any`. Entry categories include `background`, `character`, `core`, `item`, `location`, `monster`, `organization`, `other`, `place`, `relationship`, `rule`, `scenario`, `secret`, `species`, `spell`, `world`, and an empty string. This is an observed list, not a complete enum or permission to normalize synonyms.

## Text-field variants

Plain paragraphs and multiple distinct sectioned layouts are observed. Use `text-prose_lorebook.txt` or a matching sectioned fragment. Preserve the literal heading sequence of the chosen fragment, including `/`, `&`, colons and blank lines. Examples include:

- `Physical Appearance:`, `Personality:`, `Background:`, `Abilities/Skills:`, `Role/Motivations:`.
- `Concept/System:`, `How It Works:`, `Origins & History:`, `Scope & Effects on Society:`.
- `Rule Name:`, `Purpose/Function:`, `How It Works:`, `Guidelines for Implementation:`, `Consequences:`.

Location, purpose/function, and time-period variants have their own ordered templates. These are optional content layouts inside `entries[*].content`, not additional JSON fields or universal section requirements. Other exact layouts are traceable in your own reference files; source-specific headings and creative bodies must be replaced, not reused.

## Extensions and metadata

All examples share these observed extension values: `world_info_depth: 2`, `world_info_budget: 2048`, `world_info_min_activations: 0`, `world_info_max_activations: 100`, `world_info_recursive_scanning: true`, `world_info_overflow_alert: true`, `world_info_case_sensitive: false`, `world_info_match_whole_words: false`. Preserve names and types. Their uniformity does not prove that these values are mandatory; treat them as observed configurable defaults.

`meta.title` mirrors `name`; `meta.description` mirrors root description. `meta.entryCount` and `meta.tokenStats.entryCount` must describe the generated entry count. Token statistics are derived values; zeros in blank templates are provisional, not measured token counts. `meta.totalTokens` is zero in the samples that include it despite nonzero `tokenStats.totalTokens`; record this as an observed discrepancy, not a schema error to silently repair. `totalTokens`, `featured`, `changelog`, `lastChanges`, and `lastMeaningfulUpdate` vary in presence. Preserve the selected variant or explicitly document an alternative from the evidence.

## Check before delivery

Check map keys/UIDs for consistency and uniqueness; verify arrays, booleans and numeric values stay typed. Match the compact or extended entry variant. Check content headings and keywords against newly approved lore only. Reconcile duplicate metadata and actual entry counts. Do not claim exact token counts without the appropriate measurement or platform result.

## Current observed fields

Counts below use 27 decoded asset documents, including PNG payloads where present. They are observations, not required-field lists. Exact nested shapes and source mappings remain in the category rules and templates.

### Outer fields

| JSON pointer | Observed types | Documents |
|---|---|---:|
| `/description` | string | 27/27 |
| `/entries` | object | 27/27 |
| `/extensions` | object | 27/27 |
| `/meta` | object | 27/27 |
| `/name` | string | 27/27 |

### Metadata fields

| JSON pointer | Observed types | Documents |
|---|---|---:|
| `/meta/aiAssist` | object | 27/27 |
| `/meta/allowCharacterCreation` | boolean | 27/27 |
| `/meta/author` | string | 27/27 |
| `/meta/category` | string | 27/27 |
| `/meta/changelog` | array | 21/27 |
| `/meta/contentWarningDetails` | string | 27/27 |
| `/meta/creatorUsername` | string | 1/27 |
| `/meta/description` | string | 27/27 |
| `/meta/entryCount` | integer | 27/27 |
| `/meta/featured` | boolean | 21/27 |
| `/meta/hasContentWarning` | boolean | 27/27 |
| `/meta/lastChanges` | object | 14/27 |
| `/meta/lastMeaningfulUpdate` | string | 2/27 |
| `/meta/source` | string | 27/27 |
| `/meta/tags` | array | 27/27 |
| `/meta/title` | string | 27/27 |
| `/meta/tokenStats` | object | 27/27 |
| `/meta/totalTokens` | integer | 21/27 |
| `/meta/version` | string | 27/27 |

## Value classification and unresolved assumptions

- **Observed format literals:** only the family-specific discriminators, source/version markers and text delimiters identified above. Keep spelling and type for the selected variant. Repeated values do not prove universal requirements.
- **Replaceable:** all names, descriptions, text bodies, lore, profile data, keywords, identifiers, dates, images, author/license claims and project settings. Blank templates use `__SLOTS__`; booleans/numbers remain typed and require review.
- **Derived/application state:** counters, statistics and export history where present. Provisional blank values are not measurements or proof of platform activity.
- **Uncertain:** importer-required fields, omission/default behavior, complete enums, empty-container item schemas and runtime semantics. Do not resolve these by guessing or copying from another category.

## Evidence scope

These rules retain observed format variants. Private source files and evidence indexes are not distributed. Compare your own exports when resolving an uncertainty. Counts describe the historical review, not required field presence or an official specification.

## File naming

Use `<name>_lorebook.json` for a standalone JSON asset, `<name>_lorebook.txt` for paste text or a supported text export, and `<name>_lorebook.png` only for a correctly packaged supported PNG card. The suffix identifies the category; it does not determine the schema. Blank templates now carry `_lorebook` in their names. Files ending `.fragment.json` are partial values/blocks, not standalone imports. Leave supplied reference filenames unchanged.
