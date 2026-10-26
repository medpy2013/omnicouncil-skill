<!-- Copyright 2026 Mohamed Aouaci. SPDX-License-Identifier: Apache-2.0 -->

# Installation and invocation

**Documentation checked: 2026-10-26.** Product interfaces, plans, and agent-skill support change. Recheck each linked official guide before following a UI path.

## What this ZIP does

A model does not install a skill by itself. The host application or agent runtime must support a skill directory, reusable instructions, knowledge files, or an API prompt. This ZIP contains portable Markdown and references. It is a native skill only in hosts that load this format and its files.

The install ZIP has one top-level folder named **omnicouncil/**. Extract it intact. When a host has no skill loader, attach or paste **SKILL.md** for that task and include only the relevant reference file.

## OpenAI Codex

1. Download **onlySkills.zip** from the repository and extract it.
2. Copy the extracted **omnicouncil** folder to the Codex user skills directory:
   - Windows: **%USERPROFILE%\.codex\skills\omnicouncil**
   - macOS/Linux: **~/.codex/skills/omnicouncil/**
3. Keep **SKILL.md**, **agents/**, **references/**, and the other package folders together.
4. Restart Codex or refresh skill discovery if needed.
5. Invoke **$omnicouncil**. The Codex metadata disables implicit invocation.
6. Confirm that the skill appears, then run the relevant cases in **EVALUATION.md**.

Official guide: [OpenAI Codex skills](https://developers.openai.com/codex/skills).

## Claude Code

1. Extract the ZIP and place the **omnicouncil** folder in your user skills directory, **~/.claude/skills/omnicouncil/**, or in a project at **.claude/skills/omnicouncil/**.
2. To make Claude Code invocation manual-only, add this Claude-specific field to the YAML frontmatter at the top of **SKILL.md**, below **description** and before the closing separator:

    disable-model-invocation: true

3. Start or reload Claude Code, then invoke **/omnicouncil**.

That setting is specific to Claude Code; it does not configure Claude.ai, Claude API integrations, or other hosts. The portable core file does not include this host-specific key.

