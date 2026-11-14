---
name: design-polished-websites
description: Use when Andrew requests a website, landing page, dashboard, frontend UI, visual redesign, or help making an AI-generated page look less basic, especially when he provides an idea and wants the AI to choose the design.
---

# Design Polished Websites

Take responsibility for art direction. Andrew supplies the idea; choose the most suitable visual approach and resources automatically. He does not need to know design terminology. Existing branding and explicit project instructions take precedence. This skill guides design; use the environment's available implementation tools to build the result.

## 1. Establish purpose without an interview

Read the brief, existing UI, project instructions, stack and supplied references. Identify audience, page purpose, primary action and real available content. Infer ordinary reversible design choices and state the chosen direction briefly. Ask only when missing information materially changes the product. Do not require a style questionnaire or option approval by default. If visual alternatives are requested, present them.

## 2. Choose references and direction

Read [resources.md](references/resources.md) for the curated resource inventory and selection rules. Choose only resources that serve this project. Use available browsing to inspect a small number of relevant examples, ideally two or three. Record what was actually observed: hierarchy, composition, type, imagery, interaction or spacing. Links alone are not evidence that a design was inspected. If browsing is unavailable, proceed with an explicitly self-authored direction and disclose the reference limitation briefly.

Select a coherent direction appropriate to the audience. Examples: editorial/product photography for a café or physical product; quiet dense clarity for a working dashboard; expressive typography for a creative portfolio; restrained credibility for enterprise services. These are starting points, not fixed themes. Adapt principles rather than copying branding, protected artwork or a complete competitor page.

## 3. Produce a concrete design contract

Before implementation, capture these fields in a concise project note or working response, then proceed without a separate approval gate unless requested:

- Audience, purpose and primary action.
- Chosen visual direction and one sentence explaining fit.
- Source observations, with URLs and access limitations.
- Palette: actual values for background, surfaces, text, muted text, accent and states.
- Typography: available font families, weights, responsive heading/body sizes, line heights and reading width.
- Layout: content width, grid, spacing scale, section sequence, image placement and mobile stacking.
- Component treatment: buttons, inputs, borders, radii, shadows and focus states.
- One distinctive visual element tied to the product, such as an NFC tag-to-phone demonstration or a meaningful dashboard visualization.
- Motion: purpose, trigger, duration/physics and reduced-motion alternative.

Choose concrete values, not only adjectives such as modern, premium or beautiful. Check contrast for the chosen text/background pairs. Preserve established tokens when improving an existing product.

## 4. Build the visual hierarchy

Start with accurate content and the most important viewport. Make the primary action obvious. Use purposeful images, product previews or diagrams appropriate to the content. Give sections varied composition when their jobs differ; use repetition for comparable items. Apply consistent tokens throughout. A page should still communicate clearly without decorative animation.

Use real supplied assets or properly licensed/generated assets. Label demo data. Never fabricate testimonials, client logos, awards, prices or business metrics. Inspect imagery crops and text wrapping. Keep icon style consistent. Use semantic controls, accessible labels, visible keyboard focus and readable contrast.

Match the existing stack. Prefer CSS for simple transitions; use a motion library when its capabilities justify the dependency. Avoid adding React to a plain HTML project just to use React Spring. Keep third-party platforms optional. Do not upload project data or purchase a service merely because it appears in the resource list.

## 5. Render, critique, improve

When a runnable project and browser are available, inspect the actual rendered page at representative narrow mobile and desktop widths (for example 390 and 1440 CSS pixels). For a redesign, compare against the original when available. Check:

- Hierarchy and product-specific character; replace generic placeholder sections.
- Type scale, line breaks, spacing rhythm, alignment and image crops.
- Overflow, clipping, horizontal scroll and mobile reading order.
- Keyboard navigation, focus visibility, labels, text contrast and reduced motion.
- Navigation, primary CTA, forms and important loading/empty/error states.
- Asset loading, layout shifts and excessive animation/dependencies.

Correct observed problems and recheck affected views. Run relevant existing build/lint checks. A successful build is not visual verification. If execution or visual inspection is unavailable, identify exactly which checks remain unverified; never report assumed checks as passed.

## 6. Deliver

Briefly report the chosen direction, implemented result, verified checks and unresolved limitations. Provide the project's normal preview or artifact. Keep technical detail proportional to Andrew's request.

## Common mistakes

- Using every resource regardless of fit: choose tools per need.
- Giving only inspiration links: translate observations into concrete tokens and composition.
- Treating polish as more gradients, cards or animation: first fix hierarchy, content, type and spacing.
- Claiming all reel tools are captured: consult the explicit verification status in resources.md.
- Claiming a saved skill is available in another agent or GitHub repo: verify each installation or destination separately.
