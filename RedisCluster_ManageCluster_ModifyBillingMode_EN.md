# Modify Billing Mode

> Dubai Hybrid Cloud · Public Cloud Documentation Center
> Path: Key-Value Database Redis Cluster › Operations Guide › Manage Cluster › Modify Billing Mode
> Last updated: 2026-06-29 10:11:06

---

Redis clusters support **Hourly**, **Monthly**, and **Annual** billing, and you can change the billing mode at any time.

## Background Information

Compared with hourly billing, monthly and annual billing (subscription) offers more favorable pricing — the longer the usage period, the cheaper it gets. If you have medium- or long-term usage needs, choosing monthly or annual billing is recommended; if you only have short-term testing needs, hourly billing is a better fit.

## Precautions

- When switching from hourly to monthly or annual billing, the first month's / year's fee is deducted in a single charge and cannot be refunded once deducted. Make sure your balance is sufficient so the deduction does not affect your use of other resources. If you need to top up, do so on the top-up page.
- When switching from hourly to monthly or annual billing, a new purchase order is generated. You must complete the payment flow for that order before the billing-mode change takes effect. If payment is not made or is unsuccessful, an incomplete order will appear on your order management page.
- When switching from monthly or annual billing back to hourly billing, you must first cancel the subscription contract.

## Steps

1. Log in to the **Dubai Hybrid Cloud** management console through a web browser.
2. In the top navigation menu, go to **Products & Services › Database & Cache › Key-Value Database Redis Cluster** to enter the Redis Cluster management page.

> _(Screenshot: the Redis Cluster cluster list. Toolbar: **+ Create**, **▶ Start**, **■ Stop**, **More Actions ▾**, a search field with placeholder "Enter cluster name / ID", **Tag**, refresh, and a column-settings icon.)_

Columns shown in the cluster list (example row, for layout reference — not real data):

| Cluster Name/ID | App Name/Version | Status | Zone | Node Count | Network | Billing Method | Tag | Alarm Associated | Actions |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Redis Cluster / cl-cq6rcl6f | Redis Cluster / 7.0.4 – v2.0.0 | ● Active | QA1A | 6 | AppCenter Metadata Service | Hourly | cl-cq6rcl6f | – | Stop · Restart · ⋮ |

3. In the cluster list, right-click the target cluster and select **Cost Management › Modify Billing Mode**.
4. In the **Modify Billing Mode** window that pops up, select the billing mode and confirm the price. Click **Pay Now** to return to the node list page.

---

> Previous: Delete a Cluster · Next: Authorize Provider Access
