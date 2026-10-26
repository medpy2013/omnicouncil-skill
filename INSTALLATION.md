<!-- Copyright 2026 Mohamed Aouaci. SPDX-License-Identifier: Apache-2.0 -->

# Installation and invocation

Last reviewed: 2026-10-26. A skill belongs to a host application or agent runtime, not to an AI model by itself. This ZIP is a portable folder; each platform may interpret its files and commands differently.

## Download

Download [onlySkills.zip](https://github.com/medpy2013/omnicouncil-skill/raw/refs/heads/main/onlySkills.zip) and extract it intact. It contains one top-level omnicouncil/ folder with SKILL.md, references, examples, guides, and assets.

## OpenAI Codex

1. Copy omnicouncil/ to ~/.codex/skills/omnicouncil/ (on Windows: %USERPROFILE%\.codex\skills\omnicouncil\).
2. Keep the complete folder structure. Refresh skill discovery or restart Codex if needed.
3. Invoke with $omnicouncil. The included agents/openai.yaml disables implicit invocation in Codex.
4. Confirm it appears in your skills list and run the relevant checks in EVALUATION.md.

Docs: [Codex skills](https://developers.openai.com/codex/skills).

## Claude Code

1. Put the folder at ~/.claude/skills/omnicouncil/ or .claude/skills/omnicouncil/ in a project.
2. To require manual invocation, add this Claude Code-specific field to the SKILL.md YAML frontmatter: disable-model-invocation: true
3. Start or reload Claude Code and invoke /omnicouncil.

That setting applies to Claude Code; it does not configure Claude.ai or every Anthropic product. Docs: [Claude Code skills](https://code.claude.com/docs/en/skills).

## Gemini CLI

Gemini CLI supports Agent Skills. Follow its current installation prompts; then use /skills list to confirm discovery and explicitly request OmniCouncil. Depending on the CLI version, relevant skills may be activated automatically. This package cannot enforce manual-only use there. Docs: [Gemini CLI Agent Skills](https://github.com/google-gemini/gemini-cli/blob/main/docs/cli/using-agent-skills.md).

## ChatGPT app

For one request, attach SKILL.md and the single relevant reference file, then say “Use OmniCouncil.” For a reusable custom GPT, place the core procedure in Instructions and add accessible reference files as Knowledge. This is not the same as installing a skill folder, and it does not guarantee explicit-only activation.

## OpenAI API and other hosts

Use the supported skills/instructions mechanism documented by your runtime. The OpenAI API supports skill ZIPs in compatible tool workflows; this requires application-side configuration. If no skill system exists, attach or paste SKILL.md and the relevant reference file for each request.

## Compatibility and testing

No universal installer can make every model or app load these files. Reference routing works only when the host can read the referenced files. Codex has explicit-only metadata; Claude Code has a host-specific setting; Gemini CLI may auto-activate matching skills. Other hosts are manual-use guidance until tested. Record host, exact model/version, date, and results using EVALUATION.md. Do not claim universal compatibility or guaranteed accuracy.
