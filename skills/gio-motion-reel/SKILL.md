---
name: gio-motion-reel
description: Make a 30-second motion graphics reel with synced, synthesized music for the current repo's product, as one scrubbable HTML page.
disable-model-invocation: true
argument-hint: "[optional length in seconds or focus, e.g. '45' or 'focus on the AI agent']"
---

# Motion reel

Make a **30-second motion graphics reel with synced music** for this product: one HTML page, published as an Artifact when that tool exists. Every word and number is true for this product. An argument can change the length or the focus; scale the storyboard times to match.

This skill's folder holds two references:

- `references/example-reel.html`: a complete, working reel (the product "Forja" with its mascot "Chispa"). Reuse only its engine parts: easing, `seg`, `render(t)` and the scrubber. Its drum score, its pitched action sounds and its audio clock break principles 11, 12 and 15. Do not copy them; follow Step 4.
- `references/apple-design.md`: motion craft and multimodal feedback (causality, harmony, utility). Read sections 13 and 14 before you write the sound and the reduced-motion path.

## Principles (hard rules)

These 18 rules bind every step below. When a step and a principle disagree, the principle wins. In the reply, name each principle that changed a decision.

### Direction

1. **One subject, one audience.** When: you write the storyboard. Rule: every scene answers what the person asked for. Context the audience already knows gets no scene. If you break it: the main message gets lost in context that nobody needed.
2. **One idea per scene.** When: you write a scene. Rule: if the scene needs an "and" to explain it, it is two scenes. If you break it: the viewer does not know which of the two ideas is the important one.
3. **Text is read once.** When: you put text on screen. Rule: one short headline and at most one support line. Reference material goes outside the reel, on the page under the player. If you break it: the reel moves on while the viewer is still reading.
4. **Show, do not tell.** When: you choose between animating an act and writing it. Rule: the scene shows what the person or the product does. Animate the act; do not write a description of it. If you break it: the reel becomes a slide deck that moves.
5. **The product's identity rules.** When: the product already has its own color, type or motion language. Rule: the reel uses that language. Your own style does not replace it. If you break it: the reel looks like another brand.

### Animation

6. **One focus at a time (staging).** When: in every frame. Rule: only one thing moves. Everything else stays still or dims. If you break it: the eye follows everything that moves, so two moving things split it, and that causes stress.
7. **Every movement has a purpose.** When: you add a movement. Rule: the movement reveals, connects or confirms something. A movement that only decorates goes out, and so do endless background loops. If you break it: visual noise hides the idea.
8. **Calm by default, energy on request.** When: you choose curves and effects. Rule: soft entrances and short travel. Bounce, particles and flashes only when the tone asks for them. If you break it: the reel feels generic and tiring.
9. **Continuity between scenes.** When: you go from one scene to the next. Rule: one element of the scene before leads into the next one: it moves, changes size or changes role. Do not clear everything and start from zero. If you break it: every cut makes the viewer find their place again.
10. **Time to read and breathe.** When: you set the rhythm of the reel. Rule: every text stays still long enough to read it. A scene leaves completely before the next one enters, and a pause separates two ideas. If you break it: texts overlap and nothing stays in memory.

### Music and sound

11. **The music is the base, not the star.** When: you choose the music. Rule: calm music, with a harmony that changes per section. No short loop that repeats. If you break it: it sounds generic and pulls attention from the message.
12. **An action sound does not compete with the music.** When: you give a visual event a sound. Rule: sounds with no musical pitch, short and quieter than the music. If you break it: a pitched note can clash with the harmony and break the mood.
13. **Picture and sound are one event.** When: you sync the sounds. Rule: the sound lands at the same instant as its visible cause. A sound with no visible cause goes out, and a minor act needs no sound. If you break it: the viewer links the sound to nothing and hears it as noise.
14. **Silence never happens by accident.** When: the viewer starts, pauses or jumps to another moment. Rule: the sound of that moment plays at once. If you break it: the sound looks broken.

### Quality

15. **Smooth motion is worth more than an effect.** When: an effect makes the motion less smooth. Rule: remove the effect. If you break it: an animation that stutters looks worse than a simple, smooth one.
16. **Test as the viewer tests.** When: before you deliver. Rule: test in the viewer's environment, with sound, from start to end, at real speed. A test with no sound does not test the sound. If you break it: the bugs that show only in real use reach the viewer.
17. **Review as a viewer, not as the author.** When: you review the key frames. Rule: look for two focuses at the same time, cut or overlapping texts, remains of the scene before, and elements out of place. If you break it: the author sees what they meant to make, not what is on screen.
18. **Accessible by design.** When: always. Rule: with reduced motion, the reel shows one still, readable frame. The contrast is enough to read. The message does not depend only on sound or on color. If you break it: part of the audience is left out.

## Step 0. Read the project

- Read `design-system-prototypes/README.md` and `REDESIGN-STATE.md` if they exist, and use the chosen design system: palette, fonts, tokens, motion guide and mascot files. If they do not exist, use the repo's tokens, theme and logo files (principle 5).
- Read `CLAUDE.md`, `README`, `docs/` and the landing copy. Find the product name, the tagline, the main user action, the AI features, the incumbents or old standards this product replaces, and the copy and vocabulary rules.
- Collect every number from the code: block types, question types, locales, integrations, anything countable. Count real files or enum members, and keep the source of each number for the reply.

Done when you have the brand inputs, the positioning facts and every number with its source.

## Step 1. Storyboard

Write it before any code: a list of scenes with start and end times. Then remove every scene that fails principle 1 or 2. The default arc for a 30-second product reel follows; adapt it to the ask.

