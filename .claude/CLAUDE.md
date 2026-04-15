# Flat Cut Builder
> A single-page product configuration form for "Flat Cut" signage — lets sales/vendor teams configure custom flat-cut signs (shape, dimensions, material, finishing, mounting) and export a PDF quote.
> Initialized: 2026-04-15

## Stack
- **Frontend**: Pure HTML5 + CSS3 + Vanilla JavaScript (ES6+) — no framework, no build system
- **Styling**: Inline CSS with CSS custom properties (`--color-*`, `--radius-*`, `--shadow-*` tokens)
- **Fonts**: Google Fonts CDN — Space Grotesk (headings) + Inter (body)
- **PDF export**: html2pdf.js v0.10.1 via cdnjs CDN
- **Persistence**: `localStorage` only (no backend, no database)
- **Dev server**: Python `http.server` (port 8080) or `npx serve` (port 3000) — both configured in `.claude/launch.json`
- **TypeScript**: None
- **Tests**: None
- **Deployment**: Static file hosting (no build step required)

## Project structure
```
Flat Cut Builder/
├── index.html                        # Entire application (HTML + CSS + JS, single file)
├── .claude/
│   ├── CLAUDE.md                     # This file
│   ├── launch.json                   # Dev server launch configs
│   └── settings.local.json           # Allowed bash permissions
├── FLAT_CUT_FINAL_SPECIFICATION.md   # Full technical product spec
├── FLAT_CUT_QUICK_REFERENCE.md       # Sales desk quick-lookup
├── FLAT_CUT_VENDOR_QUICK_CARD.md     # Ultra-concise vendor card
├── FLAT_CUT_DECISION_TREES.md        # Visual decision flow
├── FLAT_CUT_FORM_DOCUMENTATION.md    # Form design documentation
├── README_FLAT_CUT.md                # Vendor workflow overview
├── CAMBIOS_FINALES_V2.md             # Changelog for final v2 changes
├── RESUMEN_COMPACTO.md               # Compact summary
├── ENTREGA_FLAT_CUT_COMPLETA.md      # Delivery checklist
├── PRODUCTO_ROADMAP.md               # Roadmap for future products (Decal, 3D Letters, etc.)
├── FLAT_CUT_FORM_v5_STABLE.html      # Old version — archived
├── FLAT_CUT_FORM_v8_ok.html          # Old version — archived
└── FLAT_CUT_FORM_v9_stable.html      # Old version — archived
```

## Commands
```bash
# Development (Python — port 8080)
python -m http.server 8080

# Development (Node — port 3000)
npx serve . -p 3000 --no-clipboard

# Build
# None required — index.html is the deployable artifact

# Tests
# No tests configured

# Typecheck
# No TypeScript — N/A

# Lint
# No linter configured
```

## Conventions
- **Single-file architecture**: All HTML, CSS, and JS live in `index.html`. This is intentional for portability (no toolchain needed).
- **Inline CSS**: All styles are in a `<style>` block in `<head>`. CSS custom properties define the design tokens.
- **Inline JS**: All JavaScript is in a `<script>` block at the bottom of `<body>`.
- **No modules**: Everything is global scope. No `import`/`export`.
- **Class naming**: BEM-like: `.form-section`, `.button-group`, `.button-option`, `.text-line-item`, `.control-group`.
- **Bug fix comments**: Changes are annotated with `// [FIX #N]` comments referencing the fix number (e.g. `// [FIX #1]`).
- **No default exports / no named exports**: N/A — no module system.
- **No error handling on happy paths**: Validation is only done at user input boundaries.

## Key files
| File | Purpose |
|------|---------|
| `index.html` | The entire app — form, CSS, and all JavaScript logic |
| `FLAT_CUT_FINAL_SPECIFICATION.md` | Authoritative product spec (materials, thicknesses, constraints) |
| `FLAT_CUT_QUICK_REFERENCE.md` | Quick lookup for sales team |
| `FLAT_CUT_VENDOR_QUICK_CARD.md` | Ultra-concise card for reps |
| `PRODUCTO_ROADMAP.md` | Planned next products (Decal, 3D Letters, Edge Glow, etc.) |
| `.claude/launch.json` | Dev server launch configurations |

