# Personas: format rules

Revision: 0.2 — updated from the 2026-09-11 rescan; DRAFT templates awaiting review.

Evidence: current counts and variants are given in the revision section below. These rules apply only to Personas. Documented requirements are the user’s authoring/delivery instructions in the root AGENTS.md; no official importer specification was supplied. Observed fields below are not automatically required fields. The reviewed reference collection was reported as generated on LoreBary or submitted and working. This is user-reported compatibility evidence; this workspace has not independently imported its blank templates.

## Revision 0.2: export envelope, detailed root, and PNG payload

The rescan covers 13 JSON files plus eight PNGs containing persona data: 11 JSON files use the six-field export envelope; two JSON files and seven PNG payloads use a 63-key detailed root; one PNG has a 65-key freeform root. These families must remain separate from character cards.

- **Six-field export:** `name`, `author`, `description`, `archetype`, `content`, `meta` remains supported. `meta.creatorUsername` is a newly observed optional string, both with and without `lastChanges`; use the two `persona-creator-...` templates when selecting that variant. It is truthful replaceable account metadata, not a format constant. Earlier templates without it remain available.
- **63-key detailed root:** no `meta` envelope. Profile fields occur at root, alongside `code`, `folderId`, creator/badge flags, counters, `createdDate`, `updatedDate`, `pronouns`, `nameDetails`, `aiAssist`, content/backstory/appearance/quirks/personality strings, `personaTraits`, `attributes`, `relationships`, and loader state. `personaTraits` is this category's own object with array traits, six numeric spectrums (`social`, `approach`, `emotion`, `morality`, `trust`, `nature`), and `customDescription`. It is not the character personality object. `attributes` contains arrays and the string `species`; preserve all fields from `detailed-persona-export_persona.json`. Root `gender` is observed as string or null; root `age` is string. Relationship objects have `name`, `type`, `age`, `status`, `notes`, with `id` optionally present. Preserve the selected shape. Root `aiAssist.method` is null or string. Badge and loader fields are application metadata, not entitlement claims for new content.
- **65-key freeform root:** adds boolean `isFreeForm` and string `freeFormContent` to the detailed family. Use `png-freeform-persona-payload_persona.json`. Retain `isFreeForm: true` for this observed freeform variant and maintain any intended content duplication consistently.

All eight persona PNGs have a `tEXt` chunk named `lorebary_persona` containing **direct UTF-8 JSON**, not the base64 `chara` encoding. Seven payloads are 63-key detailed roots; one is the freeform root. A payload JSON template is not a PNG card; packaging and import need separate verification. Do not infer a standalone plain-text export envelope from these PNGs.

Detailed persona appearance strings can contain `【Body】`, `【Face】`, `【Eyes】`, `【Hair】`, `【Attire】`, and content can contain `{{user}}`. These are now persona-specific observations, not permission to impose character-card formatting on the six-field export. Keep creative content and reference instructions out of templates.

## Earlier format baseline (retained variants)

The original eight examples used root `name`, `author`, `description`, `archetype`, and `content` strings, plus a `meta` object. Seven include `meta.lastChanges`; one does not. Use `persona-with-change-metadata_persona.json` or `persona-without-change-metadata_persona.json` accordingly. Empty `content` is observed; other examples contain paragraphs or a short statement. Empty content is not automatically a malformed export.

## Fields and text

`meta` repeats `name`, `author`, `archetype`, and `description`. It also contains tags/traits arrays, public/download/detail booleans, coverImage string, warning fields, `creditPolicy`, gender, age, pronouns, nameDetails, dates, aiAssist, source and version. `meta.age` is a **string**, including ranges; do not convert it into a numeric character age. `meta.pronouns` has the exact string keys `preset`, `sub`, `obj`, `poss`, `possp`, `ref`. `meta.nameDetails` has string keys `title`, `nickname`, `birthName`, `alias`, `surname`.

The six-field export does not require character-card headings, a system prompt, an opening message, a personality object or an appearance section. Use `content_persona.txt` as field-only prose. Description can contain HTML paragraphs, bold/italic tags, spans and style attributes; preserve the chosen markup layout while replacing all creative text. A paired standalone text export was not supplied for this category, so the field-only file is a workspace delivery convenience, not a proven export envelope.

Archetypes and profile choices are replaceable content, not fixed rules. A reference persona's claims about eligibility, identity, observation mode or private history are example content only and never authoring-assistant instructions.

## Check before delivery

Match the root fields and selected metadata variant. Keep age/pronouns/nameDetails typed correctly. Reconcile duplicated metadata. Distinguish intentional empty content from an unfinished slot. Use only the approved new persona and no inferred user biography. Do not introduce character-card or scenario fields; select the separately evidenced detailed persona family when those root profile fields are needed.

## Current observed fields

Counts below use 21 decoded asset documents, including PNG payloads where present. They are observations, not required-field lists. Exact nested shapes and source mappings remain in the category rules and templates.

### Outer fields

