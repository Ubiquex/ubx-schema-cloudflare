# HISTORY.md — narrative archive

> Consulted only when a session needs to know why a decision was made, not on
> every open. For what's current, read `STATE.md` instead.

## Real, known decisions worth carrying forward

**First real published version was `1.0.0`**, matching every other schema
repo in this org.

**`namespace_from_tags = true`, a real, flagged judgment call, not a clean
win (UBI-222).** Cloudflare's own real operation tags (551 distinct) are
finer-grained than DigitalOcean's own were relative to wire-type count --
enabling this flag drops single-resource-service fragmentation from 54.7%
to 33.9%, but raises the total real group count from 362 to 443. Enabled
on the strength of the fragmentation reduction (the specific problem this
flag exists to fix), not because it was an unambiguous improvement on
every real metric. See `sdk/providers/.onboarding/cloudflare.json` in
`ubiquex` for the full real numbers this decision was made from, and
`ubiquex-docs`/`write-artifacts` sessions working this provider's own
categories for how it plays out in practice.

**`v1.0.0` required a real `ubx-provider-dynamic` fix before it could be
generated at all.** `ubx-provider-dynamic` v1.0.7 (the latest real release
at the start of this onboarding) crashed outright generating this
provider's own data sources -- a `deriveNoun` path-fallback bug that
picked the wrong path segment for a collection-shaped read path with no
trailing `{param}`, real and common for Cloudflare specifically. The same
release also had a live-path gap that made `namespace_from_tags` have no
effect at all before a snapshot existed, making the flag's own real
effect unverifiable at the point `/onboard-provider`'s own hop 3 asks a
session to check it. Both fixed in `ubx-provider-dynamic` PR #59, released
as v1.0.8 -- this snapshot's own real `min_binary_version`.
