
|  Legacy PHP Application  |  Region: us-east-2

**Prepared by:** Muhammad Ashar
**Date:** March 25, 2026**Period:** Dec 2025 – Feb 2026**Type:** Read-only · No changes made
```
Key Metrics — Cost Overview
Dec 2025 Total
$411.76
Baseline month
Feb 2026 Total
$552.02
▲ $140.26 vs Dec
MoM Increase
34%
Primarily RDS
Est. Annual Run Rate
~$6,624
At Feb 2026 pace

```
### Monthly cost by service (Dec 2025 → Jan 2026 → Feb 2026)

``RDSEC2 InstancesEC2 - OtherWorkMailELBVPCSupport
### RDS cost breakdown — Feb 2026 (major driver)

``db.m7g.large (new)MySQL 5.7 Extended Supportdb.m5.large (new)Existing RDS (Dec)

### Service cost breakdown

|Service|Dec 2025|Jan 2026|Feb 2026|Change|Status|
|---|---|---|---|---|---|
|**Relational Database Service**|$204.67|~$205|$343.54|+$138.87|Critical|
|EC2 - Instances|$69.04|$69.04|$62.36|-$6.68|Improving|
|WorkMail|$60.00|$60.00|$60.00|$0.00|Review|
|Support (Developer)|$29.00|$29.00|$29.00|$0.00|Review|
|VPC|$19.43|$19.42|$20.19|+$0.76|Stable|
|Elastic Load Balancing|$17.09|$16.99|$15.33|-$1.76|Stable|
|EC2 - Other|$12.00|$13.01|$21.00|+$9.00|Monitor|
|Route 53|$0.52|$0.53|$0.61|+$0.09|Stable|
|**Total**|**$411.76**|**~$413**|**$552.02**|**+$140.26**||

---

Findings & Recommendations

``FinOps — Cost Reduction

``F1 — RDS: Two new instances appeared in Feb 2026 (db.m7g.large + db.m5.large)

Usage jumped from 0 hrs to 227.52 hrs and 213.40 hrs respectively in a single month. These may be test/staging instances left running. The db.m7g.large alone added $76.67 in one month. Verify if both are needed in production simultaneously.

Potential saving: $80–$115/month if one instance is unused or can be stopped

``F2 — MySQL 5.7 Extended Support: $42.68/month and growing

MySQL 5.7 reached end-of-life in Oct 2023. AWS charges Extended Support for Yr1–Yr2 at per-vCPU-hour rates (426.80 vCPU-hours in Feb). This cost will increase further in Year 2 support. Upgrading to MySQL 8.0 eliminates this cost entirely.

Potential saving: $42–$85+/month (doubles in Yr2 extended support)

``F3 — RDS Instance Right-Sizing Opportunity

Running db.m7g.large and db.m5.large simultaneously for a legacy PHP app is likely over-provisioned. Without CloudWatch CPU/memory metrics it's hard to confirm, but for most PHP web apps a db.t4g.medium or db.t3.medium is sufficient at a fraction of the cost.

Potential saving: $40–$80/month by downsizing to burstable instance class

``F4 — WorkMail: $60/month flat — review active mailboxes

AWS WorkMail costs $4/user/month. At $60/month this implies 15 active mailboxes. For a PHP project, this may be unnecessary. Consider consolidating to 1–2 technical mailboxes, or migrating to an external email provider to eliminate this cost.

Potential saving: $20–$50/month by reducing mailbox count

``F5 — AWS Support Plan: $29/month Developer tier — consider downgrading

Developer support at $29/month provides business-hours email support. If the team has sufficient in-house AWS expertise, downgrading to Basic (free) or retaining only for critical go-live periods could reduce cost.

Potential saving: $29/month if downgraded to Basic

``F6 — VPC: NAT Gateway charges ($19–$20/month) — review data transfer

NAT Gateway charges include an hourly fee plus per-GB data processing. For a PHP app, check if all subnets truly need NAT Gateway. Private resources that only need outbound internet access could use NAT Instance (cheaper) or VPC Endpoints for AWS services.

Potential saving: $5–$12/month via VPC endpoint optimization

``F7 — Reserved Instances / Savings Plans for predictable workloads

EC2 ($62/month) and any stable RDS instance are good candidates for 1-year Reserved Instances. EC2 RI for a t3.medium (if that's the instance type) saves ~38% vs on-demand. For RDS, Reserved Instances save 30–40% over on-demand.

Potential saving: $25–$50/month on compute via 1yr Reserved Instances

``F8 — Enable Cost Anomaly Detection & AWS Budgets

The $140 spike in Feb went undetected until billing review. Set a Budget alert at $450/month with SNS email notifications. Enable Cost Anomaly Detection for RDS specifically — this would have flagged the new instances immediately.

Preventive: catches future spikes before month-end billing surprise