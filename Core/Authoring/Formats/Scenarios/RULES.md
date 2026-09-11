# Scenarios: format rules

Revision: 0.2 — updated from the 2026-09-11 rescan; DRAFT templates awaiting review.

Evidence: current counts and variants are given in the revision section below. These rules apply only to Scenarios. Documented requirements are the user’s authoring/delivery instructions in the root AGENTS.md; no official importer specification was supplied. Observed fields below are not automatically required fields. The reviewed reference collection was reported as generated on LoreBary or submitted and working. This is user-reported compatibility evidence; this workspace has not independently imported its blank templates.

## Revision 0.2: repopulated references

The revision reviewed 18 scenario JSON files. The existing scenario root/metadata envelope and content-string distinction remain supported. `meta.creatorUsername` is a newly observed optional string: use `creator-username_scenario.fragment.json` as its value only when matching that metadata variant. Do not promote it into a universal requirement.

Existing scenario text layouts remain available as historical observed variants even when their original source file is no longer present. Earlier observed variants are retained in the templates. Compare your own new files with the matching templates for their own heading sequences; authored titles/headings and prose are replaceable. New exports do not make an older template erroneous merely through differing optional metadata or prose. The collection still does not establish a populated `lorebooks`/`plugins` array item schema.

## Earlier format baseline (retained variants)

All 17 examples use `name`, `author`, `description`, `category`, `content` strings; `lorebooks` and `plugins` arrays; and a `meta` object. Ten include `meta.lastChanges` and seven omit it. Use the matching outer template. These counts describe exports, not required/optional rules proven by an importer.

## Fields and text

`meta.rules` has **six string fields**: `world`, `characters`, `player`, `narrative`, `goals`, `boundaries`. Also preserve the separate `meta.worldRules` string, plus `tone` and `pov` strings. If root and metadata name/author/category/description repeat, keep their intended values synchronized. `Other` and `other` both occur as categories; do not silently recase them.

The opening content is a string, distinct from `meta.rules` and HTML-capable description. It may be plain prose, an intake layout, or a sectioned layout. Choose a field-only `content-*.txt` template:

| Variant | Literal heading sequence |
|---|---|
| logistics | `SETTING` → `STARTING CAST` → `CURRENT LOGISTICS` → `BEGINNING START` → `DELAYED ENTRY` |
| known-facts | `SETTING` → `STARTING CAST` → `KNOWN FACTS` → `BEGINNING START` → `DELAYED ENTRY` |
| contract | `SETTING` → `STARTING CAST` → `INCITING CONTRACT` → `BEGINNING START` → `DELAYED ENTRY` |
| ensemble | `RECOMMENDED LOREBOOK` → `RECOMMENDED PLUGIN` → `FORMAT` → `SETTING` → `USER POSITION` → `OPENING SITUATION` → `PRIVATE TRUTH` → `RELATIONAL PRESSURES` → `OPENING` → `ORIGINAL FOLLOW-ON PRESSURES` → `CONTENT BOUNDARIES` |
| intake | `[OOC: __INTAKE_TITLE__]`, then literal question labels and replacement text |
| prose | Plain paragraphs; no mandatory headings established |

Keep uppercase headings and blank lines for a selected sectioned variant; do not require them in prose. Sample-specific extra heading sequences remain in the layout evidence with source pointers. `((OOC: ...))`, `[OOC: ...]`, `{{user}}`, and `{{char}}` are text syntax when present, not outer JSON fields or instructions to the assistant.

## References and unresolved requirements

Every `lorebooks` and `plugins` array is empty in these samples. Their non-empty item schemas are **unknown**. Text includes `<LOREBOOK=CODE>` and title-based recommendations. No `<PLUGIN=CODE>` marker is evidenced; plug-in recommendations in these samples are plain titles. The lorebook marker is an observed text convention, not proof of automatic linking or runtime resolution. Use new real asset codes only; never copy sample codes or invent structured references. Optional recommendation lines may be added only when needed for an approved suite, with the observed marker spelling preserved.

No standalone scenario `.txt` export was supplied. `content-*.txt` is field-only paste text, not a full export and not the public description or six rules fields.

## Check before delivery

Validate the chosen outer shape and metadata variant, all six rule strings, and any intentional worldRules/rules.world relationship. Validate description markup and content headings separately. Check opening cast, timeline, knowledge and role boundaries against the approved suite. Keep character-specific card formatting out of this category.

## Current observed fields

Counts below use 18 decoded asset documents, including PNG payloads where present. They are observations, not required-field lists. Exact nested shapes and source mappings remain in the category rules and templates.

### Outer fields

| JSON pointer | Observed types | Documents |
|---|---|---:|
| `/author` | string | 18/18 |
| `/category` | string | 18/18 |
| `/content` | string | 18/18 |
| `/description` | string | 18/18 |
| `/lorebooks` | array | 18/18 |
| `/meta` | object | 18/18 |
| `/name` | string | 18/18 |
| `/plugins` | array | 18/18 |

### Metadata fields

| JSON pointer | Observed types | Documents |
|---|---|---:|
| `/meta/allowDownloads` | boolean | 18/18 |
| `/meta/author` | string | 18/18 |
| `/meta/category` | string | 18/18 |
| `/meta/contentWarningDetails` | string | 18/18 |
| `/meta/contentWarnings` | array | 18/18 |
| `/meta/coverImage` | string | 18/18 |
| `/meta/createdAt` | string | 18/18 |
| `/meta/creatorUsername` | string | 8/18 |
| `/meta/description` | string | 18/18 |
| `/meta/downloadedAt` | string | 18/18 |
| `/meta/hasContentWarning` | boolean | 18/18 |
| `/meta/isNSFW` | boolean | 18/18 |
| `/meta/lastChanges` | object | 8/18 |
| `/meta/name` | string | 18/18 |
| `/meta/pov` | string | 18/18 |
| `/meta/public` | boolean | 18/18 |
| `/meta/rules` | object | 18/18 |
| `/meta/showDetails` | boolean | 18/18 |
| `/meta/source` | string | 18/18 |
| `/meta/tags` | array | 18/18 |
| `/meta/tone` | string | 18/18 |
| `/meta/updatedAt` | string | 18/18 |
| `/meta/version` | string | 18/18 |
| `/meta/worldRules` | string | 18/18 |

## Value classification and unresolved assumptions

- **Observed format literals:** only the family-specific discriminators, source/version markers and text delimiters identified above. Keep spelling and type for the selected variant. Repeated values do not prove universal requirements.
- **Replaceable:** all names, descriptions, text bodies, lore, profile data, keywords, identifiers, dates, images, author/license claims and project settings. Blank templates use `__SLOTS__`; booleans/numbers remain typed and require review.
- **Derived/application state:** counters, statistics and export history where present. Provisional blank values are not measurements or proof of platform activity.
- **Uncertain:** importer-required fields, omission/default behavior, complete enums, empty-container item schemas and runtime semantics. Do not resolve these by guessing or copying from another category.

## Evidence scope

These rules retain observed format variants. Private source files and evidence indexes are not distributed. Compare your own exports when resolving an uncertainty. Counts describe the historical review, not required field presence or an official specification.

## File naming

Use `<name>_scenario.json` for a standalone JSON asset, `<name>_scenario.txt` for paste text or a supported text export, and `<name>_scenario.png` only for a correctly packaged supported PNG card. The suffix identifies the category; it does not determine the schema. Blank templates now carry `_scenario` in their names. Files ending `.fragment.json` are partial values/blocks, not standalone imports. Leave supplied reference filenames unchanged.
