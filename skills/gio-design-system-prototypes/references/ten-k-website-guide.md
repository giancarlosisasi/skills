# Build a $10K Website in Claude Code: Free Setup Guide

Full copy of the noocap guide, taken on 2026-09-25 from its public Notion page:
https://noocap.notion.site/Build-a-10K-Website-in-Claude-Code-Free-Setup-Guide-356508e99dda816c9d15ea892d4139f9

It is embedded here because the link can break. The text below is the guide itself, quoted as published.

---

The exact 4-step setup to go from blank terminal to a polished, production-ready site — using Claude Code as your developer.

## Why this works

You don't need a designer. You don't need a dev team. You need the right setup before you start prompting — because Claude Code is only as good as the environment, animations, design taste, and components you give it access to.

This guide is the exact stack that turns Claude Code from a generic code generator into a senior-level web designer.

## Step 1 — Install Claude Code

Claude Code runs locally on your machine through your terminal. One command and you're in.

Install command:

```
npm install -g @anthropic-ai/claude-code
```

Then run:

```
claude
```

Requirements: Node.js 18+ installed. Sign in with your Anthropic account when prompted.

Why this matters: Claude Code can read your full project, edit multiple files at once, run commands, and iterate — that's what makes it different from copy-pasting code from a chat window.

## Step 2 — Add Animation Support (Framer Motion)

Default AI-generated sites look static and lifeless. Animation is the #1 thing that makes a site feel premium.

Install Framer Motion:

```
npm install framer-motion
```

Then tell Claude Code in your project context:

> "Use Framer Motion for all animations. Apply scroll-triggered fades, staggered reveals, and smooth hover transitions on interactive elements."

What changes: Hero sections breathe. Cards slide in on scroll. Buttons feel alive. This single addition is what separates "AI website" from "agency website."

## Step 3 — Add a Design-Focused Skill

Claude Code supports Skills — reusable instruction sets that guide how Claude approaches a task. A frontend design skill teaches Claude taste: spacing, hierarchy, typography, color systems, and layout principles.

How to add it:

1. Create a .claude/skills/ folder in your project root
2. Add a SKILL.md file with design rules (or use the public frontend-design skill)
3. Claude Code will automatically reference it when building UI

What to include in the skill:

- Typography scale (use a real type system — not random font sizes)
- Spacing system (8px base grid)
- Color tokens (primary, neutral, accent — no random hex codes)
- Component patterns (button states, card structure, form layouts)
- "Avoid generic AI aesthetic" instructions

Why this matters: Without a design skill, Claude Code defaults to generic Tailwind patterns. With one, every component follows a consistent design system — the kind agencies charge $10K to build.

## Step 4 — Integrate a Component Library (21st.dev)

Don't reinvent the wheel. 21st.dev (http://21st.dev) is a library of production-ready, beautifully designed components you can drop straight into your project.

How to use it:

1. Visit 21st.dev
2. Browse components (heroes, pricing tables, testimonials, navbars, footers)
3. Copy the component code
4. Paste into your project and tell Claude Code to integrate it

Prompt to use:

> "Integrate this 21st.dev component into our landing page. Match it to our design tokens, replace the placeholder content with our copy, and add Framer Motion entrance animations."

Why this matters: Every component is already designed by professionals. Claude Code adapts it to your brand. You skip 80% of the design work and end up with a site that looks expensive.

## The Full Stack at a Glance

- Code generation: builds and edits your site locally. Tool: Claude Code.
- Animation: adds polish and motion. Tool: Framer Motion.
- Design system: teaches Claude design taste. Tool: Frontend Design Skill.
- Components: production-ready UI blocks. Tool: 21st.dev.

## Starter Prompt to Use After Setup

Once all 4 layers are in place, drop this into Claude Code to kick off your site:

```
Build a modern landing page for [YOUR PRODUCT/SERVICE].

Requirements:
- Use Next.js 14 with the App Router
- Tailwind CSS for styling
- Framer Motion for all animations (scroll reveals, hover states, page transitions)
- Pull hero, features, and pricing sections from 21st.dev components
- Follow the design tokens defined in our frontend design skill
- Add a sticky navbar, a hero with a headline + CTA, 3 feature cards, social proof section, pricing, FAQ, and footer
- Mobile-first, fully responsive
- Lighthouse score 90+ on performance

Start by setting up the project structure, then build section by section. Show me each section before moving to the next.
```

## Common Mistakes to Avoid

- Skipping the design skill. Without it, you'll get a generic site that screams "AI-generated."
- Vague prompts. Be specific about sections, animations, and content. Claude Code is only as good as your brief.
- Not iterating. First output is rarely the final output. Ask Claude Code to refine spacing, contrast, and motion.
- Forgetting performance. Always ask for lazy-loaded images, optimized fonts, and a Lighthouse audit at the end.

## What You Just Saved

- Hire a web designer: 4–8 weeks, $5K–$15K.
- Hire an agency: 6–12 weeks, $10K–$30K.
- Claude Code + this stack: 1–3 days, $20/month.

## Next Steps

1. Install Claude Code today
2. Set up Framer Motion + a frontend design skill in your starter template
3. Bookmark 21st.dev
4. Build your first site this week

That's it. No fluff, no upsell. Just the stack.

---

## How the gio-design-system-prototypes skill applies this guide

- Step 2 (animation): on a plain HTML prototype page, use Motion, the vanilla build of Framer Motion, from the CDN: `<script src="https://cdn.jsdelivr.net/npm/motion@11.11.13/dist/motion.js"></script>`. It defines the global `Motion` with `animate`, `inView`, `scroll`, `stagger` and `spring`. In product code that uses React, use the `motion` package the repo already pins.
- Step 3 (design skill): the chosen design system page IS that skill's source. Its tokens (type scale, 8px spacing grid, color roles, component states) are exported at the end of the process.
- Step 4 (components): build components at 21st.dev quality in vanilla HTML, CSS and JS. Examples of that level: a bento grid, a spotlight card with a radial highlight that follows the pointer, a magnetic button, an animated gradient border, a marquee, a number ticker, animated beams between nodes, a dock with magnification, a text reveal by word.
