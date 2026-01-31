# /slidev-generate

Convert a structured outline file into Slidev presentation slides.

## Usage

```
/slidev-generate <outline-file-path> [--target <presentation-folder>]
```

**Examples:**
```
/slidev-generate docs/slides/Week1-Detailed-Outline.md
/slidev-generate docs/slides/Week1-Detailed-Outline.md --target presentations/week1-scrum-foundations
```

## Arguments

- `outline-file-path`: Path to the markdown outline file
- `--target` (optional): Target presentation folder. If not specified, creates new folder based on outline title.

## What This Skill Does

1. **Reads and parses** the outline file
2. **Extracts slide information** (titles, content, visual notes)
3. **Maps to Slidev layouts** based on slide type
4. **Generates slides.md** with proper frontmatter
5. **Adds presenter notes** from visual descriptions
6. **Uses clean, modern design patterns** - Card-based layouts with colored backgrounds, gradient text, simple HTML/CSS instead of custom Vue components

---

## Outline Format Recognition

The skill recognizes these patterns in outlines:

### Slide Definitions

```markdown
**Slide N: Title**
- Title: "Slide Title"
- Content: Description or bullet points
- **Visual:** Description of desired appearance
```

### Section Markers

```markdown
### SECTION NAME (Slides X-Y)
```

### Chapter Dividers

```markdown
**Slide N: Chapter Divider**
- Large number "X"
- Title: "Chapter Title"
```

---

## Slide Type Mapping

| Outline Pattern | Slidev Layout | Design Pattern |
|-----------------|---------------|----------------|
| "Title Slide" / "Cover" | `cover` | Gradient text with centered layout |
| "Chapter Divider" | `center` | Large gradient number + gradient title |
| "Agenda" / multiple cards | `default` | Card grid with colored left borders |
| "Learning Objectives" / checklist | `default` | Green checkmark circles with flex layout |
| "Do's and Don'ts" / comparison | `default` | Side-by-side colored cards |
| "Timeline" / events | `default` | Vertical timeline with colored dots |
| "Break Slide" | `center` | Simple centered text |
| "Thank You" / closing | `center` or `end` | - |
| Content with sidebar | `two-cols` | - |
| Default content | `default` | - |

---

## Instructions for Claude

When this skill is invoked:

### Step 1: Read the Outline File

```
Read the outline file at the specified path
```

### Step 2: Parse Structure

Identify:
- Week/Presentation title
- Duration
- Learning goals
- Sections and their slide ranges
- Individual slides with their:
  - Slide number
  - Title
  - Content (bullets, text)
  - Visual description

### Step 3: Determine Slide Types

For each slide, analyze the title and content to determine type:

**Cover/Title slides:**
- Contains "Title Slide" or is first slide
- Has program/presentation title

**Chapter Dividers:**
- Contains "Chapter Divider"
- Has large number + title format
- Usually marks section beginnings

**Checklist slides:**
- Contains "Learning Objectives" or "What You'll Learn"
- Has list of items with checkmarks (✓)

**Card-based slides:**
- Contains multiple distinct topics
- Visual mentions "cards" or "boxes"
- Good for 3-5 related concepts

**Comparison slides:**
- Contains "Do's and Don'ts" or comparisons
- Has contrasting items (❌/✅)

**Timeline slides:**
- Contains time-based events
- Agenda or schedule format

**Break slides:**
- Contains "Break" in title
- Short break announcement

### Step 4: Generate Slides

For each slide, generate Slidev markdown:

**Example - Cover Slide:**
```markdown
---
layout: cover
---

<div class="h-full grid place-items-center">
  <div class="text-center">
    <h1 class="text-7xl font-bold mb-6 bg-gradient-to-r from-cyan-500 to-blue-500 bg-clip-text text-transparent">
      Professional Scrum Master
    </h1>
    <p class="text-3xl text-gray-600 dark:text-gray-300 mb-4">PSM I Certification Training</p>
    <p class="text-xl text-gray-500 dark:text-gray-400">4-Week Intensive Program</p>
    <p class="text-sm text-gray-400 dark:text-gray-500 mt-8">2025 Training Program</p>
  </div>
</div>

<!--
Welcome participants
Introduce the program structure
Set expectations for the journey
-->
```

