# Foundations Diagram Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Redesign `foundations.svg` into a flat document-flow illustration with a central Gentlii Foundations application screen.

**Architecture:** Replace the current primitive rectangles and solid connectors with structured SVG groups for input documents, a central application window, and organized output documents. Preserve a single standalone SVG file and verify the result with targeted content checks against the edited markup.

**Tech Stack:** SVG markup, Inkscape-compatible XML

---

### Task 1: Add a regression check for the new diagram structure

**Files:**
- Modify: `foundations.svg`
- Verify: `foundations.svg`

**Step 1: Write the failing test**

Define the required diagram markers to check after implementation:

- `Gentlii Foundations`
- `Brief`
- `Notes`
- `Research`
- `Email`
- `Jobs To Be Done`
- `stroke-dasharray`

**Step 2: Run test to verify it fails**

Run: `rg -n "Brief|Notes|Research|Jobs To Be Done|stroke-dasharray" foundations.svg`
Expected: missing matches for the new labels and dotted stroke markers in the current file.

**Step 3: Write minimal implementation**

Update the SVG so those labels and dotted connector styles exist in the file.

**Step 4: Run test to verify it passes**

Run: `rg -n "Brief|Notes|Research|Jobs To Be Done|stroke-dasharray" foundations.svg`
Expected: all required markers are present.

### Task 2: Replace the central block with an application screen

**Files:**
- Modify: `foundations.svg`

**Step 1: Implement the application window**

Replace the current center rectangle with:

- window frame
- title bar
- terminal / application content rows
- clear `Gentlii Foundations` label

**Step 2: Verify the center reads as software**

Run: `sed -n '1,260p' foundations.svg`
Expected: grouped window markup with multiple shapes instead of a single central block.

### Task 3: Redesign left and right document groups and dotted flows

**Files:**
- Modify: `foundations.svg`

**Step 1: Implement the left input documents**

Create four smaller flat document cards labeled:

- `Brief`
- `Notes`
- `Research`
- `Email`

Add a few duplicate offset papers behind the visible cards to suggest loose, unorganized source material while keeping the front labels readable.

**Step 2: Implement the right output cards**

Create five neatly aligned rounded output cards labeled:

- `Strategy`
- `Business Case`
- `Product Vision`
- `Jobs To Be Done`
- `Product Charter`

Make them visually closer to the central application's `Organizing` panel than to file documents.

**Step 3: Soften left document lines and implement dotted information flow**

Increase the weight of the internal input-document lines and shift them to a softer blue-gray. Add four dotted incoming paths from the left documents to the intake circle, and one dotted outbound path with an arrow from the application toward the right-side cards.

**Step 4: Verify the SVG structure**

Run: `rg -n "Brief|Notes|Research|Email|Strategy|Business Case|Product Vision|Jobs To Be Done|Product Charter|stroke-dasharray" foundations.svg`
Expected: all labels and dotted-line styling are present.
