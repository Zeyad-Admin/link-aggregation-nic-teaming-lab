# Link Aggregation & NIC Teaming Lab

---

## 📌 Objective

The objective of this lab is to demonstrate how **Link Aggregation (LAG)** and **NIC Teaming** combine multiple physical network connections into a single logical interface to:

* Increase available bandwidth
* Provide redundancy and failover
* Improve network reliability and performance

---

## 🧠 Concept Overview

Link Aggregation is a networking technique that groups multiple physical links into a single logical connection.

### Key Benefits:

* **Increased Bandwidth** → Multiple links combined (e.g., 4 × 1 Gbps = 4 Gbps)
* **Redundancy** → If one link fails, traffic continues on remaining links
* **Load Balancing** → Traffic is distributed across multiple interfaces

---

### Terminology

| Term                         | Description                         |
| ---------------------------- | ----------------------------------- |
| LAG (Link Aggregation Group) | Logical grouping of multiple links  |
| NIC Teaming                  | Server-side link aggregation        |
| EtherChannel                 | Cisco implementation of LAG         |
| Bonding                      | Linux term for link aggregation     |
| LACP (802.3ad / 802.1ax)     | Protocol used to manage aggregation |

---

## ⚙️ Environment

| Role   | Hostname    | OS                  | Description                   |
| ------ | ----------- | ------------------- | ----------------------------- |
| Server | SRV-LAG01   | Windows Server      | NIC Teaming configured        |
| Client | CL-TEST01   | Windows 10          | Connectivity testing          |
| Switch | vSwitch-LAB | Hyper-V / Simulated | Logical switching environment |

---

## 🛠️ Technologies Used

* Link Aggregation (LAG)
* NIC Teaming
* LACP (IEEE 802.3ad / 802.1ax)
* Hyper-V Virtual Networking
* Windows Server NIC Teaming

---

## 🔧 Lab Implementation

### Step 1: Create Multiple Network Adapters

Multiple virtual network adapters were created to simulate multiple physical links.

![Create Adapters](screenshots/LAG_S01_Create_Adapters.png)

---

### Step 2: Configure NIC Teaming

NIC Teaming was configured on the server to combine multiple interfaces into a single logical adapter.

![NIC Teaming](screenshots/LAG_S02_NIC_Teaming.png)

---

### Step 3: Assign Teaming Mode

Configured the teaming mode (Switch Independent / LACP depending on scenario).

![Teaming Mode](screenshots/LAG_S03_Teaming_Mode.png)

---

### Step 4: Verify Team Status

Verified that all adapters are active and part of the team.

![Team Status](screenshots/LAG_S04_Status.png)

---

### Step 5: Test Failover

Disabled one adapter to simulate failure and verified connectivity remained active.

![Failover Test](screenshots/LAG_S05_Failover.png)

---

## ✅ Verification

* Confirmed multiple adapters are combined into one logical interface
* Verified network connectivity using ping tests
* Tested failover by disabling one interface
* Observed no network interruption during link failure

---

## 🔍 Key Concepts Demonstrated

* Aggregation of bandwidth using multiple links
* Redundancy and fault tolerance
* Logical vs physical interfaces
* LACP negotiation behavior

---

## ⚠️ Important Notes

* LACP requires at least one side to be set to **active**
* Passive + Passive configuration will NOT form a link
* Full redundancy depends on bandwidth requirements
* All links in the group must have matching speed and duplex settings

---

## 🧠 Real-World Use Case

Link aggregation is commonly used in:

* Data center uplinks
* Switch-to-switch connections
* Server high availability configurations
* Enterprise core network design

---

## 🎯 Key Takeaways

* Link aggregation improves both **performance and availability**
* NIC teaming allows servers to maintain connectivity during failures
* Proper configuration is required to avoid negotiation issues
* LACP helps detect and manage link failures automatically

---

## 📂 Repository Structure

```text
link-aggregation-nic-teaming-lab/
│
├── README.md
└── screenshots/
    ├── LAG_S01_Create_Adapters.png
    ├── LAG_S02_NIC_Teaming.png
    ├── LAG_S03_Teaming_Mode.png
    ├── LAG_S04_Status.png
    └── LAG_S05_Failover.png
```

---

## 🚀 Author

**Zeyad Al Mahmoudi**
BCIT Technology Support Professional (TSP) Student
Focus: Networking | Systems Administration | Azure

---
