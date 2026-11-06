---
name: "ux-design-partner"
description: "Use when designing or auditing UI, landing pages, app screens or components: explores 5-8 reference-led variations, or audits existing work, using each project's own design values."
---

# UX Design Partner

A working method for product and UI design with AI. The method is fixed. The **design values change per project**, and they always come from the project, never from this file.

There are two modes:
- **Explore**: new designs, a new page or screen, or a new direction. Taste comes from references and variations.
- **Audit**: improving something that already exists. Diagnose first, then fix in priority order.

If the request doesn't make the mode clear, ask: "Are we exploring new directions or auditing what's there?"

---

## Step 0: Load the project's design values (always first)

Look for the values in this order and use the first source you find:
1. A Project doc called "Design values" (or similar: brand, tokens, design system) in the current Claude Project.
2. In a repo: `design-values.md`, `DESIGN.md`, token files (`tokens.json`, `tailwind.config.*`, CSS custom properties), or an existing component library.
3. A Figma file or design-system link the person has given.
4. A design-system artifact the person points to.

Then:
- Briefly say which source you're using.
- If the source conflicts with a rule in this skill, **the project wins**. This skill's rules are defaults for when the project says nothing.
- If there is **no source**, don't make one up silently. Ask the 5 intake questions in the template at the bottom, or offer to draft a Design values doc from the template for the person to approve. Only if they say "just go" should you use neutral defaults, and label them clearly as provisional.

---

## Mode A: Explore

The principle: rules can't supply taste, but examples can. Don't one-shot it.

### A1. Intake (keep it short)
You need these before any visuals:
- **Product & audience**: what it is, who it's for, and the one job this page or screen must do.
- **Real content**: actual copy, features, data and customer pain points. Placeholder text makes any design look like AI output.
- **References**: 2-4 sites, products or past work the person admires, and *what* they like about each (type, density, motion, tone).
- **Constraints**: platform, breakpoints, accessibility needs, tech stack, and existing components that must be reused.

If references are missing, suggest 3-4 relevant ones and ask the person to choose. Don't proceed without at least one.

### A2. Study the references, and actually look
- Load and view images or screenshots of every reference. Don't work from the name or memory alone.
- For each one, write 3-5 concrete observations: type pairing and scale, grid and whitespace, colour strategy, how it shows the product, motion, copy tone.
- Pull **lessons, not layouts**. Never copy a reference's structure or assets.

### A3. Generate 5-8 variations
- Put them all on one artifact or canvas side by side, not as separate files.
- Make them **really different**: each variation takes a distinct, named direction (e.g. "Editorial calm", "Product-led walkthrough", "Dense dashboard", "Dark luxury").
- Under each, add one line on what it borrows from which reference and the trade-off it makes.
- Every variation uses the project's design values and the real content.
- Push yourself: the later variations must not drift back to generic. If one starts looking like the defaults below, replace it.

**Defaults to avoid** (they read as AI-made):
- Three equal cards in a row, or a 2×2 grid of identical feature tiles.
- A centred hero with a gradient blob and a vague headline.
- Icon + bold title + one sentence, repeated six times.
- Everything the same size, weight and spacing, with no hierarchy.
- Stock buzzword copy ("Empower your workflow", "Built for the future").

### A4. Look at your own output
Render every variation and view it, as a screenshot or in the artifact, before presenting. Check the hierarchy, the rhythm, overflow, contrast, and mobile at about 375px. Fix what's obviously broken. Never present work you haven't seen rendered.

### A5. Hand the judgment to the person
Show the set and ask which parts work, not which one wins: "What do you like from each?" The creative judgment is theirs.

### A6. Remix loop
Turn their picks into the next round, for example "#3's layout in #5's visual language, with #1's pricing block".
- Generate **3-5** new variations per round. Never just 1, because that caps the exploration.
- Repeat until they're happy, then move to refinement: states, responsive behaviour, edge cases (see Craft rules).

---

## Mode B: Audit

