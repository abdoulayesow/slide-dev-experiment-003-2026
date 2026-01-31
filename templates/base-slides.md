---
theme: default
title: "{{TITLE}}"
info: |
  Presentation created with Slidev
  Learn more at https://sli.dev
class: text-center
drawings:
  persist: false
transition: slide-left
mdc: true
---

# {{TITLE}}

<div class="pt-12">
  <span class="px-2 py-1 rounded cursor-pointer text-muted" hover="bg-white bg-opacity-10">
    Press Space to start
  </span>
</div>

<!--
Welcome to the presentation!
Press Space or arrow keys to navigate.
Press 'p' for presenter mode with notes.
-->

---
layout: default
---

# Today's Agenda

<div class="grid grid-cols-3 gap-6 mt-8">
  <Card title="Part 1" icon="1️⃣" color="blue">
    Topic description here
  </Card>
  <Card title="Part 2" icon="2️⃣" color="amber">
    Topic description here
  </Card>
  <Card title="Part 3" icon="3️⃣" color="green">
    Topic description here
  </Card>
</div>

<!--
Walk through the agenda
Set expectations for timing
-->

---
layout: default
---

# Learning Objectives

<Checklist :items="[
  'First learning objective',
  'Second learning objective',
  'Third learning objective',
  'Fourth learning objective'
]" />

<!--
Review what participants will learn
Check for prior knowledge
-->

---
layout: center
class: chapter-divider
---

<ChapterDivider number="1" title="First Topic" />

<!--
Transition to first major section
-->

---
layout: default
---

# Sample Content Slide

Content goes here. Use markdown formatting:

- **Bold text** for emphasis
- *Italic text* for terms
- `Code snippets` inline

<div class="mt-8 grid grid-cols-2 gap-6">
  <Card title="Key Point" color="blue">
    Important information in a card
  </Card>
  <Card title="Remember" color="green">
    Another key takeaway
  </Card>
</div>

<!--
Presenter notes for this slide
Key teaching points to cover
-->

---
layout: default
---

# Do's and Don'ts

<Comparison>
  <template #do>
    <li>Follow best practices</li>
    <li>Keep it simple</li>
    <li>Test regularly</li>
  </template>
  <template #dont>
    <li>Skip testing</li>
    <li>Overcomplicate</li>
    <li>Ignore feedback</li>
  </template>
</Comparison>

<!--
Discuss each point
Use examples from experience
-->

---
layout: default
---

# Timeline Example

<Timeline :events="[
  { time: '9:00', title: 'Introduction', color: 'blue' },
  { time: '9:30', title: 'Main Content', color: 'green' },
  { time: '10:30', title: 'Practice', color: 'amber' },
  { time: '11:00', title: 'Wrap-up', color: 'purple' }
]" />

<!--
Review the schedule
Note any time adjustments
-->

---
layout: center
---

# ☕ Break Time

Take 10 minutes to stretch and refresh

<!--
Announce break duration
Set expectations for return
-->

---
layout: default
---

# Summary

<div class="grid grid-cols-2 gap-6">
  <Card title="What We Learned" color="blue">
    <ul>
      <li>Key point 1</li>
      <li>Key point 2</li>
      <li>Key point 3</li>
    </ul>
  </Card>
  <Card title="Next Steps" color="green">
    <ul>
      <li>Action item 1</li>
      <li>Action item 2</li>
      <li>Action item 3</li>
    </ul>
  </Card>
</div>

<!--
Recap main takeaways
Preview what's next
-->

---
layout: center
---

# Thank You!

Questions?

<div class="mt-8 text-muted">
  Contact: your@email.com
</div>

<!--
Open floor for questions
Share contact information
-->
