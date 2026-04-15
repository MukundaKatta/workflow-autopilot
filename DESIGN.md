# workflow-autopilot — Design

> Learn a user's manual workflow by watching them do it three times, then offer to run it with one command. No drag-and-drop builder.

## Problem

Zapier / n8n / Make require you to know your workflow in advance and translate it into their visual DSL. But most real workflows start tacit — the person doing them can't articulate every step. The visual builder model is backwards for these cases.

workflow-autopilot watches user actions (via a browser extension or desktop recorder), infers the pattern from 2-3 examples, and proposes a parameterized playbook. The user reviews/edits it in plain English, then the tool can execute it headlessly on demand.

## Primary users

- Knowledge workers who repeat the same 5-20 step web workflow weekly
- Small-team ops leads who don't have time to build Zaps for every recurring task
- Support teams running manual data-entry flows across 3+ internal tools

## Use cases

- Record logging into 3 tools → pulling a report → pasting into a Google Doc → Slack-sending the link. Replay on Mondays.
- Onboard a new customer: walk through CRM + Stripe + Notion setup manually 3x, then automate
- Pull data from a paginated admin UI that has no API — the workflow becomes a scraper
- Review a proposed workflow diff before running ('the login step now has 2FA')

## Planned stack

- Python 3.11+ runtime, FastAPI for the control plane
- Playwright for browser automation
- Anthropic API (Claude) for workflow induction from recorded traces
- Postgres for workflows, runs, artifacts
- Chrome extension (optional) for recording
- CLI via Typer for headless runs

## MVP scope (v0.1)

- [ ] Record-and-replay of a single browser session via Playwright trace viewer
- [ ] Claude-based induction: given 2-3 traces, produce a parameterized playbook (English + structured steps)
- [ ] `autopilot run <playbook>` executes it headlessly
- [ ] Artifacts stored per run (screenshots, extracted data)

## Roadmap

- v0.2: Desktop app recording (not just browser)
- v0.3: Scheduled runs with alerting on failure
- v0.4: Diff viewer — 'this workflow ran 12 times; step 4 has been flaky the last 2 runs'
- v1.0: Team sharing, role-based access, audit log

---

_This is a living design document. Status: **concept / active planning**. Follow progress at [github.com/MukundaKatta](https://github.com/MukundaKatta)._
