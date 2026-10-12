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

## Design System Validation Rules

### COLOR RULES
- Primary button MUST use background #44403C with white text #FFFFFF
- Secondary button MUST use border #44403C with transparent background
- Warning button MUST use background #C2790A with white text
- Danger button MUST use background #B3261E with white text
- Disabled button MUST use background #CCCCCC with opacity 50%
- Input focus MUST use border #4A90A4 with blue glow shadow
- Input error MUST use border #B3261E
- Alert Info MUST use background #4A90A4
- Alert Success MUST use background #2E7D32
- Alert Warning MUST use background #C2790A
- Alert Error MUST use background #B3261E
- ✗ NEVER use colors outside this palette

### SIZE RULES
- Button height MUST be exactly 48px
- Input height MUST be exactly 40px
- Card/Modal border-radius MUST be 8px
- Input border-radius MUST be 6px
- ✗ NEVER use custom sizes

### FONT RULES
- Body text MUST be 14px, 400 weight, Inter
- Heading MUST be 18px, 600 weight, Inter
- Label MUST be 12px, 600 weight, Inter
- Button text MUST be 14px, 600 weight, Inter
- ✗ NEVER use other fonts or weights

### SPACING RULES
- Container padding MUST be 16px
- Component gap MUST be 8px
- Section margin MUST be 24px
- ✗ NEVER use inconsistent spacing

## Design System Validation Rules

### COLOR RULES
✓ Primary button MUST use #44403C
✓ Primary button text MUST be white (#FFFFFF)
✓ Secondary button MUST use border #44403C
✗ NEVER use colors outside this palette: #44403C, #ECE8E2, #C2790A, #B3261E, #CCCCCC, #4A90A4

### SIZE RULES
✓ Button height MUST be 48px (not 44px, not 50px)
✓ Input height MUST be 40px
✓ Border radius for buttons MUST be 8px
✓ Border radius for inputs MUST be 6px
✗ NEVER use custom sizes

### FONT RULES
✓ Body text MUST be 14px, 400 weight, Inter
✓ Heading MUST be 18px, 600 weight, Inter
✗ NEVER use other fonts or weights

## Examples of Violations (What the checker looks for)

### VIOLATION: Wrong button color
❌ Bad:
```tsx
<button style={{backgroundColor: '#FF0000'}}>Click</button>
```

✅ Good:
```tsx
<button style={{backgroundColor: '#44403C'}}>Click</button>
```

### VIOLATION: Wrong button height
❌ Bad:
```tsx
<button style={{height: '44px'}}>Click</button>
```

✅ Good:
```tsx
<button style={{height: '48px'}}>Click</button>
```

### VIOLATION: Wrong font size
❌ Bad:
```tsx
<p style={{fontSize: '16px'}}>Body text</p>
```

✅ Good:
```tsx
<p style={{fontSize: '14px'}}>Body text</p>
```

## How to use

**Check a single file:**
```
/design-system-checker src/components/Button.tsx
```

**Check a folder:**
```
/design-system-checker src/components/
```

**Output includes:**
- ✓ What's correct
- ✗ What's wrong
- 🔧 Suggested fixes

## Example

**Input:**
```tsx
<button style={{backgroundColor: '#FF0000', height: '44px'}}>
  Click me
</button>
```

**Output:**
````
❌ Violation found:

* Background color `#FF0000` should be `#44403C` (Primary)
* Height 44px should be 48px

✅ Suggested fix:
```tsx
<button style={{backgroundColor: '#44403C', height: '48px'}}>
  Click me
</button>
```
````

## When to use
- After writing component code
- Before pushing to GitHub
- In weekly automation routine
- When refactoring existing code

---

*Design System Checker v1.0*
