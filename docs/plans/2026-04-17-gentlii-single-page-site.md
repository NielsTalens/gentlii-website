# Gentlii Single Page Site Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Build a single-page static HTML site in `gentlii-website/index.html` using the content from `gentlii-website.md`, with a centered hero, left-aligned remaining sections, a `#071423` background, and `#1186b8ff` accent styling around the provided logo.

**Architecture:** Use one self-contained HTML document with embedded CSS and semantic sections. Treat the first markdown heading and introduction as a centered hero, then render each remaining top-level markdown section as a left-aligned content block with large, bold headings and clean readable spacing.

**Tech Stack:** HTML5, embedded CSS

---

### Task 1: Plan The Static Page Check

**Files:**
- Create: `gentlii-website/docs/plans/2026-04-17-gentlii-single-page-site.md`
- Test: `gentlii-website/index.html`

**Step 1: Write the failing test**

Use shell checks that require `gentlii-website/index.html` to exist and contain:
- `background: #071423`
- `logo.png`
- `text-align: center`
- `text-align: left`
- `Gentlii product thinking suite`

**Step 2: Run test to verify it fails**

Run: `test -f gentlii-website/index.html && rg -n "background: #071423|logo.png|text-align: center|text-align: left|Gentlii product thinking suite" gentlii-website/index.html`

Expected: FAIL because `gentlii-website/index.html` does not exist yet.

### Task 2: Build The Page

**Files:**
- Create: `gentlii-website/index.html`
- Read: `gentlii-website/gentlii-website.md`
- Read: `gentlii-website/logo.png`

**Step 1: Write minimal implementation**

Create a single HTML page that:
- references `logo.png`
- sets the page background to `#071423`
- uses `#1186b8ff` as the accent color
- centers the logo, main title, intro paragraphs, and suite list in the first section
- renders the remaining sections left-aligned
- uses large bold heading styles for all headers

**Step 2: Run test to verify it passes**

Run: `test -f gentlii-website/index.html && rg -n "background: #071423|logo.png|text-align: center|text-align: left|Gentlii product thinking suite" gentlii-website/index.html`

Expected: PASS with matching lines from `gentlii-website/index.html`.

### Task 3: Verify Final Output

**Files:**
- Test: `gentlii-website/index.html`

**Step 1: Run a broader verification**

Run: `python - <<'PY'\nfrom pathlib import Path\nhtml = Path('gentlii-website/index.html').read_text()\nchecks = [\n    'Gentlii Foundations',\n    'Gentlii Product Guard',\n    'Gentlii Feature Validator',\n    '#071423',\n    '#1186b8ff',\n    'logo.png'\n]\nmissing = [item for item in checks if item not in html]\nprint('missing=' + ','.join(missing) if missing else 'ok')\nPY`

Expected: `ok`
