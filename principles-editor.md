# Editor and workspace principles

Extends [principles.md](principles.md). Read that first; everything in it still applies. This file covers tools people work in for hours: editors, design tools, IDEs, dashboards and admin consoles. It only adds rules or makes core rules stricter. It never relaxes them.

## Layout and spacing

- **A calm, dense tool.** A tool people work in for hours fits a lot on screen and stays steady: little layout variety, panels that keep their place and shape. The variety goes into the content.
- **Open beside, not instead.** Settings, menus and side panels open as trays next to what you clicked, so you never lose your place. Full screen swaps are for leaving the current task.
- **Group by what it changes.** Controls that change the same thing sit together in one section, not spread across cards.
- **Panels never scroll sideways.** Core allows wide content like a table. A panel has no such exception: if something doesn't fit, it wraps. Vertical scroll is fine.

## Colour and surfaces

- **Panels stay quiet.** Panels use neutral surfaces with one accent. If a panel draws the eye away from the main content, it is too loud.
- **Corners follow the role.** One radius for floating panels, a smaller one for cards inside them, pills for controls. The card's radius is the panel's radius minus the padding between them, so the corners stay concentric. No card inside a card.

## Type and words

- **Live values are mono and tabular.** Counts and values you compare use the mono typeface. Numbers that change while you watch use tabular figures, in one format across a panel, so they don't jiggle.
- **Readouts earn their place.** A value shown in a panel is one someone acts on. "Opacity" next to a slider is enough; "Current opacity value: 80%" and "Drag to change" are not.
- **Panel words are short.** Labels name things ("Colours", "Layers"), buttons are verb plus object ("Add layer", "Export PNG"), and placeholders are a word or two ("Search layers").

## Motion

- **Constant actions don't move.** Dragging a slider, scrubbing a value, undo and redo, picking a layer, and nudging with the arrow keys get no motion, or a colour change only. A selected item is a surface step, not an animation.
- **A tray can be grabbed mid-motion.** If someone catches the tray while it opens or closes, it follows the pointer from where it is, and the release keeps its speed. The edge of the tray is a handle even when it has no visible grip.
- **Panels open as trays.** A tray slides out from the edge it's attached to on the drawer curve, 250ms in and 150ms out. Whatever sits beside it steps aside with the same timing and direction.

## Before shipping an editor change

Run the core checklist, then check these too.

- [ ] Nothing in a panel scrolls sideways
- [ ] Settings and menus open beside, not instead
- [ ] Controls that change the same thing sit in one section
- [ ] Panels are neutral with one accent
- [ ] No card inside a card
- [ ] Live numbers are mono, tabular and in one format
- [ ] Dragging, scrubbing, undo and redo have no motion
- [ ] A tray can be grabbed mid-motion and keeps its speed

## Sources

Most of these rules come from the sources listed in [principles.md](principles.md), mainly Pond (trays and panels), Apple's fluid interfaces (a tray caught mid-motion) and antiwebslop (the calm, dense "operate" surface).
