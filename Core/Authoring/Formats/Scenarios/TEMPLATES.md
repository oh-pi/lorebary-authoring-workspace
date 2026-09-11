# Scenarios template chooser

All templates are drafts. JSON fragments and field-only text are not standalone JSON imports. Select a family using RULES.md first.

| Template | Kind / controls | Source pointer |
|---|---|---|
| [scenario-with-change-metadata_scenario.json](Templates/scenario-with-change-metadata_scenario.json) | Outer JSON template; see RULES.md | Local reference sample `` |
| [scenario-without-change-metadata_scenario.json](Templates/scenario-without-change-metadata_scenario.json) | Outer JSON template; see RULES.md | Local reference sample `` |
| [content-logistics_scenario.txt](Templates/content-logistics_scenario.txt) | Field-only text layout | Local reference sample `/content` |
| [content-known-facts_scenario.txt](Templates/content-known-facts_scenario.txt) | Field-only text layout | Local reference sample `/content` |
| [content-contract_scenario.txt](Templates/content-contract_scenario.txt) | Field-only text layout | Local reference sample `/content` |
| [content-ensemble_scenario.txt](Templates/content-ensemble_scenario.txt) | Field-only text layout | Local reference sample `/content` |
| [content-prose_scenario.txt](Templates/content-prose_scenario.txt) | Field-only text layout | Local reference sample `/content` |
| [content-intake_scenario.txt](Templates/content-intake_scenario.txt) | Field-only text layout | Local reference sample `/content` |
| [description-html_scenario.txt](Templates/description-html_scenario.txt) | Field-only text layout | Local reference sample `/description` |
| [content-expanded_scenario.txt](Templates/content-expanded_scenario.txt) | Field-only text layout | Local reference sample `/content` |

## Revision 0.2 addition

[creator-username_scenario.fragment.json](Templates/creator-username_scenario.fragment.json) is the optional string value for `meta.creatorUsername`, not a standalone JSON asset. Keep earlier templates without it available.

[scenario-creator-metadata_scenario.json](Templates/scenario-creator-metadata_scenario.json) preserves a complete current scenario export including `meta.creatorUsername`.
