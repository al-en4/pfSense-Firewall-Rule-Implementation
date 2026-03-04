
# 🔐 Firewall Rule Implementation using pfSense

## 📌 Project Overview

This project demonstrates how to configure a firewall and implement network access control rules using **pfSense** in a virtual lab environment created with **Oracle VM VirtualBox**.

The objective of this project is to simulate how organizations use firewall policies to control user access to specific websites. In this lab, firewall rules are created to block access to the social media platform **Facebook** from a client machine inside the network.

This project demonstrates practical skills in:

* Firewall configuration
* Network segmentation
* Website filtering
* Security policy enforcement

Such implementations are commonly used in enterprise environments to enforce **organizational internet usage policies and improve network security**.

---

# 🎯 Objectives

* Deploy a firewall using pfSense in a virtual environment
* Configure WAN and LAN network interfaces
* Enable DHCP service for client machines
* Implement firewall rules to block access to a specific website
* Test and verify firewall rule enforcement

---

# 🧰 Tools & Technologies Used

| Tool       | Purpose                                   |
| ---------- | ----------------------------------------- |
| pfSense    | Firewall and network security platform    |
| VirtualBox | Virtual lab virtualization environment    |
| Ubuntu     | Client machine for testing network access |

---

# 🖥️ Lab Architecture

The lab environment consists of two virtual machines:

1️⃣ **Firewall Machine**

* pfSense installed
* Handles traffic filtering and network routing

2️⃣ **Client Machine**

* Ubuntu operating system
* Used to test network access policies

Network structure:

```
Internet (WAN)
      │
      │
  pfSense Firewall
      │
      │
Internal Network (LAN)
      │
      │
 Ubuntu Client Machine
```

The firewall monitors and filters all network traffic between the client machine and external networks.

---

# ⚙️ Virtual Machine Configuration

## pfSense Firewall VM

* RAM: 1 GB
* Network Adapter 1: NAT (WAN)
* Network Adapter 2: Internal Network (LAN)

Internal Network Name:

```
INTNET
```

---

## Ubuntu Client VM

* RAM: 2 GB
* Network Adapter: Internal Network

Network Name:

```
INTNET
```

This allows the Ubuntu client to communicate with the pfSense LAN interface.

---

# 🌐 Network Configuration

LAN Interface Configuration in pfSense:

```
LAN IP Address: 192.168.1.1
Subnet Mask: 24
Network: 192.168.1.0/24
```

DHCP configuration:

```
DHCP Range:
192.168.1.100 – 192.168.1.200
```

The Ubuntu client automatically receives an IP address from this range.

Example client IP:

```
192.168.1.101
```

---

# 🔐 Firewall Rule Implementation

To restrict access to specific websites, a firewall rule was created to block traffic to **Facebook**.

## Step 1: Create Alias

Navigate to:

```
Firewall → Aliases
```

Create an alias named:

```
facebook_block
```

Add the following domains:

```
facebook.com
www.facebook.com
m.facebook.com
```

Aliases help group multiple addresses under a single name for easier firewall rule management.

---

## Step 2: Create Firewall Rule

Navigate to:

```
Firewall → Rules → LAN
```

Add a new rule with the following settings:

| Parameter   | Value          |
| ----------- | -------------- |
| Action      | Block          |
| Interface   | LAN            |
| Protocol    | Any            |
| Source      | LAN Network    |
| Destination | facebook_block |

This rule blocks any LAN client from accessing the Facebook domain.

---

# 🧪 Testing the Firewall Rule

Testing was performed using the Ubuntu client machine.

### Step 1

Open a web browser.

### Step 2

Attempt to access:

```
https://facebook.com
```

### Step 3

The connection fails because the firewall rule blocks the request.

---

# 📊 Firewall Logs Verification

Blocked traffic can be verified in pfSense logs.

Navigate to:

```
Status → System Logs → Firewall
```

The logs show blocked connections to Facebook domains from the client IP address.

This confirms that the firewall rule is functioning correctly.

---

# screenshots

## pfSense Dashboard

![pfSense Dashboard]screenshot/VirtualBox_pfSense_03_03_2026_22_31_40.png



---

# ✅ Results

The firewall rule successfully prevented the client machine from accessing Facebook while allowing other network traffic.

This demonstrates how pfSense can be used to enforce **internet usage policies and control access to specific web services within a network**.

---

# 📚 Key Learning Outcomes

Through this project, the following concepts were learned:

* Firewall configuration and management
* Network interface configuration
* DHCP service configuration
* Website filtering using firewall rules
* Network traffic monitoring and log analysis

---

# 🚀 Future Improvements

Possible improvements to this lab include:

* Blocking multiple social media platforms
* Implementing URL filtering
* Integrating intrusion detection systems
* Monitoring traffic using a SIEM platform

---

# 👨‍💻 Author

Cybersecurity Lab Project
Firewall Rule Implementation using pfSense