Official guide: [Claude Code skills](https://code.claude.com/docs/en/skills).

## Gemini CLI

Gemini CLI has a native Agent Skills system. From a terminal, install the repository with the current CLI command:

    gemini skills install https://github.com/medpy2013/omnicouncil-skill

In an interactive session, confirm discovery with **/skills list**; use **/skills reload** after changing files. The CLI may activate an enabled skill when it considers the task relevant and asks for permission. This package cannot force manual-only invocation there. If you need strict opt-in behavior, keep the skill disabled until needed or attach **SKILL.md** to only the requests where you want it.

Official guides: [Gemini CLI skills](https://github.com/google-gemini/gemini-cli/blob/main/docs/cli/using-agent-skills.md) and [Gemini CLI skill setup](https://github.com/google-gemini/gemini-cli/blob/main/docs/cli/tutorials/skills-getting-started.md).

## Gemini Apps and Gems

In the Gemini web app, a Gem can store instructions and reference files:

1. Open **Explore Gems**, choose **New Gem**, and enter the OmniCouncil workflow in its instructions.
2. Add **SKILL.md** and any reference files you want the Gem to use under **Knowledge**.
3. Save and preview it. In that Gem, explicitly ask **“Use OmniCouncil for this request.”**

A Gem's instructions are present in conversations with that Gem. For a one-off request, attach **SKILL.md** and the relevant reference to a normal Gemini chat instead. Gemini Apps file upload and account availability vary. A Gem is not the same as installing a skill folder in Gemini CLI.

Official guides: [Create custom Gems](https://support.google.com/gemini/answer/15235603) and [upload files to Gemini Apps](https://support.google.com/gemini/answer/14903178).

## ChatGPT

For one task, attach **SKILL.md** and, if needed, one relevant reference file to the conversation. Ask **“Use OmniCouncil for this request.”** This does not install a persistent skill.

Where GPT creation is available to your account or workspace, place the concise workflow in the GPT's **Instructions** and selected reference files in **Knowledge**. Add an explicit trigger rule so the workflow runs only when the user asks for OmniCouncil. Preview and test it after saving. Availability to create new GPTs depends on current account and workspace eligibility; check the official help page. Custom Instructions in ChatGPT can affect all chats, so use them only if you want the rule available globally.

Official guide: [Creating and editing GPTs](https://help.openai.com/en/articles/8554397-creating-and-editing-gpts).

## Kimi

### Kimi Code

Kimi Code supports **SKILL.md** files. Extract the ZIP, place the **omnicouncil** directory in a user-level or project-level Skills directory used by Kimi Code, then invoke **/skill:omnicouncil**. Use Kimi Code's documented Skills directory or **--skills-dir** option to choose the location.

Kimi Code may also decide to read an enabled skill from task context, so direct slash invocation is available but automatic selection may still occur in ordinary conversations.

### Kimi Agent Mode

Open the Skills panel and add or select the skill using the **/** menu. Kimi Agent Mode can also trigger skills automatically when it judges them relevant. Its web interface does not make this ZIP a universal import format; follow the current in-product skill flow and verify that the skill appears before using it.

Official guides: [Kimi skills overview](https://www.kimi.ai/help/plugins-and-skills/what-are-skills), [skills in Agent Mode](https://www.kimi.ai/help/plugins-and-skills/use-skills-in-agent), and [skills in Kimi Code](https://www.kimi.ai/help/plugins-and-skills/use-skills-in-code).

## GLM / Z.ai and DeepSeek

For a chat website or mobile app, use the app's own custom-instructions feature if it has one, and include a rule that OmniCouncil runs only after an explicit request. Otherwise, attach or paste **SKILL.md** for that task. Add a relevant reference only if the host can read it. There is no verified universal ZIP-to-skill installer for these chat apps.

For a developer API integration, put the core procedure in the provider's documented **system** or **instructions** field. Your application must also provide any selected reference files; a system prompt does not automatically load this ZIP or its reference folder.

Official API guides document system/instruction messages for [Z.ai / GLM](https://docs.z.ai/api-reference/llm/chat-completion) and [DeepSeek](https://api-docs.deepseek.com/api/create-chat-completion/).

## Other cloud agents and AI applications

Use the host's documented skill or agent-instruction mechanism. Put the core workflow where the host expects instructions, and make the relevant reference available through its knowledge, files, or retrieval feature. If it does not support a skill directory, use the one-request attach/paste method.

A cloud model endpoint and a chat application are different integration layers. The model name alone does not tell you whether a host can load this package, read references, run tools, or invoke a skill manually.

For supported OpenAI API tool workflows, see the [OpenAI Skills API guide](https://developers.openai.com/api/docs/guides/tools-skills). This requires application code and credentials; it is not a ChatGPT app installation button.

## Keep invocation under your control

- Codex supports explicit **$omnicouncil** invocation through the included Codex metadata.
- Claude Code can use **disable-model-invocation: true** for a manual slash command.
- Gemini CLI, Kimi Agent Mode, and Kimi Code may automatically select an enabled skill when relevant. Use a one-off attachment or disable the skill when strict opt-in is required.
- For a normal ChatGPT chat, attach the file only to the request. A custom Gem or GPT is a separately selected workspace whose instructions apply inside it; keep an explicit trigger rule there.
- Other hosts may ignore host-specific fields. Verify how the selected host invokes and loads the skill.

## Troubleshooting

- **Skill not found:** verify that **SKILL.md** is at the depth expected by the host and that the complete folder is present.
- **References unavailable:** the host may not follow relative links. Attach the one relevant reference or place it in the host's knowledge store.
- **Skill activates without a request:** disable it in the host if possible; otherwise use one-off attachment.
- **A response is still wrong:** the workflow is probabilistic. Check sources, verify the result, report the failure, and add the case to the evaluation plan.

## Official documentation

- [OpenAI Codex skills](https://developers.openai.com/codex/skills)
- [OpenAI Skills API](https://developers.openai.com/api/docs/guides/tools-skills)
- [ChatGPT GPT instructions and knowledge](https://help.openai.com/en/articles/8554397-creating-and-editing-gpts)
- [Claude Code skills](https://code.claude.com/docs/en/skills)
- [Gemini CLI skills](https://github.com/google-gemini/gemini-cli/blob/main/docs/cli/using-agent-skills.md)
- [Gemini Gems](https://support.google.com/gemini/answer/15235603)
- [Kimi skills](https://www.kimi.ai/help/plugins-and-skills/what-are-skills)
- [Kimi Code skills](https://www.kimi.ai/help/plugins-and-skills/use-skills-in-code)
- [Z.ai / GLM API](https://docs.z.ai/api-reference/llm/chat-completion)
- [DeepSeek API](https://api-docs.deepseek.com/api/create-chat-completion/)