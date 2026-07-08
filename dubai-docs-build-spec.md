# Dubai Hybrid Cloud — Console Documentation · Build Spec

**Purpose.** This is a build specification for the web designer/developer. It describes, page by page, everything needed to reproduce the target documentation pages — both the **content** (final English copy) and the **format/layout** (components, structure, states). Source of content: the benchmark site (QingCloud public-cloud documentation center). Content has been translated to English. Product/technical proper nouns (Redis, VPC, EIP, redis-cli, FLUSHALL, FLUSHDB, ACL, DHCP, CPU, AppCenter, etc.) are kept as-is.

**Visual language / target design system.** Reproduce these pages in the **existing Dubai Hybrid Cloud "Console Documentation" template** (the reference page provided, e.g. the *Computing* page). Take the **content and page structure from the benchmark**, and the **visual styling, chrome, and components from the Dubai template**. Where the two differ, Dubai styling wins for look-and-feel; the benchmark wins for what content exists and how it is organized.

**How to read each page spec.** Every page lists: route/nav location → breadcrumb → title block → on-this-page anchors → each content section in order (heading + final copy + component type + tables/callouts) → previous/next. Copy shown in quote blocks (`>`) or tables is the **final on-page text** — use verbatim.

**Status.**

| # | Page | Nav location | Status |
|---|------|--------------|--------|
| RC-01 | Connect a Redis Cluster Instance | Redis Cluster / Quick Start | ✅ Complete |
| RC-02 | Create a Redis Cluster Instance | Redis Cluster / Quick Start | ✅ Complete |
| RC-03 | Command Support | Redis Cluster / Product Introduction | ⚠️ Structure complete; per-cell data to supply |
| RC-04 | Parameter Support | Redis Cluster / Product Introduction | ⚠️ Structure complete; per-cell data to supply |

---

## 1. Design tokens

> Approximate values read from the Dubai template — confirm exact values against the live design system before build.

| Token | Value / description |
|---|---|
| Primary / accent | Amber-gold (~`#C8981F`). Used for: eyebrow section labels, active nav item text, step-number badges, primary buttons (e.g. "Talk to Experts"), link accents. |
| Accent (soft) | Pale amber tint (~`#F7EFD8`) for active nav background and step-number badge fill. |
| Text — heading | Near-black (~`#1A1A1A`). |
| Text — body | Dark gray (~`#3F3F46`). |
| Text — muted | Gray (~`#8A8A8F`) for timestamps, labels, breadcrumb. |
| Background — page | White (`#FFFFFF`). |
| Background — soft card | Light gray (~`#F6F6F4`) for the bottom CTA card. |
| Border / divider | Light gray hairline (~`#E5E5E5`). |
| Font | Clean humanist sans-serif (system/Inter-like). |
| Eyebrow label | Uppercase, letter-spaced, small, amber-gold. |
| Callout — note (info) | Blue-tinted background, left accent, ℹ️. |
| Callout — warning | Amber/yellow-tinted background, left accent, ⚠️. |

---

## 2. Page shell (shared by all pages)

All doc pages use one three-column shell. Build once as a template; each page fills the center column + right rail.

### 2.1 Header (top bar)
- Full-width, white, thin bottom border.
- **Left:** brand lockup — logo mark + **"Dubai Hybrid Cloud"** (bold) + divider + **"Console Documentation"** (muted).
- **Right:** search field (pill, magnifier icon, placeholder **"Search documentation"**, keyboard hint **⌘K**) then a **"Back to site"** link.

### 2.2 Left sidebar — Redis Cluster navigation tree
- Fixed-width left column (~260px). Group labels in muted uppercase; items below them. Active item: amber text on pale-amber background.
- Group heading at top of tree: **Key-Value Database Redis Cluster**.

```
Updates & Announcements
  · Product Updates
Product Introduction
  · What Is Redis Cluster
  · Product Advantages
  · Features
  · Use Cases
  · Product Architecture
  · Resource Configuration
  · Product Editions
  · Parameter Support        (RC-04)
  · Command Support          (RC-03)
Billing Guide
  · Billing Description
Quick Start
  · Create a Redis Cluster Instance   (RC-02)
  · Connect a Redis Cluster Instance  (RC-01)
Operation Guide
  · Manage Cluster
  · Configure Cluster
  · Cluster Backup & Restore
  · Upgrade Cluster
  · User Management (ACL)
  · Connect to Database
  · Execute Commands
  · Monitoring & Alarms
  · Download Files
Best Practices
Performance Testing
FAQ
```

