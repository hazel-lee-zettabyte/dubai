# Parameter Support

> Dubai Hybrid Cloud · Public Cloud Documentation Center
> Path: Key-Value Database Redis Cluster › Product Introduction › Parameter Support
> Last updated: 2026-06-29

---

Redis Cluster supports a range of configuration parameters. The set of supported parameters varies slightly by version. This page lists parameter support and descriptions across versions.

> ⚠️ **Confirm** the intro wording against the source — the original intro was not legible at the supplied zoom.

> ℹ️ **Note:** This page is **different from Command Support**. *Command Support* is a matrix of Redis **commands**; *Parameter Support* is a matrix of Redis **configuration parameters**.

## Layout

This page is a single large matrix (possibly with minor sub-sections). Columns:

**Parameter · Description · Redis 4.0.6 · Redis 5.0.8 · Redis 6.x · Redis 7.x**

Support cells show `✓` / `✗`. Some **Description** cells contain an ℹ️ note or ⚠️ warning callout, plus the parameter's allowed values / default (e.g. `yes` / `no`, default value).

Parameter names partially legible (reference only; support values TBD — keep as-is):

`maxmemory`, `maxmemory-policy`, `maxmemory-samples`, `maxclients`, `timeout`, `tcp-backlog`, `tcp-keepalive`, `databases`, `hash-max-ziplist-entries`, `hash-max-ziplist-value`, `list-max-ziplist-size`, `set-max-intset-entries`, `zset-max-ziplist-entries`, `zset-max-ziplist-value`, `activerehashing`, `appendonly`, `appendfsync`, `notify-keyspace-events`, `slowlog-log-slower-than`, `lua-time-limit`, …

## Support Matrix

> ⚠️ **TABLE PENDING legible source.** Same full-page-screenshot limitation as Command Support — **structure confirmed, per-cell ✓/✗ and some parameter names/descriptions to be supplied from source.** Paste the table text/HTML or higher-res crops and I'll fill it in.

Row template:

| Parameter | Description | Redis 4.0.6 | Redis 5.0.8 | Redis 6.x | Redis 7.x |
| --- | --- | :---: | :---: | :---: | :---: |
| `<parameter>` | `<description / allowed values / default>` | ✓/✗ | ✓/✗ | ✓/✗ | ✓/✗ |
