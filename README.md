# UX Design Partner

A design skill for AI tools (Claude, Claude Code, Cursor, Codex, Windsurf and anything else that reads a markdown rules file).

It doesn't hard-code a visual style. The **method** is fixed, and the **design values** come from each project (a Figma file, token files, or a "Design values" doc), so the same skill works across different clients and products.

## What it does

**Explore** (new designs)
1. Short intake: product, audience, real copy, references, constraints
2. Studies the references by actually viewing them
3. Generates 5–8 different, named variations on one canvas
4. Renders and checks its own output before showing you
5. You pick what works from each, then it remixes your picks in rounds of 3–5

**Audit** (existing work)
1. Diagnoses first and reports findings by severity
2. Waits for your approval
3. Fixes in order: tokens → accessibility → states → layout → copy → motion → shipping checks

It also includes baseline craft rules (WCAG 2.2 AA, full component states, nested radius, no AI-sounding copy) that apply when a project doesn't say otherwise, plus a template for a per-project Design values doc.

## Install

**Claude (web / desktop)**
Download `ux-design-partner.zip` from [Releases](../../releases), or zip the `skills/ux-design-partner` folder yourself, then go to **Customize → Skills → + → Upload a skill**.

**Claude Code**
```bash
git clone https://github.com/simonhannabuss/design-partner
cp -r design-partner/skills/ux-design-partner ~/.claude/skills/        # all projects
# or: cp -r ... your-project/.claude/skills/                                # one project
```

**Skills CLI (Claude Code, Cursor, Codex and others)**
```bash
npx skills add simonhannabuss/design-partner
```

**Cursor / Codex / Windsurf / Cline**
Copy `SKILL.md` into `.cursor/rules/`, `AGENTS.md`, `.windsurfrules` or `.clinerules`.

## Using it with your own design system

Add your design values to the project the skill is working in (Figma variables, `tokens.json`, `tailwind.config`, or a `design-values.md` built from the template at the bottom of `SKILL.md`). Your project's values always override the skill's defaults. You don't need to fork the skill.

## Author

Simon Hannabuss, freelance Senior Product Designer (UX/UI): e-commerce, B2B SaaS and AR.

## Licence

MIT
