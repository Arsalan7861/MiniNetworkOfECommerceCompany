# E-Commerce Network Infrastructure Design

This project outlines the network infrastructure design for an e-commerce company, ensuring secure and efficient communication across multiple locations.

---

## Locations and Setup

### Headquarters (Istanbul)
- **Structure:**
  - Main_Router → Multilayer Switch
  - Multilayer Switch → Istanbul_Switch_1
  - Multilayer Switch → Istanbul_Switch_2
  - Istanbul_Switch_1 → Manager PC
  - Istanbul_Switch_1 → Server
  - Istanbul_Switch_2 → User PC
  - Istanbul_Switch_2 → Guest PC

### Warehouses
- **Locations:** Ankara and Bursa
- **Structure:**
  - Main_Router → Warehouse_Assistant_Router
  - Warehouse_Assistant_Router → Ankara_Router
  - Warehouse_Assistant_Router → Bursa_Router
  - Ankara_Router → Ankara_Switch
    - Ankara_Switch → Ankara_PC
    - Ankara_Switch → Ankara_Warehouse_Server
  - Bursa_Router → Bursa_Switch
    - Bursa_Switch → Bursa_PC
    - Bursa_Switch → Bursa_Warehouse_Server

### Sales Offices
- **Locations:** Izmir and Gaziantep
- **Structure:**
  - Main_Router → Sales_Assistant_Router
  - Sales_Assistant_Router → Izmir_Router
  - Sales_Assistant_Router → Gaziantep_Router
  - Izmir_Router → Izmir_Switch
    - Izmir_Switch → Izmir_PC
    - Izmir_Switch → Izmir_Sales_Server
  - Gaziantep_Router → Gaziantep_Switch
    - Gaziantep_Switch → Gaziantep_PC
    - Gaziantep_Switch → Gaziantep_Sales_Server

---

## IP Distribution and VLAN Configuration

### Headquarters (Istanbul)
- **Manager VLAN:** `10.0.10.0/24`
- **Server VLAN:** `10.0.20.0/24`
- **User VLAN:** `10.0.30.0/24`
- **Guest VLAN:** `10.0.40.0/24`

### Warehouses
- **Ankara Warehouse VLAN:** `192.168.1.0/24`
- **Bursa Warehouse VLAN:** `192.168.2.0/24`

### Sales Offices
- **Izmir Office VLAN:** `172.16.1.0/24`
- **Gaziantep Office VLAN:** `172.16.2.0/24`

---

## HTML Files and HTTP Servers

### Warehouses
- **Ankara Warehouse:** Hosts the `Ankara_Warehouse.html` file on its HTTP server (**Ankara_Warehouse_Server**).
- **Bursa Warehouse:** Hosts the `Bursa_Warehouse.html` file on its HTTP server (**Bursa_Warehouse_Server**).

### Sales Offices
- **Izmir Sales Office:** Hosts the `Izmir_Sales.html` file on its HTTP server (**Izmir_Sales_Server**).
- **Gaziantep Sales Office:** Hosts the `Gaziantep_Sales.html` file on its HTTP server (**Gaziantep_Sales_Server**).

*Note: HTML files are available on the project announcement page.*

---

## Access Rules

### Headquarters Access
- **Manager VLAN:** Full access to all networks.
- **User VLAN:** Full access to all networks.
- **Guest VLAN:** Restricted to Headquarters only; cannot communicate with other networks.

### Warehouse Access
- **Ankara and Bursa:** Can only access Headquarters.

### Sales Office Access
- **Izmir and Gaziantep:** Can only access Headquarters.

### HTTP Server Access
- From **Istanbul Headquarters**:
  - **Manager PCs** and **User PCs** can access all HTTP servers.
  - **Guest PCs** are restricted from accessing HTTP servers.
- From **Warehouses and Sales Offices**:
  - Each location can access only its own HTTP server.
  - Access to other locations' HTTP servers is restricted.
  
## Prerequisites
- Cisco Packet Tracer : version ->  8.2.1.0118
