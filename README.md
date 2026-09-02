# ubx-schema-cloudflare

A real, frozen, versioned Cloudflare provider schema snapshot -- the pinnable
distribution artifact `ubx-provider-dynamic` and `ubiquex` resolve a
single `[providers.cloudflare]` entry against, with zero network calls at
schema resolution time (see `provider/acquireschema.go` in `ubiquex`, and
`internal/snapshot`'s own doc comment in `ubx-provider-dynamic`). The
resource/data-source split below is a real, internal discovery-time
detail -- one pin resolves both.

## What's here

Cloudflare's own real published identity is a GROUP of two members, both
fetched from the identical real, public OpenAPI 3.0.3 spec
(github.com/cloudflare/api-schemas) but built through genuinely different
pipelines:

- `cloudflare` -- resource mode (268 real resource types).
- `cloudflare_ds` -- data-source mode (820 real, unclaimed read-only
  operations).

`namespace_from_tags = true` (UBI-222): Cloudflare's own real operation
tags reduce single-resource-service fragmentation (54.7% -> 33.9% of real
groups) even though the total group count is not clearly better (443
tag-based vs 362 mechanical) -- a real, flagged judgment call, not a clean
win the way this flag was for DigitalOcean. See
`sdk/providers/.onboarding/cloudflare.json` in `ubiquex` for the full real
numbers this decision was made from.

- `manifest.json` -- the group's own real identity: `schema_format`,
  `provider`, one `version` for the WHOLE group, and which member names
  it bundles.
- `members/<name>.json` -- one real, complete, independently-diffable
  file per member (`cloudflare.json`, `cloudflare_ds.json`). Committed as
  separate files, not one combined blob, so a real version bump's own
  git diff shows exactly which members changed.
- `.github/workflows/hash-watch.yml` -- runs weekly (and on manual
  dispatch), regenerates every member from the live spec and opens a PR
  only when the group's own mechanically-derived version (the highest
  real change level found across every member -- `internal/snapshot`'s
  `AssembleGroup`) actually moves. Never auto-merges.
- `.github/workflows/publish.yml` -- manual-dispatch-only. Packs
  `manifest.json` and every `members/*.json` into one compressed archive
  (`snapshot.tar.gz`) and cuts a real GitHub Release tagged `v<version>`
  carrying exactly two assets: `snapshot.tar.gz` and `SHA256SUMS`. The
  archive exists purely so a real pinned resolution is still one real
  download regardless of how many members a group has -- the COMMITTED
  files (what a reviewer actually sees) are always the separate,
  per-member ones above.

## Consuming a real, published version

In `ubiquex`, one real pin resolves the whole group -- both real members
(`cloudflare` resource mode, `cloudflare_ds` data-source mode) are served
together from the SAME launch, the SAME real download:

```toml
[providers.cloudflare]
source  = "ubiquex/cloudflare"
version = "1.0.0"
```

`provider.AcquireSchema`'s own cache-by-source+version resolves ONE real
download and ONE extracted cache directory
(`~/.ubx/schemas/ubiquex/cloudflare/1.0.0/`) -- the launched process
merges every real member of the group (`internal/snapshot.MergeOpenAPIGroup`)
into one served schema, `ResourceSchemas` and `DataSourceSchemas`
together, exactly like a real, hand-written Terraform provider already
looks from the outside.

## Versioning

One real, mechanically-derived semver number for the WHOLE group, not
one per member: the highest real change level found across every
member (a brand new resource type or a field that gained write access
bumps MINOR; a resource type or field that disappeared, or a field that
lost write access, bumps MAJOR; a pure description-text change bumps
PATCH), plus an unconditional MAJOR if a member the group used to bundle
is gone entirely. See `internal/snapshot/diff.go` and `AssembleGroup` in
`ubx-provider-dynamic` for the real rule.

`v1.0.0` is this group's real, first-ever snapshot, generated from
`ubx-provider-dynamic` v1.0.8 -- the first released version carrying both
real fixes this onboarding needed (a `deriveNoun` path-fallback bug that
crashed generation outright on certain data source paths, and a live-path
gap that made `namespace_from_tags` have no effect before a snapshot
existed). See `ubx-provider-dynamic` PR #59 for the full account.

<!-- README-GEN:BEGIN -->
**Real, current published version:** `v1.0.0`

## Links

- Docs: https://docs.ubiquex.io
- Internals (architecture and design): https://github.com/Ubiquex/ubiquex-internals
- Linear board: https://linear.app/ubiquex
<!-- README-GEN:END -->
