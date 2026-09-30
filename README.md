# ServiceNow Incident Lifecycle Automation & Workspace Management

An end-to-end IT Service Management (ITSM) implementation in ServiceNow demonstrating CMDB relationship mapping, Service Operations Workspace triage, automated incident escalation, emergency change management, child incident cascade resolution, and knowledge base capture.

---

## 📌 Project Overview

This project simulates a real-world enterprise IT service disruption scenario: a widespread remote VPN connection failure reported by end-users. The goal was to build a closed-loop incident management lifecycle in **ServiceNow Service Operations Workspace** that connects CMDB dependencies, reduces MTTR (Mean Time to Resolution), and automates multi-tier escalation and resolution inheritance.

### Key Highlights
* **CMDB Hierarchy:** Linked Business Service (`Remote Access`) with Service Offering (`Corporate VPN`).
* **Service Operations Workspace:** Streamlined agent triage, workspace navigation, and contextual AI via Agent Assist.
* **Multi-Tier Escalation:** L1 Service Desk triage, Work Notes documentation, and dynamic queue routing to L2 Network Engineering.
* **Emergency Change Hold:** Updated infrastructure CI (`PowerEdge`) and set ticket `On Hold` (`Awaiting Change`).
* **Parent-Child Cascade:** Linked concurrent user reports under a primary parent ticket to automate status propagation.
* **Knowledge Management:** Attached context-relevant KB articles during triage and generated a new Standard KB Article (`KB0000008`) upon resolution.

---

## 🛠️ System Architecture & Workflow
[ CMDB Setup ]
└── Business Service: Remote Access
└── Service Offering: Corporate VPN
└── Incident Logged: INC0010002 (Michael Hoefer)
│
├── L1 Triage (Beth Anglin) ──► Agent Assist KB Linked
│                               Watch Lists Populated
│                               Reassigned to Network Group
│
├── L2 Investigation (David Loo) ──► CI Updated to PowerEdge
│                                     State set to On Hold (Awaiting Change)
│                                     Child Incident Linked (INC0010005)
│
└── Resolution & Closure ──► Root Cause & Resolution Notes Logged
Parent Resolved ──► Child Auto-Resolved
Published KB Article (KB0000008)

---

## 🚀 Step-by-Step Execution Summary

### Phase 1: CMDB & Service Catalog Setup
1. Created Business Service **Remote Access** (`Operational`, `Business Service`).
2. Created Service Offering **Corporate VPN** under parent `Remote Access`.

### Phase 2: L1 Triage & Classification
1. Logged ticket **INC0010002** for caller *Michael Hoefer* in **Service Operations Workspace**.
2. Categorized under **Network / VPN**, Urgency **2 - Medium**, and targeted CI **ThinkStationS20**.
3. Logged initial triage work notes and claimed ticket ownership under L1 Agent *Beth Anglin*.

### Phase 3: Contextual AI & Multi-Tier Escalation
1. Scanned recommended solutions via **Agent Assist**, marked article as helpful, and attached it to the incident.
2. Added stakeholders to **Watch List** (*Samantha Bordwell*) and **Work Notes List** (*Beth Anglin*).
3. Reassigned ticket to **Network** group, clearing the individual assignee field for L2 queue routing.

### Phase 4: L2 Investigation & Infrastructure Emergency
1. Impersonated L2 Specialist *David Loo* and took ownership of the ticket.
2. Monitored active **Task SLAs** in workspace view.
3. Identified infrastructure dependency issue, updated target CI to **PowerEdge**, and placed record **On Hold** with reason **Awaiting Change**.

### Phase 5: Child Incident Linkage & Automated Resolution
1. Created/linked child ticket **INC0010005** under **Related Records**.
2. Documented Probable Cause (*PowerEdge service suspended*) and Resolution Notes (*Restarted VPN-SRV-02 service*).
3. Resolved parent ticket **INC0010002**, which **automatically cascaded the Resolved state down to child ticket INC0010005**.
4. Published a new Standard Knowledge Article (**KB0000008**) directly into the **IT Knowledge Base**.

---

## 🖼️ Verification & Artifacts

| Component | Status / Artifact | Verification |
| :--- | :--- | :--- |
| **Parent Incident** | `INC0010002` | State = **Resolved** |
| **Child Incident** | `INC0010005` | State = **Resolved** (Inherited) |
| **Business Service** | `Remote Access` | CMDB Operational |
| **Service Offering** | `Corporate VPN` | CMDB Operational |
| **Configuration Item** | `PowerEdge` | Infrastructure Updated |
| **SLA Tracking** | Response / Resolution | Task SLAs Active/Completed |
| **Knowledge Capture** | `KB0000008` | Published to IT KB |

---

## 👤 Author & Acknowledgments

* **Project Developer:** Mrudula
* **Platform:** ServiceNow (Service Operations Workspace)
* **Role Simulation:** Beth Anglin (L1 Service Desk Agent), David Loo (L2 Network Engineer), Michael Hoefer (End User)
