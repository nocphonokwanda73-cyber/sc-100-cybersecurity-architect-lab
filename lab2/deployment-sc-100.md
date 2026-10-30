# Lab 2: Security Operations Center (SC-100)

## Lab scenario
Contoso's Security Operations Center (SOC) needs to deploy Microsoft Sentinel as its SIEM solution and configure access controls for two roles (security analysts and security engineers) using least privilege.

**In this lab I:**
- Created a Log Analytics workspace
- Deployed Microsoft Sentinel to the workspace
- Configured role-based access control (RBAC) for the SOC roles
- Reviewed the steps to build a custom workbook for incidents and alerts

---

## Task 1: Create the Log Analytics workspace
I created a new resource group named `rg_eastus_soc` and a Log Analytics workspace named `law-sentinel` in the **East US** region. This workspace stores all the data Microsoft Sentinel ingests for detections and analytics.

**Deployment complete (resource group `rg_eastus_soc`):**

![Task 1 - Deployment complete](images/1-deployment-complete.png)

---

## Task 2: Deploy Microsoft Sentinel
I added Microsoft Sentinel to the `law-sentinel` workspace from the Microsoft Sentinel page.

**Selecting `law-sentinel` in "Add Microsoft Sentinel to a workspace":**

![Task 2a - Add Sentinel to workspace](images/2a-add-sentinel-to-workspace.png)

**Sentinel added and free trial activated:**

![Task 2b - Sentinel free trial](images/2b-sentinel-free-trial-guides.png)

---

## Task 3: Set up RBAC (least privilege)

| Role | Assigned to | Purpose |
|---|---|---|
| Microsoft Sentinel Responder | SOC Analysts | View data, incidents and workbooks; assign and dismiss incidents |
| Microsoft Sentinel Contributor | SOC Engineers | Create and edit workbooks and analytics rules; install and update content hub solutions |

Both roles were assigned at the `rg_eastus_soc` resource group scope.

**Responder role assigned to the SOC Analysts group (Review + assign):**

![Task 3a - Responder to SOC Analysts](images/3a-responder-soc-analysts-review.png)

**Contributor role assigned to the SOC Engineers group (assignment confirmation):**

![Task 3b - Contributor to SOC Engineers](images/3b-contributor-soc-engineers-added.png)

---

## Task 4: Review the steps to create a dashboard (workbook)
This task is informational because the new workspace has no data. I started building the workbook and added three parameters:

- **TimeRange** (time range picker, default Last 7 days)
- **AlertSeverity** (drop down, built from the `SecurityAlert` table)
- **ProductName** (drop down, built from the `SecurityAlert` table)

**TimeRange parameter (Azure portal):**

![Task 4a - TimeRange parameter](images/4a-workbook-timerange-parameter.png)

**All three parameters (Defender portal workbook editor):**

![Task 4b - All parameters](images/4b-workbook-all-parameters.png)

**Problems I ruin to:**
- The Defender portal's workbook editor did not show the **Add query** option, so I reviewed the incident and alert queries and the steps rather than building them.
- Steps that need data (Run Query, Column Settings, selecting an incident) were skipped, as the lab instructs, because the workspace has no data.

---

## Summary
I deployed a Log Analytics workspace and Microsoft Sentinel, then applied least-privilege RBAC with the Sentinel Responder role for analysts and the Sentinel Contributor role for engineers, and reviewed how to build an incidents and alerts workbook.
