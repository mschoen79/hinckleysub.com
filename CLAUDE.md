# CLAUDE.md — Working with hinckley-sub.html

## What This Document Is

`hinckley-sub.html` (served as `index.html` on hinckleysub.com) is a single self-contained HTML document — a layout design reference for an N scale model railroad based on the BNSF Hinckley Subdivision and DM&IR ore operations in Minnesota. It is hosted on GitHub Pages. There are no external dependencies except a Google Fonts import. No JavaScript, no build step, no frameworks.

The user is Matthew. He is an N scale model railroader working on this layout design. He is knowledgeable about DCC systems (Digitrax), prototype railroad operations, and model railroad construction.

---

## Document Structure

The document is organized into sections separated by HTML comment markers. The order is:

```
<!-- ==================== COVER PAGE ==================== -->
<!-- ==================== VERSION HISTORY ==================== -->
<!-- ==================== WIP ROADMAP ==================== -->
<!-- ==================== HISTORY PAGE ==================== -->
<!-- ==================== PAGE 1: SCHEMATIC ==================== -->
  (includes Pages 1A, 1B, 1C with detailed track plans)
<!-- ==================== PAGE 2: CAR TYPES ==================== -->
<!-- ==================== PAGE 3: OPERATIONS ==================== -->
<!-- ==================== PAGE 4: BUILD PLAN ==================== -->
<!-- ==================== PAGE 5: LOCOMOTIVE & ROLLING STOCK ROSTER ==================== -->
<!-- ==================== FOOTER ==================== -->
```

Each section is wrapped in a `<div class="container">` with a `.page-header` containing an `<h1>` and `.page-badge`. The cover page uses a special `.cover` class instead.

---

## Version Management

**CRITICAL: Every edit to this document MUST include a version bump.**

1. **Bump the version number** in three places:
   - Cover page: `<div class="cover-rev">Version X.X — Month Year</div>`
   - Page 1 subtitle: `<div class="subtitle">Prototype-based N Scale Modular Layout — vX.X</div>`
   - Footer: `<div>Prototype-based N Scale Layout Design — Version X.X</div>`

2. **Add a changelog entry** to the VERSION HISTORY section. New entries go at the TOP (newest first). Use this template:

```html
<div class="train-card freight" style="padding:16px 20px">
  <div style="display:flex;align-items:baseline;gap:14px;margin-bottom:8px">
    <div style="font-size:14px;font-weight:700;color:#4895ef;font-family:'JetBrains Mono',monospace;flex-shrink:0">vX.X</div>
    <div style="font-size:11px;color:#5a6a8a;font-family:'JetBrains Mono',monospace">Month Day, Year</div>
  </div>
  <div style="font-size:11px;color:#8899bb;font-family:'JetBrains Mono',monospace;line-height:1.7">
    <strong style="color:#f0f0f0">Short title.</strong> Description of what changed.
  </div>
</div>
```

3. **Update the WIP ROADMAP** if the edit completes a planned item — move it from the Planned section to Complete (change the icon to ✅, add `opacity:0.6` to the card style, change the card class to `local`).

4. Version numbering: increment the minor version (0.1 → 0.2 → 0.3, etc.) for each update.

---

## Color Palette

The document uses a consistent dark theme with semantic colors tied to railroad/location types:

### Background & Surface
| Color | Hex | Usage |
|-------|-----|-------|
| Body background | `#1a1a2e` | Page background |
| Container background | `#16213e` | Card/section backgrounds |
| Border | `#2a3a5c` | All borders, dividers |
| Inner card background | `#1a1a2e` | Track plans, notes boxes |

### Text
| Color | Hex | Usage |
|-------|-----|-------|
| Primary text | `#f0f0f0` | Headings, titles, strong emphasis |
| Secondary text | `#e0e0e0` | Body text |
| Tertiary text | `#8899bb` | Descriptions, secondary info |
| Muted text | `#6a7a9a` | Notes, captions, subtle labels |
| Dim text | `#5a6a8a` | Subtitles, metadata |
| Very dim text | `#3a4a6c` | SVG annotations, context labels |
| Badge/label text | `#7a8bb5` | Page badges, section headers |

### Semantic / Railroad Colors
| Color | Hex | CSS Class | Usage |
|-------|-----|-----------|-------|
| Red | `#e63946` | `.division` | Division points (Northtown), Amtrak/passenger |
| Orange | `#f4a261` | `.junction` | Junctions (Proctor), DM&IR indicators, warnings |
| Blue | `#4895ef` | `.town` | Towns, BNSF mainline, freight trains |
| Light blue | `#70a8ef` | — | Bypass track, secondary BNSF lines |
| Teal | `#2a9d8f` | `.branch` | Branch lines (Cloquet) |
| Purple | `#c77dff` | `.terminal` | Terminals (Rices Point, Ore Docks) |
| Gold | `#e9c46a` | — | DM&IR railroad, ore operations |
| Gray | `#888` | `.staging` | Hidden staging modules |

