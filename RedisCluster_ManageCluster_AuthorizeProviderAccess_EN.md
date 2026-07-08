# Authorize Provider Access

> Dubai Hybrid Cloud · Public Cloud Documentation Center
> Path: Key-Value Database Redis Cluster › Operations Guide › Manage Cluster › Authorize Provider Access
> Last updated: 2026-06-29 10:11:06

---

This section describes how to authorize the provider to access cluster nodes.

## Operation Scenario

By default, cluster nodes do not support logging in through the VNC console. However, when you need the provider to log in to a cluster node to help with troubleshooting or fault handling, you can lift this restriction using the **Authorize Provider Access** feature.

## Precautions

To safeguard information and data security, be sure to arrange the login with the provider in advance, and revoke the authorization promptly once the login is complete.

## Authorize Access

1. Log in to the **Dubai Hybrid Cloud** management console through a web browser.
2. In the top navigation menu, go to **Products & Services › Database & Cache › Key-Value Database Redis Cluster** to enter the Redis Cluster management page.
3. In the cluster list, click the target cluster ID to enter its details page.
4. On the cluster details page, click **More Actions** in the top-right corner.

> _(Screenshot: the Redis Cluster details page with the **Nodes** tab selected. Header shows **← Redis Cluster** ● Active, with **⇄ Switch to Legacy**, **■ Stop**, **⟳ Restart**, and **More Actions ▾** (highlighted). Tabs: **Cluster Info**, **Nodes**, **Monitoring**, **Alarms**, **Configuration Info**, **Operation Logs**. Node toolbar: **+ Add Shard**, **+ Add Replica**, **Delete**, and a search field with placeholder "Enter node name / ID".)_

Node list columns (example rows, for layout reference — not real data):

| Node Name/ID | Zone | Role | Instance Type | Node Status | Service Status | Configuration | IP | Security Group | Actions |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| cln-98hx0hro | QA1A | Shard | Performance | ● Active | ● Normal | 2 cores / 2 GB / 110 GB | 172.20.253.24 | – | Modify \| Delete |
| cln-aktutjfb | QA1A | cln-qjhwhwmp Replica | Performance | ● Active | ● Normal | 2 cores / 2 GB / 110 GB | 172.20.253.22 | – | Modify \| Delete |
| cln-fs0kit9v | QA1A | Shard | Performance | ● Active | ● Normal | 2 cores / 2 GB / 110 GB | 172.20.253.26 | – | Modify \| Delete |

5. Expand the dropdown menu and click **Network & Security › Authorize Provider Access**.
6. In the prompt window that pops up, confirm the information is correct and click **Confirm**.

## Revoke Authorization

1. Log in to the **Dubai Hybrid Cloud** management console through a web browser.
2. In the top navigation menu, go to **Products & Services › Database & Cache › Key-Value Database Redis Cluster** to enter the Redis Cluster management page.

> _(Screenshot: the Redis Cluster details page with the **Nodes** tab selected, same layout as above.)_

3. Expand the dropdown menu and click **Network & Security › Revoke Provider Authorization**.
4. In the prompt window that pops up, click **Confirm**.

---

> Previous: Modify Billing Mode · Next: Change Node Configuration