### 2.3 Main content column (center)
Vertical order:
1. **Breadcrumb** (muted, "/" separators).
2. **H1 page title.**
3. **Meta row:** "Last updated: `YYYY-MM-DD HH:MM:SS`" (muted, left) + **PDF** download control (right).
4. Intro paragraph, then content sections (H2 headings + body/tables/callouts).

### 2.4 Right rail — "On this page"
- Sticky. Label **"ON THIS PAGE"** (eyebrow style) + anchor list of the page's H2s. Active anchor highlighted on scroll.

### 2.5 Previous / Next footer
- Two bordered cards side by side. Left card: label **"Previous"**, ← arrow, target title. Right card: label **"Next"**, target title, → arrow.

### 2.6 Bottom CTA card (from Dubai template)
- Centered soft-gray rounded card below prev/next.
- Heading **"Talk to Our Team"**, subtext **"See a sovereign cloud and AI platform built for regulated business."**, primary gold button **"Talk to Experts"**.

### 2.7 Reusable components
- **Data table:** header row (muted labels), hairline row dividers; optional leading checkbox column; optional trailing **Actions** column with inline text links separated by `|`. Status cells render a colored dot + label.
- **Toolbar (above a data table):** left-aligned action buttons; right-aligned search field + icon buttons (refresh, tags, column settings).
- **Parameter table:** two columns **Parameter | Description**; description cells may contain bullet lists and callouts.
- **Callout:** info (ℹ️, blue) or warning (⚠️, amber), see tokens.
- **Numbered steps:** amber step-number badge + text; supports nested sub-steps (a/b/c…).

---

## 3. Pages

### RC-01 · Connect a Redis Cluster Instance

**Route / nav:** Redis Cluster → Quick Start → Connect a Redis Cluster Instance
**Breadcrumb:** Documentation Center / Key-Value Database Redis Cluster / Quick Start / Connect a Redis Cluster Instance
**H1:** Connect a Redis Cluster Instance
**Meta:** Last updated: 2026-06-29 10:11:06 · PDF
**On this page:** Get the Connection Address · Connection Methods

**Intro**
> Redis Cluster supports multiple connection methods. This article explains how to connect to a Redis instance using redis-cli.

**Section — Get the Connection Address** *(H2)*
> After the Redis Cluster instance is created, open the Redis Cluster details page and select the **Nodes** tab. The IP address shown for each Redis node is its connection address. You can connect to any one of the master nodes.

*Component: toolbar + data table.*
- Toolbar buttons (left): **+ Add Shard**, **+ Add Replica**, **Delete**. Right: search field (placeholder **"Enter node name / ID"**) + refresh icon.
- Table columns: **Node Name/ID · Zone · Role · Instance Type · Node Status · Service Status · Configuration · IP · Security Group · Actions**.
- Leading checkbox column. Status cells: green dot + label. Actions cell: **Modify | Delete**.

*Example rows (for layout only — not real data):*

| Node Name/ID | Zone | Role | Instance Type | Node Status | Service Status | Configuration | IP | Security Group | Actions |
|---|---|---|---|---|---|---|---|---|---|
| cln-98hx0hro | QA1A | Shard | Performance | ● Active | ● Normal | 2 cores / 2 GB / 110 GB | 172.20.253.24 | – | Modify \| Delete |
| cln-aktutjfb | QA1A | cln-qjhwhwmp Replica | Performance | ● Active | ● Normal | 2 cores / 2 GB / 110 GB | 172.20.253.22 | – | Modify \| Delete |
| cln-fs0kit9v | QA1A | Shard | Performance | ● Active | ● Normal | 2 cores / 2 GB / 110 GB | 172.20.253.26 | – | Modify \| Delete |
| cln-neidnv23 | QA1A | cln-98hx0hro Replica | Performance | ● Active | ● Normal | 2 cores / 2 GB / 110 GB | 172.20.253.23 | – | Modify \| Delete |
| cln-ogtvf9ek | QA1A | cln-fs0kit9v Replica | Performance | ● Active | ● Normal | 2 cores / 2 GB / 110 GB | 172.20.253.27 | – | Modify \| Delete |
| cln-qjhwhwmp | QA1A | Shard | Performance | ● Active | ● Normal | 2 cores / 2 GB / 110 GB | 172.20.253.25 | – | Modify \| Delete |

