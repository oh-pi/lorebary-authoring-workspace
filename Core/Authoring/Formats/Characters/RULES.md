# Characters: format rules

Revision: 0.1 — DRAFT, awaiting review.

Evidence: 21 supplied JSON files. These rules apply only to Characters. Documented requirements are the user’s authoring/delivery instructions in the root AGENTS.md; no official importer specification was supplied. Observed fields below are not automatically required fields. Actual LoreBary import: **not tested**.

## Choose a format

| Template | Observed family | Use / limitation |
|---|---|---|
| `card-v2-structured.json` | 18 files; 17 distinct byte contents | `spec`, `spec_version`, `data`; `data.personality` is a JSON-encoded object **inside a string** |
| `card-v2-freeform.json` | 1 file | Same card envelope; empty personality string; `data.extensions.lorebary.isFreeForm` and `freeFormContent` present |
| `detailed-structured-export.json` | 1 file | Detailed root object; personality/background/scenario are objects; messages and relationships are arrays |
| `detailed-freeform-export.json` | 1 file | Detailed root object plus `isFreeForm` and `freeFormContent`; many structured fields remain blank |

These are distinct observed export shapes, not confirmed interchangeable import formats. Two structured-card reference files are byte-identical; duplicate evidence does not establish a requirement.

## Fields and text

Card root literals: `spec: "chara_card_v2"`, `spec_version: "2.0"`. All 19 card files have the same 15 data keys: `name`, `description`, `personality`, `scenario`, `first_mes`, `mes_example`, `creator`, `creator_notes`, `character_version`, `tags`, `system_prompt`, `post_history_instructions`, `alternate_greetings`, `character_book`, `extensions`.

The first twelve named textual fields are strings except `tags` (array); `alternate_greetings` is an array of strings. `character_book` is null in every supplied card; a populated book schema is unknown. `extensions.lorebary` is an object with source/code/download metadata, appearance string, background object, relationships array, gender string, and age/chatName string-or-null. Freeform adds a boolean and a string. The full nested fields and relationship variants are recorded in your own local structure notes; do not flatten them or impose one relationship sample's optional keys universally.

`personality-object.fragment.json` preserves the 25-key nested personality object, including `spectrums` and `sexuality`. For structured cards, serialize this object exactly once and assign the resulting string to `data.personality`. The outer JSON parser must return a **string** there; parsing that string should then return the object. Detailed exports use that object directly. Freeform personality is an empty string in the supplied card; do not try to parse it as JSON.

Appearance uses literal full-width markers such as `【Body】`, `【Face】`, `【Eyes】`, `【Hair】`, `【Attire】`, `【Voice】`; `【Marks & Scars】`, `【Skin】`, `【Scent】`, and `【Other】` also occur. Some fields are empty or use only `【Other】`. `appearance-sections.txt` is one observed layout, not a mandatory list of sections. Dialogue strings use `{{user}}:` and `{{char}}:` with newlines; some are empty. Keep these exact braces and colons. No `<START>` requirement is established by these samples.

Freeform description/content may contain Markdown headings, inline labels, bold markers, and prose. The supplied freeform card duplicates its freeform text in `data.description` and `data.extensions.lorebary.freeFormContent`; preserve consistency when choosing that pattern. These are authoring layouts, not fixed character biographies. Description fields can also contain HTML; do not strip markup accidentally.

Detailed-export `initialMessages[*]` has `id`, `content`, `isEnabled`; `exampleDialogs[*]` has `id`, `userMessage`, `characterResponse`. Detailed `scenario` is `{enabled, content}`. This is **not** the separate Scenarios category's format. Detailed root fields such as author badges, counters, `_loading`, `_fullLoaded`, and `_detailTimestamp` are observed application/export state, not established authoring requirements.

## Check before delivery

Select one family; match its exact fields/types, including empty-string versus null. Resolve identity and metadata slots; never reuse sample codes, badge claims, images or attribution. Check nested personality serialization and freeform duplication. Inspect appearance markers and dialogue prefixes separately from outer JSON. Do not add character-card fields to any other category.

## Observed outer fields

