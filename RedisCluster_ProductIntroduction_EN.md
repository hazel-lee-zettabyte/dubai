# Key-Value Database Redis Cluster — Product Introduction

> Dubai Hybrid Cloud · Public Cloud Documentation Center
> Path: Key-Value Database Redis Cluster › Product Introduction
> Last updated: 2026-06-29

> _Scope: this file currently covers the **Command Support** and **Parameter Support** pages. Other Product Introduction pages (What Is Redis Cluster, Product Advantages, Features, Use Cases, Product Architecture, Resource Configuration, Product Editions) are not yet captured._

---

## Command Support

Redis Cluster supports the native Redis commands. The set of supported commands varies slightly by Redis version. This page lists command support across versions.

> ⚠️ **Confirm** the intro wording against the source — the original intro was not legible at the supplied zoom.

This page is a set of **command-category blocks**; each block is a heading followed by one table. Every table uses the same columns:

**Command · Description · Redis 4.0.6 · Redis 5.0.8 · Redis 6.x · Redis 7.x**

Support cells show `✓` (supported) or `✗` (not supported).

Command categories (grouped by the standard Redis command groups — confirm the exact set/order against the source):

Bitmap · Cluster · Connection · Geo · Hash · HyperLogLog · Keys · Lists · Pub/Sub · Scripting · Server · Set · Sorted Set · Streams · Strings · Transactions

> ⚠️ **TABLE PENDING legible source.** This page is a large command × version matrix supplied as a full-page screenshot at very small type. The **layout is confirmed**, but the **per-cell ✓/✗ values and individual command names/descriptions cannot be transcribed reliably** at that resolution. Paste the table text/HTML or higher-res crops (ideally one crop per command category) and I'll fill it in.

Row template (per category table):

| Command | Description | Redis 4.0.6 | Redis 5.0.8 | Redis 6.x | Redis 7.x |
| --- | --- | :---: | :---: | :---: | :---: |
| `<command>` | `<description>` | ✓/✗ | ✓/✗ | ✓/✗ | ✓/✗ |

---

## Parameter Support

Redis Cluster supports a range of configuration parameters. The set of supported parameters varies slightly by version. This page lists parameter support and descriptions across versions.

> ⚠️ **Confirm** the intro wording against the source — the original intro was not legible at the supplied zoom.

> ℹ️ **Note:** This page is **different from Command Support**. *Command Support* is a matrix of Redis **commands**; *Parameter Support* is a matrix of Redis **configuration parameters**.

This page is a single large matrix (possibly with minor sub-sections). Columns:

**Parameter · Description · Redis 4.0.6 · Redis 5.0.8 · Redis 6.x · Redis 7.x**

Support cells show `✓` / `✗`. Some **Description** cells contain an ℹ️ note or ⚠️ warning callout, plus the parameter's allowed values / default (e.g. `yes` / `no`, default value).

Parameter names partially legible (reference only; support values TBD — keep as-is):

`maxmemory`, `maxmemory-policy`, `maxmemory-samples`, `maxclients`, `timeout`, `tcp-backlog`, `tcp-keepalive`, `databases`, `hash-max-ziplist-entries`, `hash-max-ziplist-value`, `list-max-ziplist-size`, `set-max-intset-entries`, `zset-max-ziplist-entries`, `zset-max-ziplist-value`, `activerehashing`, `appendonly`, `appendfsync`, `notify-keyspace-events`, `slowlog-log-slower-than`, `lua-time-limit`, …

> ⚠️ **TABLE PENDING legible source.** Same full-page-screenshot limitation as above — **structure confirmed, per-cell ✓/✗ and some parameter names/descriptions to be supplied from source.** Paste the table text/HTML or higher-res crops and I'll fill it in.

Row template:

| Parameter | Description | Redis 4.0.6 | Redis 5.0.8 | Redis 6.x | Redis 7.x |
| --- | --- | :---: | :---: | :---: | :---: |
| `<parameter>` | `<description / allowed values / default>` | ✓/✗ | ✓/✗ | ✓/✗ | ✓/✗ |
