# Scenarios: format rules

Revision: 0.1 — DRAFT, awaiting review.

Evidence: 17 supplied JSON files. These rules apply only to Scenarios. Documented requirements are the user’s authoring/delivery instructions in the root AGENTS.md; no official importer specification was supplied. Observed fields below are not automatically required fields. Actual LoreBary import: **not tested**.

## Choose a format

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

## Observed outer fields

| JSON pointer | Observed types | Files containing field |
|---|---|---:|
| `/author` | string | 17/17 |
| `/category` | string | 17/17 |
| `/content` | string | 17/17 |
| `/description` | string | 17/17 |
| `/lorebooks` | array | 17/17 |
| `/meta` | object | 17/17 |
| `/name` | string | 17/17 |
| `/plugins` | array | 17/17 |

## Observed metadata fields

These counts preserve variation; they are not a proposed required-field list. Detailed nested keys, types and per-file shapes are in your own local structure notes.

| JSON pointer | Observed types | Files containing field |
|---|---|---:|
| `/meta/allowDownloads` | boolean | 17/17 |
| `/meta/author` | string | 17/17 |
| `/meta/category` | string | 17/17 |
| `/meta/contentWarningDetails` | string | 17/17 |
| `/meta/contentWarnings` | array | 17/17 |
| `/meta/coverImage` | string | 17/17 |
| `/meta/createdAt` | string | 17/17 |
| `/meta/description` | string | 17/17 |
| `/meta/downloadedAt` | string | 17/17 |
| `/meta/hasContentWarning` | boolean | 17/17 |
| `/meta/isNSFW` | boolean | 17/17 |
| `/meta/lastChanges` | object | 10/17 |
| `/meta/name` | string | 17/17 |
| `/meta/pov` | string | 17/17 |
| `/meta/public` | boolean | 17/17 |
| `/meta/rules` | object | 17/17 |
| `/meta/showDetails` | boolean | 17/17 |
| `/meta/source` | string | 17/17 |
| `/meta/tags` | array | 17/17 |
| `/meta/tone` | string | 17/17 |
| `/meta/updatedAt` | string | 17/17 |
| `/meta/version` | string | 17/17 |
| `/meta/worldRules` | string | 17/17 |

## Value classification and unresolved assumptions

- **Observed format literals:** only the family-specific discriminators, source/version markers and text delimiters identified above. Keep spelling and type for the selected variant. Repeated values do not prove universal requirements.
- **Replaceable:** all names, descriptions, text bodies, lore, profile data, keywords, identifiers, dates, images, author/license claims and project settings. Blank templates use `__SLOTS__`; booleans/numbers remain typed and require review.
- **Derived/application state:** counters, statistics and export history where present. Provisional blank values are not measurements or proof of platform activity.
- **Uncertain:** importer-required fields, omission/default behavior, complete enums, empty-container item schemas and runtime semantics. Do not resolve these by guessing or copying from another category.

## Provenance and independent verification

These rules summarize observed export structures; no original reference files, personal metadata, source-filename indexes, or original creative material are distributed. Historic sample counts are context, not a claim about the contents of your Reference folders. No importer certification is implied.

Use the blank templates and this rule set as a starting baseline. To verify or extend a variant, create your own content in LoreBary, download it into this category’s Reference folder, compare its structure and text formatting, and record your own decisions. Examples are formatting evidence only. Keep any local evidence notes private unless intentionally sanitized for sharing.