**Example - Chapter Divider:**
```markdown
---
layout: center
---

<div class="h-full grid place-items-center">
  <div class="text-center">
    <div class="text-9xl font-bold opacity-10 mb-8 bg-gradient-to-r from-cyan-500 to-blue-500 bg-clip-text text-transparent">1</div>
    <h1 class="text-6xl font-semibold -mt-20 bg-gradient-to-r from-cyan-500 to-blue-500 bg-clip-text text-transparent">Why Agile & Scrum?</h1>
  </div>
</div>

<!--
Transition to explaining why Scrum exists
Connect to participants' experiences with waterfall
-->
```

**Example - Card-based Content:**
```markdown
---
layout: default
---

# The Three Pillars of Empiricism

<div class="text-gray-500 dark:text-gray-400 mb-6">Scrum is founded on empirical process control</div>

<div class="grid grid-cols-3 gap-4 mt-6">
  <div class="bg-cyan-50 dark:bg-cyan-950 dark:bg-opacity-20 rounded-2xl p-6 border-l-4 border-cyan-500">
    <div class="text-4xl mb-3">👁️</div>
    <h3 class="text-cyan-600 dark:text-cyan-400 text-lg font-semibold mb-3">Transparency</h3>
    <p>Significant aspects must be visible to those responsible for the outcome</p>
  </div>
  <div class="bg-amber-50 dark:bg-amber-950 dark:bg-opacity-20 rounded-2xl p-6 border-l-4 border-amber-500">
    <div class="text-4xl mb-3">🔍</div>
    <h3 class="text-amber-600 dark:text-amber-400 text-lg font-semibold mb-3">Inspection</h3>
    <p>Artifacts and progress inspected frequently and diligently</p>
  </div>
  <div class="bg-green-50 dark:bg-green-950 dark:bg-opacity-20 rounded-2xl p-6 border-l-4 border-green-500">
    <div class="text-4xl mb-3">⚡</div>
    <h3 class="text-green-600 dark:text-green-400 text-lg font-semibold mb-3">Adaptation</h3>
    <p>Adjust when aspects deviate outside acceptable limits</p>
  </div>
</div>

<div class="mt-6 p-4 bg-gray-100 dark:bg-gray-800 rounded-lg text-center">
  <span class="text-cyan-600 dark:text-cyan-400 font-semibold">Empiricism = Knowledge comes from experience</span>
</div>

<!--
Key teaching points:
- All three pillars work together
- Cannot have inspection without transparency
- Adaptation is the goal - we inspect to adapt
- Ask: "Where do you see these in daily work?"
-->
```

**Example - Checklist:**
```markdown
---
layout: default
---

# What You'll Learn Today

<div class="space-y-3">
  <div class="flex items-start gap-3">
    <div class="w-6 h-6 rounded-full bg-green-500 flex items-center justify-center text-white text-sm flex-shrink-0 mt-1">✓</div>
    <div>Explain why Scrum works better than Waterfall</div>
  </div>
  <div class="flex items-start gap-3">
    <div class="w-6 h-6 rounded-full bg-green-500 flex items-center justify-center text-white text-sm flex-shrink-0 mt-1">✓</div>
    <div>Describe the 3 pillars of empiricism</div>
  </div>
  <div class="flex items-start gap-3">
    <div class="w-6 h-6 rounded-full bg-green-500 flex items-center justify-center text-white text-sm flex-shrink-0 mt-1">✓</div>
    <div>Identify the 5 Scrum values</div>
  </div>
  <div class="flex items-start gap-3">
    <div class="w-6 h-6 rounded-full bg-green-500 flex items-center justify-center text-white text-sm flex-shrink-0 mt-1">✓</div>
    <div>Understand the 3 roles, 5 events, 3 artifacts</div>
  </div>
  <div class="flex items-start gap-3">
    <div class="w-6 h-6 rounded-full bg-green-500 flex items-center justify-center text-white text-sm flex-shrink-0 mt-1">✓</div>
    <div>Set up a Product Backlog and Sprint Goal</div>
  </div>
</div>

<!--
Review objectives with participants
Check for prior experience with any of these
Adjust depth based on audience
-->
```

