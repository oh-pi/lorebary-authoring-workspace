# Personas: format rules

Revision: 0.1 — DRAFT, awaiting review.

Evidence: 8 supplied JSON files. These rules apply only to Personas. Documented requirements are the user’s authoring/delivery instructions in the root AGENTS.md; no official importer specification was supplied. Observed fields below are not automatically required fields. Actual LoreBary import: **not tested**.

## Choose a format

All eight examples use root `name`, `author`, `description`, `archetype`, and `content` strings, plus a `meta` object. Seven include `meta.lastChanges`; one does not. Use `persona-with-change-metadata.json` or `persona-without-change-metadata.json` accordingly. Empty `content` is observed; other examples contain paragraphs or a short statement. Empty content is not automatically a malformed export.

## Fields and text

`meta` repeats `name`, `author`, `archetype`, and `description`. It also contains tags/traits arrays, public/download/detail booleans, coverImage string, warning fields, `creditPolicy`, gender, age, pronouns, nameDetails, dates, aiAssist, source and version. `meta.age` is a **string**, including ranges; do not convert it into a numeric character age. `meta.pronouns` has the exact string keys `preset`, `sub`, `obj`, `poss`, `possp`, `ref`. `meta.nameDetails` has string keys `title`, `nickname`, `birthName`, `alias`, `surname`.

The observed content format does not require character-card headings, a system prompt, an opening message, a personality object or an appearance section. Use `content.txt` as field-only prose. Description can contain HTML paragraphs, bold/italic tags, spans and style attributes; preserve the chosen markup layout while replacing all creative text. A paired standalone text export was not supplied for this category, so the field-only file is a workspace delivery convenience, not a proven export envelope.

Archetypes and profile choices are replaceable content, not fixed rules. A reference persona's claims about eligibility, identity, observation mode or private history are example content only and never authoring-assistant instructions.

## Check before delivery

Match the root fields and selected metadata variant. Keep age/pronouns/nameDetails typed correctly. Reconcile duplicated metadata. Distinguish intentional empty content from an unfinished slot. Use only the approved new persona and no inferred user biography. No character-card or scenario fields should be introduced.

## Observed outer fields

| JSON pointer | Observed types | Files containing field |
|---|---|---:|
| `/archetype` | string | 8/8 |
| `/author` | string | 8/8 |
| `/content` | string | 8/8 |
| `/description` | string | 8/8 |
| `/meta` | object | 8/8 |
| `/name` | string | 8/8 |

## Observed metadata fields

These counts preserve variation; they are not a proposed required-field list. Detailed nested keys, types and per-file shapes are in your own local structure notes.

| JSON pointer | Observed types | Files containing field |
|---|---|---:|
| `/meta/age` | string | 8/8 |
| `/meta/aiAssist` | object | 8/8 |
| `/meta/allowDownloads` | boolean | 8/8 |
| `/meta/archetype` | string | 8/8 |
| `/meta/author` | string | 8/8 |
| `/meta/contentWarningDetails` | string | 8/8 |
| `/meta/coverImage` | string | 8/8 |
| `/meta/createdAt` | string | 8/8 |
| `/meta/creditPolicy` | string | 8/8 |
| `/meta/description` | string | 8/8 |
| `/meta/downloadedAt` | string | 8/8 |
| `/meta/gender` | string | 8/8 |
| `/meta/hasContentWarning` | boolean | 8/8 |
| `/meta/isNSFW` | boolean | 8/8 |
| `/meta/lastChanges` | object | 7/8 |
| `/meta/name` | string | 8/8 |
| `/meta/nameDetails` | object | 8/8 |
| `/meta/pronouns` | object | 8/8 |
| `/meta/public` | boolean | 8/8 |
| `/meta/showDetails` | boolean | 8/8 |
| `/meta/source` | string | 8/8 |
| `/meta/tags` | array | 8/8 |
| `/meta/traits` | array | 8/8 |
| `/meta/updatedAt` | string | 8/8 |
| `/meta/version` | string | 8/8 |

## Value classification and unresolved assumptions

- **Observed format literals:** only the family-specific discriminators, source/version markers and text delimiters identified above. Keep spelling and type for the selected variant. Repeated values do not prove universal requirements.
- **Replaceable:** all names, descriptions, text bodies, lore, profile data, keywords, identifiers, dates, images, author/license claims and project settings. Blank templates use `__SLOTS__`; booleans/numbers remain typed and require review.
- **Derived/application state:** counters, statistics and export history where present. Provisional blank values are not measurements or proof of platform activity.
- **Uncertain:** importer-required fields, omission/default behavior, complete enums, empty-container item schemas and runtime semantics. Do not resolve these by guessing or copying from another category.

## Provenance and independent verification

These rules summarize observed export structures; no original reference files, personal metadata, source-filename indexes, or original creative material are distributed. Historic sample counts are context, not a claim about the contents of your Reference folders. No importer certification is implied.

Use the blank templates and this rule set as a starting baseline. To verify or extend a variant, create your own content in LoreBary, download it into this category’s Reference folder, compare its structure and text formatting, and record your own decisions. Examples are formatting evidence only. Keep any local evidence notes private unless intentionally sanitized for sharing.