## Environment variables
None. Fully static application — no secrets, no env config.

## Architecture notes

### Form flow (8 steps)
```
1. Shape      → Panel | Custom Shape | Letters
2. Dimensions → W × H mm (max 1200×2400) — or canvas size for Letters mode
3. Material   → ACM 3mm | Back Black ACM 3mm | Acrylic 3-10mm | Acrylic 10-20mm | PVC 10-30mm
4. Location   → Interior | Exterior
5. Finishing  → Raw | UV Print + Laminate | UV Print + Clear Coat | Vinyl Wrap + Laminate
               (options filtered by material via `materialFinishing` lookup table)
6. Finish Type → Matte | Gloss (only shown when Laminate or Clear Coat is selected)
7. Mounting   → Adhesive Backing | Pre-drilled Holes | Standoff | Railing
               (options filtered by material via `materialMounting` lookup table)
8. Notes      → Free text (font, rush, orientation, custom requests)
```

### Key data structures
- **`materialFinishing`** (JS object): maps material → available finishing options
- **`materialMounting`** (JS object): maps material → available mounting options
- **`TextLine` class**: manages individual letter lines (font, weight, size, condense, relPosX/Y)
- **`textLines[]`**: global array of `TextLine` instances for Letters mode
- **localStorage key**: `flatCutConfig` — stores full form state as JSON

### Validation rules
- Width or Height > 2400mm → hard error
- Both W and H > 1200mm (non-Letters) → error (max is 1200×2400)
- PVC + Exterior → warning (UV decolouration risk)
- Exterior + UV Print (Laminate or Clear Coat) → advisory (recommend Vinyl Wrap)

### Letters mode
When shape = Letters, the normal dimensions section hides and a canvas-based preview appears.
- Users add text lines, configure font/weight/size/condense per line or globally (sync toggle)
- Text lines are draggable on the preview canvas (mouse drag)
- Canvas dimensions (optional) show a boundary box

### PDF export
- Uses `html2pdf.js` CDN library
- Exports the `#flatCutForm` element as A4 PDF
- Filename: `flat-cut-config.pdf`

### Save/restore
- "Save Configuration" writes to `localStorage['flatCutConfig']`
- On `DOMContentLoaded`, `loadConfig()` restores previous session automatically
- Includes full `TextLine` state (relPosX/Y, condense)

## Rules
- Never hardcode secrets — use environment variables (N/A here, but applies to future backend)
- TypeScript strict: N/A (no TypeScript)
- Keep everything in `index.html` unless explicitly refactoring to multi-file
- When adding new materials, update BOTH `materialFinishing` and `materialMounting` lookup tables
- When adding new steps, update the `STEP_FIELDS` object and the `#progressStepper` HTML
- Mark all bug fixes with `// [FIX #N]` comments for traceability
- Archived versions (v5, v8, v9) should not be modified — they are reference copies only

## Handoff
When starting a session, check `.claude/handoffs/` for recent context from previous sessions.
If a handoff exists, read it before starting work.

## Agents available
Global agents: @architect, @senior-dev, @ui-builder, @code-reviewer, @qa-engineer, @git
Project agents: see `.claude/agents/` (empty at init — add project-specific agents here)

## What I don't know yet
- Pricing logic: The product spec mentions pricing but the form has no pricing calculations — unclear if this is intentional or planned
- Print/production system integration: The form generates a PDF but there's no API or submission endpoint — unclear how quotes reach production team
- Deployment target: No hosting config found — unknown where this is deployed (local only? internal server?)
- Font availability: Roboto, Futura, Gotham are listed as font options but not loaded via Google Fonts — they may fall back to system fonts
- Browser support requirements: No polyfills — assumed modern browsers only
