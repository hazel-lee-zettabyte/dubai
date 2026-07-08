# Key-Value Database Redis Cluster — Quick Start

> Dubai Hybrid Cloud · Public Cloud Documentation Center
> Path: Key-Value Database Redis Cluster › Quick Start
> Last updated: 2026-06-29

---

## Create a Redis Cluster Instance

Through AppCenter's cluster management console, you can quickly create a Redis cluster. This section describes how to create a Redis Cluster instance.

### Prerequisites

- You have a registered, valid cloud-platform account and have completed identity verification.

> ⚠️ **Confirm:** the source prerequisite is 实名认证 (real-name / identity verification), a China-regulatory step. Rendered above as generic "identity verification." Tell me if this does not apply to Dubai Hybrid Cloud and I'll drop it (as with ICP filing).

### Steps

1. Log in to the **Dubai Hybrid Cloud** management console through a web browser.
2. In the top navigation menu, go to **Products & Services › Database & Cache › Key-Value Database Redis Cluster**.
   - First-time deployment: you land on the Redis Cluster app introduction page; open the app manager to reach the deployment page.
   - If you have created a Redis cluster before: you land on the Redis Cluster management page; click **Create** to reach the deployment page.
3. On the deployment page, follow the prompts to configure the app's basic attributes, app information, network information, and environment parameters:
   a. Basic Configuration
   b. Cluster Specifications
   c. Network Settings
   d. Service Parameter Settings
4. After confirming that the configuration and cost information are correct, click **Deploy Now** to create the cluster. Once creation completes, view and manage the Redis Cluster on the cluster management page.

> _(Screenshot: the Redis Cluster cluster list showing a created cluster with an **Active** status.)_

Columns shown in the cluster list (example row, for layout reference — not real data):

| Cluster Name/ID | App Name/Version | Status | Zone | Node Count | Network | Billing Method | Tag | Alarm Associated | Actions |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Redis Cluster / cl-cq9rcl6f | Redis Cluster / 7.0.4 – v2.0.0 | ● Active | QA1A | 6 | AppCenter Metadata Service | Hourly | cl-cq9rcl6f | – | Stop · Restart · ⋮ |

### Basic Configuration

Configure the cluster's basic information — name, description, version, billing method, and availability zone.

| Parameter | Description |
| --- | --- |
| Zone (区域) | Choose a zone close to or local to your business to reduce network latency and improve access speed. |
| Version (版本) | Select the cluster version. Available options vary by version. |
| Deployment Mode (部署方式) | Choose **Multi-AZ** or **Single-AZ** deployment. Default: Single-AZ.<br>· **Multi-AZ:** distributes nodes across different availability zones in the current region for higher availability.<br>· **Single-AZ:** places nodes in the same availability zone within the current region for the lowest network latency; you may specify the AZ. |
| Availability Zone (可用区) | · Multi-AZ: select multiple AZs to specify the deployment zones.<br>· Single-AZ: select one AZ to specify the deployment zone. |
| Name (名称) | (Optional) Enter a custom cluster name. Default: `Redis Cluster`. |
| Description (描述) | (Optional) A brief description of the cluster. |

### Cluster Specifications

Based on your actual business needs, configure the node resource type / specifications. Node configuration parameters vary slightly by Redis version:

- **Redis 4.0.6** — select node memory, instance type, disk type, disk size, and the number of master/replica nodes.
- **Redis 5.0.8** — select node CPU, memory, instance type, disk type, disk size, and the number of master/replica nodes.
- **Redis 6.x and above** — select shard resource configuration, memory, and the number of shards and shard replicas.

> How to configure node memory, type, shard count, etc., should be decided based on your actual business needs.

### Purchase Information

| Parameter | Description |
| --- | --- |
| Billing Method (计费方式) | Select the cluster billing method: **Hourly**, **Monthly**, or **Annual**. |
| Purchase Term (购买时长) | Shown when Monthly/Annual is selected. Options: 1 month, 3 months, 6 months, 1 year, 2 years, 3 years, 4 years, 5 years. |
| Auto-Renewal (自动续费) | Shown when Monthly/Annual is selected. If left unchecked, billing switches to hourly after expiry. |

### Network Settings

Configure the cluster's network. This gives the cluster a dedicated private network for access control without affecting other private networks, ensuring databases are network-isolated across workloads. A database cluster can only join an already-connected private network, and that network's **DHCP must be enabled**.

| Parameter | Description |
| --- | --- |
| VPC Network (VPC 网络) | Configure the VPC network.<br>· Existing VPC networks in the region are loaded by default; select one from the dropdown.<br>· If none is available, click **Create** to create one.<br>⚠️ **Warning:** Do not select a free-tier VPC — creating a cluster in a free-tier VPC is not currently supported. |
| Private Network (私有网络) | Select the private network.<br>· Existing private networks are loaded by default; select one from the dropdown.<br>· If none is available, click **Create** to create one.<br>ℹ️ **Note:** The private network's deployment mode must match the cluster's — both Multi-AZ or both Single-AZ. |
| Security Group (安全组) | (Optional) Click to select; choose a security group in the popup. Multiple selection supported. |
| Node IP (节点 IP) | Configure node IP addresses.<br>· Auto-assigned by default.<br>· Choose **Manual** to set an IP per node. |
| Reserved IP (预留 IP) | Configure the cluster's reserved high-availability IP.<br>· Auto-assigned by default.<br>· Choose **Manual** to set the HA IP. |

### Service Parameter Settings

| Parameter | Description |
| --- | --- |
| Disable FLUSH Commands (禁用 FLUSH 命令) | Choose whether to disable the `FLUSHALL` and `FLUSHDB` commands. Default: **No** (not disabled).<br>⚠️ **Warning:**<br>· Cannot be changed after the cluster is created.<br>· Because these commands can affect data irreversibly, disabling them is recommended in production.<br>· Supported from Redis 5.0.10. |
| Manage ACL Control (控制管理 ACL) | Choose whether to enable the Manage ACL Control service. Supported from Redis 6.2.5.<br>· Default **Yes** — enables the service; ACL accounts can be created via commands.<br>· **No** — disables the service. |
| More Service Environment Parameters (更多服务环境参数) | Click to expand additional parameter rows and configure more service parameters. These relate to database performance; changing some triggers a database service restart. See the parameter descriptions for details. |

> ⚠️ **Confirm:** the source copy for the **Manage ACL Control → "No"** case is ambiguous (both branches appeared to mention creating ACL accounts via commands). Verify the exact "No" behavior against the original page.

---

## Connect to a Redis Cluster Instance

Redis Cluster supports multiple connection methods. This section describes how to connect to a Redis instance using redis-cli.

### Get the Connection Address

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

### Connection Methods

| Connection Method | Description |
| --- | --- |
| Connect to a Redis instance via redis-cli *(link)* | redis-cli is the native command-line tool that ships with Redis. Install redis-cli on a cloud server that resides in the **same VPC network** as the Redis Cluster instance, then connect to the Redis Cluster instance to manage data. |

> ⚠️ **Confirm (structure):** The Redis **Cluster** source page for connecting was simpler than the Redis **Standalone** reference — it showed only *Get the Connection Address* and *Connection Methods*, without the Standalone page's *Prerequisites*, *Step 1 / Step 2*, redis-cli parameter table, and connection examples. Confirm whether the Cluster page should mirror the richer Standalone structure, or stay as-is per its source.
