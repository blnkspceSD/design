---
name: design-principles
description: Ferg's design and motion principles for building and reviewing interfaces. Use when designing, building, styling, animating or reviewing any UI, writing interface copy, choosing tokens, spacing, colour, type or motion values, or checking a UI change before it ships. Includes extra rules for editors, design tools, IDEs, dashboards and admin consoles.
---

# Design principles

These are the rules for how an interface looks, reads, behaves and moves. Follow them when you build UI, and use them as the standard when you review it.

## Which file to read

Read [references/principles.md](references/principles.md) for any UI work. It holds the general rules: how to decide, layout and spacing, colour and surfaces, type, words and icons, interaction and states, accessibility, the slop list, motion, motion values, the pre-ship checklist and web build notes.

Also read [references/principles-editor.md](references/principles-editor.md) when the product is a tool people work in for hours: an editor, design tool, IDE, dashboard or admin console. It adds rules and makes some general rules stricter. It never relaxes them, so the general file still applies in full.

Read only the sections the task needs. A copy change needs "Type, words and icons" and the slop list. An animation needs the motion sections and the motion values table. A full review needs everything.

## When building

- Take spacing, colour, radius, duration and easing from the project's tokens. If the project has none, set up a small token set first, named for each value's job, like `--color-text-muted`, and use those names.
- Use the exact numbers in the motion values table: 150ms fast, 250ms normal, the ease-out curve `cubic-bezier(0.23, 1, 0.32, 1)`, a 0.97 press scale, and so on. Don't invent new ones.
- Leave out everything on the slop list, even if the request seems to invite it. If someone asks for one of those things by name, do it and mention which rule it breaks.
- Before you call the work done, run the "Before shipping a UI change" checklist, and the editor checklist too when it applies. Say which checks you could not verify, such as how something looks slowed down in DevTools.

## When reviewing

- Name the rule each problem breaks, using its bold title from the principles file, so the person can look it up.
- Give the fix as a concrete change: the value, the token, the new label text. "Tighten the spacing" is not a fix; "change the 12px gap between groups to the 16px token" is.
- Put problems that affect use first (accessibility, state, broken interaction), then visual consistency, then polish.
- Skip rules that don't apply. Don't pad a review with things that are already fine.

## When rules conflict

The "How to decide" section at the top of principles.md breaks ties: purpose, agency, responsibility, familiarity, flexibility, simplicity, craft, delight. If a principle and a UI change genuinely disagree, change one of them on purpose and write down why. Don't quietly ignore a rule.

## Writing interface copy

The words rules apply to anything you write for the interface, and to how you describe your own work:

- Labels name things. Buttons are a verb plus an object, like "Save draft".
- Sentence case everywhere. No trailing periods on labels, no exclamation marks.
- Address people as "you".
- No marketing words like seamless, supercharge, elevate or unlock, and no made-up numbers.
- Write plainly. Avoid stock phrasing such as "It's not X, it's Y."
