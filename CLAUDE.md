# Slidev Presentation Generator

This project provides reusable skills and infrastructure for generating professional Slidev presentations.

## Project Overview

**Purpose:** Create professional slide decks using Slidev (Markdown-based presentations for developers).

**Current Use Case:** PSM I Certification Training Program (4-week, 12-hour curriculum with 237 slides)

## Quick Start

```bash
# Initialize a new presentation
/slidev-init <folder-name> "<title>"

# Generate slides from an outline
/slidev-generate <outline-file-path>

# Preview slides
/slidev-preview <folder-name>
```

## Project Structure

```
slide-dev-experiment-003-2026/
├── CLAUDE.md                     # This file
├── templates/                    # Reusable templates
│   ├── components/              # Vue components for slides
│   ├── theme/                   # CSS themes
│   └── base-slides.md           # Starter template
├── docs/slides/                 # Source outlines
└── presentations/               # Generated presentations
```

## Available Skills

### Slash Commands

| Command | Description |
|---------|-------------|
| `/slidev-init` | Initialize a new Slidev presentation project |
| `/slidev-generate` | Convert outline to Slidev slides |
| `/slidev-preview` | Preview and validate slides |

### Hookify Rules

- **slidev-format** - Auto-validates slide syntax
- **slidev-style-guard** - Enforces theme consistency
- **slidev-notes-reminder** - Reminds to add presenter notes

---

## Slidev Reference

### Slide Separators

Use `---` with blank lines to separate slides:

```markdown
---
layout: cover
---

# Slide 1 Title

---

# Slide 2 Title

Content here
```

### Frontmatter (Per Slide)

```yaml
---
layout: default      # Layout type
class: text-center   # CSS classes
transition: slide-left
---
```

### Available Layouts

| Layout | Use For |
|--------|---------|
| `cover` | Title/opening slides |
| `center` | Centered content, chapter dividers |
| `default` | Standard content slides |
| `two-cols` | Side-by-side content |
| `two-cols-header` | Header + two columns |
| `image-left` | Image on left, content on right |
| `image-right` | Image on right, content on left |
| `quote` | Prominent quotations |
| `section` | Section dividers |
| `fact` | Statistics/data emphasis |
| `end` | Closing slides |

### Presenter Notes

Add notes as HTML comments at end of slide:

```markdown
---

# My Slide

Content here

<!--
These are presenter notes.
Only visible in presenter mode (press 'p').
- Key point 1
- Key point 2
-->
```

### Code Blocks

```markdown
```ts {2-3}
// Line 1
// Lines 2-3 highlighted
// Line 4
```
```

### Using Vue Components

```markdown
<Card title="My Card" color="blue">
  Content inside the card
</Card>
```

---

## Theme Specification

### Color Palette

| Variable | Hex | Usage |
|----------|-----|-------|
| `--color-background` | #1a1a2e | Dark navy background |
| `--color-primary` | #0ea5e9 | Cyan blue accent |
| `--color-success` | #10b981 | Green (positive) |
| `--color-warning` | #f59e0b | Amber (caution) |
| `--color-danger` | #ef4444 | Red (negative) |
| `--color-secondary` | #8b5cf6 | Purple accent |
| `--color-text` | #ffffff | White text |
| `--color-muted` | #94a3b8 | Gray text |
| `--color-card` | #2d2d44 | Card backgrounds |

### Typography

- Titles: 36-48px, bold, cyan or white
- Subtitles: 16-20px, muted gray
- Body: 14-16px, white
- Lists: 13-15px, white or light gray

---

## Component Library

### Card

Gradient card with icon and title.

```vue
<Card
  title="Card Title"
  icon="icon-name"
  color="blue|green|amber|red|purple"
>
  Card content goes here
</Card>
```

### ChapterDivider

Large numbered section break.

```vue
<ChapterDivider
  number="1"
  title="Chapter Title"
/>
```

### Checklist

Learning objectives with checkmarks.

```vue
<Checklist :items="[
  'First objective',
  'Second objective',
  'Third objective'
]" />
```

### Comparison

Side-by-side do's and don'ts.

```vue
<Comparison>
  <template #do>
    <li>Do this</li>
    <li>Also do this</li>
  </template>
  <template #dont>
    <li>Don't do this</li>
    <li>Avoid this</li>
  </template>
</Comparison>
```

### Timeline

Event sequence visualization.

```vue
<Timeline :events="[
  { time: '9:00', title: 'Sprint Planning' },
  { time: '9:15', title: 'Daily Scrum' }
]" />
```

---

## Commands Reference

```bash
# Development server (live preview)
npm run dev

# Build static site
npm run build

# Export to PDF
npm run export

# Format slides
npm run format
```

---

## Outline Format

Source outlines should follow this structure:

```markdown
# WEEK N: TITLE
**Duration:** X hours

---

## SLIDE-BY-SLIDE CONTENT

### SECTION NAME (Slides X-Y)

**Slide N: Slide Title**
- Title: "Slide Title"
- Content: Bullet points
- **Visual:** Description of desired visual style
```

The `/slidev-generate` skill parses this format to create slides.

---

## Best Practices

1. **One idea per slide** - Keep content focused
2. **Use layouts appropriately** - Match content to layout
3. **Include presenter notes** - Add context for delivery
4. **Follow theme colors** - Use CSS variables, not hardcoded colors
5. **Test on multiple screens** - Verify responsive behavior
6. **Export PDFs as backup** - Always have offline version
