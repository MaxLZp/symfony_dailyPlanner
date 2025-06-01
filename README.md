# Project Name (suggested): *FocusForge* – Daily Planner & Goal Tracker

## Core Concepts

* **Goals**: Long-term or short-term outcomes the user wants to achieve.
* **Tasks**: Concrete actions assigned to days and optionally linked to goals.
* **Daily Plans**: A list of tasks planned for each day.
* **Categories**: Domains of life (Health, Work, Learning, Finance, etc.)
* **Progress**: % of completed tasks toward goals or daily plans.
* **Reflections**: Short end-of-day entries to encourage review and learning.

---

## **MVP Features (Phase 1)**

### 1. **User Registration and Login**

* Standard Symfony security.
* Password hashing, login throttling.
* Optionally: Social login (Google, GitHub) via OAuth (HWIOAuthBundle).

### 2. **Goal Management**

* Create/Edit/Delete goals.
* Set goal type (daily, weekly, long-term).
* Define categories (health, work, learning…).
* Define metrics (e.g., number of hours, # of repetitions).

### 3. **Task Management**

* Create/Edit/Delete tasks.
* Assign tasks to a specific date and optionally to a goal.
* Add priority, time estimate, and tags.
* Task recurrence (daily, weekly) – optional.

### 4. **Daily Plan**

* View a dashboard of today’s tasks.
* Drag & drop (if using a frontend component like FullCalendar or Vue).
* Mark task as complete or postponed.
* Auto-recommend overdue tasks from previous days.

### 5. **Progress Tracking**

* Daily progress (how many tasks completed today).
* Goal progress (task completions toward goal).
* Timeline view (past days/weeks).

---

## **Advanced Features (Phase 2)**

### 6. **Goal Templates**

* Create reusable goal structures with predefined tasks.
* Useful for things like “Learn 500 Czech words”, “Get fit in 30 days”.

### 7. **Weekly Planning Board**

* View and manage tasks across an entire week.
* Plan in batches (e.g., Sunday for the whole week).

### 8. **Reminders & Notifications**

* Schedule email or browser reminders (Symfony Messenger + Mailer).
* Remind users about incomplete goals at the end of the week.

### 9. **Reflection Journal**

* Let users write a short daily reflection: “What went well?”, “What to improve?”
* Markdown or WYSIWYG input.
* Export to PDF or Markdown.

### 10. **Analytics & Charts**

* Stats: completion rate per week/month.
* Pie charts for domain distribution (health vs. work tasks).
* Burn-down charts for long-term goals.

---

## **Tech Opportunities**

| Symfony Feature          | How It's Used                                                    |
| ------------------------ | ---------------------------------------------------------------- |
| **Forms**                | Task creation, goal editing, recurrence rules.                   |
| **Validation**           | Custom validators for time overlaps, goal deadlines, etc.        |
| **Doctrine**             | Entity relations: User → Goals → Tasks. Custom DQL queries.      |
| **Event Listeners**      | On task completion, trigger goal progress update.                |
| **Messenger Component**  | Schedule reminders, email digests.                               |
| **Security**             | User roles (admin vs. user), password hashing, token-based APIs. |
| **API Platform or REST** | Mobile or frontend API for tasks/goals.                          |
| **Workflow Component**   | Model task states: `open → in_progress → done → verified`.       |
| **Twig + Stimulus (UX)** | Live interactions (marking complete, toggling filters, etc.).    |
| **Scheduler Component**  | Symfony 6.3+ to schedule recurring tasks and reminders.          |

---

## Nice-to-Have Additions (Phase 3)

* **Mobile App Integration** via REST or GraphQL.
* **Dark mode UI** using Tailwind.
* **CSV/JSON Export** of tasks and reflections.
* **Time-block planner**: visually allocate blocks of time to tasks.
* **AI Assistant**: Suggest tasks based on goals (can be a placeholder logic).

---

## Suggested Entities (simplified)

```php
User
- id
- email
- password

Goal
- id
- user_id
- title
- description
- category
- target_value (e.g., 100 hours)
- type (short_term, long_term, daily)
- deadline

Task
- id
- goal_id (nullable)
- user_id
- title
- date
- is_done
- priority
- estimated_minutes

DailyReflection
- id
- user_id
- date
- text

Reminder
- id
- task_id
- send_at
- was_sent
```

---

Would you like a full **database schema** or **project structure** (controllers, services, templates) for this idea?

Or do you want to use **API Platform** for a headless version + frontend?