| JSON pointer | Observed types | Documents |
|---|---|---:|
| `/_detailTimestamp` | integer | 10/21 |
| `/_fullLoaded` | boolean | 10/21 |
| `/_loading` | boolean | 10/21 |
| `/age` | string | 10/21 |
| `/aiAssist` | object | 10/21 |
| `/allowDownloads` | boolean | 10/21 |
| `/appearance` | null / string | 10/21 |
| `/archetype` | string | 21/21 |
| `/attributes` | object | 10/21 |
| `/author` | string | 21/21 |
| `/authorIsFeatured` | boolean | 10/21 |
| `/backstory` | null / string | 10/21 |
| `/code` | string | 10/21 |
| `/constantTokens` | integer | 10/21 |
| `/content` | string | 21/21 |
| `/contentWarningDetails` | string | 10/21 |
| `/coverImage` | string | 10/21 |
| `/createdDate` | string | 10/21 |
| `/description` | string | 21/21 |
| `/displayedBadges` | array | 10/21 |
| `/downloads` | integer | 10/21 |
| `/featured` | boolean | 10/21 |
| `/folderId` | null / string | 10/21 |
| `/freeFormContent` | string | 1/21 |
| `/gender` | null / string | 10/21 |
| `/hasContentWarning` | boolean | 10/21 |
| `/hasCoverImage` | boolean | 10/21 |
| `/isAcademyGraduate` | boolean | 10/21 |
| `/isAdmin` | boolean | 10/21 |
| `/isBetaTester` | boolean | 10/21 |
| `/isBirthdayCreator` | boolean | 10/21 |
| `/isChildOfFirstForge` | boolean | 10/21 |
| `/isChildOfReforge` | boolean | 10/21 |
| `/isCommunityMod` | boolean | 10/21 |
| `/isDeveloper` | boolean | 10/21 |
| `/isDonatorMonthly` | boolean | 10/21 |
| `/isDonatorSingle` | boolean | 10/21 |
| `/isFreeForm` | boolean | 1/21 |
| `/isHonoraryGuardian` | boolean | 10/21 |
| `/isLegalAngel` | boolean | 10/21 |
| `/isMod` | boolean | 10/21 |
| `/isOriginUser` | boolean | 10/21 |
| `/isPrivate` | boolean | 10/21 |
| `/isPublic` | boolean | 10/21 |
| `/isRelicMaker` | boolean | 10/21 |
| `/isRmq226Badge` | boolean | 10/21 |
| `/isRmq326Badge` | boolean | 10/21 |
| `/isStaff` | boolean | 10/21 |
| `/likes` | integer | 10/21 |
| `/meta` | object | 11/21 |
| `/name` | string | 21/21 |
| `/nameDetails` | object | 10/21 |
| `/personaTraits` | object | 10/21 |
| `/personality` | null / string | 10/21 |
| `/pronouns` | object | 10/21 |
| `/public` | boolean | 10/21 |
| `/quirks` | null / string | 10/21 |
| `/rating` | null | 10/21 |
| `/ratingCount` | integer | 10/21 |
| `/relationships` | array | 10/21 |
| `/showDetails` | boolean | 10/21 |
| `/tags` | array | 10/21 |
| `/traits` | array | 10/21 |
| `/updatedDate` | string | 10/21 |
| `/views` | integer | 10/21 |
| `/visibility` | string | 10/21 |

### Metadata fields

| JSON pointer | Observed types | Documents |
|---|---|---:|
| `/meta/age` | string | 11/21 |
| `/meta/aiAssist` | object | 11/21 |
| `/meta/allowDownloads` | boolean | 11/21 |
| `/meta/archetype` | string | 11/21 |
| `/meta/author` | string | 11/21 |
| `/meta/contentWarningDetails` | string | 11/21 |
| `/meta/coverImage` | string | 11/21 |
| `/meta/createdAt` | string | 11/21 |
| `/meta/creatorUsername` | string | 7/21 |
| `/meta/creditPolicy` | string | 11/21 |
| `/meta/description` | string | 11/21 |
| `/meta/downloadedAt` | string | 11/21 |
| `/meta/gender` | string | 11/21 |
| `/meta/hasContentWarning` | boolean | 11/21 |
| `/meta/isNSFW` | boolean | 11/21 |
| `/meta/lastChanges` | object | 8/21 |
| `/meta/name` | string | 11/21 |
| `/meta/nameDetails` | object | 11/21 |
| `/meta/pronouns` | object | 11/21 |
| `/meta/public` | boolean | 11/21 |
| `/meta/showDetails` | boolean | 11/21 |
| `/meta/source` | string | 11/21 |
| `/meta/tags` | array | 11/21 |
| `/meta/traits` | array | 11/21 |
| `/meta/updatedAt` | string | 11/21 |
| `/meta/version` | string | 11/21 |

## Value classification and unresolved assumptions

- **Observed format literals:** only the family-specific discriminators, source/version markers and text delimiters identified above. Keep spelling and type for the selected variant. Repeated values do not prove universal requirements.
- **Replaceable:** all names, descriptions, text bodies, lore, profile data, keywords, identifiers, dates, images, author/license claims and project settings. Blank templates use `__SLOTS__`; booleans/numbers remain typed and require review.
- **Derived/application state:** counters, statistics and export history where present. Provisional blank values are not measurements or proof of platform activity.
- **Uncertain:** importer-required fields, omission/default behavior, complete enums, empty-container item schemas and runtime semantics. Do not resolve these by guessing or copying from another category.

## Evidence scope

These rules retain observed format variants. Private source files and evidence indexes are not distributed. Compare your own exports when resolving an uncertainty. Counts describe the historical review, not required field presence or an official specification.

## File naming

Use `<name>_persona.json` for a standalone JSON asset, `<name>_persona.txt` for paste text or a supported text export, and `<name>_persona.png` only for a correctly packaged supported PNG card. The suffix identifies the category; it does not determine the schema. Blank templates now carry `_persona` in their names. Files ending `.fragment.json` are partial values/blocks, not standalone imports. Leave supplied reference filenames unchanged.
