# nagrs
nagrs is a Rust-based Telegram bot and reminder engine that helps you actually finish job search tasks. It doesn’t just notify — it waits for confirmation, asks follow-up questions, and keeps reminding you in a persistent “nag mode” until the task is done or consciously postponed.

# nagrs 🦀

**nagrs** is a Rust-based Telegram bot and reminder engine that helps you actually
finish job search tasks — not just plan them.

It doesn’t just notify.
It waits for confirmation, asks follow-up questions, and keeps reminding you
in a persistent *nag mode* until the task is done or consciously postponed.

---

## What problem does it solve?

Job searching is full of small but important actions:

- apply to a vacancy
- reply to a recruiter
- update a resume
- prepare for an interview
- finish a test assignment

Regular reminders are easy to ignore.
**nagrs** is built to prevent tasks from silently disappearing.

---

## Core idea

> A task is considered complete **only after explicit confirmation**.

If the user doesn’t confirm completion, the reminder comes back.
Again. And again.

---

## Reminder types

### One-time reminders

Single job search actions.

Examples:
- Apply to Backend Developer position
- Message a recruiter on Telegram
- Submit a test assignment

Behavior:
- **Done** → reminder is removed
- No confirmation → reminder repeats after a defined interval (e.g. every 5 minutes)

---

### Periodic reminders

Recurring job search routines.

Examples:
- Check new vacancies
- Send 3 applications per day
- Review recruiter replies
- Improve resume or GitHub profile

Supported intervals:
- every N minutes
- every N hours
- every N days
- every N months

Each trigger requires confirmation.

---

## Interaction flow

When a reminder fires, the user is asked to respond:

- **Done**
- **In progress**
- **Remind later**

---

### Done

- Task is completed
- One-time reminders are removed
- Periodic reminders schedule the next cycle

---

### In progress

Used when the task has started but is not finished yet.

The bot asks:
> Did you finish it?

- **Yes** → task completed
- **No** → nag mode is activated

---

### Remind later

The user chooses when to be reminded again:
- in 5 minutes
- in 15 minutes
- in 1 hour
- at a custom time

---

## Nag mode

If the user:
- doesn’t respond
- or confirms the task is still not done

**nagrs** enters *nag mode*.

In this mode:
- reminders repeat with a fixed interval
- the task stays active until explicitly completed
- the goal is persistence, not punishment

Nag mode is intentionally uncomfortable — and effective.

---

## Architecture

The project is built with a strict separation of concerns.

- **Core logic** (reminder states, scheduling, nag mode) lives in a standalone Rust crate
- **Interfaces** (Telegram bot, CLI, etc.) are thin adapters

This makes the system reusable as:
- a Telegram bot
- a CLI tool
- a library for other applications

UI is replaceable.  
Logic is not.

---

## Technology

- Rust
- Async runtime (Tokio)
- Telegram Bot API
- Interface-agnostic core design

---

## Project goals

This project is built primarily for personal use —
to make job searching more structured, honest, and consistent.

If it helps others do the same, that’s a welcome bonus.

---

## License

MIT License