### B1. Diagnose before touching anything
Review the existing work: screens, a URL, a Figma file or code. Report your findings grouped by severity:
- **Blocking**: broken flows, accessibility failures, missing critical states, content that misleads.
- **Important**: hierarchy problems, inconsistency with the design values, generic patterns, weak copy.
- **Polish**: spacing drift, radius mismatches, motion, micro-copy.

For each finding, give: where it is, what's wrong, why it matters for the user, and the proposed fix.

**Stop and get approval** before making changes. The person may reprioritise.

### B2. Fix in this order
1. Design values: type, colour and spacing tokens brought into line with the project.
2. Accessibility and contrast.
3. States: hover, focus, active, disabled, loading, empty, error, success.
4. Layout and hierarchy.
5. Copy.
6. Motion.
7. Shipping checklist.

Fix within the existing structure. Don't rewrite the project unless asked. Re-render and look after each group of fixes.

---

## Craft rules (both modes; the project's values override these)

**Tokens**
- Use only the project's spacing, type, radius and colour tokens, and never invent in-between values. If a value is truly missing, flag it and propose adding it to the system.
- Nested radius: inner radius = outer radius − padding (minimum 2px). A 16px card with 8px padding gets 8px children.

**Hierarchy & layout**
- One clear primary action per view.
- Vary the size and weight of content blocks to show importance, rather than giving everything equal tiles.
- Align baselines across cards, and use optical padding where icons or text look off-centre.

**States**: every interactive element needs hover, focus-visible, active and disabled states. Every data view needs loading, empty, error and partial states. Forms need validation, error recovery and success.

**Accessibility (WCAG 2.2 AA minimum)**
- 4.5:1 contrast for text, 3:1 for large text and UI components.
- Visible focus, keyboard reachability, and target sizes of at least 24×24px (44px preferred on touch).
- Semantic structure, labelled inputs, alt text, and no meaning carried by colour alone.
- Respect `prefers-reduced-motion`.

**Motion**: purposeful, short (150-300ms for UI), with custom easing. Prefer IntersectionObserver over scroll listeners.

**Copy**
- Use real copy from the person, in the project's voice and locale (e.g. UK English).
- No lorem ipsum, fake names or round fake numbers.
- Avoid the usual AI tells: em-dash overuse, triplets, back-to-back fragment sentences, "not just X, it's Y", buzzwords.
- Headlines say what the product does for whom. Buttons say what happens next.
- If a dedicated copy skill is available, hand the copy pass to it.

**Shipping checklist** (web): favicon, meta and OG tags, 404 page, legal links, form validation, alt text, responsive at 375 / 768 / 1280+, and nothing broken at 200% zoom.

---

## Output conventions
- Design work goes on an artifact or canvas the person can keep and edit (or into Figma if they're working there), not as code pasted in chat.
- Keep commentary short: a named direction plus one line of rationale per variation.
- At the end of a session, offer to update the project's Design values doc with any decisions made (new tokens, or patterns approved or rejected), so the next session starts from them.

---

## Template: Design values (one per project)

Use this when the project has no values doc. Ask these 5 intake questions first:
1. Who is it for, and what's the one job of the product or page?
2. 2-4 references you admire, and what you like about each.
3. Existing brand assets: logo, colours, fonts, guidelines?
4. Tone of voice in three words, plus words to avoid.
5. Constraints: platform, stack, component library, accessibility requirements, locale.

Then draft the doc below for the person to approve and save to the project:

```markdown
# Design values: <Project / Client>

## Context
Product · audience · primary job · locale

## References
- <site> — take: <what>; avoid: <what>

## Type
Families (display / text / mono) · scale · weights allowed · line-heights

## Colour
Neutrals · one primary accent · semantic (success / warning / error / info) · light/dark rules

## Spacing & layout
Scale (e.g. 4 / 8 / 12 / 16 / 24 / 32 / 48 / 64 / 96) · grid · max widths · breakpoints

## Shape & elevation
Radius scale · borders · shadow style

## Motion
Durations · easing curve · reduced-motion behaviour

## Components
Library / source of truth (Figma link, repo path) · must-reuse components

## Voice
Three words · do / don't · banned phrases

## Decisions log
<date> — <decision> — <why>
```