# Start / Stop a Cluster

> Dubai Hybrid Cloud · Public Cloud Documentation Center
> Path: Key-Value Database Redis Cluster › Operations Guide › Manage Cluster › Start / Stop a Cluster
> Last updated: 2026-06-29 10:11:06

---

This section describes how to stop, start, and restart a Redis cluster.

## Operation Scenario

When a cluster runs into connection-overflow or performance issues, you can restart the Redis cluster to release all connections.

## Precautions

- Stopping a cluster interrupts its connections. Until the cluster has successfully started again, you cannot perform read or write operations on it; performing this operation during off-peak business hours is recommended.
- While a cluster is starting, its nodes synchronize state and data internally. If a large amount of data keeps being written before synchronization completes, internal synchronization can take a long time, and the cluster status stays **Starting** until synchronization finishes — only then does the status switch to **Active**.

## Start a Cluster

1. Log in to the **Dubai Hybrid Cloud** management console through a web browser.
2. In the top navigation menu, go to **Products & Services › Database & Cache › Key-Value Database Redis Cluster** to enter the Redis Cluster management page.

> _(Screenshot: the Redis Cluster cluster list. Toolbar: **+ Create**, **▶ Start**, **■ Stop**, **More Actions ▾**, a search field with placeholder "Enter cluster name / ID", **Tag**, refresh, and a column-settings icon.)_

Columns shown in the cluster list (example row, for layout reference — not real data):

| Cluster Name/ID | App Name/Version | Status | Zone | Node Count | Network | Billing Method | Tag | Alarm Associated | Actions |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Redis Cluster / cl-cq6rcl6f | Redis Cluster / 7.0.4 – v2.0.0 | ● Active | QA1A | 6 | AppCenter Metadata Service | Hourly | cl-cq6rcl6f | – | Stop · Restart · ⋮ |

3. Select the target cluster, then click **Start** in the Actions column. The start-cluster confirmation window pops up.
4. After confirming the information is correct, click **Confirm** to return to the cluster list page.
   When the cluster status switches to **Active**, the cluster has finished starting.

## Stop a Cluster

1. Log in to the **Dubai Hybrid Cloud** management console through a web browser.
2. In the top navigation menu, go to **Products & Services › Database & Cache › Key-Value Database Redis Cluster** to enter the Redis Cluster management page.

> _(Screenshot: the Redis Cluster cluster list, same layout as above.)_

3. Select the target cluster, then click **Stop** in the Actions column. The stop-cluster confirmation window pops up.
4. After confirming the information is correct, click **Stop Now** to return to the cluster list page.
   When the cluster status switches to **Stopped**, the cluster has finished stopping.

> ⚠️ **Confirm (source typo):** In step 4 above, the source reads "则集群启动完毕" (*the cluster has finished **starting***) inside the *Stop a Cluster* section — apparently copied from the Start section. Rendered here as "finished stopping" to match intent. Verify against the original page.

## Schedule Cluster Start / Stop

Using the Timer feature, you can create scheduled tasks that start or stop the cluster automatically at set times.

1. Log in to the **Dubai Hybrid Cloud** management console through a web browser.
2. Go to **Products & Services › Operations & Management › Timer** to enter the timer list page.
3. Create a timer.
   a. Click **Create** to open the timer's basic-configuration page.
   b. Configure the timer type, cycle (only when **Repeat** is selected), time, notification events, and related information.
   c. Click **Submit** to return to the timer list page.

> _(Screenshot: the **Create Timer** dialog.)_

Fields in the **Create Timer** dialog (example values, for layout reference — not real data):

| Field | Control / Value |
| --- | --- |
| Name (名称) | Text input — e.g. `redis cluster` |
| Type (类型) | Radio — ● **Repeat** (重复执行) / ○ **Run Once** (仅执行一次) |
| Cycle (周期) | Dropdown — e.g. **Daily** (每天) |
| Time (时间) | Time input — e.g. `1 : 00` |
| Notification Events (通知事件) | Checkboxes — ☐ **Success** (成功) / ☑ **Failure** (失败) |
| Notification List (通知列表) | Dropdown — e.g. `test` — plus a **+ New List** (新列表) button |

> **Note:** The notification list stores the contact methods used to receive notifications.
>
> Dialog buttons: **Cancel** · **Submit**.

4. Create a scheduled task.
   Click the timer ID to enter its details page.
   a. Click **Create** to open the task-configuration window.
   b. Configure the scheduled-task information.
      For **Type**, select **Start Cluster** (开启集群) or **Stop Cluster** (关闭集群); for **Resource**, select the target cluster.
   c. Click **Submit** to return to the timer's task list page.
      Once configured, the cluster will start or stop at the time specified by the timer.

> _(Screenshot: the **Create Timer Task** dialog.)_

Fields in the **Create Timer Task** dialog (example values, for layout reference — not real data):

| Field | Control / Value |
| --- | --- |
| Name (名称) | Text input — e.g. `start` |
| Type (类型) | Dropdown — e.g. **Start Cluster** (启动集群) |
| Resource (资源) | Selected cluster chip — e.g. `cl-icca76z6` ✕ — plus a **+ Select Cluster** (选择集群) button |

> Dialog buttons: **Cancel** · **Submit**.

---

> Previous: Connect a Redis Cluster Instance · Next: Delete a Cluster
