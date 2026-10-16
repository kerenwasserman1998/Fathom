# Fathom

Fathom is a design system built across Figma and code, designed to be readable by people and AI models.
Figma is the source of truth for design decisions; code must match it.

## Repo structure

- `figma/`: Figma library exports and documentation
- `tokens/`: design tokens in Design Tokens JSON format, exported from Figma Variables
- `packages/`: code packages, starting with the React component library

## Naming

- Components use PascalCase: `Button`, `TextInput`, `Badge`.
- Component props must match the Figma variant and property names exactly. If Figma says `size: sm | md | lg`, the prop is `size` with values `"sm" | "md" | "lg"`.
- Tokens use slashes in Figma and hyphens in code: `color/text/primary` in Figma becomes `--color-text-primary` in CSS.

## Tokens

Tokens have two layers:

- **Primitives** hold raw values and use a numbered scale: `color/pink/500 = #AB003B`, `space/4 = 16px`.
- **Semantic tokens** describe purpose and point to a primitive: `color/text/primary → color/pink/500`. Semantic names never contain scale numbers.

Rules:

- Components use semantic tokens only. Never use a primitive directly in a component.
- Never hardcode a color, size, or spacing value. If no token fits, stop and ask me rather than inventing one.
- Light and dark modes change which primitive a semantic token points to. The semantic name stays the same.

## Accessibility

Target: WCAG 2.2, level AA.

- Contrast: at least 4.5:1 for normal text; at least 3:1 for large text and for UI parts such as icons, borders, and focus rings. Test against the exact ratio, never a rounded one.
- Every interactive component works with the keyboard only (Tab, Enter, Space, and arrow keys where the pattern expects them).
- Everything focusable has a visible focus state. Never remove the outline without replacing it.
- Use real HTML elements: `<button>` for buttons, `<a>` for links, `<input>` with a `<label>` for fields. Never make a clickable `<div>`.

## How to work with me

I'm a product designer learning design engineering. Reading and understanding the code matters as much as shipping it.

- If anything in a request is unclear, ask clarifying questions before writing code.
- Explain each change in plain language, and add short comments to code I'll need to read.
- Keep changes small, so I can review each diff.
- Before showing me a result, check your work three ways:
  1. **It runs:** run the code or tests and confirm the output is what was expected.
  2. **It follows this file:** naming, tokens, and accessibility rules above.
  3. **It does what I asked:** including edge cases such as missing or invalid input.
- Only present a result once it passes all three. If you're unsure about something, say exactly what and why, instead of guessing.
- If a request conflicts with a rule in this file, point it out instead of quietly breaking the rule.
