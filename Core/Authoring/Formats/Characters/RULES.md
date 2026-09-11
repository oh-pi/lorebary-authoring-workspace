# Characters: format rules

Revision: 0.2 — updated from the 2026-09-11 rescan; DRAFT templates awaiting review.

Evidence: current counts and variants are given in the revision section below. These rules apply only to Characters. Documented requirements are the user’s authoring/delivery instructions in the root AGENTS.md; no official importer specification was supplied. Observed fields below are not automatically required fields. The reviewed reference collection was reported as generated on LoreBary or submitted and working. This is user-reported compatibility evidence; this workspace has not independently imported its blank templates.

## Revision 0.2: current JSON and PNG variants

The rescan covers 31 JSON files and 20 PNG cards (51 decoded asset documents). Among JSON files, 21 use card-v2 envelopes (20 structured, including one 29-key personality; one freeform); nine use detailed roots (eight structured, one freeform); one uses a 38-key structured root without detailed-loader state. Duplicate downloads are not independent proof of requirements.

- **JSON card family:** retains the 15 data keys, including null `character_book`. Its structured `data.personality` is a JSON-encoded string. The extended variant adds string fields `careerGoals`, `personalGrowth`, `relationshipGoals`, and `unfinishedBusiness` to the original 25-key personality. Use `card-v2-extended-personality_character.json` / `personality-extended_character.fragment.json` only for that variant; do not add those keys universally.
- **PNG card payload family:** all 20 PNGs contain a `tEXt` chunk named `chara` whose value is base64-encoded UTF-8 JSON. Decoding yields card-v2 with 14 data keys: `character_book` is absent. `data.personality` is prose (18 cards) or an empty string (two), not serialized JSON. `data.extensions.lorebary` has exactly `code`, `meta`, `appearance`, `personality`, `background`, `scenario`, `relationships`, `exampleDialogs`, `initialMessages`; here personality is an object, scenario is `{enabled, content}`, and `meta` is empty in all 20. Do not transplant the JSON-download extension shape. No `isFreeForm` / `freeFormContent` keys are present in these PNG payloads, including those with an empty personality. See `png-card-payload_character.json` and `png-card-empty-personality-payload_character.json`.
- **Structured roots:** use `structured-root-export_character.json` for the observed 38-key root or a matching detailed template for the 54/56-key loader-state roots. Root `age` can be string or null and `coverImage` can be string or null. Preserve the source variant's type, not one universal default. `detailed-populated-export_character.json` demonstrates populated arrays of strings where earlier detailed references were empty. These are root variants, not card fields.

PNG payload templates are JSON extracted from an image container, not finished PNG assets. A PNG delivery needs appropriate user-owned/new artwork, the correct chunk key/encoding, valid CRCs, and an extraction round trip; changing a `.json` extension to `.png` does not produce a card. Packaging/import is not tested here. PNGs and similarly named JSON downloads need not represent the same export shape.

`<START>` is now observed before dialogue exchanges in PNG `data.mes_example`; `dialogue-start_character.txt` preserves `<START>`, `{{user}}:` and `{{char}}:` with newlines. Existing dialogue without `<START>` remains valid evidence. `【Movement】` and `【Footwear】` are additional optional appearance markers; the two new appearance fragments preserve their respective observed sequences, not a synthetic mandatory list. HTML variants now include `code`, `h3`, `hr`, and styled containers; style values and authored headings remain replaceable presentation content. Use the matching text fragments and compare your own exports for additional layouts.

## Earlier format baseline (retained variants)

| Template | Observed family | Use / limitation |
|---|---|---|
| `card-v2-structured_character.json` | 18 files; 17 distinct byte contents | `spec`, `spec_version`, `data`; `data.personality` is a JSON-encoded object **inside a string** |
| `card-v2-freeform_character.json` | 1 file | Same card envelope; empty personality string; `data.extensions.lorebary.isFreeForm` and `freeFormContent` present |
| `detailed-structured-export_character.json` | 1 file | Detailed root object; personality/background/scenario are objects; messages and relationships are arrays |
| `detailed-freeform-export_character.json` | 1 file | Detailed root object plus `isFreeForm` and `freeFormContent`; many structured fields remain blank |

