# Design and motion principles

Rules for how an interface looks, reads, behaves and moves: layout and spacing, colour and surfaces, type and words, interaction and states, and motion. They apply to any product, on any screen. When a UI change and a principle disagree, change one of them on purpose and write down why.

Some kinds of product need more than this. Those rules live in an extension that builds on this file and never contradicts it:

- [principles-editor.md](principles-editor.md): editors and workspaces, the tools people work in for hours.

## How to decide

When two rules pull against each other, these eight break the tie. They decide what to build as much as how it looks.

- **Purpose.** Every feature asks for people's time, attention and trust. Spend that budget only where it pays, and decide what not to build.
- **Agency.** Offer choices, keep a way back, and make undo the safety net. A confirmation dialog is for a costly action that can't be undone; using it more often trains people to click through it.
- **Responsibility.** Act in the interest of the people using it. Ask for private data only when it's needed, only for what's needed, and say what happens to it. Anticipate how the product could mislead or harm, especially when it gives advice.
- **Familiarity.** Build on what people know, and keep the same-looking thing in the same place behaving the same way. Break a familiar pattern only when you can show the new one is better.
- **Flexibility.** One layout rarely fits every device, language and pair of eyes. Adapt to the platform, design for the full range of abilities, and let people adjust what they see.
- **Simplicity, not minimalism.** Cut what doesn't serve the purpose; hiding everything to look clean is not simple. The common path comes first, rare options one step deeper.
- **Craft.** Every spacing, timing and alignment value is a deliberate choice you can defend. Jitter, misalignment and a layout that breaks on rotation read as carelessness.
- **Delight.** The result of getting the other seven right, not confetti on top. Decide the feeling you want, then reinforce it everywhere.

## Interface design principles

### Layout and spacing

- **Space shows what belongs together.** The gap between groups is at least twice the gap inside one, like 8px inside and 16px between. Gaps and padding come from a small spacing scale, never a number typed into one component.
- **A control sits with what it changes.** Place it next to the thing it affects and arrange controls to mirror what they change. If a label has to explain the mapping, move the control.
- **Same thing, same size, same line.** Rows in one list share one height and one gap; sibling cards share one padding. Icons sit in one column, labels start on one line, numbers align right. Line things up by eye, not by the numbers: a triangle or a round shape often needs a small optical nudge to look centred, and a button with an icon gets slightly less padding on the icon side. Any other stray margin or translate is a bug.
- **Nothing scrolls sideways.** If something doesn't fit, it wraps. Vertical scroll is fine. The exception is content that is wide by nature, like a data table or a map.

### Colour and surfaces

- **Surfaces stay quiet.** Use neutral surfaces with one accent. If the chrome draws the eye away from the main content, it is too loud.
- **One accent, one job.** The accent is the brand colour. It marks what's selected, switched on, or the main action. Success, warning and danger colours appear only for those states. One primary button per view. Text on the accent uses its own ink colour, never grey. Call it accent, never primary, so primary never means both the brand and the body text.
- **Three text roles.** One colour for what you read, a muted one for secondary text and icons, a faint one only for meta like counts. No in-between greys.
- **A shadow means it floats.** Only things that sit above the page, like menus, popovers and dialogs, get a shadow. Inside a surface, depth comes from a surface one step lighter, never an outline or a divider line; a selected row is a surface step, not a glow. Corners follow the role, and each role has one radius. Nested corners are concentric: the inner radius is the outer radius minus the padding between them.
- **Decoration has to do a job.** No glows, glass, blurred blobs, gradient text, decorative grids or emoji in the interface. A gradient is allowed only as a small tone shift inside one colour, like a sheen on a button, never from one hue to another. A grid stays only when it helps, like the gridlines on a chart that help you read a value.
- **Images get a hairline edge.** A 1px outline set 1px inside the image: black at 8% in light mode, white at 8% in dark. It keeps an image's edge from bleeding into the surface, and it's the one border and the one tint allowed outside the ramp.
- **Values come from tokens.** Colours, radii, spacing, durations and easings come from one set of tokens. No one-off numbers in a component. If a token is wrong, change the token. Components use tokens named for their job, like `--color-text-muted` or `--color-accent-solid`, never raw values like `--blue-500`. Every step in a scale has a use; drop the steps nothing uses.
- **Dark mode is its own palette.** Build it on purpose instead of inverting light mode. Check contrast against the surface directly behind each element, not the page.

