---
name: gio-design-system-prototypes
description: Create design-system-prototypes/ for the current repo — three complete design systems built from the product itself, published as pages, then the pick, the tokens and screen mockups.
disable-model-invocation: true
argument-hint: "[optional direction, e.g. 'dark first, playful' or a fixed brand color]"
---

# Design system prototypes

Build a folder `design-system-prototypes/` at the repo root with **three complete design systems** for this product. The user picks one, and it becomes the visual base of every screen.

Every repository gets its **own** style. Take every choice (palette, fonts, motion, mascot, copy) from what this product is, who uses it, and what it must feel like. If the user passed a direction as an argument, treat it as a fixed input.

Two references live in this skill's folder. Read both in full before you write any page:

- `references/apple-design.md`: fluid motion and craft (springs, interruptible motion, materials, typography, accessibility).
- `references/ten-k-website-guide.md`: the "$10K website" stack (animation, design skill with real tokens, 21st.dev-level components) and how this skill applies it.

## Step 0. Read the project

- Read `CLAUDE.md`, `README`, `docs/`, the landing copy, any tokens or theme file, any logo or brand file, and the i18n files.
- Find: the product, the audience, the one job of the main screen, the locales, the copy voice, and the style stack (CSS variables, Tailwind, StyleX, other).
- Collect the real domain content: entity names, real numbers, statuses, sample records. Every specimen uses this content.
- An existing brand color or logo is a fixed input. Keep it and say so in the brief.
- Read the repo rules about vocabulary, copy and themes. They bind every page.
- Write `design-system-prototypes/briefs/BRIEF.md`: product, audience, personality in 3 adjectives, sample content, constraints, and the 10 sections of Step 2.

Done when the brief exists and every specimen you plan has real content from this repo.

## Step 1. Choose three directions

