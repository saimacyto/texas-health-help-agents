# Texas Health Help agents and skills

Agents and skills for Texas Health Help navigators and the nonprofit's content work.

## Layout

- `.claude/agents/`: agents built for Texas Health Help. They use the Texas Health Help MCP tools (benefit guides, blog posts, county resources, contacts).
- `.claude/skills/`: open-source skills copied from [anthropics/skills](https://github.com/anthropics/skills). Each keeps its own `LICENSE.txt`. See `THIRD_PARTY_NOTICES.md`.

## Licensing

Only the Apache 2.0 skills from the Anthropic repo are included. The document skills (`docx`, `pdf`, `pptx`, `xlsx`) are governed by Anthropic's Consumer and Commercial Terms, so they are not copied here. `doc-coauthoring` has no license and is not copied.

## Ground rules for Texas Health Help agents

- Public benefit information only. Share source links and let people verify.
- Eligibility rules change. A navigator confirms eligibility for each family.
- No medical advice. Clinical questions go to a clinician.

## Skills adapted from awesome-llm-apps

- `.claude/skills/thh-document-qa`: answers from provided documents, with citations.
- `.claude/skills/thh-source-check`: checks draft claims against official Texas Health Help sources.

Both are adapted from Apache 2.0 workflows in [Shubhamsaboo/awesome-llm-apps](https://github.com/Shubhamsaboo/awesome-llm-apps). See `THIRD_PARTY_NOTICES.md`.