> Note (for the designer): the **Role** column has two value shapes — "Shard" (a master node) and "`<node-id>` Replica" (a replica of that master). The example is 3 shards × 1 replica each = 6 nodes.

**Section — Connection Methods** *(H2)*

| Connection Method | Description |
|---|---|
| Connect to a Redis instance via redis-cli *(link)* | redis-cli is the native command-line tool bundled with Redis. Install redis-cli on a cloud server that resides in the **same VPC network** as the Redis Cluster instance, then connect to the Redis Cluster instance to manage data. |

**Previous / Next:** Previous → Create a Redis Cluster Instance · Next → Start/Stop Cluster

---

### RC-02 · Create a Redis Cluster Instance

**Route / nav:** Redis Cluster → Quick Start → Create a Redis Cluster Instance
**Breadcrumb:** Documentation Center / Key-Value Database Redis Cluster / Quick Start / Create a Redis Cluster Instance
**H1:** Create a Redis Cluster Instance
**Meta:** Last updated: 2026-06-29 10:11:0X · PDF *(exact seconds to confirm)*
**On this page:** Prerequisites · Steps · Basic Configuration · Cluster Specifications · Purchase Information · Network Settings · Service Parameter Settings

**Intro**
> Using the AppCenter cluster management console, you can quickly create a Redis cluster. This section describes how to do so.

**Section — Prerequisites** *(H2)*
> You have a registered, valid cloud-platform account and have completed identity (real-name) verification.

**Section — Steps** *(H2)* — *numbered steps component*
1. Log in to the management console in a web browser.
2. In the top navigation menu, choose **Products & Services → Database & Cache → Key-Value Database Redis Cluster**.
   - First-time deployment: you land on the Redis Cluster app introduction page; open the app manager to reach the deployment page.
   - If you have created a Redis cluster before: you land on the Redis Cluster management page; click **Create** to reach the deployment page.
3. On the deployment page, follow the prompts to configure the app's basic attributes, app information, network information, environment parameters, and so on:
   a. Basic Configuration
   b. Cluster Specifications
   c. Network Settings
   d. Service Parameter Settings
4. After confirming the configuration and cost details, click **Deploy Now** to create the cluster. Once created, view and manage the Redis Cluster on the cluster management page.

*Component: toolbar + data table (created-cluster list). Example row for layout only:*
- Toolbar: **+ Create**, **Start**, **Stop**, **More Actions ▾**; right: search (**"Enter cluster name / ID"**), tags, refresh, column-settings icons.
- Columns: **Cluster Name/ID · App Name/Version · Status · Zone · Node Count · Network · Billing Method · Tag · Alarm Associated · Actions**.

| Cluster Name/ID | App Name/Version | Status | Zone | Node Count | Network | Billing Method | Tag | Alarm Associated | Actions |
|---|---|---|---|---|---|---|---|---|---|
| Redis Cluster / cl-cq9rcl6f | Redis Cluster / 7.0.4 – v2.0.0 | ● Active | QA1A | 6 | AppCenter Metadata Service | Hourly | cl-cq9rcl6f | – | Stop · Restart · ⋮ |

**Section — Basic Configuration** *(H2)*
> Configure the cluster's basic information: name, description, version, billing method, and availability zone.

| Parameter | Description |
|---|---|
| Zone | Choose a zone close to or local to your business to reduce network latency and improve access speed. |
| Version | Select the cluster version. Available options vary by version. |
| Deployment Mode | Choose **Multi-AZ** or **Single-AZ** deployment. Default: Single-AZ.<br>· **Multi-AZ:** distributes nodes across different availability zones in the current region for higher availability.<br>· **Single-AZ:** places nodes in the same availability zone within the current region for the lowest network latency; you may specify which AZ. |
| Availability Zone | · Multi-AZ: select multiple AZs to specify deployment zones.<br>· Single-AZ: select one AZ to specify the deployment zone. |
| Name | (Optional) Enter a custom cluster name. Default: `Redis Cluster`. |
| Description | (Optional) A brief description of the cluster. |

