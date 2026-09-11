# Plugins: format rules

Revision: 0.2 — updated from the 2026-09-11 rescan; DRAFT templates awaiting review.

Evidence: current counts and variants are given in the revision section below. These rules apply only to Plugins. Documented requirements are the user’s authoring/delivery instructions in the root AGENTS.md; no official importer specification was supplied. Observed fields below are not automatically required fields. The reviewed reference collection was reported as generated on LoreBary or submitted and working. This is user-reported compatibility evidence; this workspace has not independently imported its blank templates.

## Revision 0.2: expanded reference check

23 JSON files were inspected, plus four image files with no supported embedded asset JSON. The three existing outer families remain represented. All currently observed trigger/action/variable field shapes and their discriminators are covered by the existing fragment sets. Entries may combine those fragments in combinations absent from a particular blank outer example; select each nested fragment independently. A whole entry differing from one illustrative template is not automatically invalid.

`meta.creatorUsername` is a newly observed optional string on full exports. Add the value from `creator-username_plugin.fragment.json` inside `meta` only for the selected variant, using truthful project/account attribution. It is not required on copyright/meta or array families, and no new runtime API or root feature-container schema was established. New description HTML includes a styled `span`; markup must be preserved when selected, and presentation/creative values are replaceable. Reference code was read as data and never executed.

## Earlier format baseline (retained variants) before editing

| Template | Observed files | Outer structure |
|---|---:|---|
| `full-entry-map_plugin.json` | 13 | Root name/author/description/category/tag, object maps, empty feature containers, advancedCode string, logic null, and export meta |
| `copyright-meta-entry-map_plugin.json` | 3 | `_copyright`, `meta`, `entries`, `variables`, `switches`, `agents`, `tables`; no full-export feature shell |
| `array-advanced-code_plugin.json` | 2 | Root name/description/version/author/tags, **arrays** for entries/variables/switches, and advancedCode string |

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

The template chooser identifies every fragment's family source, exact pointer, key set and discriminator. Use it to choose a precise entry, trigger, action or variable shape without reopening creative content. A fragment is not a standalone import file. Repeat/extend blocks only as needed; item counts in blank templates are illustrative.

Check selected family containers first, then every nested trigger/action/state type. Check map key/uid consistency, identifier references, conditions, interpolation, regex escaping and HTML text separately. Do not substitute prose for requested functioning code. Code-enabled deliverables need bounded runtime testing when actually authored; syntax validation alone cannot establish runtime behavior.

## Current observed fields

Counts below use 23 decoded asset documents, including PNG payloads where present. They are observations, not required-field lists. Exact nested shapes and source mappings remain in the category rules and templates.

### Outer fields

| JSON pointer | Observed types | Documents |
|---|---|---:|
| `/_copyright` | object | 3/23 |
| `/actions` | object | 18/23 |
| `/advancedCode` | string | 20/23 |
| `/agents` | array | 21/23 |
| `/author` | string | 20/23 |
| `/category` | string | 18/23 |
| `/conditions` | array | 18/23 |
| `/description` | string | 20/23 |
| `/entries` | array / object | 23/23 |
| `/logic` | null | 18/23 |
| `/meta` | object | 21/23 |
| `/name` | string | 20/23 |
| `/regexPatterns` | array | 18/23 |
| `/stages` | array | 18/23 |
| `/switches` | array / object | 23/23 |
| `/tables` | array | 21/23 |
| `/tag` | string | 18/23 |
| `/tags` | array | 2/23 |
| `/templates` | array | 18/23 |
| `/transformations` | array | 18/23 |
| `/triggerGroups` | array | 18/23 |
| `/variables` | array / object | 23/23 |
| `/version` | string | 2/23 |
| `/weightedPools` | object | 18/23 |

### Metadata fields

| JSON pointer | Observed types | Documents |
|---|---|---:|
| `/meta/aiAssist` | object | 18/23 |
| `/meta/allowDownloads` | boolean | 18/23 |
| `/meta/author` | string | 21/23 |
| `/meta/category` | string | 21/23 |
| `/meta/changelog` | array | 11/23 |
| `/meta/contentWarningDetails` | string | 18/23 |
| `/meta/createdAt` | string | 18/23 |
| `/meta/creatorUsername` | string | 16/23 |
| `/meta/description` | string | 21/23 |
| `/meta/downloadedAt` | string | 18/23 |
| `/meta/downloads` | integer | 18/23 |
| `/meta/forkedFrom` | null | 18/23 |
| `/meta/handbook` | object | 3/23 |
| `/meta/hasContentWarning` | boolean | 18/23 |
| `/meta/lastChanges` | object | 10/23 |
| `/meta/lastMeaningfulUpdate` | string | 1/23 |
| `/meta/name` | string | 21/23 |
| `/meta/public` | boolean | 18/23 |
| `/meta/showDetailedView` | boolean | 18/23 |
| `/meta/source` | string | 18/23 |
| `/meta/tag` | string | 21/23 |
| `/meta/tags` | array | 21/23 |
| `/meta/updatedAt` | string | 18/23 |
| `/meta/version` | string | 18/23 |

## Value classification and unresolved assumptions

- **Observed format literals:** only the family-specific discriminators, source/version markers and text delimiters identified above. Keep spelling and type for the selected variant. Repeated values do not prove universal requirements.
- **Replaceable:** all names, descriptions, text bodies, lore, profile data, keywords, identifiers, dates, images, author/license claims and project settings. Blank templates use `__SLOTS__`; booleans/numbers remain typed and require review.
- **Derived/application state:** counters, statistics and export history where present. Provisional blank values are not measurements or proof of platform activity.
- **Uncertain:** importer-required fields, omission/default behavior, complete enums, empty-container item schemas and runtime semantics. Do not resolve these by guessing or copying from another category.

## Evidence scope

These rules retain observed format variants. Private source files and evidence indexes are not distributed. Compare your own exports when resolving an uncertainty. Counts describe the historical review, not required field presence or an official specification.

## File naming

Use `<name>_plugin.json` for a standalone JSON asset, `<name>_plugin.txt` for paste text or a supported text export, and `<name>_plugin.png` only for a correctly packaged supported PNG card. The suffix identifies the category; it does not determine the schema. Blank templates now carry `_plugin` in their names. Files ending `.fragment.json` are partial values/blocks, not standalone imports. Leave supplied reference filenames unchanged.
