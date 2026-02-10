# BLG Company Ltd. Network Design and Implementation
## Project  Overview
This project focuses on designing and implementing a secure, scalable, and efficient enterprise network for **BLG Company**, a growing organization expanding its operations into a new branch located in **Metro Manila, Philippines**. The facility spans multiple floors, each dedicated to different departments such as Management, Research, Human Resources, Finance, and IT Support.

The goal is to establish a network infrastructure that supports both wired and wireless connectivity, ensures seamless communication between departments, and provides strong security measures to protect sensitive company data.

## Case Study Requirement
BLG Company  outlined the following key requirements for the network setup:
  * **Hierarchical Network Design:**  The network must follow a three-tier hierarchical model (Core, Distribution, Access) to ensure scalability, manageability, and performance.
  * **Simulation Environment:** Cisco Packet Tracer will be used to simulate the design, configuration, and testing of the network.
  * **Routing Protocol:** OSPF (Open Shortest Path First) will be configured to dynamically advertise routes across the network.
  * **Wireless Connectivity:** Each department will be equipped with wireless access points to support mobile and non-wired devices.
  * **Dynamic IP Allocation:** A centralized DHCP server will dynamically assign IP addresses to hosts across all VLANs.
  * **VLAN Segmentation:** Each department will be assigned its own VLAN for isolation, improved security, and efficient traffic management.
  * **Server Deployment:** HTTP Server for internal web services, DHCP Server for IP allocation, Email Server for internal communication
  *  **Remote Access Security:** SSH will be configured on all routers to enable secure remote login and management.
  *  **Port Security:** Switches will be configured with sticky MAC and shutdown violation mode to prevent unauthorized access.
  *  **Basic Configuration Standards:** All devices will be configured with hostnames, password encryption, banners, and DNS lookup disabled.
  *  **Inter-VLAN Routing:** Multilayer switches will be configured with Switch Virtual Interfaces (SVIs) to enable communication between VLANs.

## Network Topology
The network topology is structured hierarchically across four floors, with each floor hosting distinct departments—segmented into VLANs, supported by centralized servers, and provisioned with secure wired and wireless connectivity for staff and guests.

### 🏢 Floor-Wise Department Layout

| Floor | Department(s) | No. of PCs (min 20 per dept.) | Guest PCs (50 per floor) | Printers (4 per floor) | Servers |
|-------|---------------|-------------------------------|---------------------------|-------------------------|---------|
| **Ground Floor (Floor 1)** | Reception, Customer Service, Security Office | 20 (Reception), 20 (Customer Service), 20 (Security) | 50 | 4 | – |
| **Second Floor (Floor 2)** | Management, Finance & Accounting, Loan Services | 20 (Management), 20 (Finance), 20 (Loans) | 50 | 4 | – |
| **Third Floor (Floor 3)** | Human Resources, Marketing, Guest Area | 20 (HR), 20 (Marketing), 20 (Training) | 50 (Guest PCs) | 4 | – |
| **Fourth Floor (Floor 4)** | IT Support, Administration, Server Room | 20 (IT), 20 (Admin), 2 (Admin PCs in Server Room) | 50 | 4 | 3 (DHCP, HTTP, Email) |

### 🔐VLAN  Assignment:
Each department is assigned its own VLAN to ensure network segmentation:

| VLAN ID | Department        | Subnet            | IP Range                        | Broadcast Address |
|---------|-------------------|-------------------|---------------------------------|-------------------|
| 10      | Reception         | 192.168.10.0/26   | 192.168.10.1 – 192.168.10.62    | 192.168.10.63     |
| 20      | Customer Service  | 192.168.10.64/26  | 192.168.10.65 – 192.168.10.126  | 192.168.10.127    |
| 30      | Security Office   | 192.168.10.128/26 | 192.168.10.129 – 192.168.10.190 | 192.168.10.191    |
| 40      | Management        | 192.168.10.192/26 | 192.168.10.193 – 192.168.10.254 | 192.168.10.255    |
| 50      | Finance           | 192.168.11.0/26   | 192.168.11.1 – 192.168.11.62    | 192.168.11.63     |
| 60      | Accounting        | 192.168.11.64/26  | 192.168.11.65 – 192.168.11.126  | 192.168.11.127    |
| 70      | Loan Services     | 192.168.11.128/26 | 192.168.11.129 – 192.168.11.190 | 192.168.11.191    |
| 80      | HR                | 192.168.11.192/26 | 192.168.11.193 – 192.168.11.254 | 192.168.11.255    |
| 90      | Marketing         | 192.168.12.0/26   | 192.168.12.1 – 192.168.12.62    | 192.168.12.63     |
| 100     | Guest Area        | 192.168.12.64/26  | 192.168.12.65 – 192.168.12.126  | 192.168.12.127    |
| 110     | IT Support        | 192.168.12.128/26 | 192.168.12.129 – 192.168.12.190 | 192.168.12.191    |
| 120     | Administration    | 192.168.12.192/26 | 192.168.12.193 – 192.168.12.254 | 192.168.12.255    |
| 130     | Server Room       | 192.168.13.0/26   | 192.168.13.1 – 192.168.13.62    | 192.168.13.63     |