**Example - Comparison:**
```markdown
---
layout: default
---

# The Iron Triangle

<div class="grid grid-cols-2 gap-12 mt-8">
  <div class="bg-red-50 dark:bg-red-950 dark:bg-opacity-20 rounded-2xl p-8">
    <h3 class="text-red-600 dark:text-red-400 text-2xl font-semibold mb-6 text-center uppercase tracking-wide">Traditional (Waterfall)</h3>
    <div class="space-y-6">
      <div class="text-center">
        <div class="inline-block px-6 py-3 bg-red-600 text-white rounded-lg font-semibold text-lg mb-4">
          SCOPE (Fixed)
        </div>
      </div>
      <div class="flex justify-around">
        <div class="px-4 py-2 bg-gray-200 dark:bg-gray-700 rounded-lg text-sm">Time</div>
        <div class="px-4 py-2 bg-gray-200 dark:bg-gray-700 rounded-lg text-sm">Cost</div>
      </div>
      <div class="text-center pt-4">
        <p class="text-red-600 dark:text-red-400 font-medium">⚠️ Quality suffers</p>
      </div>
    </div>
  </div>

  <div class="bg-green-50 dark:bg-green-950 dark:bg-opacity-20 rounded-2xl p-8">
    <h3 class="text-green-600 dark:text-green-400 text-2xl font-semibold mb-6 text-center uppercase tracking-wide">Agile (Scrum)</h3>
    <div class="space-y-6">
      <div class="flex justify-around">
        <div class="px-4 py-2 bg-green-600 text-white rounded-lg font-semibold">Time</div>
        <div class="px-4 py-2 bg-green-600 text-white rounded-lg font-semibold">Cost</div>
      </div>
      <div class="text-center">
        <div class="inline-block px-6 py-3 bg-gray-200 dark:bg-gray-700 rounded-lg text-sm mb-4">
          Scope (Flexible)
        </div>
      </div>
      <div class="text-center pt-4">
        <p class="text-green-600 dark:text-green-400 font-medium">✓ Quality guaranteed</p>
      </div>
    </div>
  </div>
</div>

<!--
Draw both triangles on whiteboard if possible
Explain why fixing scope leads to quality issues
Discuss how Scrum handles scope negotiation
-->
```

**Example - Timeline:**
```markdown
---
layout: default
---

# The Waterfall Challenge

<div class="grid grid-cols-2 gap-8">
  <div>
    <h3 class="text-gray-500 dark:text-gray-400 text-sm uppercase tracking-wider mb-6">Traditional Approach</h3>
    <div class="space-y-3">
      <div class="flex items-center gap-3">
        <div class="w-3 h-3 rounded-full bg-cyan-500"></div>
        <div class="flex-1">
          <div class="text-sm text-gray-500 dark:text-gray-400">Phase 1</div>
          <div class="font-medium">Requirements</div>
        </div>
      </div>
      <div class="flex items-center gap-3">
        <div class="w-3 h-3 rounded-full bg-cyan-500"></div>
        <div class="flex-1">
          <div class="text-sm text-gray-500 dark:text-gray-400">Phase 2</div>
          <div class="font-medium">Analysis</div>
        </div>
      </div>
      <div class="flex items-center gap-3">
        <div class="w-3 h-3 rounded-full bg-amber-500"></div>
        <div class="flex-1">
          <div class="text-sm text-gray-500 dark:text-gray-400">Phase 3</div>
          <div class="font-medium">Design</div>
        </div>
      </div>
    </div>
  </div>
  <div class="bg-red-50 dark:bg-red-950 dark:bg-opacity-20 rounded-2xl p-6 border-l-4 border-red-500">
    <h3 class="text-red-600 dark:text-red-400 text-xl font-semibold mb-4 uppercase tracking-wide">The Problems</h3>
    <ul class="space-y-3">
      <li class="flex items-start gap-2">
        <span class="text-red-500 text-xl">✕</span>
        <div><strong>Change is expensive</strong> — requirements frozen early</div>
      </li>
    </ul>
  </div>
</div>

<!--
Teaching points about waterfall challenges
Use colored dots to show progression
-->
```

**Example - Break Slide:**
```markdown
---
layout: center
class: text-center
---

# ☕ 10-Minute Break

<div class="mt-4 text-muted">
  Stand up, stretch, grab coffee
</div>

<div class="mt-8 text-sm text-muted">
  We'll discuss exercise results when we return
</div>

<!--
Announce break duration
Remind what's coming next
-->
```

### Step 5: Add Presenter Notes

Extract from "**Visual:**" descriptions and other context:
- Teaching points
- Questions to ask
- Examples to use
- Timing notes

Format as HTML comments:
```markdown
<!--
Key points:
- First important point
- Second important point

Questions to ask:
- "Has anyone experienced this?"
- "What challenges did you face?"

Timing: 5 minutes for this slide
-->
```

