# Gentlii Transparent Header Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Make the sticky header transparent while keeping the bottom border and current layout behavior.

**Architecture:** Keep the header markup and spacing unchanged. Update only the embedded CSS for the header surface so the fill becomes transparent while the border remains.

**Tech Stack:** HTML5, embedded CSS

---

### Task 1: Add A Failing Style Check

**Files:**
- Test: `index.html`

**Step 1: Write the failing test**

Use a shell check that confirms the current opaque header background is still present before removal.

**Step 2: Run test to verify current state**

Run: `test -f index.html && rg -n 'background: rgba\\(8, 28, 46, 0\\.9\\);|border-bottom: 1px solid var\\(--border\\);|backdrop-filter: blur\\(18px\\);' index.html`

Expected: PASS because the opaque background is still in the file.

### Task 2: Make The Header Transparent

**Files:**
- Modify: `index.html`

**Step 1: Write minimal implementation**

Update the header CSS to:
- replace the opaque header background with `transparent`
- keep the bottom border
- remove the blur effect since there is no longer a filled surface

**Step 2: Run test to verify the new state**

Run: `test -f index.html && rg -n 'background: transparent;|border-bottom: 1px solid var\\(--border\\);' index.html && ! rg -n 'background: rgba\\(8, 28, 46, 0\\.9\\);|backdrop-filter: blur\\(18px\\);' index.html`

Expected: PASS