**Section — Cluster Specifications** *(H2)*
> Based on your actual business needs, configure the node resource type/specifications. Node configuration parameters vary slightly by Redis version:
- **Redis 4.0.6** — select node memory, instance type, disk type, disk size, and the number of master/replica nodes.
- **Redis 5.0.8** — select node CPU, memory, instance type, disk type, disk size, and the number of master/replica nodes.
- **Redis 6.x and above** — select shard resource configuration, memory, and the number of shards and shard replicas.
> How to configure node memory, type, shard count, etc., should be decided based on your actual business needs.

**Section — Purchase Information** *(H2)*

| Parameter | Description |
|---|---|
| Billing Method | Select the cluster billing method: **Hourly**, **Monthly**, or **Annual**. |
| Purchase Term | Shown when Monthly/Annual is selected. Options: 1 month, 3 months, 6 months, 1 year, 2 years, 3 years, 4 years, 5 years. |
| Auto-Renew | Shown when Monthly/Annual is selected. If left unchecked, billing switches to hourly after expiry. |

**Section — Network Settings** *(H2)*
> Network settings give the cluster a dedicated private network for access control, without affecting other private networks — ensuring databases are network-isolated across workloads. A database cluster can only join an already-connected private network, and that network's **DHCP must be enabled**.

| Parameter | Description |
|---|---|
| VPC Network | Configure the VPC network.<br>· Existing VPC networks in the region are loaded by default; select one from the dropdown.<br>· If none is available, click **Create** to create one.<br>⚠️ **Warning:** Do not select a free-tier VPC — creating a cluster in a free-tier VPC is not currently supported. |
| Private Network | Select the private network.<br>· Existing private networks are loaded by default; select one from the dropdown.<br>· If none is available, click **Create** to create one.<br>ℹ️ **Note:** The private network's deployment mode must match the cluster's — both Multi-AZ or both Single-AZ. |
| Security Group | (Optional) Click to select; choose a security group in the popup. Multiple selection supported. |
| Node IP | Configure node IP addresses.<br>· Auto-assigned by default.<br>· Choose **Manual** to set an IP per node. |
| Reserved IP | Configure the cluster's reserved high-availability IP.<br>· Auto-assigned by default.<br>· Choose **Manual** to set the HA IP. |

**Section — Service Parameter Settings** *(H2)*

| Parameter | Description |
|---|---|
| Disable FLUSH Commands | Choose whether to disable the `FLUSHALL` and `FLUSHDB` commands. Default: **No** (not disabled).<br>⚠️ **Warning:**<br>· Cannot be changed after the cluster is created.<br>· Because these commands can affect data irreversibly, disabling them is recommended in production.<br>· Supported from Redis 5.0.10. |
| Manage ACL Control | Choose whether to enable the Manage ACL Control service. Supported from Redis 6.2.5.<br>· Default **Yes** — enables the service; ACL accounts can be created via commands.<br>· **No** — disables the service. *(Source copy is ambiguous here — verify the exact behavior for "No" against the original.)* |
| More Service Environment Parameters | Click to expand additional parameter rows and configure more service parameters. These relate to database performance; changing some triggers a database service restart. See the parameter descriptions for details. |

**Previous / Next:** Previous → Billing Description · Next → Connect a Redis Cluster Instance

---

### RC-03 · Command Support

**Route / nav:** Redis Cluster → Product Introduction → Command Support
**Breadcrumb:** Documentation Center / Key-Value Database Redis Cluster / Product Introduction / Command Support
**H1:** Command Support
**Meta:** Last updated: `YYYY-MM-DD HH:MM:SS` *(to confirm)* · PDF
**On this page:** one anchor per command category (Bitmap, Cluster, Connection, Geo, Hash, …).

> ⚠️ **Designer note.** This page is a large **command × version** support matrix. The screenshot supplied is a full-page capture at very small type: the **layout is confirmed**, but the **per-cell ✓/✗ values and many individual command names cannot be transcribed reliably** at that resolution. Fill per-cell values from source data / a high-resolution capture — do not guess.