### Type, words and icons

- **Two typefaces, each with a job.** A sans for everything you read. A mono only for codes and values you compare. Numbers that change or sit in columns, like timers, prices and tables, use tabular figures so they don't shift; the mono already has them.
- **Hierarchy from size and colour, not weight.** Reach for a bigger size or a stronger text role before a heavier weight. Keep to a few set weights, no italic for emphasis, and no negative letter spacing on small text. Everything is sentence case, headings included: no capitals with wide tracking.
- **Type is tuned per size.** Leading tightens as text grows and loosens for body copy; large text takes slight negative tracking, small text a little positive. Choose weight, size and leading together. Set spacing in `rem` so the layout grows with the reader's text size, and start from the system font. Body text runs 60–75 characters per line. Headings balance their line breaks, and descriptions avoid a single orphaned word.
- **Labels name things; they don't give instructions.** "Colours" is enough. Drop helper lines like "Pick a colour" and readouts nobody acts on. Keep a line of text only when the control can't explain itself. Labels, buttons and captions have no trailing period and no exclamation marks; placeholders are short, like "Search". A toggle says what happens when it's on: "Send read receipts", not "Disable read receipts". A link says where it goes.
- **Buttons say what happens.** Verb plus object: "Save draft", "Send invite", "Download report". No "Get started" or "Learn more", no marketing words like seamless, supercharge, elevate or unlock, and no made-up numbers. A confirmation button repeats the action: "Delete project" beside "Cancel". A flow uses one label, like "Continue", for every next step. A changelog entry says what changed and where to find it.
- **Talk to the reader.** Address people as "you", never "the user".
- **Punctuation is typographic.** Curly quotes, an en dash for ranges (2–4), an em dash for asides, and the … character instead of three dots. Write words in normal case and let styling change the case.
- **Cut text stays reachable.** When text is cut with an ellipsis, the full text is in a tooltip or an expanded view. Long words, links and IDs wrap inside their container; short labels don't wrap.
- **One icon set, used where it helps.** Every icon comes from one set, at one size scale. No hand-drawn one-offs. An icon takes the colour and stroke weight of the text beside it and sits in a fixed-width box so labels line up. It earns its place by making something faster to find; an icon-only button always has a tooltip and an accessible name.

### Interaction and states

- **Every control shows its state.** Resting, hover, pressed, selected, on and disabled each look different. Hover is a colour or surface change; cards and buttons never grow on hover. Press shrinks slightly; selected and on use the accent.
- **Answer on press.** Press shows on pointer-down and commits on release; sliding away cancels. Feedback continues for as long as the gesture lasts, not only at the end.
- **The thing follows the finger.** A drag tracks 1:1 from where it was grabbed, not from its centre. A short threshold decides the direction, then it commits.
- **Say why something is off.** A disabled control gets a short tooltip with the reason and the way out. A form's submit button is the exception: it stays enabled until the request starts, and the form is checked when it's sent.
- **Hover only where there's a mouse.** Hover styles sit behind `@media (hover: hover)` so a tap on a phone doesn't leave them stuck.
- **Undo beats a confirmation.** Give people a way back from a mistake. Confirm only what is destructive and can't be undone.
- **Say what happened.** Status, success, warning and error each have a place. Put an error where the problem is, not only in a summary after submit. Colour is never the only signal; pair it with an icon, a word or an underline.
- **Every screen answers where you are.** Where am I, what can I do here, and how do I leave. Never a dead end. An empty view says what belongs there and offers one action to start.

### Accessibility

- **Native elements first.** A button is a button and a link is a link, so keyboard, screen reader and browser behaviour come for free. Tab order follows the page; never a positive tab index.
- **Focus is always visible.** Keyboard focus shows a ring. Never remove an outline without putting something as clear in its place. Text keeps at least 4.5:1 contrast, controls and large text at least 3:1.
- **Hit areas are big enough.** At least 24 by 24px. Aim for 44 by 44px on touch screens and 40 by 40px with a mouse. Hit areas never overlap.
- **Every input has a visible label.** The field type and keyboard match what goes in. Never block paste; people paste passwords and one-time codes.
- **Name what can't be seen.** An icon-only button has an accessible name. Alt text says what an image shows and why it's there; a decorative image has empty alt text. Nothing that can take focus is hidden from screen readers.
- **Errors are found on submit.** Check the form when it's sent, mark each invalid field, tie each error message to its field, and move focus to the first one.
- **Announce at the right volume.** Routine updates are announced politely. Only urgent errors interrupt.

