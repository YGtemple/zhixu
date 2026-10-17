<div align="right">

**[English](README.md)** · [简体中文](README.zh-CN.md)

</div>

# zhixu

An offline-first schedule assistant — multiple views, recurring tasks, natural-language entry.

<sub>Single HTML file · no backend · data stays local</sub>

---

## What it does

Daily scheduling in one page:

- **Multiple views** — day, week, month
- **Recurring tasks** — daily, weekly, by weekday, month-end
- **Natural-language entry** — type "明天下午三点开会" and it becomes an event
- **Offline** — all data in `localStorage`; the page works with no network at all

## Why single-file, no backend

An assistant you check every morning should load instantly and never fail because a server is down. A single HTML file opens from disk in one click.

The trade-off is real: no cross-device sync, and clearing browser data loses the schedule. Export to JSON exists for that reason.

## Design decisions worth noting

**Recurrence is computed, not stored.** A repeating task keeps one rule, not many instances. The month view generates occurrences on demand, so a daily task does not create 365 rows.

**Natural language is parsed locally.** No model call — a small rule set handles the common shapes (relative dates, weekday names, time expressions). It fails on complicated input, and says so rather than guessing.

**Month-end recurrence is handled explicitly.** "The 31st" in February is the last day, not skipped. This is the case most recurring-task code gets wrong.

## Layout

```
index.html      the whole application
```

## Running

Open `index.html` in a browser. Nothing to install.

## License

MIT