These colors are used consistently across ALL elements — SVG track plans, cards, dots, badges, borders, and text. When adding new content, match the location type to its color.

---

## Typography

Two fonts are used throughout:

- **DM Sans** (`font-family: 'DM Sans', sans-serif`) — Body text, headings, prose content
- **JetBrains Mono** (`font-family: 'JetBrains Mono', monospace`) — Technical labels, badges, subtitles, notes, SVG text, car tags, all monospaced content

Imported via: `@import url('https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;700&family=JetBrains+Mono:wght@400;500&display=swap');`

### Font Size Guide
| Size | Usage |
|------|-------|
| 22px | Page h1 titles |
| 16px | Track plan names (`.tp-name`) |
| 15px | Train card names |
| 14px | Section headings within pages |
| 13px | Page subtitles |
| 12px | Section subheadings, step location names |
| 11-11.5px | Body text, descriptions, notes |
| 10-10.5px | Badges, car tags, legend items |
| 9-9.5px | SVG module labels, small annotations |
| 7-8px | SVG track labels, direction arrows |
| 6-6.5px | SVG detail labels (AR1, BXP88 markers) |

---

## Key CSS Components

### Page Structure
```html
<div class="container">
  <div class="page-header">
    <h1>PAGE TITLE</h1>
    <div class="page-badge">PAGE X — DESCRIPTION</div>
  </div>
  <div class="subtitle">Descriptive subtitle text</div>
  <!-- content -->
</div>
```

### Track Plans
```html
<div class="track-plan">
  <div class="tp-header">
    <div class="tp-dot town"></div>          <!-- color dot: division/junction/town/branch/terminal/staging -->
    <div class="tp-name">Location Name</div>
    <div class="tp-type town">Type — dimensions</div>  <!-- same class as dot -->
  </div>
  <div class="tp-subtitle">MP and prototype description</div>
  <svg viewBox="0 0 1200 XXX" xmlns="http://www.w3.org/2000/svg">
    <!-- track plan SVG content -->
  </svg>
  <div class="tp-notes">
    <strong>Label:</strong> Description text...
  </div>
</div>
```

### Train Cards (used for operations, build plan, changelog)
```html
<div class="train-card freight">  <!-- freight/unit/local/ore/passenger -->
  <div class="train-header">
    <div class="train-icon">🚂</div>
    <div class="train-name">Card Title</div>
    <div class="train-badge">BADGE TEXT</div>
  </div>
  <div class="train-subtitle">Subtitle text</div>
  <div class="consist-note">
    Body content...
  </div>
</div>
```

### Location Cards (Page 2 traffic reference)
```html
<div class="location-card town">  <!-- division/junction/town/branch/terminal/staging -->
  <div class="card-header">
    <div class="card-dot"></div>
    <div class="card-title">Location Name</div>
    <div class="card-type">TYPE</div>
  </div>
  <div class="card-desc">Description</div>
  <div class="traffic-section">
    <div class="traffic-label">INBOUND</div>
    <div class="car-list">
      <div class="car-tag">🛢️ Tank Cars <span class="car-detail">(propane, LP gas)</span></div>
    </div>
  </div>
</div>
```

### Notes Boxes
```html
<div class="tp-notes">
  <strong>Bold label:</strong> Regular description text...
</div>
```

---

## SVG Track Plan Conventions

All track plan SVGs use these conventions:

### Standard ViewBox
- Most modules: `viewBox="0 0 1200 XXX"` where XXX varies by complexity (180-360)
- Direction labels at top: `← To [location] (direction)` left side, `To [location] (direction) →` right side

### Track Colors in SVGs
| Element | Stroke Color | Width |
|---------|-------------|-------|
| BNSF mainline | `#4895ef` | 3.5 |
| Passing siding | `#70a8ef` | 2 |
| Industry spur | `#4895ef` opacity 0.5 | 1.5 |
| Branch line | `#2a9d8f` | 2.5 |
| DM&IR track | `#e9c46a` | 2.5 |
| Hidden/staging | `#888` | 2, dashed |
| Storage tracks | `#8899bb` | 1.5 |
| Turnout diverge | Same as parent | 1.5-2 |