**Intro (gist — verify against source)**
> Redis Cluster supports the native Redis commands. The set of supported commands varies slightly by Redis version. This page lists command support across versions.

**Structure (confirmed)**
- The page is a series of **command-category blocks**; each block is a small heading + one table.
- Each table's columns: **Command · Description · Redis 4.0.6 · Redis 5.0.8 · Redis 6.x · Redis 7.x**.
- Support cells render `✓` (supported) / `✗` (not supported).
- Command categories (grouped by the standard Redis command groups; confirm exact set/order against the source):
  Bitmap · Cluster · Connection · Geo · Hash · HyperLogLog · Keys · Lists · Pub/Sub · Scripting · Server · Set · Sorted Set · Streams · Strings · Transactions

**Per-cell content:** ⚠️ to supply (needs high-resolution source). Row template for the designer to lay out against:

| Command | Description | Redis 4.0.6 | Redis 5.0.8 | Redis 6.x | Redis 7.x |
|---|---|:---:|:---:|:---:|:---:|
| `<command>` | `<description>` | ✓/✗ | ✓/✗ | ✓/✗ | ✓/✗ |

---

### RC-04 · Parameter Support

**Route / nav:** Redis Cluster → Product Introduction → Parameter Support
**Breadcrumb:** Documentation Center / Key-Value Database Redis Cluster / Product Introduction / Parameter Support
**H1:** Parameter Support
**Meta:** Last updated: `YYYY-MM-DD HH:MM:SS` *(to confirm)* · PDF
**On this page:** anchors matching the page's sections.

> ⚠️ **Designer note.** This page is **different from RC-03**: RC-03 is a **command** support matrix; RC-04 is a **configuration-parameter** support matrix. Same full-page-capture limitation applies — **structure confirmed, per-cell ✓/✗ and some parameter names to be supplied from source**.

**Intro (gist — verify against source)**
> Redis Cluster supports a range of configuration parameters. The set of supported parameters varies slightly by version. This page lists parameter support and descriptions across versions.

**Structure (confirmed)**
- A single large support matrix (possibly with minor sub-sections).
- Columns: **Parameter · Description · Redis 4.0.6 · Redis 5.0.8 · Redis 6.x · Redis 7.x**.
- Support cells render `✓` / `✗`.
- Some **Description** cells contain an ℹ️ note or ⚠️ warning callout, plus the parameter's allowed values / default (e.g. `yes`/`no`, default value).

**Parameter names partially legible (reference only; support values TBD — keep as-is):**
> `maxmemory`, `maxmemory-policy`, `maxmemory-samples`, `maxclients`, `timeout`, `tcp-backlog`, `tcp-keepalive`, `databases`, `hash-max-ziplist-entries`, `hash-max-ziplist-value`, `list-max-ziplist-size`, `set-max-intset-entries`, `zset-max-ziplist-entries`, `zset-max-ziplist-value`, `activerehashing`, `appendonly`, `appendfsync`, `notify-keyspace-events`, `slowlog-log-slower-than`, `lua-time-limit`, …

**Per-cell content:** ⚠️ to supply (needs high-resolution source). Row template:

| Parameter | Description | Redis 4.0.6 | Redis 5.0.8 | Redis 6.x | Redis 7.x |
|---|---|:---:|:---:|:---:|:---:|
| `<parameter>` | `<description / allowed values / default>` | ✓/✗ | ✓/✗ | ✓/✗ | ✓/✗ |

---

## 4. Open items (to supply / confirm)

1. **RC-03 & RC-04 matrices** — high-resolution or cropped/zoomed captures (or source text/HTML) so per-cell `✓/✗`, command/parameter names, and description text can be transcribed accurately.
2. **RC-02 "Manage ACL Control"** — the source copy for the "No" case is ambiguous; confirm exact behavior.
3. **Timestamps** for RC-03/RC-04 (and exact seconds for RC-02).
4. **Design tokens** — confirm exact hex values, spacing scale, and fonts against the live Dubai design system.
5. **IA decision** — whether the Redis Cluster nav tree slots under the existing Dubai left-nav groups, or is its own product doc set. (Spec currently treats it as its own Redis Cluster tree.)
