# /slidev-init

Initialize a new Slidev presentation project with custom theme and components.

## Usage

```
/slidev-init <folder-name> "<presentation-title>"
```

**Examples:**
```
/slidev-init week1-scrum-foundations "Week 1: Scrum Foundations"
/slidev-init quarterly-review "Q1 2025 Business Review"
```

## Arguments

- `folder-name`: Name of the presentation folder (will be created under `presentations/`)
- `presentation-title`: Title displayed on cover slide

## What This Skill Does

1. **Creates project folder** at `presentations/<folder-name>/`

2. **Initializes Slidev project** with:
   - `package.json` with Slidev dependencies
   - `slides.md` with base frontmatter and title slide
   - `components/` folder with theme components copied from templates
   - `public/` folder for images and assets

3. **Configures theme** with:
   - Custom dark theme matching project style guide
   - UnoCSS configuration for utility classes
   - CSS variables for consistent colors

4. **Installs dependencies** using npm

## Instructions for Claude

When this skill is invoked:

1. **Parse arguments** - Extract folder name and title from user input

2. **Create folder structure**:
   ```
   presentations/<folder-name>/
   ├── slides.md
   ├── package.json
   ├── components/
   │   ├── Card.vue
   │   ├── ChapterDivider.vue
   │   ├── Checklist.vue
   │   ├── Comparison.vue
   │   └── global.d.ts
   ├── styles/
   │   └── theme.css
   └── public/
   ```

3. **Create package.json**:
   ```json
   {
     "name": "<folder-name>",
     "private": true,
     "scripts": {
       "dev": "slidev --open",
       "build": "slidev build",
       "export": "slidev export"
     },
     "dependencies": {
       "@slidev/cli": "latest",
       "@slidev/theme-default": "latest"
     }
   }
   ```

4. **Create slides.md** with frontmatter:
   ```markdown
   ---
   theme: default
   title: "<presentation-title>"
   info: |
     Presentation created with Slidev
   class: text-center
   drawings:
     persist: false
   transition: slide-left
   mdc: true
   ---

   # <presentation-title>

   <div class="pt-12">
     <span class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
       Press Space to start
     </span>
   </div>

   <!--
   Welcome! Press Space or arrow keys to navigate.
   Press 'p' for presenter mode.
   -->

   ---
   layout: default
   ---

   # Add your slides here

   Use `---` to separate slides.

   <!--
   Presenter notes go here
   -->
   ```

5. **Copy components** from `templates/components/` to `presentations/<folder-name>/components/`

6. **Copy theme** from `templates/theme/` to `presentations/<folder-name>/styles/`

7. **Run npm install** in the new project folder

8. **Report success** with instructions:
   ```
   Created presentation: presentations/<folder-name>

   To start development:
     cd presentations/<folder-name>
     npm run dev

   To export to PDF:
     npm run export

   Next steps:
   - Edit slides.md to add your content
   - Use /slidev-generate to convert an outline
   ```

## Dependencies

- Node.js >= 18.0 (user confirmed installed)
- Templates must exist in `templates/` folder
- npm must be available

## Error Handling

- If folder already exists, ask user if they want to overwrite
- If templates don't exist, create basic versions inline
- If npm install fails, report error and suggest manual installation
