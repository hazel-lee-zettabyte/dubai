# Connect a Redis Cluster Instance

> Dubai Hybrid Cloud · Public Cloud Documentation Center
> Path: Key-Value Database Redis Cluster › Quick Start › Connect a Redis Cluster Instance
> Last updated: 2026-06-29 10:11:06

---

Redis Cluster supports multiple connection methods. This section describes how to connect to a Redis instance using redis-cli.

## Get the Connection Address

After the Redis Cluster instance is created, open the Redis Cluster details page and select the **Nodes** tab. The IP address shown for each Redis node is its connection address; you can connect to any one of the master nodes.

> _(Screenshot: the Nodes tab of the Redis Cluster details page, showing the node list with a toolbar: **+ Add Shard**, **+ Add Replica**, **Delete**, and a search field with placeholder "Enter node name / ID".)_

Node list columns (example rows, for layout reference — not real data):

| Node Name/ID | Zone | Role | Instance Type | Node Status | Service Status | Configuration | IP | Security Group | Actions |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| cln-98hx0hro | QA1A | Shard | Performance | ● Active | ● Normal | 2 cores / 2 GB / 110 GB | 172.20.253.24 | – | Modify \| Delete |
| cln-aktutjfb | QA1A | cln-qjhwhwmp Replica | Performance | ● Active | ● Normal | 2 cores / 2 GB / 110 GB | 172.20.253.22 | – | Modify \| Delete |
| cln-fs0kit9v | QA1A | Shard | Performance | ● Active | ● Normal | 2 cores / 2 GB / 110 GB | 172.20.253.26 | – | Modify \| Delete |
| cln-neidnv23 | QA1A | cln-98hx0hro Replica | Performance | ● Active | ● Normal | 2 cores / 2 GB / 110 GB | 172.20.253.23 | – | Modify \| Delete |
| cln-ogtvf9ek | QA1A | cln-fs0kit9v Replica | Performance | ● Active | ● Normal | 2 cores / 2 GB / 110 GB | 172.20.253.27 | – | Modify \| Delete |
| cln-qjhwhwmp | QA1A | Shard | Performance | ● Active | ● Normal | 2 cores / 2 GB / 110 GB | 172.20.253.25 | – | Modify \| Delete |

> **Note:** The **Role** column has two value shapes — "Shard" (a master node) and "`<node-id>` Replica" (a replica of that master). The example above is 3 shards × 1 replica each = 6 nodes.

## Connection Methods

| Connection Method | Description |
| --- | --- |
| Connect to a Redis instance via redis-cli *(link)* | redis-cli is the native command-line tool that ships with Redis. Install redis-cli on a cloud server that resides in the **same VPC network** as the Redis Cluster instance, then connect to the Redis Cluster instance to manage data. |

> ⚠️ **Confirm (structure):** The Redis **Cluster** source page for connecting was simpler than the Redis **Standalone** reference — it showed only *Get the Connection Address* and *Connection Methods*, without the Standalone page's *Prerequisites*, *Step 1 / Step 2*, redis-cli parameter table, and connection examples. Confirm whether the Cluster page should mirror the richer Standalone structure, or stay as-is per its source.
