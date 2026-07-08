# Command Support

> Dubai Hybrid Cloud · Public Cloud Documentation Center
> Path: Key-Value Database Redis Cluster › Product Introduction › Command Support
> Last updated: 2026-06-29

---

Redis Cluster supports the native Redis commands. The set of supported commands varies slightly by Redis version. This page lists command support across versions.

> ⚠️ **Confirm** the intro wording against the source — the original intro was not legible at the supplied zoom.

## Layout

This page is a set of **command-category blocks**; each block is a heading followed by one table. Every table uses the same columns:

**Command · Description · Redis 4.0.6 · Redis 5.0.8 · Redis 6.x · Redis 7.x**

Support cells show `✓` (supported) or `✗` (not supported).

Command categories (grouped by the standard Redis command groups — confirm the exact set/order against the source):

Bitmap · Cluster · Connection · Geo · Hash · HyperLogLog · Keys · Lists · Pub/Sub · Scripting · Server · Set · Sorted Set · Streams · Strings · Transactions

## Support Matrix

> ⚠️ **TABLE PENDING legible source.** This page is a large command × version matrix supplied as a full-page screenshot at very small type. The **layout is confirmed**, but the **per-cell ✓/✗ values and individual command names/descriptions cannot be transcribed reliably** at that resolution. Paste the table text/HTML or higher-res crops (ideally one crop per command category) and I'll fill it in.

Row template (per category table):

| Command | Description | Redis 4.0.6 | Redis 5.0.8 | Redis 6.x | Redis 7.x |
| --- | --- | :---: | :---: | :---: | :---: |
| `<command>` | `<description>` | ✓/✗ | ✓/✗ | ✓/✗ | ✓/✗ |
