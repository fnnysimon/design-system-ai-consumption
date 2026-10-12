---
name: design-system-checker
description: Validates code against design system rules and suggests fixes
---

# Design System Checker Skill

## Purpose
Automatically check if your code follows the design system rules defined in https://designsystemforai.vercel.app/

## What this skill does

1. **Extracts your design rules** from the design system
2. **Analyzes code** (React, CSS, Tailwind, HTML)
3. **Finds violations** (wrong colors, wrong fonts, wrong spacing)
4. **Suggests fixes** that make code compliant

## Design System Rules (Reference)

### Colors
- Primary: #44403C
- Secondary: #ECE8E2
- Warning: #C2790A
- Danger: #B3261E
- Disabled: #CCCCCC
- Focus: #4A90A4

### Typography
- Body: 14px, 400 weight, Inter
- Heading: 18px, 600 weight, Inter
- Label: 12px, 600 weight, Inter

### Sizing
- Button height: 48px
- Input height: 40px
- Border radius (components): 8px
- Border radius (inputs): 6px

### Spacing
- Container padding: 16px
- Component gap: 8px
- Section margin: 24px

## How to use

**Check a single file:**
