# Old-School Researcher

[简体中文](README.md) | [English](README.en.md)

[![MIT License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![PRs welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/aidealee/old-school-researcher/pulls)

**Quick links:** [Skill](old-school-researcher/SKILL.md) · [AGENTS.md](paper-project/AGENTS.md)

**Natural, direct, accurate academic writing in Chinese and English.** Current version: **1.1.2**.

Old-School Researcher provides a complete set of academic writing and editing instructions for AI writing assistants. It helps authors organize arguments around their research contributions and remove formulaic and defensive phrasing while preserving the original views, data, equations, citations, and reproducibility information.

The project offers two independent options, **Skill** and **AGENTS.md**, for papers, theses, reviewer responses, research reports, and grant proposals.

## What it does

- **Highlights research contributions:** clarifies the problem, method, results, and significance, using existing evidence to explain the work's strengths.
- **Improves Chinese and English prose:** addresses formulaic openings, repeated summaries, empty emphasis, excessive transitions, long Chinese modifiers, and English grammar and collocations.
- **Uses a direct academic voice:** recasts qualifying, negative, concessive, and defensive prose as affirmative statements of specific research objects, scope, evidence types, and work status, preserving the original meaning and degree of certainty.
- **Protects research content:** preserves all numbers, formal statements, author views, and reproducibility information, and checks the correspondence among objects, metrics, values, conditions, and citations. Equations, formal statements, and quotations retain their original text.
- **Controls the extent of editing:** offers diagnosis, cleanup, polishing, restructuring/compression, and drafting, with attention to the author's or target journal's style.

## Choose Skill or AGENTS.md

| Your use case | Choose | Entry point |
|---|---|---|
| Invoke the rules as needed across papers and tasks | **Skill** | Install the [Skill directory](old-school-researcher) and invoke `$old-school-researcher` |
| Apply the rules throughout a manuscript project | **AGENTS.md** | Place the [project instruction file](paper-project/AGENTS.md) in the manuscript project for the client to load |

Both files contain the same complete writing rules and work independently. The rules are written in Chinese and apply to writing in Chinese and English. Loading either file in full provides the entire rule set. The installation instructions below use Codex as an example.

## Installation

Get the repository:

```sh
git clone https://github.com/aidealee/old-school-researcher.git
cd old-school-researcher
```

The installation sources are inside the repository:

```text
old-school-researcher/          # Repository root
├── old-school-researcher/      # Skill installation source
│   ├── SKILL.md                # Complete writing rules
│   └── agents/
│       └── openai.yaml         # Display name, default prompt, invocation policy
└── paper-project/
    └── AGENTS.md               # Independent project instructions
```

### Option 1: Install the Skill

1. Copy the **inner `old-school-researcher/` directory** containing `SKILL.md`, including its `agents/` subdirectory, into the client's skills directory.
2. Codex uses `~/.agents/skills/old-school-researcher/` for a user installation and `<manuscript-project>/.agents/skills/old-school-researcher/` for a project installation. Environments with a custom skills directory should use the directory their client scans. Here, `~` denotes your home directory. See the [Codex Skills documentation](https://developers.openai.com/codex/skills) for directory discovery.
3. Select **Old-School Researcher** in the skills list or include `$old-school-researcher` in a Codex prompt. Check the skills list in a new session after installation.

The installed entry point is `<skills-directory>/old-school-researcher/SKILL.md`. This file contains all writing rules.

### Option 2: Use AGENTS.md

1. Copy `paper-project/AGENTS.md` from this repository to the root of your manuscript project, keeping the filename `AGENTS.md`.
2. For projects with an existing `AGENTS.md`, integrate the complete rules with the project's current instructions.
3. Start a new session with the manuscript project as the working directory. Ask the assistant to list the instruction files it loaded and summarize the writing rules, then submit your writing task.

Codex loads project instructions according to directory scope and instruction precedence. For projects with multiple instruction files, check overrides and `project_doc_max_bytes` so the full rule set is loaded into context. See the [Codex AGENTS.md documentation](https://developers.openai.com/codex/guides/agents-md).

### Use with other assistants

For clients that support Skills or AGENTS.md, place the relevant files according to their installation and instruction-loading mechanisms. In a chat assistant that accepts file attachments or long text, provide either complete rule file and explicitly ask it to read the entire file and follow it as instructions for the writing task.

## Usage

### Polish an English paper with the Skill

```text
Use $old-school-researcher to polish the following English manuscript passage.
Keep the manuscript in English and write the editing notes in Chinese.
Preserve the original views, all numbers, equations, citations, and reproducibility information.

[Paste the manuscript passage]
```

### Clean up a final Chinese draft with AGENTS.md

Submit this request in a session that has loaded the project instructions:

```text
Follow this project's AGENTS.md to clean up the following Chinese manuscript passage.
Make minimal edits, preserve paragraph and sentence order, and retain unaffected sentences verbatim.
Return the complete revised passage and brief editing notes.

[Paste the manuscript passage]
```

### Choose an editing mode

| Mode | Use case | Scope of changes |
|---|---|---|
| **Diagnosis** | Identify problems or assess a draft | Locate issues, explain them, and suggest minimal changes while retaining the original draft |
| **Cleanup** | Final drafts, formulaic language, minimal edits | Edit affected wording only, preserving paragraph and sentence order |
| **Polishing** | General draft revision; the default mode | Improve grammar, collocations, and transitions while retaining heading levels and paragraph structure |
| **Restructuring/compression** | Rewrite an abstract, reorganize an argument, or shorten a text | Adjust structure within explicit authorization while preserving substantive views, data, and citations |
| **Drafting** | Write new text from research materials | Use the supplied evidence and mark gaps with `[[EVIDENCE: evidence needed]]` |

Provide the draft or research materials and specify the editing mode, target language, and journal or author style. Explanations follow the language of your request; manuscript text follows the specified language or the original draft. The default output is the complete revision with brief editing notes. You can also request the revised text alone.

## Contributing

[Pull requests](https://github.com/aidealee/old-school-researcher/pulls) improving wording, usage instructions, or writing rules are welcome. Update both the Skill and AGENTS.md when changing rules, keeping their bodies identical and each file complete. Maintain both README languages when updating usage instructions.

## Sources and license

This project reorganizes and adapts academic writing instructions from:

- [Academic-Humanizer](https://github.com/junbolian/Academic-Humanizer/tree/62b0a02627e063015466c70f0a4dd4929a9f7f5b), by Junbo Lian, with contributions from AIScientists-Dev (building on humanizer by blader) and shiujan.
- [anti-defensive-writing-Skill](https://github.com/Adkid-Zephyr/anti-defensive-writing-Skill/tree/82d31402caa0db1790026824399044538483171b), by Adkid-Zephyr.

Released under the [MIT License](LICENSE), Copyright © 2026 aidealee. See [third-party notices](THIRD_PARTY_NOTICES.md) and [licenses/](licenses/) for attribution, pinned source revisions, and complete license texts. The Skill and AGENTS.md each include third-party attribution and full license text; retain these notices when distributing either file independently.

When copying or distributing either option, also retain this project's copyright and permission notice from the root [LICENSE](LICENSE), either alongside the files or in the target project's third-party license notices.

For development collaboration principles, see the companion project [Old-School Programmer](https://github.com/aidealee/old-school-programmer).
