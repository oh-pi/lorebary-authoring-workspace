# LoreBary Authoring Workspace — unofficial

Reusable rules and blank templates for authoring fictional characters, personas, scenarios, lorebooks, plug-ins, and prompts. Each category keeps its own formatting context. Coordinated suites can share newly approved creative content without sharing the wrong asset schema.

**Unofficial and independent:** not affiliated with, backed, endorsed, certified, or authorized by LoreBary or any AI provider. Intended for educational exploration and fictional-content authoring. **You MUST read [legal.md](legal.md), LoreBary's current [Terms of Service](https://lorebary.com/terms), and your AI provider's applicable terms before use. Use at your own risk; no protection against bans, removals, or account restrictions is promised.**

[MIT licensed](LICENSE): free to use, modify, and redistribute, including commercially, with the license notices retained. You do not have to publish your modifications or private creative content. This license applies to this project's materials; it grants no rights to LoreBary or other people's content.

## Start here

1. Download or clone this repository into a folder of your choice. Open **that folder** as your LLM/editor workspace. All paths are relative; work under the existing `Core/` hierarchy.
2. Read [the authoring guide](Core/Authoring/README.md), [AGENTS.md](AGENTS.md), and the matching category's rules and template chooser. Formats are reviewable drafts based on observed exports, not a certified or official importer specification.
3. Optionally create a few pieces of **your own content in LoreBary first**. Download the available exports and put each in the matching `Reference` subfolder below. Include both JSON and text versions when available. A few different examples can reveal structural variants.
4. Ask your LLM to compare each category's examples with its saved rules. Treat references as **formatting evidence only**. Do not copy their characters, settings, prose, personality, narrative, or behavioral instructions into your new work. Do not rebuild all rules unnecessarily.
5. Review the chosen format, discuss new creative content, and record your decisions in your own local approval/brief files. Then generate one asset or a coordinated suite using the appropriate templates. Use a new named set folder for **every** delivery, even one file.
6. Inspect the output, parse JSON, check nested field types and text markers, review all content, and test an import on a copy if appropriate. Record the actual result. Valid JSON alone is not a successful LoreBary import.

You can begin with the included rules and templates without any reference files. Supply your own downloads when verifying compatibility, resolving an uncertainty, or adding a new variant. Do not submit private reference material to a hosted LLM unless you intend that disclosure and have the right to do so.

## Folder layout

| Content | Put your own downloads here | Put new sets here |
|---|---|---|
| Characters | `Core/Characters/Reference/` | `Core/Characters/Generated/<set-name>/` |
| Personas | `Core/Personas/Reference/` | `Core/Personas/Generated/<set-name>/` |
| Scenarios | `Core/Scenarios/Reference/` | `Core/Scenarios/Generated/<set-name>/` |
| Lorebooks | `Core/Lorebooks/Reference/` | `Core/Lorebooks/Generated/<set-name>/` |
| Plug-ins | `Core/Plugins/Reference/` | `Core/Plugins/Generated/<set-name>/` |
| Prompts | `Core/Prompts/Reference/` | `Core/Prompts/Generated/<set-name>/` |
| Coordinated suites | Use the matching category Reference folders | `Core/Suites/GENERATED/<suite-name>/` |

Shared rules and blank templates live in `Core/Authoring/Formats/<Category>/`. A suite gets category subfolders inside its set folder. Do not put loose output files directly in Generated/GENERATED. Preserve existing capitalization; do not create a second `CORE` directory.

The public Reference and Generated folders contain only empty `.gitkeep` placeholders. The original reference files, source indexes, personal metadata, generated projects, and private history are **not included**. Adding your own examples is optional; published examples are not required.

## Suggested LLM thinking level

These are **practical starting recommendations for this workspace**, not benchmark results or guarantees. Use a model that follows file-format instructions well, supports the required context, and is permitted for your intended content. No specific provider or paid plan is required.

| Work | Suggested setting, if your model exposes it |
|---|---|
| Small wording changes or filling a straightforward approved template | Low / standard |
| A new individual character, persona, scenario, lorebook, or prompt | Medium / balanced — the usual starting point |
| Comparing unfamiliar export variants, complex plug-in logic, or coordinating several assets | High / extended, especially if medium misses constraints |
| Difficult unresolved contradictions or repeated failures | Try a higher setting only if comparison shows a useful improvement; narrow the task first |

Higher effort is not automatically better and can increase latency or cost. Setting names and availability differ by model and app. If no reasoning control exists, use its normal mode and split drafting, format validation, and suite consistency review into separate passes. Reasoning effort is not the same as temperature, verbosity, or context length; it is not a way to bypass content policies.

For example, [OpenAI's model guidance](https://developers.openai.com/api/docs/guides/latest-model?model=gpt-5.5) describes medium as a balanced starting point and recommends increasing effort only when the quality gain justifies the trade-off. The task-to-setting table above is this project's recommendation, not an OpenAI or LoreBary endorsement. Check your chosen provider's current documentation rather than assuming every model supports the same settings.

## A prompt to get started

```text
Use this existing workspace and its Core folder.
Read AGENTS.md, legal.md, the authoring workflow, and the rules/templates for
[category]. If I have supplied references in that category's Reference folder,
use them only to check formatting; never reuse their creative content.
Keep uncertain requirements explicit and preserve JSON types and text markers.
First discuss my new creative brief: [brief]. After I approve the format and
content, create the requested files in a new named Generated set folder.
Check the result and report exactly what was and was not tested.
Do not publish my references or generated content.
```

A request for a suite does **not** authorize reusing existing content. That requires an explicit request identifying the existing assets and permitted adaptation. Keep that decision in the individual suite's brief, not the shared rules.

## Sharing your fork

The `.gitignore` excludes Reference contents, Generated sets, local approvals, private format notes, and credentials while retaining empty folder placeholders. Before every public push, review `git status` and `git diff --cached`. Git ignore rules do not protect already tracked files or override deliberate `git add -f`.

Contribute reusable formatting improvements and blank templates, not private projects or downloaded creative material. See [CONTRIBUTING.md](CONTRIBUTING.md). Maintain category boundaries and preserve observed/documented/uncertain distinctions. Never imply that a template is officially approved or that an import passed without an actual test.