### Slop to avoid

Things that make an interface look generated. Leave them out, and do the plain thing instead.

- **Tags and badges.** No "New" or "Beta" pills on things. Say it in words where it matters, or not at all.
- **Italic words.** No italics for emphasis or flavour. A logo can be the exception.
- **Editorial serifs and negative kerning.** No serif display type like Instrument Serif, and no tightened letter spacing to make headings look designed.
- **Over-detailed UI.** Every extra line, tick, label and tiny icon has to earn its place. When in doubt, take it out.
- **Dividers.** Separate groups with space, not lines.
- **Many shades and opacities.** Use the ramp steps and the three text roles. No new 40% or 60% tints of a colour. An image's hairline edge is the one exception.
- **Containers with borders.** Don't wrap groups in outlined boxes. Space and a surface step do the grouping. The outer edge of a floating layer can be the exception, when it has to stay readable over busy content, and so can an image's hairline edge.
- **Diagrams.** Only when one is really needed, and as simple as it can be. The more detailed, the worse.
- **Code breadcrumbs.** No file paths, token names or `a / b / c` trails in the interface. Say it in words.
- **Section numbering.** No "01" or "1." in front of section titles.

## Motion principles

Content is allowed to move as much as it likes. The interface around it moves only to explain a change.

- **Animate by how often it happens.** The more often someone does a thing, the less it should move.

   | How often | Examples | Motion |
   | --- | --- | --- |
   | All the time | Typing, picking an item in a list, moving with arrow keys, keyboard shortcuts | None, or a colour change only |
   | Often | Hover, press, toggles, switching tabs | Colour plus a 0.97 press, 150ms |
   | Sometimes | Drawers, menus, popovers, dialogs | Standard enter and exit |
   | Rarely | Loading screen, first launch, empty states, a finished upload | Room for something with character |

   A menu people open many times a day opens instantly and only animates its close.

- **Nothing appears out of nowhere.** New UI comes from the thing that opened it. A drawer slides out from the edge it's attached to. A menu grows from its button (`transform-origin` at the trigger). A dialog with no trigger scales from its centre.
- **Motion never blocks input.** You can click, type or drag the moment something starts opening. Use CSS transitions for anything that opens and closes, because a transition can reverse halfway and a keyframe restarts from zero.
- **Start from where it is.** An interrupted animation picks up from its current on-screen value and speed. Restarting from the target, or from zero, is a visible jump.
- **Springs for what you touch, transitions for chrome.** Anything a finger drags or throws uses a spring: it takes a new target and keeps moving. Chrome that opens and closes uses a transition, which can reverse halfway. Neither uses keyframes.
- **Carry the throw.** When a drag ends, hand its speed to the animation and send it where the throw was going, not to the nearest edge from where the finger left. Choose the target from the projected landing point.
- **Edges give.** At a boundary, resist more the further it's pushed, then spring back on release. A hard stop reads as frozen.
- **Leave the way you came.** Exit along the path it entered, with the easing mirrored, so the way out matches the way in.
- **Sound and haptics land on the same frame** as the visual, fire on the cause, and are kept for commit, success and error. Anything more trains people to ignore them.
- **Leave faster than you arrive.** Exits are about half the enter time. A drawer that opens in 250ms closes in 150ms. Exits are smaller too: a shorter move, a fade and a 4px blur.
- **Ease out, never in.** Enter and exit use the ease-out curve. Something moving from one place to another on screen uses ease-in-out. Drawers and sheets that slide out use the drawer curve. Hover and colour use the same short ease-out. Never an ease-in curve on UI: it holds back right when the person is waiting.
- **Start close to the end.** Enter from `scale(0.95)` to `scale(0.98)` with opacity 0, or a 4px to 8px nudge. Never from `scale(0)`.
- **One change, one movement.** When one thing opens and another steps aside, they share timing and direction so it reads as one event.
- **Only move what's cheap.** Animate `transform`, `opacity` and colours, plus a blur of 4px or less on exits and icon swaps. List the properties; never `transition: all`. Height animations stay short because they cost layout on every frame.
- **Icons swap in place.** The old icon fades out as the new one fades in. The new one scales from 0.25 to 1 and goes from a 4px blur to sharp; the old one does the reverse.
- **Enter in small groups.** A list arrives in a few groups with a short stagger between them, not item by item and not as one block.
- **Nothing moves on arrival.** Nothing animates on page load unless that moment was designed. Switching between light and dark mode turns transitions off, so every colour changes in the same frame.
- **Bounce follows momentum, and nothing loops for attention.** A release that carried speed can overshoot. A loader can too. A control that simply appeared doesn't. A loader is the only thing that loops, and only while you're waiting. No pulsing dots, shimmer, breathing glows, marquees, tickers or parallax.
- **Reduced motion gets the same end state.** With reduced motion on, things fade instead of move, and nothing depends on seeing the animation to make sense. Reduced transparency makes floating surfaces solid; more contrast gives edges a defined boundary. Neither loses information.
- **Watch it before you ship it.** Build the interaction before you judge it, because motion and visuals are designed together, not in layers. Play it at normal speed, then slowed down 5x in DevTools, and look at the frames in between. Look again the next day.

