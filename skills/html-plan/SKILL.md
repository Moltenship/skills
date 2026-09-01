---
name: html-plan
description: Create human-readable plans as standalone HTML pages. Use when the user asks to create, write, or export a plan in HTML format. Follows the Vercel design system (vercel.com/design.md) strictly for all visuals, and runs the unslop skill on all copy so the plan reads like a human wrote it.
---

# HTML Plan

Produce a plan as a single self-contained HTML file that is pleasant to read and strictly follows Vercel's design language.

## Prerequisites

1. **unslop skill (required).** Check whether the `unslop` skill is available. If it is not installed, stop and ask the user to install it first:

   ```
   npx skills add https://github.com/cursor/plugins --skill unslop
   ```

   Do not proceed without it — every piece of text in the plan must pass through unslop.

2. **Vercel design guide (required).** Fetch https://vercel.com/design.md and treat it as the single source of truth for all visual decisions. Follow it strictly: colors, typography, spacing, radii, borders, light/dark handling — no improvisation, no substitute palettes, no decorative extras the guide doesn't sanction.

## Workflow

1. Fetch https://vercel.com/design.md before writing any markup or CSS. Re-fetch it every time; do not rely on a remembered version.
2. Draft the plan content: goal, context, phases/steps, risks, open questions — whatever structure fits the task. Keep it scannable.
3. Apply the `unslop` skill to all prose in the plan. Remove AI tells: filler intros, hedging, bullet spam, em-dash overuse, "delve/leverage/robust" vocabulary, symmetrical fluff.
4. Build a single self-contained HTML file:
   - All CSS inline in a `<style>` block; no external stylesheets, frameworks, or JS unless the plan genuinely needs interactivity.
   - Use only design tokens, type scale, and spacing from design.md.
   - Semantic HTML: `<header>`, `<main>`, `<section>`, real heading hierarchy.
   - Support light and dark color schemes if design.md defines both.
5. Save the file next to the work it describes (default: `plan.html` in the current directory, or the path the user gives) and tell the user where it is.

## Tone: document, not landing page

This is a working plan, not a marketing page. It should read like a well-typeset internal document:

- No hero sections, no oversized display headings, no taglines or punchy one-liners.
- Headings are quiet and functional — modest sizes, sentence case, there to navigate, not to sell.
- No calls to action, badges, gradients, cards-for-the-sake-of-cards, or promotional layout patterns.
- Body text carries the plan; density and readability beat visual drama. When in doubt, make it calmer.

## Quality bar

- A reader should grasp the whole plan by skimming headings and the first line of each section.
- Visuals must be indistinguishable from a page built by someone following Vercel's design system by hand.
- No lorem ipsum, no placeholder sections, no empty decorative chrome.