| JSON pointer | Observed types | Files containing field |
|---|---|---:|
| `/_detailTimestamp` | integer | 2/21 |
| `/_fullLoaded` | boolean | 2/21 |
| `/_loading` | boolean | 2/21 |
| `/age` | null | 2/21 |
| `/aiAssist` | object | 2/21 |
| `/allowDownloads` | boolean | 2/21 |
| `/appearance` | string | 2/21 |
| `/author` | string | 2/21 |
| `/authorDisplayedBadges` | array | 2/21 |
| `/authorIsAdmin` | boolean | 2/21 |
| `/authorIsBetaTester` | boolean | 2/21 |
| `/authorIsChildOfFirstForge` | boolean | 2/21 |
| `/authorIsChildOfReforge` | boolean | 2/21 |
| `/authorIsCommunityMod` | boolean | 2/21 |
| `/authorIsDonatorMonthly` | boolean | 2/21 |
| `/authorIsDonatorSingle` | boolean | 2/21 |
| `/authorIsFeatured` | boolean | 2/21 |
| `/authorIsHonoraryGuardian` | boolean | 2/21 |
| `/authorIsLegalAngel` | boolean | 2/21 |
| `/authorIsMod` | boolean | 2/21 |
| `/authorIsOriginUser` | boolean | 2/21 |
| `/authorIsRelicMaker` | boolean | 2/21 |
| `/authorIsStaff` | boolean | 2/21 |
| `/background` | object | 2/21 |
| `/chatName` | null / string | 2/21 |
| `/code` | string | 2/21 |
| `/constantTokens` | integer | 2/21 |
| `/contentWarningDetails` | string | 2/21 |
| `/coverImage` | string | 2/21 |
| `/createdAt` | string | 2/21 |
| `/data` | object | 19/21 |
| `/description` | string | 2/21 |
| `/downloads` | integer | 2/21 |
| `/exampleDialogs` | array | 2/21 |
| `/featured` | boolean | 2/21 |
| `/folderId` | null / string | 2/21 |
| `/freeFormContent` | string | 1/21 |
| `/gender` | string | 2/21 |
| `/hasContentWarning` | boolean | 2/21 |
| `/hasCoverImage` | boolean | 2/21 |
| `/initialMessages` | array | 2/21 |
| `/isFreeForm` | boolean | 1/21 |
| `/isNSFW` | boolean | 2/21 |
| `/isPrivate` | boolean | 2/21 |
| `/isPublic` | boolean | 2/21 |
| `/likes` | integer | 2/21 |
| `/name` | string | 2/21 |
| `/personality` | object | 2/21 |
| `/rating` | null | 2/21 |
| `/ratingCount` | integer | 2/21 |
| `/relationships` | array | 2/21 |
| `/scenario` | object | 2/21 |
| `/showDetails` | boolean | 2/21 |
| `/spec` | string | 19/21 |
| `/spec_version` | string | 19/21 |
| `/tagline` | null | 2/21 |
| `/tags` | array | 2/21 |
| `/updatedAt` | string | 2/21 |
| `/views` | integer | 2/21 |

## Value classification and unresolved assumptions

- **Observed format literals:** only the family-specific discriminators, source/version markers and text delimiters identified above. Keep spelling and type for the selected variant. Repeated values do not prove universal requirements.
- **Replaceable:** all names, descriptions, text bodies, lore, profile data, keywords, identifiers, dates, images, author/license claims and project settings. Blank templates use `__SLOTS__`; booleans/numbers remain typed and require review.
- **Derived/application state:** counters, statistics and export history where present. Provisional blank values are not measurements or proof of platform activity.
- **Uncertain:** importer-required fields, omission/default behavior, complete enums, empty-container item schemas and runtime semantics. Do not resolve these by guessing or copying from another category.

## Provenance and independent verification

These rules summarize observed export structures; no original reference files, personal metadata, source-filename indexes, or original creative material are distributed. Historic sample counts are context, not a claim about the contents of your Reference folders. No importer certification is implied.

Use the blank templates and this rule set as a starting baseline. To verify or extend a variant, create your own content in LoreBary, download it into this category’s Reference folder, compare its structure and text formatting, and record your own decisions. Examples are formatting evidence only. Keep any local evidence notes private unless intentionally sanitized for sharing.
