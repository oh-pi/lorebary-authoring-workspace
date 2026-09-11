# Plugins: format rules

Revision: 0.1 — DRAFT, awaiting review.

Evidence: 18 supplied JSON files. These rules apply only to Plugins. Documented requirements are the user’s authoring/delivery instructions in the root AGENTS.md; no official importer specification was supplied. Observed fields below are not automatically required fields. Actual LoreBary import: **not tested**.

## Choose a format before editing

| Template | Observed files | Outer structure |
|---|---:|---|
| `full-entry-map.json` | 13 | Root name/author/description/category/tag, object maps, empty feature containers, advancedCode string, logic null, and export meta |
| `copyright-meta-entry-map.json` | 3 | `_copyright`, `meta`, `entries`, `variables`, `switches`, `agents`, `tables`; no full-export feature shell |
| `array-advanced-code.json` | 2 | Root name/description/version/author/tags, **arrays** for entries/variables/switches, and advancedCode string |

The array family has no LoreBary source/export metadata in these files; its import/runtime compatibility is particularly uncertain. Preserve it as a separate candidate shape. Do not silently translate it into the map format or treat its JavaScript as a verified LoreBary API. No reference code was executed or copied into templates.

## Map entries and triggers

`entries` is an object keyed by numeric strings, with integer `uid` inside each entry. Map entry fields include `name`, `comment`, `order`, `triggerGroups` array, `triggerLogic`, `actions` object and `advancedCode` string. The full export includes `actionLogic`; the copyright/meta samples do not. These are distinct entry variants.

Two trigger-object shapes occur. Copyright/meta triggers include fields such as `id`, `name`, `flags`, `priority`; full-export triggers include `variableValueMin`, `variableValueMax`, `agentId`, `agentMatch`, `agentValue`, and message-length fields instead. Keep the complete chosen trigger shape from `trigger-*.fragment.json`; do not combine them into an invented superset.

Observed trigger type strings: `always`, `keyword`, `messageCount`, `messageCountInterval`, `message_count`, `random`, `regex`, `switch`, `variable`. The differences in message-count spellings are preserved, not declared equivalent or corrected. `chance` values are integers in examples; their scale/semantics are unverified. `variableValue` and its min/max variants are strings even when they contain digits; retain that type. `switchState` is boolean. AND/OR logic strings and regex flags are configurable observed controls, not host instructions.

## Actions and state

`actions.default` is an array. Choose the matching action fragment:

| Type | Observed additional fields |
|---|---|
| `add_message` | `role` string, `pool` array of strings; `append` boolean in some variants |
| `set_variable` | `variable` string, `value` integer or string, `operation` string (`set`, `plus`, `minus`) |
| `set_switch` | `switch` string, `value` boolean |
| `replace` | `find`, `replace`, `replaceTarget` strings; observed target `bot` |
| `embed_image` | `imageUrl`, `placement` strings; observed placement `top` / `bottom` |

Map `variables` use variable-name keys with `{type, value}` objects; observed number and string types must agree with their values. Map `switches` use switch-name keys with **boolean values**, not objects. Identifiers in triggers/actions/message tokens must be updated consistently with declarations. A message that merely asks for a state change is not evidence that a programmatic state change occurs.

Array entries instead use string `id`, `name`, boolean `enabled`, `triggerType`, integer `priority`, `order`, `position`, `messageInterval`, and `messagePool` string arrays. Some also have `conditions` string arrays or `primaryKeys` string arrays. Observed triggerType values: `constant`, `interval`, `anyKey`. Array variables use `{name, type, defaultValue, persistent}` with string/integer/boolean defaults. Array switches use `{name, defaultValue}`. Keep these separate from the map family. Expression/API semantics remain untested.

Full export's root feature containers are observed empty: `triggerGroups`, `stages`, `conditions`, `templates`, `transformations`, `regexPatterns`, `agents`, `tables` are arrays; `actions`, `weightedPools` are objects; `logic` is null. Their populated schemas are not established. Entries can contain populated trigger/action structures even while root containers are empty.

## Message text and metadata

Message pools contain plain text, `[System Note: ...]`, `[OOC: ...]`, multi-line headings/status labels, HTML/CSS tags, variable interpolation and `{{user}}` / `{{char}}`. Use a matching message layout; preserve delimiters and markup while replacing authored prose. Status-panel titles, menu labels, variable names, images and narrative effects are project content, not fixed rules. `advancedCode` is a string field; blank/placeholder code is not an implemented runtime. Never copy reference code to provide functionality accidentally.

