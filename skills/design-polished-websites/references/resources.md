# Website design resources — all five from the reel

Reviewed: 2026-11-14. All five names were visually confirmed in the original reel.
[Original video and verification notes](source-instagram-reel.md).

These are five resources used by ONE design skill, not five installed integrations.
Choose by project need; do not force all five into every build.

| ID | Website | Category | Skill capability | When to choose it |
| --- | --- | --- | --- | --- |
| 01 | [Watermelon UI](https://ui.watermelon.sh/) | Components and sections | Component selection and adaptation | A compatible React project needs a strong component starting point |
| 02 | [Manus](https://manus.im/) | AI website/platform tool | Structured brief and prototype review | The user wants a Manus workflow or already has a Manus prototype |
| 03 | [Realtime Colors](https://www.realtimecolors.com/) | Colours and typography | Palette and font selection | Choosing or refining a visual identity |
| 04 | [React Spring](https://www.react-spring.dev/) | React animation library | Purposeful motion | React interactions need spring-based animation |
| 05 | [Godly / Recent](https://recent.design/) | Design inspiration | Art direction and layout analysis | The idea needs a distinctive visual direction |

## 01 — Watermelon UI: components and sections

**Official reference:** https://ui.watermelon.sh/

Provides React components, blocks and templates. Use it as a starting point for suitable UI sections.

**AI instructions:** Inspect the chosen component and its source before use. Check its licence, dependencies and stack compatibility. Adapt colours, typography, spacing, content and states to the project's design contract. Preserve accessible semantics, keyboard focus and responsive behaviour. Test the resulting component in the actual page.

**Expected output:** A project-specific component with consistent tokens and working states.
**Skip when:** The existing design system already solves the need, or adopting it would introduce an unsuitable framework.

## 02 — Manus: structured brief and prototype review

**Official reference:** https://manus.im/

An AI platform with website-building capabilities. Its presence in the reel is not a requirement to use a third-party builder.

**AI instructions:** When Manus is relevant, prepare a brief covering audience, primary action, content, page structure, palette, typography, assets, interactions and acceptance checks. Review any generated prototype against that brief and the main skill's quality checklist. Treat the result as something to inspect and refine.

**Expected output:** A concrete build brief or reviewed prototype.
**Skip when:** Building directly in the current repository already meets the goal. Do not claim a Manus integration exists, upload private project data, subscribe or deploy merely because this reference is listed.

## 03 — Realtime Colors: palette and typography

**Official reference:** https://www.realtimecolors.com/
**Font guide:** https://www.realtimecolors.com/docs/font-setup

Previews colour and font choices on a sample website and supports exporting a palette.

**AI instructions:** Start from existing brand requirements where available. Define actual values for text, background, primary, secondary and accent colours. Preview their proportions across a realistic layout. Choose heading and body fonts that fit the audience and are available for the project. Translate decisions into named project tokens, then verify contrast and readability in the actual design.

**Expected output:** Concrete colour values, font choices and consistent reusable tokens.
**Skip when:** The established brand already specifies these choices. A preview is not proof of accessibility.

## 04 — React Spring: purposeful motion

**Official reference:** https://www.react-spring.dev/
**Getting started:** https://www.react-spring.dev/docs/getting-started

A spring-based React animation library.

**AI instructions:** Use it when motion communicates state or supports a meaningful interaction and the project uses React. Check current documentation and compatibility before installing. Define the trigger, animated properties and spring behaviour. Provide a reduced-motion alternative and ensure content remains usable without animation. Prefer simple CSS transitions when sufficient.

**Expected output:** A justified interaction with responsive behaviour and reduced-motion support.
**Skip when:** The project is not React, or a new dependency adds no practical value.

## 05 — Godly / Recent: art direction and layout

**Official reference:** https://recent.design/
**Name history:** https://recent.design/info

The reel labels it “Godly” while showing recent.design. Recent's information page explains the transition from Godly.

**AI instructions:** Inspect two or three relevant examples. Record useful observations about hierarchy, composition, typography, whitespace, imagery and interaction. Translate these into an original design contract for this product. Preserve the project's identity rather than reproducing another site's branding or artwork.

**Expected output:** A clear visual direction and concrete layout decisions.
**Skip when:** Existing references and branding already provide sufficient direction.

## Automatic selection workflow

1. Read the brief and existing project first.
2. Use Recent when direction is unclear; derive principles from observed examples.
3. Use Realtime Colors when palette or typography needs decisions.
4. Use Watermelon UI when compatible components would improve implementation.
5. Use React Spring only when justified motion benefits a React project.
6. Use Manus only when the requested workflow benefits from that platform.
7. Render the actual result, inspect mobile and desktop, and fix observed issues.

These selection rules are our authored guidance, not a transcript or endorsement from the creator. Browse current documentation when relying on changing capabilities. If a resource cannot be accessed, disclose that limitation and continue with a self-authored design where possible.
