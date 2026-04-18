# Gentlii Header Text Links Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Remove the button styling from the header navigation and keep only text-only links with hover and focus emphasis.

**Architecture:** Keep the current header markup unchanged. Update only the embedded CSS for `.header-nav a` and its interactive state so the links render as plain text without borders or background fills.

**Tech Stack:** HTML5, embedded CSS

---

### Task 1: Add A Failing Style Check

**Files:**
- Test: `index.html`

**Step 1: Write the failing test**

Use a shell check that expects the old pill styles to be absent after the change.

**Step 2: Run test to verify current state fails the desired outcome**

Run: `test -f index.html && rg -n 'border-radius: 999px;|border: 1px solid rgba\\(17, 134, 184, 0\\.18\\);|background: var\\(--accent-soft\\);' index.html`

Expected: PASS now, which confirms the old button-like styles still exist and need removal.

### Task 2: Simplify Header Link Styling

**Files:**
- Modify: `index.html`

**Step 1: Write minimal implementation**

Update the header link CSS to:
- remove border radius
- remove border
- remove hover background
- keep text-only presentation with a color shift on hover/focus

**Step 2: Run test to verify button styles are gone**

Run: `test -f index.html && ! rg -n 'border-radius: 999px;|border: 1px solid rgba\\(17, 134, 184, 0\\.18\\);|background: var\\(--accent-soft\\);' index.html`

Expected: PASS

### Task 3: Verify Final Output

**Files:**
- Test: `index.html`

**Step 1: Run a broader verification**

Run: `rg -n 'header-nav a|color: var\\(--muted\\);|color: var\\(--text\\);' index.html`

Expected: PASS with the text-only link rules still present.