## IP Addressing and Subnetting
The base network address is **192.168.10.0**, subnetted to accommodate each department.  
Each department is assigned a unique VLAN with its own subnet, IP range, and broadcast address.

| VLAN ID | Department        | Subnet            | IP Range                        | Broadcast Address |
|---------|-------------------|-------------------|---------------------------------|-------------------|
| 10      | Reception         | 192.168.10.0/26   | 192.168.10.1 – 192.168.10.62    | 192.168.10.63     |
| 20      | Customer Service  | 192.168.10.64/26  | 192.168.10.65 – 192.168.10.126  | 192.168.10.127    |
| 30      | Security Office   | 192.168.10.128/26 | 192.168.10.129 – 192.168.10.190 | 192.168.10.191    |
| 40      | Management        | 192.168.10.192/26 | 192.168.10.193 – 192.168.10.254 | 192.168.10.255    |
| 50      | Finance           | 192.168.11.0/26   | 192.168.11.1 – 192.168.11.62    | 192.168.11.63     |
| 60      | Accounting        | 192.168.11.64/26  | 192.168.11.65 – 192.168.11.126  | 192.168.11.127    |
| 70      | Loan Services     | 192.168.11.128/26 | 192.168.11.129 – 192.168.11.190 | 192.168.11.191    |
| 80      | HR                | 192.168.11.192/26 | 192.168.11.193 – 192.168.11.254 | 192.168.11.255    |
| 90      | Marketing         | 192.168.12.0/26   | 192.168.12.1 – 192.168.12.62    | 192.168.12.63     |
| 100     | Guest Area        | 192.168.12.64/26  | 192.168.12.65 – 192.168.12.126  | 192.168.12.127    |
| 110     | IT Support        | 192.168.12.128/26 | 192.168.12.129 – 192.168.12.190 | 192.168.12.191    |
| 120     | Administration    | 192.168.12.192/26 | 192.168.12.193 – 192.168.12.254 | 192.168.12.255    |
| 130     | Server Room       | 192.168.13.0/26   | 192.168.13.1 – 192.168.13.62    | 192.168.13.63     |


## Network Implementation
1. **VLAN Configuration** – Each department is assigned a unique VLAN; switch ports are mapped accordingly.  
2. **IP Addressing** – DHCP server allocates dynamic IPs per VLAN.  
3. **Routing Protocol** – OSPF configured for dynamic route advertisement.  
4. **Remote Access** – SSH enabled on routers for secure management.  
5. **Port Security** – Sticky MAC with violation mode set to *shutdown*.  
6. **Wireless Access** – Access Points deployed per floor for mobile devices.  


### Device Configurations
- **Routers** – Hostname, OSPF, SSH, and security hardening.  
- **Switches** – VLANs, port security, and access port assignments.  
- **Servers** – DHCP, HTTP, and Email services centralized in the Server Room.

### ✅ Testing and Verification

To ensure the network functions correctly, the following tests were conducted:

- **Ping Test** – Verified communication between devices across different VLANs.
- **DHCP Test** – Confirmed that hosts automatically obtained IP addresses from the DHCP server.
- **SSH Test** – Tested secure remote login into routers using SSH.
- **Port Security Test** – Checked that unauthorized devices triggered port shutdown as expected.

### ⚙️ Technologies and Features Used

The project implementation utilized the following tools and configurations:

- **Cisco Packet Tracer** for simulation and design.
- **Hierarchical Network Design** for scalability and manageability.
- **OSPF Routing** for dynamic route advertisement.
- **VLAN Configuration & Inter-VLAN Routing** for segmentation and communication.
- **DHCP** for dynamic IP allocation across departments.
- **SSH** for secure remote management of routers.
- **Switchport Security** with sticky MAC and shutdown violation mode.
- **Wireless Networks (WLAN)** with Access Points for mobile devices.
- **Testing & Troubleshooting** using Cisco tools and commands.

### ▶️ How to Run

1. **Open the Network Simulation File**  
   Launch **Cisco Packet Tracer** or **GNS3** and open the project file.

2. **Verify Device Configurations**  
   - Confirm VLANs, IP addressing scheme, and basic configurations on all switches, routers, and access points.  
   - Ensure SSH, DHCP, and OSPF configurations are active.

3. **Access Network Devices**  
   - To log into any router or switch, use the password **cisco** for console, VTY (SSH), and enable mode.

4. **Test Network Connectivity**  
   - Ping devices across different VLANs to verify successful inter‑VLAN routing.  
   - Check that all hosts obtain IP addresses dynamically via DHCP.  
   - Test remote access to routers via SSH using the password **cisco**.

5. **Test Servers**  
   - Open a browser on any end device and access the **HTTP server** using its IP address.  
   - Configure an email client on any device to connect to the **Email server** for testing.

6. **Monitor Security**  
   - Check port‑security settings on switches to confirm sticky MAC configurations.  
   - Verify that unauthorized devices trigger port shutdown as expected.

---

✅ With these steps complete, the network should be fully operational and secure, enabling seamless communication between all departments.
