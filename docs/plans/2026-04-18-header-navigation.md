# Gentlii Header Navigation Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Add a sticky site header with the Gentlii logo, brand name, and in-page navigation links to the three suite modules.

**Architecture:** Keep the site as a single static HTML document. Add a header before the hero, give each module section an anchor ID, and extend the embedded CSS for sticky positioning and responsive wrapping.

**Tech Stack:** HTML5, embedded CSS

---

### Task 1: Add A Failing Navigation Check

**Files:**
- Test: `index.html`

**Step 1: Write the failing test**

Use a shell check that expects the header classes and section IDs to exist.

**Step 2: Run test to verify it fails**

Run: `test -f index.html && rg -n 'site-header|header-nav|id="foundations"|id="product-guard"|id="feature-validator"' index.html`

Expected: FAIL because the header markup and anchor IDs do not exist yet.

### Task 2: Implement Header Navigation

**Files:**
- Modify: `index.html`

**Step 1: Write minimal implementation**

Update `index.html` to:
- add a sticky header with `logo.png` and the `Gentlii` wordmark
- add three in-page links for the suite modules
- assign `id` attributes to the module sections
- extend CSS for header layout, hover states, and mobile wrapping

**Step 2: Run test to verify it passes**

Run: `test -f index.html && rg -n 'site-header|header-nav|id="foundations"|id="product-guard"|id="feature-validator"' index.html`

Expected: PASS with matching lines from `index.html`.

### Task 3: Verify Final Output

**Files:**
- Test: `index.html`

**Step 1: Run a broader verification**

Run: `rg -n 'Gentlii</span>|href="#foundations"|href="#product-guard"|href="#feature-validator"|position: sticky' index.html`

Expected: PASS with matches for the sticky header brand and all three links.