These are distinct observed export shapes, not confirmed interchangeable import formats. Two structured-card reference files are byte-identical; duplicate evidence does not establish a requirement.

## Fields and text

Card root literals: `spec: "chara_card_v2"`, `spec_version: "2.0"`. All 19 card files have the same 15 data keys: `name`, `description`, `personality`, `scenario`, `first_mes`, `mes_example`, `creator`, `creator_notes`, `character_version`, `tags`, `system_prompt`, `post_history_instructions`, `alternate_greetings`, `character_book`, `extensions`.

The first twelve named textual fields are strings except `tags` (array); `alternate_greetings` is an array of strings. `character_book` is null in every supplied card; a populated book schema is unknown. `extensions.lorebary` is an object with source/code/download metadata, appearance string, background object, relationships array, gender string, and age/chatName string-or-null. Freeform adds a boolean and a string. The full nested fields and relationship variants are recorded in the category rules and templates; do not flatten them or impose one relationship sample's optional keys universally.

`personality-object_character.fragment.json` preserves the 25-key nested personality object, including `spectrums` and `sexuality`. For structured cards, serialize this object exactly once and assign the resulting string to `data.personality`. The outer JSON parser must return a **string** there; parsing that string should then return the object. Detailed exports use that object directly. Freeform personality is an empty string in the supplied card; do not try to parse it as JSON.

Appearance uses literal full-width markers such as `【Body】`, `【Face】`, `【Eyes】`, `【Hair】`, `【Attire】`, `【Voice】`; `【Marks & Scars】`, `【Skin】`, `【Scent】`, and `【Other】` also occur. Some fields are empty or use only `【Other】`. `appearance-sections_character.txt` is one observed layout, not a mandatory list of sections. Dialogue strings use `{{user}}:` and `{{char}}:` with newlines; some are empty. Keep these exact braces and colons. The earlier JSON examples did not establish `<START>`; the PNG variant described above now supplies that optional layout.

Freeform description/content may contain Markdown headings, inline labels, bold markers, and prose. The supplied freeform card duplicates its freeform text in `data.description` and `data.extensions.lorebary.freeFormContent`; preserve consistency when choosing that pattern. These are authoring layouts, not fixed character biographies. Description fields can also contain HTML; do not strip markup accidentally.

Detailed-export `initialMessages[*]` has `id`, `content`, `isEnabled`; `exampleDialogs[*]` has `id`, `userMessage`, `characterResponse`. Detailed `scenario` is `{enabled, content}`. This is **not** the separate Scenarios category's format. Detailed root fields such as author badges, counters, `_loading`, `_fullLoaded`, and `_detailTimestamp` are observed application/export state, not established authoring requirements.

## Check before delivery

Select one family; match its exact fields/types, including empty-string versus null. Resolve identity and metadata slots; never reuse sample codes, badge claims, images or attribution. Check nested personality serialization and freeform duplication. Inspect appearance markers and dialogue prefixes separately from outer JSON. Do not add character-card fields to any other category.

## Current observed fields

Counts below use 51 decoded asset documents, including PNG payloads where present. They are observations, not required-field lists. Exact nested shapes and source mappings remain in the category rules and templates.

### Outer fields

