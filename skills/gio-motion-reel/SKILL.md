---
name: gio-motion-reel
description: Make a 30-second motion graphics reel with synced, synthesized music for the current repo's product, as one scrubbable HTML page.
disable-model-invocation: true
argument-hint: "[optional length in seconds or focus, e.g. '45' or 'focus on the AI agent']"
---

# Motion reel

Make a **30-second motion graphics reel with synced music** for this product: one HTML page, published as an Artifact when that tool exists. It works as a showreel. Every shot shows motion craft, and every word and number is true for this product. An argument can change the length or the focus; scale the storyboard times to match.

This skill's folder holds two references:

- `references/example-reel.html`: a complete, working reel (the product "Forja" with its mascot "Chispa"). Reuse its engine: easing, `seg`, `render(t)`, the canvas bursts, the instruments, the score and the lookahead scheduler. Replace all of its content, colors and copy with this product's.
- `references/apple-design.md`: motion craft and multimodal feedback (causality, harmony, utility). Read sections 13 and 14 before you write the sound and the reduced-motion path.

## Step 0. Read the project

- Read `design-system-prototypes/README.md` and `REDESIGN-STATE.md` if they exist, and use the chosen design system: palette, fonts, tokens and mascot files. If they do not exist, use the repo's tokens, theme and logo files.
- Read `CLAUDE.md`, `README`, `docs/` and the landing copy. Find the product name, the tagline, the main user action, the AI features, the incumbents or old standards this product replaces, and the copy and vocabulary rules.
- Collect every number from the code: block types, question types, locales, integrations, anything countable. Count real files or enum members, and keep the source of each number for the reply.

Done when you have the brand inputs, the positioning facts and every number with its source.

## Step 1. Storyboard

Write it before any code: a list of shots with start and end times, 30 seconds in total. Use this arc and adapt it to the product.

1. **Open**, 0 to 1.5 s: the brand spark or logo mark appears with anticipation, overshoot and a shockwave, then splits into the palette colors.
2. **Palette**, 1.5 to 3.5 s: the colors become full-height bars, the hex codes scramble into place, and the bars fold into a line that the next shot uses.
3. **Name**, 3.5 to 7 s: the product name rises letter by letter from a mask with a variable-weight wave; the tagline follows.
4. **Positioning**, 7 to 11 s: a timeline with years shows the old standards or incumbents, and the product arrives last. All markers stay on screen together. Facts only: years, formats, how the work flows.
5. **Old way and new way**, 11 to 14 s: two panels. The old one shows its real flow (for example export, upload, replace). The new one shows a live edit and a publish. A neutral title such as "Same goal, another way."
6. **The AI agent or mascot**, 14 to 17 s: a match cut from the last object into the mascot. The mascot builds with squash and stretch, springs and a blink. A line says what the agent is and what it does. Status chips show its states.
7. **Demo, one prompt**, 17 to 21 s: a prompt types into a composer, the send button presses, and result tiles fly along arcs into a card and land with squash.
8. **Demo, one edit**, 21 to 25 s: a second prompt asks for a change. Only the changed part pulses and changes. One more AI action follows, for example a translation that flips the labels.
9. **Features**, 25 to 27.5 s: a bento of six tiles, each with a real number or fact and its own small live animation.
10. **Lockup**, 27.5 to 30 s: the mascot flies next to the wordmark, with a palette line, the tagline and a credit line. Everything fades to the ground for a clean loop.

The comparison in shots 4 and 5 is respectful: it shows facts the user can check, and lets the viewer draw the conclusion.

## Step 2. Reading time (hard rule)

- Every text stays **fully visible** for at least max(1.6 s, 0.3 s per word + 0.6 s), counted after its entrance ends and before its exit starts.
- A headline fits on one line at 1600 px. Shorten it or reduce the size until it does.
- One text idea on screen at a time.

## Step 3. Build

- A 1600x900 stage, scaled with a CSS transform to fit a 16:9 frame at any width.
- `render(t)` is a pure function of time: every property of every element is computed from `t`. Motion comes only from `render(t)`, so scrubbing is exact.
- Controls: Play/Pause, Sound, Restart, a scrubber with chapter buttons, and a timecode in seconds and frames at 60 fps.
- Craft: easing functions (outExpo, ioExpo, outBack, a damped spring), staggers, arcs on quadratic curves, squash and stretch on landings, match cuts between shots, blur on fast exits.
- Confetti and sparks go on one canvas. Each burst has a fixed seed and computes each particle from `t`.
- Use the design system: its Google Fonts, its color tokens, and light and dark themes with the same `:root` pattern as its pages.
- Under `prefers-reduced-motion`, show the lockup frame and play only when the viewer presses Play.
- Page format: a `<title>` and `<style>` at the top, no `<html>`, `<head>` or `<body>` tags. Scripts only from cdnjs, jsdelivr or unpkg; stylesheets only from Google Fonts.

## Step 4. Sound

Web Audio synthesis only; the page carries no audio files.

- Browsers start audio only after a click, so a **Sound** button starts it.
- A score: one sorted array of `{ time, instrument call }` events at 120 bpm (one beat is 0.5 s).
- Instruments: kick, clap, hi-hat, bass, pad chords, bell, pluck, pop, click, whoosh, riser, crash, thud, boing. A compressor on the master and a convolver reverb with a generated impulse response.
- The music follows the arc: a soft intro, a drop when the name lands, a breakdown with an arpeggio when the mascot appears, a riser into a second drop when the demo starts, a final chord on the lockup.
- Scene cuts and drops sit on the beat grid. Every visual event gets its sound **on the same frame**: letters land, tiles land, keys type, the send button presses, markers pop, confetti bursts.
- While sound plays, the audio clock drives the picture: `t = start + (audioContext.currentTime - audioStart)`. A lookahead scheduler sends the events of the next 0.2 s. On pause, seek or restart, fade the old bus out and schedule again from the new `t`. On a loop, continue with the next pass of the score.

## Step 5. Copy

- The product's main locale.
- Objective language ("show, don't tell"): each line says what the product does or what the person does.
- A comparison uses only facts you can point to in the repo docs.
- The repo's vocabulary rules still bind. If the user asked for a word those rules forbid, use it and name the conflict in the reply.

## Step 6. Check and publish

- If `agent-browser` exists: one contact sheet of about 10 key frames. Drive the scrubber with `eval`, take one screenshot per frame, join them with ImageMagick (`magick a.png b.png +append row.png`, then `-append`).
- One pass of fixes for what the sheet shows: overlaps, wrapped headlines, markers that leave before they can be read, misplaced elements. Take one more screenshot only to confirm a geometric fix.
- Close the browser and delete the screenshots.
- Publish the page as an Artifact if the tool exists; otherwise give the local path.

## Step 7. Reply, in two sections

1. **Product**: the shots in order, what each one shows, and how the sound follows the picture.
2. **Technical**: the files the reel reads, the source of each number, how the clock and the scheduler work, what you verified, and what you could not verify (for example the mix levels, because the test browser has no audio output).
