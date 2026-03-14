# Product Requirements Document - Todo App Upgrade

## 1. Summary

This document defines a lean upgrade to the Todo app so users can manage urgency without adding backend complexity. The MVP introduces due dates, priority levels, and date-based filters while keeping storage local and the implementation simple enough for a teachable bootcamp scope.

## 2. Problem Statement

The current Todo app is too limited for practical task management because tasks only capture a title and completion state. Users need a lightweight way to understand urgency, distinguish important work, and focus on tasks due today or already overdue.

## 3. Goals

- Help users identify urgent tasks by adding optional due dates.
- Help users classify task importance with a simple priority system.
- Let users quickly switch between all tasks, tasks due today, and overdue tasks.

## 4. MVP Scope

- Add an optional `dueDate` field to each task using ISO `YYYY-MM-DD` format.
- Add a `priority` field with allowed values `P1`, `P2`, and `P3`, defaulting to `P3`.
- Add filters for `All`, `Today`, and `Overdue`.
- Keep storage local only, with no backend or external storage changes.
- Allow the `All` filter to show completed and incomplete tasks.
- Limit the `Today` and `Overdue` filters to incomplete tasks only.

## 5. Post-MVP Scope

- Visually highlight overdue tasks so they stand out in the task list.
- Add sorting rules in this order: overdue first, then priority from `P1` to `P3`, then due date ascending, with undated tasks last.
- Add color-coded priority badges using red for `P1`, orange for `P2`, and gray for `P3`.

## 6. Out of Scope

- Notifications.
- Recurring tasks.
- Multi-user support.
- Keyboard navigation enhancements.
- Backend changes.
- External storage or synchronization.
- Additional accessibility work beyond the app's current baseline.

## 7. Functional Requirements

- The system must allow each task to store an optional due date.
- The system must allow each task to store a priority value of `P1`, `P2`, or `P3`.
- The system must provide `All`, `Today`, and `Overdue` filter views.
- The `Today` view must show only incomplete tasks with a due date equal to the current date.
- The `Overdue` view must show only incomplete tasks with a due date earlier than the current date.
- The `All` view must continue to show completed tasks.

## 8. Data Model And Validation

- `title` is required.
- `priority` must be one of `P1`, `P2`, or `P3` and defaults to `P3`.
- `dueDate` is optional and must use ISO date format `YYYY-MM-DD`.
- Invalid `dueDate` values must be ignored and treated as absent.

## 9. Constraints And Assumptions

- The MVP must remain simple and teachable.
- Storage remains local only.
- No backend work is allowed in this initiative.
- The existing app is being enhanced rather than replaced.

## 10. Open Questions

- Should the product standardize how the current date is determined for `Today` and `Overdue`, such as local browser date versus a normalized application date helper?
- Should priority badges ship visually with the post-MVP styling work, or should the MVP show priority as text only?

## 11. Acceptance Notes

- Stakeholders explicitly confirmed due dates, priorities, filters, and local-only storage as MVP scope.
- Stakeholders explicitly moved overdue highlighting and the sorting rules to Post-MVP.
- Invalid due date inputs should not block task usage; they should behave as if no due date was provided.

## 12. Source Artifacts

- `docs/artifacts/09162025-requirements-meeting.vtt`
- `docs/artifacts/09172025-slack-conversation-export.txt`