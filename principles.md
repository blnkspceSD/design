# Design and motion principles

Rules for how an interface looks, reads, behaves and moves: layout and spacing, colour and surfaces, type and words, interaction and states, and motion. When a UI change and a principle disagree, change one of them on purpose and write down why.

## Interface design principles

### Layout and spacing

- **A calm, dense tool.** A tool people work in for hours fits a lot on screen and stays steady: little layout variety, panels that keep their place and shape. The variety goes into the content.
- **Open beside, not instead.** Settings, menus and side panels open as trays next to what you clicked, so you never lose your place. Full screen swaps are for leaving the current task.
- **Space shows what belongs together.** The gap between groups is bigger than the gap inside one. Gaps and padding come from a small spacing scale, never a number typed into one component.
- **Same thing, same size, same line.** Rows in one list share one height and one gap; sibling cards share one padding. Icons sit in one column, labels start on one line, numbers align right. Nothing is nudged off the line with a stray margin or translate.
- **Group by what it changes.** Controls that change the same thing sit together in one section, not spread across cards.
- **Panels never scroll sideways.** If something doesn't fit, it wraps. Vertical scroll is fine.

### Colour and surfaces

- **Panels stay quiet.** Panels use neutral surfaces with one accent. If a panel draws the eye away from the main content, it is too loud.
- **One accent, one job.** The accent marks what's selected, switched on, or the main action. Success, warning and danger colours appear only for those states. One primary button per view. Text on the accent uses its own ink colour, never grey.
- **Three text roles.** One colour for what you read, a muted one for secondary text and icons, a faint one only for meta like counts. No in-between greys.
- **A shadow means it floats.** Only things that sit above the page, like panels, menus and popovers, get a shadow. Inside a panel, depth comes from a surface one step lighter, never an outline or a divider line; a selected row is a surface step, not a glow. Corners follow the role: one radius for floating panels, a smaller one for cards inside them, pills for controls. No card inside a card.
- **Decoration has to do a job.** No glows, glass, blurred blobs, gradient text, decorative grids or emoji in the interface. A gradient is allowed only as a small tone shift inside one colour, like a sheen on a button, never from one hue to another. A grid stays only when it helps, like the dots on an XY pad that help you place the point.
- **Values come from tokens.** Colours, radii, spacing, durations and easings come from one set of tokens. No one-off numbers in a component. If a token is wrong, change the token.

### Type, words and icons

- **Two typefaces, each with a job.** A sans for everything you read. A mono only for counts, codes and values you compare. Numbers that change while you watch use tabular figures, in one format across a panel, so they don't jiggle.
- **Hierarchy from size and colour, not weight.** Reach for a bigger size or a stronger text role before a heavier weight. Keep to a few set weights, no italic for emphasis, and no negative letter spacing on small text. Everything is sentence case, headings included: no capitals with wide tracking.
- **Labels name things; they don't give instructions.** "Colours" is enough. Drop helper lines like "Pick a colour" and readouts nobody acts on. Keep a line of text only when the control can't explain itself. Labels, buttons and captions have no trailing period and no exclamation marks; placeholders are short, like "Search layers".
- **Buttons say what happens.** Verb plus object: "Add layer", "Export PNG", "Save file". No "Get started" or "Learn more", no marketing words like seamless, supercharge, elevate or unlock, and no made-up numbers. A changelog entry says what changed and where to find it.
- **One icon set, used where it helps.** Every icon comes from one set, at one size scale. No hand-drawn one-offs. An icon takes the colour of the text beside it and sits in a fixed-width box so labels line up. It earns its place by making something faster to find; an icon-only button always has a tooltip and an accessible name.

### Interaction and states

- **Every control shows its state.** Resting, hover, pressed, selected, on and disabled each look different. Hover is a colour or surface change; cards and buttons never grow on hover. Press shrinks slightly; selected and on use the accent.
- **Say why something is off.** A disabled control gets a short tooltip with the reason and the way out.
- **Focus is always visible.** Keyboard focus shows a ring. Never remove an outline without putting something as clear in its place. Text keeps at least 4.5:1 contrast, controls and large text at least 3:1.
- **Hover only where there's a mouse.** Hover styles sit behind `@media (hover: hover)` so a tap on a phone doesn't leave them stuck.

### Slop to avoid

Things that make an interface look generated. Leave them out, and do the plain thing instead.

- **Tags and badges.** No "New" or "Beta" pills on things. Say it in words where it matters, or not at all.
- **Italic words.** No italics for emphasis or flavour. A logo can be the exception.
- **Editorial serifs and negative kerning.** No serif display type like Instrument Serif, and no tightened letter spacing to make headings look designed.
- **Over-detailed UI.** Every extra line, tick, label and tiny icon has to earn its place. When in doubt, take it out.
- **Dividers.** Separate groups with space, not lines.
- **Many shades and opacities.** Use the ramp steps and the three text roles. No new 40% or 60% tints of a colour.
- **Containers with borders.** Don't wrap groups in outlined boxes. Space and a surface step do the grouping. The outer edge of a floating panel can be the exception, when it has to stay readable over busy content.
- **Diagrams.** Only when one is really needed, and as simple as it can be. The more detailed, the worse.
- **Code breadcrumbs.** No file paths, token names or `a / b / c` trails in the interface. Say it in words.
- **Section numbering.** No "01" or "1." in front of section titles.

## Motion principles

Content is allowed to move as much as it likes. The interface around it moves only to explain a change.

