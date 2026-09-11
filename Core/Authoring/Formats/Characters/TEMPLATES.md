# Characters template chooser

All templates are drafts. JSON fragments and field-only text are not standalone JSON imports. Select a family using RULES.md first.

| Template | Kind / controls | Source pointer |
|---|---|---|
| [card-v2-structured_character.json](Templates/card-v2-structured_character.json) | Outer JSON template; see RULES.md | Local reference sample `` |
| [card-v2-freeform_character.json](Templates/card-v2-freeform_character.json) | Outer JSON template; see RULES.md | Local reference sample `` |
| [detailed-structured-export_character.json](Templates/detailed-structured-export_character.json) | Outer JSON template; see RULES.md | Local reference sample `` |
| [detailed-freeform-export_character.json](Templates/detailed-freeform-export_character.json) | Outer JSON template; see RULES.md | Local reference sample `` |
| [personality-object_character.fragment.json](Templates/personality-object_character.fragment.json) | JSON fragment; see RULES.md; keys: summary, traits, quirks, spectrums, strengths, flaws, values, fears, motivations, speechPatterns, habits, socialBehavior, stressResponse, bodyLanguage, hobbies, wishes, secrets, petPeeves, guiltyPleasures, coreBeliefs, emotionalTriggers, copingMechanisms, lifeGoals, shortTermGoals, sexuality | Local reference sample `/data/personality::encodedJSON` |
| [appearance-sections_character.txt](Templates/appearance-sections_character.txt) | Field-only text layout | Local reference sample `/appearance` |
| [dialogue_character.txt](Templates/dialogue_character.txt) | Field-only text layout | Local reference sample `/data/mes_example` |
| [description-html_character.txt](Templates/description-html_character.txt) | Field-only text layout | Local reference sample `/description` |
| [freeform-labeled_character.txt](Templates/freeform-labeled_character.txt) | Field-only text layout | Local reference sample `/data/extensions/lorebary/freeFormContent` |

## Revision 0.2 additions

These are additional observed variants; older templates remain available. All are drafts. PNG payload templates are decoded JSON, not complete PNG files.

| Template | Context |
|---|---|
| [card-v2-extended-personality_character.json](Templates/card-v2-extended-personality_character.json) | JSON card with 29-key encoded personality; preserve string encoding. |
| [personality-extended_character.fragment.json](Templates/personality-extended_character.fragment.json) | 29-key object; serialize once only for encoded-personality JSON card. |
| [structured-root-export_character.json](Templates/structured-root-export_character.json) | 38-key structured root without the detailed-loader flags; distinct from card envelope. |
| [detailed-populated-export_character.json](Templates/detailed-populated-export_character.json) | Detailed root with populated string arrays and string age; keep typed null variants from earlier detailed template. |
| [png-card-payload_character.json](Templates/png-card-payload_character.json) | Decoded chara PNG payload; JSON is not itself a PNG card. Personality prose and extension object remain separate. |
| [png-card-empty-personality-payload_character.json](Templates/png-card-empty-personality-payload_character.json) | Observed PNG variant with empty main personality; no isFreeForm/freeFormContent fields in PNG envelope. |
| [dialogue-start_character.txt](Templates/dialogue-start_character.txt) | Field-only observed delimiter layout; repeat START block per exchange. |
| [appearance-movement_character.txt](Templates/appearance-movement_character.txt) | Field-only appearance layout; exact observed marker order, optional for this variant. |
| [appearance-footwear_character.txt](Templates/appearance-footwear_character.txt) | Field-only appearance layout; exact observed marker order, optional for this variant. |
