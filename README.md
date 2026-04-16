# 🧩 Advanced Todo Card — Stage 1a

## 📌 Overview

This project builds upon the **Stage 0 Todo Card** by transforming it from a static, testable component into a more **interactive, stateful, and app-like UI component** using only **HTML, CSS, and JavaScript**.

The focus of this stage is to introduce:

* Editable state
* Synchronized UI behavior
* Improved accessibility patterns
* More dynamic time handling
* Better user interaction flows

---

## 🚀 What Changed from Stage 0

### 1. ✏️ Edit Mode (New)

* Users can now edit:

  * Title
  * Description
  * Priority
  * Due date
* Introduced a full edit form with:

  * `test-todo-edit-form`
  * Inputs for all editable fields
  * Save & Cancel functionality
* View mode and edit mode now **switch cleanly** (content hidden when editing)

---

### 2. 🔄 Status Control (Improved)

* Added a **status dropdown control** (`test-todo-status-control`)
* Status is now fully interactive:

  * Pending
  * In Progress
  * Done
* Synced behavior:

  * Checkbox ↔ Status dropdown ↔ Status badge

---

### 3. 🎯 Priority Indicator (Enhanced)

* Added visual indicator (`test-todo-priority-indicator`)
* Priority now affects:

  * Card border accent
  * Badge color
  * Indicator dot

---

### 4. 📖 Expand / Collapse Description

* Long descriptions are **collapsed by default**
* Expand toggle added (`test-todo-expand-toggle`)
* Accessible with:

  * `aria-expanded`
  * `aria-controls`

---

### 5. ⏱️ Time Management Improvements

* Time updates every **30 seconds**
* More granular display:

  * Minutes, hours, days
* Added:

  * `test-todo-overdue-indicator`
* Behavior:

  * Overdue → red styling + indicator
  * Completed → stops timer and shows `"Completed"`

---

### 6. 🎨 Visual State Enhancements

* **Done**

  * Strike-through title
  * Muted appearance
* **Overdue**

  * Red time text
  * Visible badge
* **In Progress**

  * Distinct styling
* **High Priority**

  * Strong visual emphasis

---

## 🎨 New Design Decisions

### 1. State-Driven UI (Centralized State Object)

All task data is managed in a single `state` object:

```js
{
  title,
  description,
  priority,
  status,
  dueDate,
  isExpanded,
  isEditing
}
```

This ensures consistent updates across UI elements.

---

### 2. View vs Edit Mode Separation

Instead of mixing UI:

* View elements are hidden during edit mode
* Edit form is shown exclusively

This simplifies:

* Logic
* Accessibility
* Visual clarity

---

### 3. CSS-Based Visual States

Used class toggles instead of inline styles:

* `.is-overdue`
* `.is-completed`
* `.priority-*`
* `.status-*`

This keeps styling scalable and maintainable.

---

### 4. Progressive Enhancement

* Works fully without frameworks
* Uses semantic HTML first
* Enhances with JavaScript behavior

---

### 5. Controlled Time Updates

* Uses `setInterval` (30s)
* Stops updates when task is `"Done"`
* Prevents unnecessary computation

---

## ⚠️ Known Limitations

* ❌ Single Todo Card only (not a full app)
* ❌ No persistence (refresh resets state)
* ❌ No animations for transitions (could be improved)
* ❌ Expand logic is based on text length, not dynamic height
* ❌ No validation beyond basic required fields
* ❌ No timezone handling (uses local browser time)

---

## ♿ Accessibility Notes

### ✅ Semantic HTML

* `<article>` used for card
* `<time>` used for due date
* `<label>` properly connected to inputs
* `<button>` used for all actions

---

### ✅ Keyboard Accessibility

Tab order:

1. Checkbox
2. Status dropdown
3. Expand toggle
4. Edit
5. Delete
6. Edit form fields (when active)

Also includes:

* Focus trapping inside edit form
* Escape key closes edit mode

---

### ✅ Screen Reader Support

* `aria-label` used where needed
* `aria-live="polite"` for time updates
* Expand toggle uses:

  * `aria-expanded`
  * `aria-controls`

---

### ✅ Visual Accessibility

* High contrast colors (WCAG-friendly)
* Visible focus states
* No reliance on color alone (badges + text labels)

---

### ⚠️ Minor Accessibility Gaps

* No announcement when switching modes (could add `aria-live`)
* Expand/collapse animation not communicated to assistive tech
* Status changes are not explicitly announced

---

## 🧪 Testing Notes

* All **Stage 0 test IDs remain intact**
* All **Stage 1a test IDs added and functional**
* Fully keyboard navigable
* Responsive from **320px → 1200px**
* No horizontal overflow

---

## 🏁 Summary

Stage 1a transforms the Todo Card from a static component into a **fully interactive, accessible, and state-driven UI component**, while maintaining:

* Clean structure
* Testability
* Responsiveness

This sets a solid foundation for scaling into a full Todo application in future stages.
