# HTML Slide Generator

Build professional presentation slides directly with HTML/CSS using the `/frontend-design` skill.

## Project Overview

**Purpose:** Create high-quality slide decks as standalone HTML pages with custom styling.

**Current Use Case:** PSM I Certification Training Program (4-week, 12-hour curriculum with 237 slides)

## Quick Start

```bash
# Create slides using the frontend-design skill
/frontend-design

# Then describe what you want, referencing the style guide and outlines
```

## Project Structure

```
slide-dev-experiment-003-2026/
├── CLAUDE.md                     # This file
├── docs/
│   ├── slides/                   # Source outlines (content)
│   │   ├── Week1-Detailed-Outline.md
│   │   ├── Week2-Detailed-Outline.md
│   │   ├── Week3-Detailed-Outline.md
│   │   └── Week4-Detailed-Outline.md
│   └── resume/                   # Coach bio
├── templates/                    # Style guide & template slides
│   └── style-guide.html          # Master branding reference
└── presentations/                # Generated HTML slide decks
    └── week1/
        ├── index.html            # Slide deck entry
        └── slides/               # Individual slide files
```

## Workflow

### 1. Create Style Guide Template

First, build `templates/style-guide.html` with:
- Color palette
- Typography scale
- Slide layouts (cover, content, chapter divider, etc.)
- Component patterns (cards, lists, timelines, comparisons)
- Branding elements

### 2. Generate Slides from Outlines

Use `/frontend-design` to create slides based on:
- The style guide template
- Content from `docs/slides/Week{N}-Detailed-Outline.md`

### 3. Output Structure

Each week's presentation:
- Single HTML file or multi-file structure
- Embedded CSS (no external dependencies)
- Print-friendly / PDF-exportable
- Keyboard navigation (arrow keys)

## Outline Format

Source outlines follow this structure:

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

## Slide Types

| Type | Use For |
|------|---------|
| Cover | Title/opening slides |
| Chapter Divider | Section breaks with large numbers |
| Content | Standard bullet points |
| Two Column | Side-by-side content |
| Comparison | Do's vs Don'ts |
| Timeline | Event sequences |
| Quote | Prominent quotations |
| Fact/Stat | Key numbers/metrics |
| Summary | Recap slides |
| End | Closing/thank you |

## Design Principles

1. **Dark theme** - Navy backgrounds, high contrast text
2. **Accent colors** - Cyan primary, semantic colors for meaning
3. **One idea per slide** - Keep content focused
4. **Visual hierarchy** - Clear titles, readable body text
5. **Consistent spacing** - Use a spacing scale
6. **Accessible** - Sufficient contrast, readable fonts

## Best Practices

- Reference the style guide when creating new slides
- Keep slides visually consistent across weeks
- Test keyboard navigation
- Verify print/PDF export looks correct
- Use semantic HTML for accessibility