- Palettes: Color Hunt popular (https://colorhunt.co/palettes/popular) and Coolors trending (https://coolors.co/palettes/trending). Pick three palettes that fit this product's personality. If a site does not load, build the palette yourself from the product's world and say so.
- Give each system a one-word name that fits the product, and a distinct personality. Example spread: one dark first, one light first, one tactile or playful.
- Pair three Google Fonts per system: a display face, a text face and a mono face. Use a different family set in each system. Pick families specific to this product, outside this list of overused faces: Inter, Space Grotesk, Geist, Unbounded, Lexend, Public Sans, IBM Plex, Roboto, Poppins, Montserrat.
- Pick one bold idea per system for its cover, and tie it to the product: the product's main action, its data, or its mascot at work.

Done when each system has a name, a palette with a link, three fonts, an icon set and one bold idea.

## Step 2. Build one page per system

File: `design-system-prototypes/design-systems/ds-<name>.html`. One self-contained file under 220 KB. Motion, Three.js and one icon library load from a CDN and do not count toward the size.

Every page has the same 10 sections **in the same order**, so the user compares the systems like for like:

1. cover
2. principles
3. color, with the live WCAG contrast ratio of each color role
4. typography
5. iconography
6. spacing and elevation
7. layout
8. motion, with the spring tokens (damping and response) and a demo the user can grab and interrupt
9. components, built from the product's real screens
10. voice and tone

At the end of each page, give the tokens as one CSS `:root` block, ready to copy: color roles for light and dark, font families, type scale, spacing (8px grid), radius, durations, easings and springs.

### Live interactions (every page)

1. a spring toggle
2. a draggable element with momentum projection and rubber-band edges
3. a staggered grid reveal
4. a number ticker
5. one orchestrated moment that shows the product's main action from start to end

Add two or three interactions that only this product has.

### Libraries

- Motion (the vanilla build of Framer Motion): `<script src="https://cdn.jsdelivr.net/npm/motion@11.11.13/dist/motion.js"></script>`. Global `Motion` with `animate`, `inView`, `scroll`, `stagger`, `spring`.
- Three.js, only for a bold 3D idea: `<script type="module">import * as THREE from 'https://cdn.jsdelivr.net/npm/three@0.169.0/build/three.module.min.js'</script>`. Import only this build; write your own shaders. Cap `devicePixelRatio` at 2. Render only while the canvas is on screen and the tab is visible. Show one still frame under reduced motion. Give the canvas a static CSS fallback from the palette.
- Fonts from Google Fonts, each with a real fallback stack.

### Page format

- Write page content directly: a `<title>` and a `<style>` at the top, then the markup and scripts. The publish step wraps it in `<html>`, `<head>` and `<body>`.
- Scripts load only from cdnjs.cloudflare.com, cdn.jsdelivr.net/npm, or unpkg.com. Stylesheets load only from Google Fonts. Inline everything else.
- The layout works at 400px width with a 16px side gutter, and the page body never scrolls sideways.

## Step 3. Rules for every page

- **Two themes, both first-class.** A System, Light and Dark switch on every page. Put the full light palette on `:root`. Redefine the tokens under `@media (prefers-color-scheme: dark)` with `:root:not([data-theme="light"])`, and again under `:root[data-theme="dark"]`, with `color-scheme: dark` in both. Give `body` an explicit background token.
- **Tinted neutrals.** Tint every grey toward a palette hue. Grounds and large surfaces are graphite, warm charcoal, ink, bone or paper. Blue and violet appear as solid, saturated, flat fills: a full-bleed band, a block, a big number, a filled button. Grounds in navy, midnight blue, blue-black or violet-black read as AI-made; keep them out. A primary button on dark is a strong fill with high contrast, never a pale lavender.
- **Color where it means something.** The palette appears at full strength in big places: the cover, one full-bleed band, category tiles, charts. Tool surfaces stay calm.
- **A look of its own.** Stay clear of the common AI looks: cream with a serif and terracotta, near-black with one acid-green accent, a purple-to-blue gradient hero, emoji as section markers, the same radius and shadow on every block.
- **Objective copy ("show, don't tell").** Each line says what a thing does or what the person does. Good: "Tap, flip, find out", "Every number comes from a recorded event". Write in the product's main locale, with real content only.
- **Complete at rest.** Every text and specimen is visible with no JS and no scroll. Scroll reveals start from a visible state, with opacity at 0.4 or more. The cover is sized to its content.
- **Motion follows `references/apple-design.md`.** Controls answer on pointer-down (`scale(0.97)`). Springs default to damping 1.0; bounce only after a gesture with momentum. Motion starts from the current on-screen value and can be grabbed mid-flight. Everything calms down under `prefers-reduced-motion`, `prefers-reduced-transparency` and `prefers-contrast`. One orchestrated moment per page; the only ambient loop is the 3D cover, paused off screen.
- **Machine limits.** Leave dev servers to the user. Give every shell command `timeout 60`. Search only inside the repo. Run at most three subagents, one per system, and each one writes only its own file. When you delegate a page, paste Steps 2 and 3 and the two reference files into the subagent prompt.

## Step 4. Check and publish

- If `agent-browser` exists on this machine, take one screenshot of each cover in each theme. Make one pass of fixes, then stop checking.
- If the Artifact tool exists, publish each page as an Artifact. If not, give the user the local file paths.
- Write `design-system-prototypes/README.md`: a list of the three systems (file, URL, palette, fonts, icon set, bold idea), the copy rule, and the decisions that bind every page.
- Write `design-system-prototypes/REDESIGN-STATE.md`: the current state and the next step.
- Leave git to the user. Tell them the folder path.

## Step 5. Reply

- The three URLs or file paths.
- For each system, three lines: its personality, its strongest interaction, its weak point.
- Your recommendation and its reason in one line.
- One question: which system the user picks. Then stop and wait.

## After the pick

1. Record the pick in `README.md` and `REDESIGN-STATE.md`.
2. Export the chosen tokens to `design-system-prototypes/tokens/` in the style format this repo uses (CSS variables, a Tailwind theme, StyleX `defineVars`, or JSON).
3. If the product needs a mascot or a brand mark: three directions in `design-system-prototypes/mascot/`, one page, with a light and a dark ground, 84, 32 and 16 px sizes, a one-color version and an idle animation. Ask the user to pick one.
4. For each new screen: three quick HTML mockups in the chosen system in `design-system-prototypes/<screen>/`, published, then one question: which mockup. Product code changes only after that pick.
