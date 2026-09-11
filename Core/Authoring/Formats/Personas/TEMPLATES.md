# Personas template chooser

All templates are drafts. JSON fragments and field-only text are not standalone JSON imports. Select a family using RULES.md first.

| Template | Kind / controls | Source pointer |
|---|---|---|
| [persona-with-change-metadata_persona.json](Templates/persona-with-change-metadata_persona.json) | Outer JSON template; see RULES.md | Local reference sample `` |
| [persona-without-change-metadata_persona.json](Templates/persona-without-change-metadata_persona.json) | Outer JSON template; see RULES.md | Local reference sample `` |
| [content_persona.txt](Templates/content_persona.txt) | Field-only text layout | Local reference sample `/content` |
| [description-html_persona.txt](Templates/description-html_persona.txt) | Field-only text layout | Local reference sample `/description` |

## Revision 0.2 additions

These are additional observed variants; older templates remain available. All are drafts. PNG payload templates are decoded JSON, not complete PNG files.

| Template | Context |
|---|---|
| [detailed-persona-export_persona.json](Templates/detailed-persona-export_persona.json) | 63-key detailed root; no meta envelope; own personaTraits schema. |
| [png-freeform-persona-payload_persona.json](Templates/png-freeform-persona-payload_persona.json) | 65-key PNG payload adds isFreeForm/freeFormContent to detailed persona family. |
| [persona-creator-with-change-metadata_persona.json](Templates/persona-creator-with-change-metadata_persona.json) | Six-root-field export with meta.creatorUsername and lastChanges. |
| [persona-creator-without-change-metadata_persona.json](Templates/persona-creator-without-change-metadata_persona.json) | Six-root-field export with creatorUsername but no lastChanges. |
| [creator-username_persona.fragment.json](Templates/creator-username_persona.fragment.json) | Optional string value for meta.creatorUsername only; truthful account metadata, not a required field. |
