# Delete a Cluster

> Dubai Hybrid Cloud · Public Cloud Documentation Center
> Path: Key-Value Database Redis Cluster › Operations Guide › Manage Cluster › Delete a Cluster
> Last updated: 2026-06-29 10:11:06

---

This section describes how to delete a cluster.

> ⚠️ **Caution:** Deleting a cluster is a destructive operation — proceed with care. Once a cluster is permanently deleted, all resources associated with the cluster are deleted.

## Constraints

- After a cluster is deleted, it is retained in the recycle bin for 2 hours, during which it can be restored. After 2 hours, the cluster resources are permanently destroyed and cannot be recovered.
- Deleting a cluster that is currently performing an operation is not supported.
- After a cluster is deleted, its associated resources are released immediately — proceed with care. If you need to keep the data, make sure to complete a data backup before deleting.

## Steps

1. Log in to the **Dubai Hybrid Cloud** management console through a web browser.
2. In the top navigation menu, go to **Products & Services › Database & Cache › Key-Value Database Redis Cluster** to enter the Redis Cluster management page.
3. On the cluster list page, in the target cluster's Actions column, click **More Actions › Delete**.

> _(Screenshot: the Redis Cluster details page with the **Nodes** tab selected. Header shows **← Redis Cluster** ● Active, with **⇄ Switch to Legacy**, **■ Stop**, **⟳ Restart**, and **More Actions ▾**. Tabs: **Cluster Info**, **Nodes**, **Monitoring**, **Alarms**, **Configuration Info**, **Operation Logs**. Node toolbar: **+ Add Shard**, **+ Add Replica**, **Delete**, and a search field with placeholder "Enter node name / ID".)_

Node list columns (example rows, for layout reference — not real data):

| Node Name/ID | Zone | Role | Instance Type | Node Status | Service Status | Configuration | IP | Security Group | Actions |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| cln-98hx0hro | QA1A | Shard | Performance | ● Active | ● Normal | 2 cores / 2 GB / 110 GB | 172.20.253.24 | – | Modify \| Delete |
| cln-aktutjfb | QA1A | cln-qjhwhwmp Replica | Performance | ● Active | ● Normal | 2 cores / 2 GB / 110 GB | 172.20.253.22 | – | Modify \| Delete |
| cln-fs0kit9v | QA1A | Shard | Performance | ● Active | ● Normal | 2 cores / 2 GB / 110 GB | 172.20.253.26 | – | Modify \| Delete |

4. Select **Force Delete**, then click **Delete** to return to the cluster list page. The cluster status changes to **Deleting**.

## Follow-up Operations

After a cluster is deleted, you can go to **Products & Services › Operations & Management › Recycle Bin** to view deleted clusters. Resources in the recycle bin are retained for 2 hours only. During this window:

- If you want to delete permanently: select the deleted cluster, click **Permanently Delete**, and click **Confirm** in the prompt that pops up.
- If you want to restore the cluster: select the deleted cluster, click **Restore**, and in the **Restore Resources** window that pops up, review the amount required to restore the resources. After confirming that your account balance exceeds the total amount owed, click **Submit**.

---

> Previous: Start / Stop a Cluster · Next: Modify Billing Mode