### Step 6: Write Output

1. If target folder exists, update `slides.md`
2. If no target, create new presentation folder
3. Ensure components are available
4. Report slide count and any issues

---

## Output Format

```
Generated slides for: Week 1: Scrum Foundations
Location: presentations/week1-scrum-foundations/slides.md

Slides created: 51
- Cover slides: 1
- Chapter dividers: 5
- Content slides: 40
- Break slides: 1
- Closing slides: 1

Components used:
- Card: 25 instances
- ChapterDivider: 5 instances
- Checklist: 6 instances
- Comparison: 4 instances

To preview:
  cd presentations/week1-scrum-foundations
  npm run dev
```

---

## Dependencies

- Outline file must follow the expected format
- Target presentation should have components installed
- Use `/slidev-init` first if creating new presentation

---

## Design Principles

### IMPORTANT: No Custom Vue Components

**DO NOT use custom Vue components** like `<Card>`, `<ChapterDivider>`, `<Checklist>`, `<Comparison>`, or `<Timeline>`. These components can cause rendering issues and layout problems.

Instead, use **clean, modern HTML/CSS patterns**:

1. **Card layouts**: Use colored background divs with border-left-4 and rounded-2xl
   ```html
   <div class="bg-cyan-50 dark:bg-cyan-950 dark:bg-opacity-20 rounded-2xl p-6 border-l-4 border-cyan-500">
     <div class="text-4xl mb-3">📚</div>
     <h3 class="text-cyan-600 dark:text-cyan-400 text-lg font-semibold mb-3">Title</h3>
     <p>Content here</p>
   </div>
   ```

2. **Chapter dividers**: Use large gradient numbers with negative margin for title overlap
   ```html
   <div class="text-9xl font-bold opacity-10 mb-8 bg-gradient-to-r from-cyan-500 to-blue-500 bg-clip-text text-transparent">1</div>
   <h1 class="text-6xl font-semibold -mt-20 bg-gradient-to-r from-cyan-500 to-blue-500 bg-clip-text text-transparent">Title</h1>
   ```

3. **Checklists**: Use flex layout with green checkmark circles
   ```html
   <div class="flex items-start gap-3">
     <div class="w-6 h-6 rounded-full bg-green-500 flex items-center justify-center text-white text-sm flex-shrink-0 mt-1">✓</div>
     <div>Item text</div>
   </div>
   ```

4. **Timelines**: Use colored dots with flex layout, not Timeline component
   ```html
   <div class="flex items-center gap-3">
     <div class="w-3 h-3 rounded-full bg-cyan-500"></div>
     <div class="flex-1">
       <div class="text-sm text-gray-500 dark:text-gray-400">Phase 1</div>
       <div class="font-medium">Requirements</div>
     </div>
   </div>
   ```

5. **Gradient text**: Use bg-gradient-to-r with bg-clip-text for titles
   ```html
   <h1 class="bg-gradient-to-r from-cyan-500 to-blue-500 bg-clip-text text-transparent">Title</h1>
   ```

### Color Palette

Use these color classes consistently:
- **Primary (Cyan)**: `bg-cyan-50/500/600`, `border-cyan-500`, `text-cyan-600`
- **Success (Green)**: `bg-green-50/500/600`, `border-green-500`, `text-green-600`
- **Warning (Amber)**: `bg-amber-50/500/600`, `border-amber-500`, `text-amber-600`
- **Danger (Red)**: `bg-red-50/500/600`, `border-red-500`, `text-red-600`
- **Secondary (Purple)**: `bg-purple-50/500/600`, `border-purple-500`, `text-purple-600`
- **Muted text**: `text-gray-500 dark:text-gray-400`
- **Card backgrounds**: `bg-gray-100 dark:bg-gray-800`

### Dark Mode Support

ALWAYS include dark mode variants:
- Backgrounds: `bg-cyan-50 dark:bg-cyan-950 dark:bg-opacity-20`
- Text: `text-gray-600 dark:text-gray-300`
- Borders maintain same color in dark mode

## Quality Guidelines

1. **One idea per slide** - Don't overcrowd
2. **Use HTML/CSS patterns** - No custom Vue components
3. **Add presenter notes** - Every slide needs context
4. **Match visual descriptions** - Use colors mentioned in outline
5. **Test rendering** - Verify output in browser
6. **Support dark mode** - Always include dark: variants