### Standard SVG Elements
- **Turnout number marker**: `<circle r="6" fill="#2a3a5c" stroke="#4895ef"/>` with `<text font-size="6">#N</text>`
- **Industry building**: `<rect rx="2" fill="#2a3a5c" stroke="#3a4a6c"/>`
- **Industry label**: `font-size="7" fill="#5a6a8a"` for name, `font-size="6" fill="#4a5a7a"` for car count
- **Bumper (end of track)**: `<circle r="2.5" fill="#e63946"/>`
- **AR1 auto-reverser**: `<rect fill="#2a3a5c" stroke="#f4a261"/>` with text label
- **BXP88 detection**: `<circle r="4" fill="#f4a261" opacity="0.6"/>`
- **Direction arrows**: `font-size="7"` with `→` or `←` characters
- **Depot/station**: `<rect fill="#2a3a5c" stroke="#f4a261"/>` (orange border for depot)

### Y-Axis Track Spacing
- Mainline: typically `y=60` (or `y=35` for first of double track)
- Passing siding: mainline + 25 (e.g., `y=85`)
- Spurs: siding + 25-30
- Each additional parallel track: +18 to +25

---

## Layout Statistics (keep updated)

When editing track plans or adding modules, keep these counts accurate:

- **Turnout totals** appear in:
  - Cover page: `#6 Turnouts (~XX total)`
  - Page 1 sizing notes: full breakdown by module with total
  - Build plan: per-module turnout counts in subtitles
  - Roadmap: BOM description references turnout count
  - OG meta description (in `<head>`)

- **Module count** appears in:
  - Cover page: `Modular — 9 Scenes + Staging`
  - Various prose descriptions
  - Build plan module sequence

- **Current totals** (as of v0.3):
  - Modules: 12 (9 scenic + 2 reverse loop + 1 hidden staging)
  - Turnouts: ~96
  - Locomotives recommended: 15-18
  - Freight cars recommended: 80-100
  - Total rolling stock: ~105-130

---

## Adding a New Track Plan Module

1. Find the correct insertion point in the Page 1 section (modules are ordered geographically: Northtown → Cambridge → Hinckley → Moose Lake → Carlton → Cloquet → Proctor → Rices Point → Ore Docks)
2. Use the track plan template from the CSS Components section above
3. Match the location type class (town, junction, division, etc.) to the semantic color
4. SVG viewBox width is always 1200; adjust height to fit content
5. Include direction labels at top of SVG
6. Number all turnouts sequentially within the module
7. Add industry buildings as labeled rectangles
8. Include a `<div class="tp-notes">` with Purpose, Track, Industries, and any special wiring notes
9. Update the turnout count in ALL locations listed above
10. Update the build plan (Page 4) if the new module affects build sequence
11. Bump the version and add a changelog entry

---

## Adding a Changelog Entry

When making ANY edit:

1. Add new entry at the TOP of the version history entries (inside the `<div style="margin-top:24px;display:flex;flex-direction:column;gap:12px">` container)
2. Use the changelog card template from the Version Management section
3. Write a short bold title + description of what changed
4. Include any count changes (turnouts, modules, etc.) in the description
5. Bump version in cover page, Page 1 subtitle, and footer

---

## File Outputs

When done editing, always:

1. Save the working copy as `/home/claude/hinckley-sub.html`
2. Copy to `/home/claude/index.html` (identical — this is what GitHub Pages serves)
3. Copy both to `/mnt/user-data/outputs/` so the user can download them
4. Present the file using the `present_files` tool

```bash
cp /home/claude/hinckley-sub.html /home/claude/index.html
cp /home/claude/index.html /mnt/user-data/outputs/index.html
cp /home/claude/hinckley-sub.html /mnt/user-data/outputs/hinckley-sub.html
```

---

## Repository Files

The GitHub repo (`hinckleysub.com` or similar) contains:

| File | Purpose |
|------|---------|
| `index.html` | The layout document (identical to hinckley-sub.html) |
| `hinckley-sub.html` | Named copy of the document |
| `README.md` | GitHub repo landing page |
| `LICENSE` | CC0 1.0 Universal (public domain) |
| `CNAME` | Custom domain config (`hinckleysub.com`) |
| `CLAUDE.md` | This file — instructions for Claude sessions |

---

## Things to Watch For

- **Single file**: Everything is inline — CSS, SVGs, all content. No external files except the Google Fonts import. Keep it this way.
- **Print styles**: There is a `@media print` block in the CSS. If adding new colored elements, ensure they have print-friendly alternatives.
- **Turnout count consistency**: The total appears in 5+ places. Use `grep -n "~XX turnout"` to find all references when updating.
- **Version consistency**: The version string appears in 3 places (cover, Page 1, footer). Always update all three.
- **SVG coordinate consistency**: When modifying track plans, check that labels don't overlap tracks. Test by viewing the rendered HTML.
- **Module interconnections**: Track plans should show connection labels (e.g., "← To Northtown" / "To Hinckley →") that match the adjacent modules.
- **Color consistency**: Always use the semantic color for the location type. Northtown is always red (#e63946), Proctor is always orange (#f4a261), etc.
