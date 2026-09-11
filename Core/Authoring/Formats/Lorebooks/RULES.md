# Lorebooks: format rules

Revision: 0.1 — DRAFT, awaiting review.

Evidence: 17 supplied JSON files. These rules apply only to Lorebooks. Documented requirements are the user’s authoring/delivery instructions in the root AGENTS.md; no official importer specification was supplied. Observed fields below are not automatically required fields. Actual LoreBary import: **not tested**.

## Choose a format

All 17 examples use an object with `name` (string), `description` (string), `entries` (object map), `extensions` (object), and `meta` (object). Entries are keyed by numeric strings such as `"1"`; their `uid` is an integer. Do not turn this map into an array.

| Template | Difference |
|---|---|
| `entry-map-extended.json` / `entry-01.fragment.json` | Includes `instructions` string and `chapterId` null |
| `entry-map-compact.json` / `entry-02.fragment.json` | Those two fields are absent |

Entry fields in both shapes: `uid` integer; `key` and `keysecondary` arrays of strings; `comment` and `content` strings; `constant`, `selective`, `disable` booleans; `order` and `position` integers; `category` and `keyMatchMode` strings. Dictionary key order differs between samples and has not been established as semantically significant. Keep a chosen template's order for readable, stable output.

`chapterId` is only observed as null; the shape and resolution of a populated chapter reference are not established. `keyMatchMode` occurs as `partial` and `any`. Entry categories include `background`, `character`, `core`, `item`, `location`, `monster`, `organization`, `other`, `place`, `relationship`, `rule`, `scenario`, `secret`, `species`, `spell`, `world`, and an empty string. This is an observed list, not a complete enum or permission to normalize synonyms.

## Text-field variants

Plain paragraphs and multiple distinct sectioned layouts are observed. Use `text-prose.txt` or a matching sectioned fragment. Preserve the literal heading sequence of the chosen fragment, including `/`, `&`, colons and blank lines. Examples include:

- `Physical Appearance:`, `Personality:`, `Background:`, `Abilities/Skills:`, `Role/Motivations:`.
- `Concept/System:`, `How It Works:`, `Origins & History:`, `Scope & Effects on Society:`.
- `Rule Name:`, `Purpose/Function:`, `How It Works:`, `Guidelines for Implementation:`, `Consequences:`.

Location, purpose/function, and time-period variants have their own ordered templates. These are optional content layouts inside `entries[*].content`, not additional JSON fields or universal section requirements. Other exact layouts are traceable in your own local text-layout notes; source-specific headings and creative bodies must be replaced, not reused.

## Extensions and metadata

All examples share these observed extension values: `world_info_depth: 2`, `world_info_budget: 2048`, `world_info_min_activations: 0`, `world_info_max_activations: 100`, `world_info_recursive_scanning: true`, `world_info_overflow_alert: true`, `world_info_case_sensitive: false`, `world_info_match_whole_words: false`. Preserve names and types. Their uniformity does not prove that these values are mandatory; treat them as observed configurable defaults.

`meta.title` mirrors `name`; `meta.description` mirrors root description. `meta.entryCount` and `meta.tokenStats.entryCount` must describe the generated entry count. Token statistics are derived values; zeros in blank templates are provisional, not measured token counts. `meta.totalTokens` is zero in the samples that include it despite nonzero `tokenStats.totalTokens`; record this as an observed discrepancy, not a schema error to silently repair. `totalTokens`, `featured`, `changelog`, `lastChanges`, and `lastMeaningfulUpdate` vary in presence. Preserve the selected variant or explicitly document an alternative from the evidence.

## Check before delivery

Check map keys/UIDs for consistency and uniqueness; verify arrays, booleans and numeric values stay typed. Match the compact or extended entry variant. Check content headings and keywords against newly approved lore only. Reconcile duplicate metadata and actual entry counts. Do not claim exact token counts without the appropriate measurement or platform result.

## Observed outer fields

| JSON pointer | Observed types | Files containing field |
|---|---|---:|
| `/description` | string | 17/17 |
| `/entries` | object | 17/17 |
| `/extensions` | object | 17/17 |
| `/meta` | object | 17/17 |
| `/name` | string | 17/17 |

## Observed metadata fields

These counts preserve variation; they are not a proposed required-field list. Detailed nested keys, types and per-file shapes are in your own local structure notes.

| JSON pointer | Observed types | Files containing field |
|---|---|---:|
| `/meta/aiAssist` | object | 17/17 |
| `/meta/allowCharacterCreation` | boolean | 17/17 |
| `/meta/author` | string | 17/17 |
| `/meta/category` | string | 17/17 |
| `/meta/changelog` | array | 16/17 |
| `/meta/contentWarningDetails` | string | 17/17 |
| `/meta/description` | string | 17/17 |
| `/meta/entryCount` | integer | 17/17 |
| `/meta/featured` | boolean | 16/17 |
| `/meta/hasContentWarning` | boolean | 17/17 |
| `/meta/lastChanges` | object | 13/17 |
| `/meta/lastMeaningfulUpdate` | string | 2/17 |
| `/meta/source` | string | 17/17 |
| `/meta/tags` | array | 17/17 |
| `/meta/title` | string | 17/17 |
| `/meta/tokenStats` | object | 17/17 |
| `/meta/totalTokens` | integer | 16/17 |
| `/meta/version` | string | 17/17 |

## Value classification and unresolved assumptions

- **Observed format literals:** only the family-specific discriminators, source/version markers and text delimiters identified above. Keep spelling and type for the selected variant. Repeated values do not prove universal requirements.
- **Replaceable:** all names, descriptions, text bodies, lore, profile data, keywords, identifiers, dates, images, author/license claims and project settings. Blank templates use `__SLOTS__`; booleans/numbers remain typed and require review.
- **Derived/application state:** counters, statistics and export history where present. Provisional blank values are not measurements or proof of platform activity.
- **Uncertain:** importer-required fields, omission/default behavior, complete enums, empty-container item schemas and runtime semantics. Do not resolve these by guessing or copying from another category.

## Provenance and independent verification

These rules summarize observed export structures; no original reference files, personal metadata, source-filename indexes, or original creative material are distributed. Historic sample counts are context, not a claim about the contents of your Reference folders. No importer certification is implied.

Use the blank templates and this rule set as a starting baseline. To verify or extend a variant, create your own content in LoreBary, download it into this category’s Reference folder, compare its structure and text formatting, and record your own decisions. Examples are formatting evidence only. Keep any local evidence notes private unless intentionally sanitized for sharing.
