---
name: design-system-checker
description: Checks that UI code follows the design system (tokens, components, spacing…). Use when writing, reviewing or refactoring UI code (components, styles, layouts), or when the user asks whether code respects the design system.
---

# Design System Checker

Verify that UI code applies the design system documented in this repository, and report every deviation with a concrete fix.

## Workflow

1. **Load the rules.** Read the design system documentation in this repository (tokens, components, spacing, typography, color, accessibility guidelines). Never check from memory: the documentation is the source of truth.
2. **Identify the scope.** Check the files the user names; otherwise the files changed in the current diff (`git diff`), limited to UI code (components, styles, templates).
3. **Check each rule category** listed below.
4. **Report** findings in the format described at the end, then offer to apply the fixes.

## What to check

### Tokens
- No hard-coded colors (`#hex`, `rgb()`, `hsl()`, named colors): use color tokens.
- No raw font sizes, weights, line heights or font families: use typography tokens.
- No arbitrary radii, shadows, z-index or durations: use the matching tokens.

### Spacing
- Margins, paddings and gaps use the spacing scale only; flag values outside the scale (e.g. `13px`).
- Layout spacing is consistent between sibling elements.

### Components
- Use design system components instead of re-implementing them (e.g. a custom `<button>` instead of the `Button` component).
- Use only documented props and variants; flag style overrides that bypass the component API.

### Accessibility
- Text/background pairs meet the contrast required by the documentation.
- Interactive elements have accessible names, visible focus states and adequate target sizes.

## Report format

Group findings by file, most severe first:

```
path/to/file.tsx:42 — [Tokens] Hard-coded color `#1A73E8`
  → Use `color.primary.500`
```

Severity:
- **Error**: breaks a documented rule (hard-coded value, re-implemented component, failed contrast).
- **Warning**: allowed but discouraged (undocumented variant, inconsistent spacing).

End with a short summary: number of errors and warnings per category. If no issues are found, say so explicitly.

## Rules

- Cite the documentation section behind each finding.
- When the documentation does not cover a case, report it as a question rather than an error.
- Do not modify files unless the user asks for the fixes.
