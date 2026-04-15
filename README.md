# workflow-autopilot

> Learn a user's manual workflow by watching them do it three times, then offer to run it with one command. No drag-and-drop builder.

![status](https://img.shields.io/badge/status-active_planning-blue)
![license](https://img.shields.io/badge/license-MIT-green)
![backlog](https://img.shields.io/badge/backlog-see_DESIGN.md-orange)

## What this is

Zapier / n8n / Make require you to know your workflow in advance and translate it into their visual DSL. But most real workflows start tacit — the person doing them can't articulate every step. The visual builder model is backwards for these cases.

**Read the full [DESIGN.md](./DESIGN.md)** for problem statement, user personas, architecture, and roadmap.

## Status

**Active planning / pre-alpha.** The design is scoped (see DESIGN.md). Code is minimal — this repo is the home for the first real implementation, not a placeholder.

## MVP (v0.1) — what ships first

- Record-and-replay of a single browser session via Playwright trace viewer
- Claude-based induction: given 2-3 traces, produce a parameterized playbook (English + structured steps)
- `autopilot run <playbook>` executes it headlessly
- Artifacts stored per run (screenshots, extracted data)

## Stack

- Python 3.11+ runtime, FastAPI for the control plane
- Playwright for browser automation
- Anthropic API (Claude) for workflow induction from recorded traces
- Postgres for workflows, runs, artifacts
- Chrome extension (optional) for recording

See [DESIGN.md](./DESIGN.md#planned-stack) for complete stack rationale.

## Quick start

```bash
git clone https://github.com/MukundaKatta/workflow-autopilot.git
cd workflow-autopilot
# See DESIGN.md for full architecture
```


## Roadmap

| Version | Focus |
|---------|-------|
| v0.1 | MVP — see checklist in [DESIGN.md](./DESIGN.md) |
| v0.2 | Desktop app recording (not just browser) |
| v0.3 | Scheduled runs with alerting on failure |

Full roadmap in [DESIGN.md](./DESIGN.md#roadmap).

## Contributing

Open an issue if:
- You'd use this tool and have a specific use case not covered
- You spot a design flaw in DESIGN.md
- You want to claim one of the v0.1 checklist items

## See also

- [My other projects](https://github.com/MukundaKatta)
- [mukunda.dev](https://mukunda-ai.vercel.app)