## Motion values

The values follow Emil Kowalski's. Keep them as tokens and use the token name in code, not the number.

| Name | Value | Use it for |
| --- | --- | --- |
| Duration fast | 150ms | Hover, press, colour changes, exits, small menus |
| Duration normal | 250ms | Drawers, menus, dialogs entering |
| Duration slow | 500ms | Rare moments only, like a loader |
| Stagger | 50ms | Gap between items entering in sequence |
| Ease out | cubic-bezier(0.23, 1, 0.32, 1) | Anything entering or leaving, hover, colour |
| Ease in-out | cubic-bezier(0.77, 0, 0.175, 1) | Something travelling across the screen |
| Ease drawer | cubic-bezier(0.32, 0.72, 0, 1) | Drawers and sheets sliding out |
| Press scale | 0.97 | Every pressable button |
| Exit blur | 4px | The most blur an exit or icon swap uses |
| Icon swap scale | 0.25 | Where an incoming icon starts |

For anything a finger drives, springs replace durations. Damping is overshoot (`1.0` settles without any) and response is how fast it gets there in seconds, not a duration. These come from Apple's fluid interfaces work.

| Name | Value | Use it for |
| --- | --- | --- |
| Spring default | damping 1.0, response 0.35 | Anything dragged, thrown or opened by a gesture |
| Spring after a flick | damping 0.8, response 0.35 | A release that carried speed. Bounce only here |
| Momentum | deceleration 0.998 | Projecting where a flick lands before choosing the target |

## Before shipping a UI change

- [ ] Every value comes from a token
- [ ] Nothing scrolls sideways
- [ ] A control sits with what it changes
- [ ] Press feedback lands on pointer-down, not on release
- [ ] A drag tracks the pointer 1:1 and can be caught mid-motion
- [ ] A flick lands where its speed was heading
- [ ] An exit leaves by the path it arrived
- [ ] Undo covers a mistake before a dialog does
- [ ] Errors appear next to the field, not only after submit
- [ ] Large text has tighter leading and tracking than body copy
- [ ] No label is an instruction the control already makes obvious
- [ ] Anything new that appears comes from where it was opened
- [ ] You can click or type while it animates
- [ ] Exit is faster than enter
- [ ] Only transform, opacity, colours and a 4px blur animate
- [ ] Nothing animates on page load, and switching theme has no transitions
- [ ] Reduced motion reaches the same end state
- [ ] Reduced transparency and more contrast have an answer
- [ ] Hover is behind `(hover: hover)`
- [ ] Nothing from the slop list
- [ ] Only floating things have a shadow
- [ ] Nested corners are concentric
- [ ] Images have the hairline edge
- [ ] The accent is the brand colour, and tokens are named for their job
- [ ] Hit areas are at least 24px, 44px on touch
- [ ] Every input has a visible label, and paste works
- [ ] Colour is never the only signal
- [ ] Toggles say what happens when they're on
- [ ] Equal things share one size and line up
- [ ] Buttons read as verb plus object, with no marketing words or emoji
- [ ] Keyboard focus is visible everywhere it can land
- [ ] Watched at normal speed and slowed down

## Build notes for the web

How to meet the rules above in HTML and CSS.

