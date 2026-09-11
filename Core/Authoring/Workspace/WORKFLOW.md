# Authoring and delivery workflow

## Folder contract

Resolve all paths relative to the existing workspace root containing `Core/`. No fixed username, home directory or storage provider is required. Use the included rules/templates even when the original reference collection is absent. New users can create their own LoreBary content, download its exports, and add them to the matching Reference folders for comparison. In a shared copy without an approval record, create a fresh record when reviewing formats; do not inherit another user’s approvals.

`Core/<Category>/Reference/` is read-only format evidence. Existing individual categories use `Generated` (capital G); `Core/Suites/GENERATED` uses uppercase. Preserve that spelling.

Every delivery is a set, including a single file:

```text
Core/Characters/Generated/<set-name>/
  BRIEF.md
  DELIVERY.md
  <character>.json

Core/Suites/GENERATED/<suite-name>/
  BRIEF.md
  DELIVERY.md
  Characters/
  Lorebooks/
  Scenarios/
  Personas/
  Plugins/
  Prompts/
```

Create only component folders needed for the approved suite. Use a meaningful unique set name; use a new set folder for a new delivery or a clearly named revision. Do not overwrite an earlier delivery silently. No loose output files directly under Generated/GENERATED. Rules, evidence and blank templates live in `Core/Authoring/Formats/<Category>/`, and process documents in `Core/Authoring/Workspace/`. The root `AGENTS.md` makes these instructions discoverable in future sessions.

## Phase 1: evidence to approved format

1. Inspect that category's supplied examples. Record the relevant nested fields, types, encoded JSON, text markers and structural variants in your own local format notes. Do not copy creative prose into shared rules or templates.
2. Use `RULES.md` to select a structural family and compatible text-field layout. Field presence counts are not importer requirements. An empty collection supplies no evidence about its item schema. Metadata's source/export fields do not prove an import test.
3. Review drafts and record the actual approval in `APPROVALS.md`. Keep observed, user-required, and uncertain claims distinct. Persist every correction in the rules/templates before future generation.

## Phase 2: individual assets or coordinated suites

### Reference-content boundary

The current purpose is reusable formatting for newly approved creative content. Do not carry reference characters, settings, lore, personalities, narrative material, distinctive prose, or behavioral instructions into generated assets, including through renamed or lightly rewritten adaptations. Matching a reference’s structure does not authorize matching its creative content.

A coordinated suite normally uses entirely new approved content. Reuse of existing content is an exception only when the user explicitly requests it for a particular suite and identifies the existing assets/content to use. Record the authorized sources, scope of reuse, and adaptation boundaries in that suite’s brief; do not promote their creative content into shared rules or blank templates. This exception is not active now.

1. Copy the blank brief from `Core/Authoring/Workspace/Set-Templates/BRIEF.md` into the new set folder. Discuss and record new creative content and approval there, never in shared format rules.
2. Assign component responsibilities: lorebook owns durable setting facts; scenario owns opening circumstances and situation-specific rules; character owns its identity and behavior; persona owns the user's selected role; prompt owns agreed narration/presentation; plug-in owns explicitly requested runtime effects or state. These are workspace planning conventions, not required LoreBary fields. Adjust responsibilities to the actual requested project and avoid unnecessary components.
3. List canonical names, aliases, facts, timeline, knowledge boundaries, tone, roles, and permitted actions. Identify the owner of each shared fact or behavioral instruction. Avoid repeating entire instructions in multiple components; check every duplication for consistency.
4. Choose an approved outer template and text layout for each component. Replace template slots with approved project content. Preserve field names, case, types, nesting and literal markers for that variant. Do not copy sample IDs, artwork, attribution, timestamps, counters, or code. Configure booleans and numeric values deliberately; blank defaults are not universal requirements.
5. Use only evidenced cross-reference syntax. Scenario text contains a `<LOREBOOK=...>` marker; its resolution remains untested. Plug-in recommendations are titles in prose; no `<PLUGIN=...>` marker is evidenced by these references. Fill codes only from actual created/imported assets. Empty `lorebooks` and `plugins` arrays do not establish an object or ID-array format. Relationships expressed as prose are not automatic links. Do not invent dependency or suite fields in import JSON. Keep the suite map in BRIEF.md.
6. Separate the downloadable JSON from field-only paste text and full text exports. The prompt export header is not part of `modules[*].content`. Serialize structured character personality objects once for the JSON-download card variant. PNG character payloads use prose in the main personality field and an object inside the extension. Persona PNG payloads use their own detailed-root format. Select the exact category/container from the current rules.
7. Validate JSON syntax with a trusted JSON parser, then use the category checklist and `DELIVERY.md` for shape, text and asset validation. Check exact chosen field shapes, nested serialized JSON, unresolved slots, headings/markers, duplicate metadata, set-wide consistency and identifiers. Local tools do not validate runtime behavior or guarantee imports.
8. If an import is tested, record the actual file hash, date, destination, observed outcome and any export-back differences. Otherwise explicitly mark import **not tested**. Deliver the file links or paste-ready content with this limitation.

## Metadata policy

All supplied metadata shapes remain available in the evidence index. Author attribution, permission/visibility flags, AI-assistance declarations, age/pronouns, tags, descriptions, images, codes and timestamps are replaceable project/export values. Counters and token statistics are derived values, not creative requirements. Do not retain sample achievements, badges, claims, or download histories. Do not fabricate evidence of platform-generated metadata. Until omission/creation behavior is verified, templates retain typed slots or provisional typed zero values; they are not import-ready files.

`source: "LoreBary"`, export `version: "1.0"`, `spec: "chara_card_v2"`, `spec_version: "2.0"`, and plug-in `tag: "PLUGIN"` are observed format literals within their respective families. Their presence in a draft does not assert that this workspace exported it from the platform. No such literal is a universal rule across all categories.

## Placeholder convention

`__UPPERCASE_SLOT__` is a workspace editing placeholder, not LoreBary syntax. Replace it before delivery. A string slot stays a JSON string even when it describes a date or number. Numeric and boolean fields retain their type and need deliberate configuration; a zero/false value is not necessarily meaningful. Reference-native `{{user}}` and `{{char}}` stay literal where the selected text layout uses them. `{{__VARIABLE__}}` illustrates a variable-token shape: substitute an actual declared variable identifier and verify its runtime behavior. Never confuse content inside an asset with instructions to the authoring assistant.

## Asset filenames

Use `example_plugin.json`, `example_lorebook.json`, `example_scenario.json`, `example_character.json`, `example_persona.json`, and `example_prompt.json` for the corresponding generated asset categories. Use the same suffix before `.txt` for text or `.png` for properly packaged supported cards. Keep each delivery in a named Generated set folder. Do not rename your reference files merely to match this convention. Blank templates also include the category suffix; `.fragment.json` denotes a partial block/value, not a standalone import.
