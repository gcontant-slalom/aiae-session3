# Product Requirements Document (PRD) - Todo App Upgrade

## 1. Overview

We are upgrading the basic Todo app to make it more practical for everyday task tracking without increasing product complexity. The current app is limited to a task title and completion state. This upgrade adds due dates, priority levels, and simple date-based filters so users can quickly identify urgent work while keeping the solution local-only and teachable.

---

## 2. MVP Scope

- Add an optional `dueDate` field to each task using ISO format `YYYY-MM-DD`.
- Add a `priority` field with allowed values `P1`, `P2`, and `P3`.
- Default `priority` to `P3` when no value is provided.
- Add filter views for `All`, `Today`, and `Overdue`.
- Keep storage local only with no backend or external storage changes.
- Require `title` for each task.
- Treat invalid `dueDate` values as absent instead of storing invalid data.
- Show completed and incomplete tasks in the `All` view.
- Show only incomplete tasks in the `Today` view.
- Show only incomplete tasks in the `Overdue` view.

---

## 3. Post-MVP Scope

- Visually highlight overdue tasks so they stand out.
- Add sorting in this order: overdue tasks first, then priority from `P1` to `P3`, then due date ascending, with undated tasks last.
- Add color-coded priority badges with red for `P1`, orange for `P2`, and gray for `P3`.

---

## 4. Out of Scope

- Notifications.
- Recurring tasks.
- Multi-user support.
- Keyboard navigation enhancements.
- External storage or sync.
- Backend changes.
- Additional accessibility features beyond the app's current baseline.