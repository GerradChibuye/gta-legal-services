# GTA Legal Services Network

A secure and segmented enterprise network designed and implemented for a fictional legal services organization, **GTA Legal Services**.

This project demonstrates practical networking and network security concepts through the design, implementation, testing, and hardening of a multi-VLAN enterprise network.

---

## Project Overview

GTA Legal Services requires a network that can support different departments while maintaining **network segmentation, controlled communication, secure administration, and reliable internal services**.

The network was designed to separate users and resources into dedicated VLANs and provide controlled communication between those network segments.

The project was developed in **Cisco Packet Tracer** and follows a practical engineering workflow:

**Requirements → Design → Addressing → Implementation → Testing → Security → Troubleshooting → Documentation**

---

## Network Architecture

The network uses a **router-on-a-stick architecture** to provide inter-VLAN routing.

```text
                         ┌─────────────────┐
                         │    R1-EDGE      │
                         │     Router      │
                         └────────┬────────┘
                                  │
                           802.1Q Trunk
                                  │
                         ┌────────▼────────┐
                         │     SW1-CORE    │
                         │  Managed Switch │
                         └────────┬────────┘
                                  │
                    ┌─────────────┴─────────────┐
                    │                           │
              ┌─────▼─────┐               ┌─────▼─────┐
              │ SW2-ACCESS│               │  Servers   │
              │   Switch  │               │ & Services │
              └─────┬─────┘               └───────────┘
                    │
              End-user devices
```

The router provides the default gateway for each VLAN through 802.1Q subinterfaces.

---

## VLAN Design

The network is segmented according to organizational function.

| VLAN | Department / Function | Purpose                            |
| ---: | --------------------- | ---------------------------------- |
|   10 | ADMIN                 | Administrative users and resources |
|   20 | LAWYERS               | Legal staff and workstations       |
|   30 | FINANCE               | Financial operations               |
|   40 | GUEST                 | Guest and non-corporate access     |

Each VLAN represents a separate **broadcast domain**, providing logical separation between departments.

---

## Core Technologies

### Layer 2 Networking

* Ethernet switching
* VLANs
* Access ports
* Trunk ports
* 802.1Q
* Broadcast domains

### Layer 3 Networking

* IPv4 addressing
* Subnetting
* Inter-VLAN routing
* Router-on-a-Stick
* Default gateways
* DHCP

### Network Security

* Extended and standard ACL concepts
* Inter-VLAN access control
* SSH
* Secure device management
* Port security
* Sticky MAC addresses
* PortFast
* BPDU Guard
* Unused-port isolation

---

## Security Architecture

Security was introduced after establishing the basic working network.

The initial network demonstrated unrestricted connectivity between VLANs, allowing the security requirements and risks to be observed before controls were introduced.

The secured implementation then applied controls including:

### Access Control Lists

ACLs are used to restrict communication between network segments according to organizational requirements.

For example, guest users should not have unrestricted access to internal administrative or financial resources.

### Secure Management

Network-device administration is performed using **SSH** rather than insecure remote-management methods.

Management access is restricted so that only authorized administrative hosts can manage network infrastructure.

### Port Security

Switch access ports use port-security controls to restrict unauthorized devices.

Sticky MAC learning is used where appropriate to associate permitted endpoint MAC addresses with access ports.

### Edge-Port Protection

PortFast and BPDU Guard are applied to appropriate endpoint-facing interfaces to reduce the risk associated with unauthorized Layer 2 topology changes.

### Unused Ports

Unused switch interfaces are placed into an unused VLAN and administratively disabled where appropriate.

---

## DHCP

The router provides DHCP services for the internal VLANs.

This allows client devices to automatically receive:

* IP addresses
* Subnet masks
* Default gateways
* DNS information

This demonstrates how network addressing and infrastructure services work together rather than treating DHCP as an isolated configuration.

---

## Engineering Process

The project was developed incrementally.

### 1. Requirements

Identify the organization's departments, users, resources, and security requirements.

### 2. Network Design

Develop the physical and logical topology.

### 3. Addressing

Design the IPv4 addressing scheme and determine the gateway addresses for each VLAN.

### 4. VLAN Implementation

Create VLANs and assign appropriate switch access ports.

### 5. Inter-VLAN Routing

Implement Router-on-a-Stick using 802.1Q subinterfaces.

### 6. DHCP

Configure centralized DHCP services on the router.

### 7. Connectivity Testing

Verify:

* Host-to-host communication
* Host-to-gateway communication
* Inter-VLAN communication
* DHCP address assignment
* Trunk operation
* Routing

### 8. Security Hardening

Introduce:

* ACLs
* SSH
* Port security
* PortFast
* BPDU Guard
* Unused-port controls

### 9. Security Validation

Test whether the implemented controls actually enforce the intended access restrictions.

### 10. Documentation

Document the architecture, configuration, testing results, security controls, and lessons learned.

---

## Testing & Validation

Testing is performed at multiple levels.

### Connectivity

* Endpoint → default gateway
* Endpoint → endpoint
* VLAN → VLAN
* DHCP operation

### Routing

* Router subinterface status
* Routing table
* Inter-VLAN forwarding

### Switching

* VLAN membership
* Trunk configuration
* MAC address learning
* Access-port behavior

### Security

* Authorized communication
* Restricted communication
* SSH access
* Unauthorized device behavior
* Port-security violations

The objective is to verify the behavior of the network rather than simply confirm that configurations were entered successfully.

---

## Project Structure

```text
gta-legal-services/
│
├── README.md
│
├── topology/
│   ├── gta-legal-services.pkt
│   └── topology.png
│
├── configurations/
│   ├── R1.txt
│   ├── SW1.txt
│   └── SW2.txt
│
├── documentation/
│   ├── requirements.md
│   ├── network-design.md
│   ├── addressing-plan.md
│   ├── security-design.md
│   └── testing.md
│
└── screenshots/
    ├── topology/
    ├── connectivity/
    └── security/
```

The structure may evolve as the project documentation develops.

---

## What This Project Demonstrates

This project demonstrates practical understanding of:

* Enterprise LAN design
* Network segmentation
* IPv4 addressing
* VLAN architecture
* 802.1Q trunking
* Router-on-a-Stick
* Inter-VLAN routing
* DHCP
* ACL-based access control
* Secure network management
* Layer 2 security
* Network testing
* Troubleshooting
* Technical documentation

More importantly, it demonstrates an engineering approach of **designing a network around requirements and validating that the resulting infrastructure behaves as intended**.

---

## Lessons & Engineering Philosophy

The project follows the principle:

**Learn → Build → Break → Troubleshoot → Understand → Document → Share**

The goal is not simply to memorize Cisco commands.

It is to understand:

* Why the network is designed this way
* Why VLANs are required
* How devices communicate across VLANs
* How routing and switching interact
* Why security controls are necessary
* How configuration errors affect connectivity
* How to diagnose failures systematically
* How to document infrastructure clearly

---

## Technologies

**Cisco Packet Tracer**

**Cisco IOS**

**Ethernet**

**IPv4**

**VLANs**

**802.1Q**

**Router-on-a-Stick**

**DHCP**

**ACLs**

**SSH**

**Port Security**

**PortFast**

**BPDU Guard**

---

## Author

**Gerrad Chibuye (GC)**

Focus areas:

**Networking • Infrastructure • Security • Linux • Systems • Automation**

---

## Project Status

**Completed and documented as a practical enterprise networking and security project.**
