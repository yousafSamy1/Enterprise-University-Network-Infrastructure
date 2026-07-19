# 🌐 Enterprise University Network Infrastructure & Simulation

![Cisco Packet Tracer](https://img.shields.io/badge/Cisco_Packet_Tracer-v8.x-005073?logo=cisco&logoColor=white)
![Network Architecture](https://img.shields.io/badge/Architecture-Hierarchical_Partial_Mesh-blue)
![License](https://img.shields.io/badge/Academic_Project-ERU_MIS-green)

A comprehensive enterprise network architecture designed and simulated for the **Egyptian Russian University (ERU)** campus using **Cisco Packet Tracer**. 

This project simulates a multi-building university campus network connecting student labs, faculty wings, central administration, and a dedicated high-availability datacenter server farm across distinct subnets and VLAN routing domains.

---

## 🏛️ Campus Architecture & Subnets

The network spans **6 distinct campus zones** interconnected via a multi-router hierarchical backbone with **Router2** serving as the core datacenter router:

| Campus Zone / Department | Subnet Range | Key Devices & Hardware | Domain / Services |
| :--- | :--- | :--- | :--- |
| **Main Campus Administration** | `192.168.7.0/24` | 18 Student PCs, Switch0, Router0 | `eru.edu.eg` |
| **Faculty of Computer & Info (FCI)** | `192.168.2.0/24` | 18 Student PCs, Switch1, Router1 | `fci.eru.edu.eg` |
| **Datacenter / Central Server Farm** | `192.168.3.0/24` | 8 Enterprise Servers, Switch2, Core Router2 | Core Services Farm |
| **Campus Right Wing** | `192.168.6.0/24` | 17 Student PCs, 2 Printers, Switch5, Router5 | `lms.eru.edu.eg` |
| **University Library Building** | `192.168.4.0/24` | 12 Student PCs, 1 Printer, Local Library Server, Switch3, Router3 | `library.eru.edu.eg` |
| **Annex / Extended Computer Lab** | `192.168.5.0/24` | 2 Student PCs, 1 Printer, Switch4, Router4 | Extended Lab Access |

---

## 🖥️ Datacenter Services (`192.168.3.0/24`)

The central datacenter hosts key network services accessible across all campus subnets:

* 🌐 **DNS Server (`192.168.3.4`)**: Central domain name resolution mapping:
  * `eru.edu.eg` → `192.168.3.6` (Main University Portal)
  * `fci.eru.edu.eg` → `192.168.3.7` (Faculty Portal)
  * `library.eru.edu.eg` → `192.168.3.8` (Library Catalog System)
  * `students.eru.edu.eg` → `192.168.3.9` (Student Information System)
  * `lms.eru.edu.eg` → `192.168.3.10` (Learning Management System)
  * `smtp.eru.edu.eg` → `192.168.3.5` (Mail Server)
* 📡 **DHCP Server (`192.168.3.3`)**: Automated dynamic IP configuration for all campus client PCs using **DHCP Relay Agents** (`ip helper-address`) configured on all sub-interfaces.
* 📧 **SMTP Mail Server (`192.168.3.5`)**: Handles internal email communication across `eru.edu.eg` domain accounts.
* 💻 **Web Server Cluster**: Dedicated HTTP web server instances hosting the university portals and LMS services.

---

## 📐 Network Topologies & Protocols

1. **Departmental LANs (Star Topology)**: Each department connects end devices (PCs, laptops, printers) directly to central Cisco switches (Switch0–Switch5), ensuring fault isolation and simple scalability.
2. **Campus Inter-Routing (Hierarchical / Partial Mesh Topology)**: Multi-router WAN links configured between department routers and the core router to optimize inter-subnet routing and provide redundancy paths.
3. **Cabling Standards**:
   * **Straight-Through Cable**: Switch-to-PC, Switch-to-Printer, and Switch-to-Router uplink connections.
   * **Crossover Cable / Auto-MDIX**: Inter-router WAN link connections.

---

## 🛠️ Simulation & Verification

The topology file (`Enterprise University Network Infrastructure.pkt`) includes verification configurations:
* ✅ **End-to-End ICMP Connectivity**: Successful ping tests between all client PCs across different subnets.
* ✅ **DHCP Lease Allocation**: Automated IP address assignment across all client pools.
* ✅ **HTTP/DNS Web Browsing**: Verified domain access to LMS, Library, and Student portals from client web browsers.
* ✅ **SMTP Email Routing**: Verified email sending and receiving between student accounts.

---

## 📁 Repository Contents

* 📄 `Enterprise University Network Infrastructure.pdf`: Complete technical design report and documentation.
* 🧪 `Enterprise University Network Infrastructure.pkt`: Cisco Packet Tracer topology simulation file.

---

## 👤 Author & Academic Info

* **Author:** Yousef Samy
* **Department:** Management Information Systems (MIS)
* **Institution:** Egyptian Russian University (ERU) — Faculty of Management, Economics and Business Technology
* **Supervision:** Dr. Ola Ayman & Dr. Abdelfattah Ayman
* **Tool:** Cisco Packet Tracer