- **Type.** Ship `.woff2` font files. Set `-webkit-font-smoothing: antialiased` and `-moz-osx-font-smoothing: grayscale` on the root. Use `font-variant-numeric: tabular-nums` for changing numbers in a sans. Use `text-wrap: balance` on headings and `text-wrap: pretty` on descriptions, neither on long-form text. Use `overflow-wrap: break-word` for long words and links, and `white-space: nowrap` on short labels. Keep underlines off the letter tails with `text-underline-position: from-font` and `text-decoration-skip-ink: auto`. Use `text-transform` for upper or lower case, never type it in capitals.
- **Colour.** Pick one way to switch themes, `prefers-color-scheme` or a `.dark` class, never both. For a tone shift in a gradient, `in oklab` keeps the brightness even.
- **Images.** The hairline edge is `outline: 1px solid rgb(0 0 0 / 0.08); outline-offset: -1px`, with white in dark mode.
- **Motion.** Put animations inside `@media (prefers-reduced-motion: no-preference)`. If something shifts by 1–2px while it animates, add `will-change: transform`; Safari on iOS needs this most. Set `transform-origin` from the trigger's position. Add a class to the root that turns off transitions while the theme switches.
- **Accessibility.** Style `:focus-visible`, not `:focus`. Use only `tabindex="0"` and `tabindex="-1"`. Never put `aria-hidden="true"` on something that can take focus. Set `type` and `inputmode` on inputs. Mark invalid fields with `aria-invalid="true"` and link each error with `aria-describedby`. Use `role="status"` for routine updates and `role="alert"` only for urgent errors. Put `pointer-events: none` on decorative layers so they never swallow a click.
- **Layout.** Give headings `scroll-margin-top` so a link to them doesn't land under a sticky header.

## Sources

- [Pond design principles](https://github.com/raphaelsalaja/pond/blob/main/apps/desktop/src/renderer/src/PRINCIPLES.md) by Raphael Salaja: trays, "fly instead of teleport", motion never gates input, reduced motion reaches the same state, the delight-impact curve. Pond takes these from Benji Taylor's [Family Values](https://benji.org/family-values).
- [emilkowalski/skills](https://github.com/emilkowalski/skills) by Emil Kowalski, mainly [emil-design-eng](https://github.com/emilkowalski/skills/blob/main/skills/emil-design-eng/SKILL.md), [animate recipes](https://github.com/emilkowalski/skills/blob/main/skills/animate/RECIPES.md) and [review standards](https://github.com/emilkowalski/skills/blob/main/skills/review-animations/STANDARDS.md): the frequency table, easing choices, press scale, origin, transitions over keyframes, stagger, performance.
- [apple-design](https://github.com/emilkowalski/skills/blob/main/skills/apple-design/SKILL.md), distilled from Apple's WWDC design talks: the eight principles, feedback on press, 1:1 tracking, springs, velocity handoff, momentum projection, rubber-banding, mirrored exits, type tuned per size, reduced transparency and contrast. Apple's translucent materials were left out because they contradict the no-glass rule in Colour and surfaces.
- Emil Kowalski, [Great animations](https://emilkowal.ski/ui/great-animations): keep UI motion under 300ms, never animate keyboard actions.
- [antiwebslop](https://github.com/cesaroeduardo/antiwebslop) by Eduardo de Cesaro: the tool as a calm, dense "operate" surface, shadows only for floating things, radius by role, one accent with one job, decoration that does a job, two typefaces, verb-plus-object buttons, banned marketing copy, visible focus and contrast, no attention loops. Its advice to ease in on exits was left out in favour of Emil Kowalski's ease-out.
- [Interface cheat sheet](https://interfaces.dev/cheat-sheet), no author listed: concentric corners, optical alignment, image edges, semantic token naming, accent as the brand, dark mode as its own palette, smaller exits with blur, icon swaps, no motion on load or theme switch, typographic punctuation, line length, hit areas, labels and errors, toggle wording, empty states and the web build notes. Its layered shadows for depth were left out because only floating things get a shadow, and its 200ms press in favour of the 150ms token.
- [unslop](https://github.com/heydamir/unslop) by Damir Sokolovsky ([@heydamir](https://x.com/heydamir)), CC BY 4.0: same thing same size, things line up, three text roles, depth from surface steps, tone-shift-only gradients, hierarchy from size and colour, sentence case headings, no trailing periods or exclamation marks, icons in their text colour and a fixed box, no hover growth, no shimmer or parallax.