- **Animate by how often it happens.** The more often someone does a thing, the less it should move.

   | How often | Examples | Motion |
   | --- | --- | --- |
   | All the time | Dragging a slider, undo and redo, picking an item in a list, keyboard shortcuts | None, or a colour change only |
   | Often | Hover, press, toggles, switching tabs | Colour plus a 0.97 press, 150ms |
   | Sometimes | Drawers, menus, popovers, dialogs | Standard enter and exit |
   | Rarely | Loading screen, first launch, empty states, a finished export | Room for something with character |

- **Nothing appears out of nowhere.** New UI comes from the thing that opened it. A drawer slides out from the edge it's attached to. A menu grows from its button (`transform-origin` at the trigger). A dialog with no trigger scales from its centre.
- **Motion never blocks input.** You can click, type or drag the moment something starts opening. Use CSS transitions for anything that opens and closes, because a transition can reverse halfway and a keyframe restarts from zero.
- **Leave faster than you arrive.** Exits are about half the enter time. A drawer that opens in 250ms closes in 150ms.
- **Ease out, never in.** Enter and exit use the ease-out curve. Something moving from one place to another on screen uses ease-in-out. Drawers and panels that slide out use the drawer curve. Hover and colour use the same short ease-out. Never an ease-in curve on UI: it holds back right when the person is waiting.
- **Start close to the end.** Enter from `scale(0.95)` to `scale(0.98)` with opacity 0, or a 4px to 8px nudge. Never from `scale(0)`.
- **One change, one movement.** When one thing opens and another steps aside, they share timing and direction so it reads as one event.
- **Only move what's cheap.** Animate `transform`, `opacity` and colours. List the properties; never `transition: all`. Height animations stay short because they cost layout on every frame.
- **Bounce is for rare moments, and nothing loops for attention.** A loader can overshoot. Everyday controls don't. A loader is the only thing that loops, and only while you're waiting. No pulsing dots, shimmer, breathing glows, marquees, tickers or parallax.
- **Reduced motion gets the same end state.** With reduced motion on, things fade instead of move, and nothing depends on seeing the animation to make sense.
- **Watch it before you ship it.** Play it at normal speed, then slowed down 5x in DevTools, and look at the frames in between. Look again the next day.

## Motion values

The values follow Emil Kowalski's. Keep them as tokens and use the token name in code, not the number.

| Name | Value | Use it for |
| --- | --- | --- |
| Duration fast | 150ms | Hover, press, colour changes, exits, small menus |
| Duration normal | 250ms | Drawers, menus, panels, dialogs entering |
| Duration slow | 500ms | Rare moments only, like a loader |
| Stagger | 50ms | Gap between items entering in sequence |
| Ease out | cubic-bezier(0.23, 1, 0.32, 1) | Anything entering or leaving, hover, colour |
| Ease in-out | cubic-bezier(0.77, 0, 0.175, 1) | Something travelling across the screen |
| Ease drawer | cubic-bezier(0.32, 0.72, 0, 1) | Drawers and panels sliding out |
| Press scale | 0.97 | Every pressable button |

## Before shipping a UI change

- [ ] Every value comes from a token
- [ ] Nothing in a panel scrolls sideways
- [ ] No label is an instruction the control already makes obvious
- [ ] Anything new that appears comes from where it was opened
- [ ] You can click or type while it animates
- [ ] Exit is faster than enter
- [ ] Only transform, opacity and colours animate
- [ ] Reduced motion reaches the same end state
- [ ] Hover is behind `(hover: hover)`
- [ ] Nothing from the slop list
- [ ] Only floating things have a shadow
- [ ] Equal things share one size and line up
- [ ] Buttons read as verb plus object, with no marketing words or emoji
- [ ] Keyboard focus is visible everywhere it can land
- [ ] Watched at normal speed and slowed down

## Sources

- [Pond design principles](https://github.com/raphaelsalaja/pond/blob/main/apps/desktop/src/renderer/src/PRINCIPLES.md) by Raphael Salaja: trays, "fly instead of teleport", motion never gates input, reduced motion reaches the same state, the delight-impact curve. Pond takes these from Benji Taylor's [Family Values](https://benji.org/family-values).
- [emilkowalski/skills](https://github.com/emilkowalski/skills) by Emil Kowalski, mainly [emil-design-eng](https://github.com/emilkowalski/skills/blob/main/skills/emil-design-eng/SKILL.md), [animate recipes](https://github.com/emilkowalski/skills/blob/main/skills/animate/RECIPES.md) and [review standards](https://github.com/emilkowalski/skills/blob/main/skills/review-animations/STANDARDS.md): the frequency table, easing choices, press scale, origin, transitions over keyframes, stagger, performance.
- Emil Kowalski, [Great animations](https://emilkowal.ski/ui/great-animations): keep UI motion under 300ms, never animate keyboard actions.
- [antiwebslop](https://github.com/cesaroeduardo/antiwebslop) by Eduardo de Cesaro: the tool as a calm, dense "operate" surface, shadows only for floating things, radius by role, one accent with one job, decoration that does a job, two typefaces, verb-plus-object buttons, banned marketing copy, visible focus and contrast, no attention loops. Its advice to ease in on exits was left out in favour of Emil Kowalski's ease-out.
- [unslop](https://github.com/heydamir/unslop) by Damir Sokolovsky ([@heydamir](https://x.com/heydamir)), CC BY 4.0: same thing same size, things line up, three text roles, depth from surface steps, tone-shift-only gradients, hierarchy from size and colour, sentence case headings, no trailing periods or exclamation marks, icons in their text colour and a fixed box, no hover growth, no shimmer or parallax.
