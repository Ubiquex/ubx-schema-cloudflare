# STATE.md — current state

> Rewritten, not appended, as the LAST act of every session. See `HISTORY.md`
> for the narrative.

## In flight

Nothing in flight as of 2026-09-03. `v1.0.0` just cut, real, not yet
consumed by `ubiquex`'s own `sdk/providers/.ubx/config` (still live,
pending hop 5 of `/onboard-provider cloudflare`).

## Blocked

Nothing blocked. Zero open PRs.

## Current release

Latest published: `v1.0.0` (verify directly — `gh api
repos/Ubiquex/ubx-schema-cloudflare/releases/tags/v1.0.0`). 2 members
(`cloudflare` resource, `cloudflare_ds` data-source), 268 real resource
types + 820 real data source types. Carries a real `min_binary_version`
(`1.0.8`) from the start — generated from `ubx-provider-dynamic` v1.0.8,
the first release with both real fixes this onboarding needed.

## Before touching anything

- Never self-merge here. See `CLAUDE.md`.
- `namespace_from_tags = true` is a real, flagged judgment call (see
  `README.md`), not an obviously-correct default to copy onto another
  provider without checking its own real numbers first.