| JSON pointer | Observed types | Documents |
|---|---|---:|
| `/_detailTimestamp` | integer | 9/51 |
| `/_fullLoaded` | boolean | 9/51 |
| `/_loading` | boolean | 10/51 |
| `/age` | null / string | 9/51 |
| `/aiAssist` | object | 9/51 |
| `/allowDownloads` | boolean | 9/51 |
| `/appearance` | string | 9/51 |
| `/author` | string | 10/51 |
| `/authorDisplayedBadges` | array | 10/51 |
| `/authorIsAdmin` | boolean | 10/51 |
| `/authorIsBetaTester` | boolean | 10/51 |
| `/authorIsChildOfFirstForge` | boolean | 10/51 |
| `/authorIsChildOfReforge` | boolean | 10/51 |
| `/authorIsCommunityMod` | boolean | 10/51 |
| `/authorIsDonatorMonthly` | boolean | 10/51 |
| `/authorIsDonatorSingle` | boolean | 10/51 |
| `/authorIsFeatured` | boolean | 10/51 |
| `/authorIsHonoraryGuardian` | boolean | 10/51 |
| `/authorIsLegalAngel` | boolean | 10/51 |
| `/authorIsMod` | boolean | 10/51 |
| `/authorIsOriginUser` | boolean | 10/51 |
| `/authorIsRelicMaker` | boolean | 10/51 |
| `/authorIsStaff` | boolean | 10/51 |
| `/background` | object | 9/51 |
| `/chatName` | null / string | 9/51 |
| `/code` | string | 10/51 |
| `/constantTokens` | integer | 9/51 |
| `/contentWarningDetails` | string | 10/51 |
| `/coverImage` | null / string | 10/51 |
| `/createdAt` | string | 10/51 |
| `/data` | object | 41/51 |
| `/description` | string | 10/51 |
| `/downloads` | integer | 10/51 |
| `/exampleDialogs` | array | 9/51 |
| `/featured` | boolean | 10/51 |
| `/folderId` | null / string | 10/51 |
| `/freeFormContent` | string | 1/51 |
| `/gender` | string | 10/51 |
| `/hasContentWarning` | boolean | 10/51 |
| `/hasCoverImage` | boolean | 10/51 |
| `/initialMessages` | array | 9/51 |
| `/isFreeForm` | boolean | 1/51 |
| `/isNSFW` | boolean | 10/51 |
| `/isPrivate` | boolean | 10/51 |
| `/isPublic` | boolean | 10/51 |
| `/likes` | integer | 9/51 |
| `/name` | string | 10/51 |
| `/personality` | object | 9/51 |
| `/rating` | null | 10/51 |
| `/ratingCount` | integer | 10/51 |
| `/relationships` | array | 9/51 |
| `/scenario` | object | 9/51 |
| `/showDetails` | boolean | 9/51 |
| `/spec` | string | 41/51 |
| `/spec_version` | string | 41/51 |
| `/tagline` | null | 10/51 |
| `/tags` | array | 10/51 |
| `/updatedAt` | string | 10/51 |
| `/views` | integer | 10/51 |

## Value classification and unresolved assumptions

- **Observed format literals:** only the family-specific discriminators, source/version markers and text delimiters identified above. Keep spelling and type for the selected variant. Repeated values do not prove universal requirements.
- **Replaceable:** all names, descriptions, text bodies, lore, profile data, keywords, identifiers, dates, images, author/license claims and project settings. Blank templates use `__SLOTS__`; booleans/numbers remain typed and require review.
- **Derived/application state:** counters, statistics and export history where present. Provisional blank values are not measurements or proof of platform activity.
- **Uncertain:** importer-required fields, omission/default behavior, complete enums, empty-container item schemas and runtime semantics. Do not resolve these by guessing or copying from another category.

## Evidence scope

These rules retain observed format variants. Private source files and evidence indexes are not distributed. Compare your own exports when resolving an uncertainty. Counts describe the historical review, not required field presence or an official specification.

## File naming

Use `<name>_character.json` for a standalone JSON asset, `<name>_character.txt` for paste text or a supported text export, and `<name>_character.png` only for a correctly packaged supported PNG card. The suffix identifies the category; it does not determine the schema. Blank templates now carry `_character` in their names. Files ending `.fragment.json` are partial values/blocks, not standalone imports. Leave supplied reference filenames unchanged.