`tag: "PLUGIN"` is an observed literal in map families. Full export uses `meta.showDetailedView`, **not** `showDetails`. Metadata repeats identity fields and contains visibility/download flags, warnings, forkedFrom null, dates, aiAssist, downloads count, optional history, source/version. Copyright/meta has `_copyright` with source/website/notice/license strings and `meta.handbook.title` observed as `How to Use This Plugin`. The copyright block's claims are not reusable license text; supply only truthful metadata for new content. Its presence does not authorize copying creative material.

## Fragment chooser and verification

The fragment register below identifies every fragment's family source, exact pointer, key set and discriminator. Use it to choose a precise entry, trigger, action or variable shape without reopening creative content. A fragment is not a standalone import file. Repeat/extend blocks only as needed; item counts in blank templates are illustrative.

Check selected family containers first, then every nested trigger/action/state type. Check map key/uid consistency, identifier references, conditions, interpolation, regex escaping and HTML text separately. Do not substitute prose for requested functioning code. Code-enabled deliverables need bounded runtime testing when actually authored; syntax validation alone cannot establish runtime behavior.

## Observed outer fields

| JSON pointer | Observed types | Files containing field |
|---|---|---:|
| `/_copyright` | object | 3/18 |
| `/actions` | object | 13/18 |
| `/advancedCode` | string | 15/18 |
| `/agents` | array | 16/18 |
| `/author` | string | 15/18 |
| `/category` | string | 13/18 |
| `/conditions` | array | 13/18 |
| `/description` | string | 15/18 |
| `/entries` | array / object | 18/18 |
| `/logic` | null | 13/18 |
| `/meta` | object | 16/18 |
| `/name` | string | 15/18 |
| `/regexPatterns` | array | 13/18 |
| `/stages` | array | 13/18 |
| `/switches` | array / object | 18/18 |
| `/tables` | array | 16/18 |
| `/tag` | string | 13/18 |
| `/tags` | array | 2/18 |
| `/templates` | array | 13/18 |
| `/transformations` | array | 13/18 |
| `/triggerGroups` | array | 13/18 |
| `/variables` | array / object | 18/18 |
| `/version` | string | 2/18 |
| `/weightedPools` | object | 13/18 |

## Observed metadata fields

These counts preserve variation; they are not a proposed required-field list. Detailed nested keys, types and per-file shapes are in your own local structure notes.

| JSON pointer | Observed types | Files containing field |
|---|---|---:|
| `/meta/aiAssist` | object | 13/18 |
| `/meta/allowDownloads` | boolean | 13/18 |
| `/meta/author` | string | 16/18 |
| `/meta/category` | string | 16/18 |
| `/meta/changelog` | array | 10/18 |
| `/meta/contentWarningDetails` | string | 13/18 |
| `/meta/createdAt` | string | 13/18 |
| `/meta/description` | string | 16/18 |
| `/meta/downloadedAt` | string | 13/18 |
| `/meta/downloads` | integer | 13/18 |
| `/meta/forkedFrom` | null | 13/18 |
| `/meta/handbook` | object | 3/18 |
| `/meta/hasContentWarning` | boolean | 13/18 |
| `/meta/lastChanges` | object | 8/18 |
| `/meta/lastMeaningfulUpdate` | string | 1/18 |
| `/meta/name` | string | 16/18 |
| `/meta/public` | boolean | 13/18 |
| `/meta/showDetailedView` | boolean | 13/18 |
| `/meta/source` | string | 13/18 |
| `/meta/tag` | string | 16/18 |
| `/meta/tags` | array | 16/18 |
| `/meta/updatedAt` | string | 13/18 |
| `/meta/version` | string | 13/18 |

## Value classification and unresolved assumptions

- **Observed format literals:** only the family-specific discriminators, source/version markers and text delimiters identified above. Keep spelling and type for the selected variant. Repeated values do not prove universal requirements.
- **Replaceable:** all names, descriptions, text bodies, lore, profile data, keywords, identifiers, dates, images, author/license claims and project settings. Blank templates use `__SLOTS__`; booleans/numbers remain typed and require review.
- **Derived/application state:** counters, statistics and export history where present. Provisional blank values are not measurements or proof of platform activity.
- **Uncertain:** importer-required fields, omission/default behavior, complete enums, empty-container item schemas and runtime semantics. Do not resolve these by guessing or copying from another category.

## Provenance and independent verification

These rules summarize observed export structures; no original reference files, personal metadata, source-filename indexes, or original creative material are distributed. Historic sample counts are context, not a claim about the contents of your Reference folders. No importer certification is implied.

Use the blank templates and this rule set as a starting baseline. To verify or extend a variant, create your own content in LoreBary, download it into this category’s Reference folder, compare its structure and text formatting, and record your own decisions. Examples are formatting evidence only. Keep any local evidence notes private unless intentionally sanitized for sharing.