1. **Open**, 0 to 2 s: the logo mark draws itself with a soft entrance.
2. **Name**, 2 to 5 s: the product name rises from a mask; the tagline follows.
3. **Positioning**, 5 to 10 s: a timeline with years shows the old standards or incumbents, and the product arrives last. Facts only: years, formats, how the work flows.
4. **Old way and new way**, 10 to 14 s: two panels. The old one shows its real flow (for example export, upload, replace). The new one shows a live edit and a publish. A neutral title such as "Same goal, another way."
5. **The AI agent or mascot**, 14 to 17 s: the last object of scene 4 becomes the agent (principle 9). One line says what the agent does.
6. **Demo, one prompt**, 17 to 21 s: a prompt types into a composer, the send button presses, and the result lands in a card.
7. **Demo, one edit**, 21 to 25 s: a second prompt asks for a change. Only the changed part moves.
8. **Features**, 25 to 27.5 s: one fact at a time, each with its real number. The fact before dims when the next one enters.
9. **Lockup**, 27.5 to 30 s: the mark returns next to the wordmark, with the tagline and a credit line. Everything fades to the ground for a clean loop.

The comparison in scenes 3 and 4 is respectful: it shows facts the user can check, and lets the viewer draw the conclusion.

## Step 2. Reading time (hard rule)

- Every text stays **fully visible** for at least max(1.6 s, 0.3 s per word + 0.6 s), counted after its entrance ends and before its exit starts.
- A headline fits on one line at 1600 px. Shorten it or reduce the size until it does.
- One text idea on screen at a time. The text of a scene is gone before the next text enters.

## Step 3. Build

- A 1600x900 stage, scaled with a CSS transform to fit a 16:9 frame at any width.
- `render(t)` is a pure function of time: every property of every element is computed from `t`. Motion comes only from `render(t)`, so scrubbing is exact.
- Controls: Play/Pause, Sound, Restart, a scrubber with chapter buttons, and a timecode in seconds and frames at 60 fps.
- Default curves: outCubic and ioCubic, short travel, staggers of about 40 ms. Use outBack, springs, squash and stretch, particles or blur only when the tone asks for energy (principle 8).
- Speed (principle 15): animate only `transform` and `opacity`. Write a style only when its value changes. Give a scene that is not on screen `display: none`. Give every function a unique name: a sound function and a loop function with the same name make the reel slow down and the music stop.
- Use the design system: its Google Fonts, its color tokens, and light and dark themes with the same `:root` pattern as its pages.
- Under `prefers-reduced-motion`, show the lockup frame and play only when the viewer presses Play.
- Page format: a `<title>` and `<style>` at the top, no `<html>`, `<head>` or `<body>` tags. Scripts only from cdnjs, jsdelivr or unpkg; stylesheets only from Google Fonts.

## Step 4. Sound

Web Audio synthesis only; the page carries no audio files.

- Browsers start audio only after a click, so a **Sound** button starts it.
- Music (principle 11): a synthesized piano with a soft pad, at about 80 bpm, with its own chord progression per section and a final chord on the lockup. Drums only when the person asks for them.
- Action sounds (principles 12 and 13): no pitch, short and quieter than the music: a key click for typing, a dry tick for an arrival, a short low tock for a confirmation. One sound per visible cause; a minor act gets no sound.
- The score: one sorted array of plain data events, `{ t, kind, ... }`.
- Render every voice once at page load with an `OfflineAudioContext`: each piano note, each pad chord and each action sound. During play, each voice is one `AudioBufferSourceNode` and one gain. A live compressor and a convolver reverb of about 2 s go on the master.
- Clock: the picture reads only `performance.now()`, never `audioContext.currentTime`. The audio follows the picture: map picture time to audio time with `getOutputTimestamp()`, smooth that offset, and schedule ahead by the output latency so a Bluetooth output stays in sync. Run the scheduler from the frame loop and from a 40 ms interval, with about 0.4 s of lookahead.
- On start, pause, seek or restart (principle 14), fade the old bus out, schedule again from the new `t`, and play the chord of the current bar at once. On `onstatechange` to `suspended` or `interrupted`, call `resume()` and schedule again when it runs. On a loop, continue with the next pass of the score.
- A diagnostic panel opens with `#debug` at the end of the link (an Artifact page never gets the query string). It shows the frames per second, the distinct `t` values per second, the audio context state and latencies, the clock source, the voices per second, the live voices and the late events dropped.

## Step 5. Copy

- The product's main locale.
- Objective language ("show, don't tell"): each line says what the product does or what the person does.
- A comparison uses only facts you can point to in the repo docs.
- The repo's vocabulary rules still bind. If the user asked for a word those rules forbid, use it and name the conflict in the reply.

## Step 6. Check and publish

- If `agent-browser` exists: one contact sheet of about 12 key frames. Drive the scrubber with `eval`, save each screenshot to an absolute path, and join them with ImageMagick (`magick a.png b.png +append row.png`, then `-append`).
- Review the sheet as a viewer (principle 17): two focuses at the same time, a headline on two lines, cut or overlapping text, remains of the scene before, elements out of place. One pass of fixes; take one more screenshot only to confirm a geometric fix.
- Test with sound at real speed (principle 16): headless Chrome runs a real `AudioContext`. Press Sound, let the reel play, and read the `#debug` numbers: 60 frames per second, no late events dropped. The agent cannot hear the mix, so the reply asks the person to listen in their own browser.
- Close the browser and delete the screenshots.
- Publish the page as an Artifact if the tool exists; otherwise give the local path.

## Step 7. Reply, in two sections

1. **Product**: the scenes in order, what each one shows, how the sound follows the picture, and the principles that changed a decision.
2. **Technical**: the files the reel reads, the source of each number, how the clock and the scheduler work, the `#debug` numbers you measured, and what you could not verify (for example the mix levels, because the agent has no ears).
