# Gentlii Blurred Transparent Header Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Make the sticky header blur content behind it while keeping the header visually light and transparent.

**Architecture:** Keep the header markup and layout unchanged. Update only the embedded CSS to swap the fully transparent background for a very light translucent tint and reintroduce `backdrop-filter`.

**Tech Stack:** HTML5, embedded CSS

---

### Task 1: Add A Failing Style Check

**Files:**
- Test: `index.html`

**Step 1: Write the failing test**

Use a shell check that confirms the current fully transparent header is still present before the blur treatment is added.

**Step 2: Run test to verify current state**

Run: `test -f index.html && rg -n 'background: transparent;|border-bottom: 1px solid var\\(--border\\);' index.html`

Expected: PASS because the header is currently transparent.

### Task 2: Add Blur To The Header

**Files:**
- Modify: `index.html`

**Step 1: Write minimal implementation**

Update the header CSS to:
- replace the fully transparent background with a very light translucent tint
- add `backdrop-filter: blur(...)`
- keep the bottom border and existing spacing

**Step 2: Run test to verify the new state**

Run: `test -f index.html && rg -n 'background: rgba\\(7, 20, 35, 0\\.08\\);|backdrop-filter: blur\\(18px\\);|border-bottom: 1px solid var\\(--border\\);' index.html && ! rg -n 'background: transparent;' index.html`

Expected: PASS
