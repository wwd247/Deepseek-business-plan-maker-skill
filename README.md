# Business Plan Maker

A skill for DeepSeek Harness (and other Agents-Skills-compatible runtimes)
that interviews the user and produces a complete business plan as a Word
document.

## Install

Copy the `business-plan-maker/` folder into your skills directory:

- Project-level: `.dsh/skills/business-plan-maker/`
- User-global:    `~/.dsh/skills/business-plan-maker/`

No API key or configuration required — the skill runs inside your existing
agent session.

## Usage

Ask the agent to create a business plan. The skill will interview you in a
few short passes, then produce the document.

## Layout

    SKILL.md                            skill definition
    references/template-structure.md    baked-in template
    scripts/build_docx.py               optional Word-output helper
