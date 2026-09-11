# Lorebooks template chooser

All templates are drafts. JSON fragments and field-only text are not standalone JSON imports. Select a family using RULES.md first.

| Template | Kind / controls | Source pointer |
|---|---|---|
| [entry-map-extended_lorebook.json](Templates/entry-map-extended_lorebook.json) | Outer JSON template; see RULES.md | Local reference sample `` |
| [entry-map-compact_lorebook.json](Templates/entry-map-compact_lorebook.json) | Outer JSON template; see RULES.md | Local reference sample `` |
| [entry-01_lorebook.fragment.json](Templates/entry-01_lorebook.fragment.json) | JSON fragment; see RULES.md; keys: uid, key, keysecondary, comment, content, instructions, constant, selective, disable, order, category, keyMatchMode, chapterId, position | Local reference sample `/entries/1` |
| [entry-02_lorebook.fragment.json](Templates/entry-02_lorebook.fragment.json) | JSON fragment; see RULES.md; keys: uid, key, keysecondary, comment, content, constant, selective, disable, order, position, category, keyMatchMode | Local reference sample `/entries/0` |
| [text-concept-system_lorebook.txt](Templates/text-concept-system_lorebook.txt) | Field-only text layout | Local reference sample `/entries/1/content` |
| [text-physical-appearance_lorebook.txt](Templates/text-physical-appearance_lorebook.txt) | Field-only text layout | Local reference sample `/entries/5/content` |
| [text-location-geography_lorebook.txt](Templates/text-location-geography_lorebook.txt) | Field-only text layout | Local reference sample `/entries/9/content` |
| [text-time-period_lorebook.txt](Templates/text-time-period_lorebook.txt) | Field-only text layout | Local reference sample `/entries/7/content` |
| [text-purpose-function_lorebook.txt](Templates/text-purpose-function_lorebook.txt) | Field-only text layout | Local reference sample `/entries/21/content` |
| [text-rule-name_lorebook.txt](Templates/text-rule-name_lorebook.txt) | Field-only text layout | Local reference sample `/entries/10/content` |
| [text-prose_lorebook.txt](Templates/text-prose_lorebook.txt) | Field-only text layout | Local reference sample `/entries/1/content` |

## Revision 0.2 additions

These are additional observed variants; older templates remain available. All are drafts. PNG payload templates are decoded JSON, not complete PNG files.

| Template | Context |
|---|---|
| [creator-username_lorebook.fragment.json](Templates/creator-username_lorebook.fragment.json) | Optional string value for meta.creatorUsername only; truthful account metadata, not a required field. |
