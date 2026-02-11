# SQL Editor — SQL Academy 101

A browser-based SQL editor for exploring the **SQL Academy 101** sample school-district database. Write queries, see results instantly, and export to CSV — no install required.

**[Launch the SQL Editor →](https://northwest-resa.github.io/sql_editor/)**

---

## Features

- **Live query execution** against a Supabase-hosted PostgreSQL database
- **SQL syntax highlighting** and **autocomplete** (tables + columns) via CodeMirror
- **Starter queries** organized by course module — click to load and run
- **Resizable split pane** — drag the divider between editor and results
- **CSV export** for any result set
- **Keyboard shortcuts** for fast workflow (see below)

## Usage

1. Open the editor using the link above (or serve `index.html` locally).
2. Type a SQL query in the top pane — `SELECT`, `JOIN`, aggregates, subqueries, etc.
3. Press **Ctrl+Enter** (or click **Run**) to execute.
4. View results in the bottom pane. Click **Export CSV** to download.

> **Tip:** Click the **Starters** button in the toolbar for pre-built example queries aligned to each course module.

## Database Schema

The database models a fictional school district with the following tables:

| Table | Description | Key Columns |
|---|---|---|
| `schools` | Schools in the district | `school_id`, `school_name`, `school_type`, `city`, `state` |
| `schoolyears` | Academic year definitions | `schoolyear_id`, `schoolyear_name`, `start_date`, `end_date` |
| `students` | Student records | `student_id`, `first_name`, `last_name`, `date_of_birth`, `gender` |
| `enrollments` | Student-school-year enrollment | `enrollment_id`, `student_id`, `school_id`, `schoolyear_id`, `grade_level` |
| `teachers` | Teacher records | `teacher_id`, `first_name`, `last_name`, `email`, `department` |
| `teacher_school` | Teacher-school assignments by year | `teacherschool_id`, `teacher_id`, `school_id`, `schoolyear_id` |
| `terms` | Terms/semesters within a school year | `term_id`, `school_id`, `schoolyear_id`, `term_name`, `term_start`, `term_end` |
| `courses` | Course catalog | `course_id`, `course_name`, `subject_name`, `discipline_name`, `credits` |
| `sections` | Scheduled class sections | `section_id`, `course_id`, `teacher_id`, `period`, `room_number` |
| `student_sections` | Student enrollment in sections | `studentsection_id`, `student_id`, `section_id`, `grade` |

> You can also explore the schema live:
> ```sql
> select table_name, table_type
> from information_schema.tables
> where table_schema = 'public'
> order by table_name;
> ```

## Keyboard Shortcuts

| Shortcut | Action |
|---|---|
| `Ctrl+Enter` | Run query |
| `Ctrl+Space` | Autocomplete |
| `Ctrl+Z` / `Ctrl+Shift+Z` | Undo / Redo |
| `Esc` | Close dialogs & drawers |
| `?` | Open shortcuts dialog |

> On macOS, use **Cmd** in place of **Ctrl**.

## Tech Stack

- **[Supabase](https://supabase.com/)** — PostgreSQL database hosting and query execution via `rpc`
- **[CodeMirror 5](https://codemirror.net/)** — In-browser code editor with SQL mode, Dracula theme, and autocomplete
- **Vanilla HTML/CSS/JS** — No build step, no framework; single-file deployment

## License

This project uses the following open-source libraries under the **MIT License**:

- **CodeMirror 5** — © Marijn Haverbeke and contributors
- **CodeMirror Dracula Theme** — © Dracula Theme
- **Supabase JavaScript Client** — © Supabase Inc.