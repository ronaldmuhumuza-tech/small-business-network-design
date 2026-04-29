# Phase 02 – Inter-VLAN Routing

## Objective

The objective of this phase is to enable communication between VLANs by implementing router-on-a-stick on R1.

This allows devices in different VLANs to communicate through a central routing point while maintaining logical separation at Layer 2.

---

## Router Trunk Configuration

The link between SW1 and R1 was configured as a trunk to carry traffic for multiple VLANs.

* SW1 G0/1 ↔ R1 G0/0
* Trunk encapsulation: 802.1Q
* Allowed VLANs: 10, 20, 30, 40

This ensures that VLAN-tagged traffic can be forwarded to the router for processing.

Relevant configuration can be found in:

* SW1: `configs/SW1.txt`

---

## Router Subinterfaces

Subinterfaces were created on R1 to handle traffic for each VLAN. Each subinterface is associated with a specific VLAN and acts as the default gateway for that subnet.

* G0/0.10 → VLAN 10 → 192.168.10.1
* G0/0.20 → VLAN 20 → 192.168.20.1
* G0/0.30 → VLAN 30 → 192.168.30.1
* G0/0.40 → VLAN 40 → 192.168.40.1

Each subinterface was configured with 802.1Q encapsulation to match its corresponding VLAN.

Relevant configuration can be found in:

* R1: `configs/R1.txt`

---

## Host Addressing

Temporary static IP addressing was configured on each host to allow connectivity testing before DHCP is introduced in the next phase.

Each device was assigned:

* An IP address within its VLAN subnet
* A default gateway corresponding to the router subinterface

This allows traffic to be forwarded to the router for inter-VLAN communication.

---

## Verification

The following checks were performed to validate the configuration:

* `show interfaces trunk` (SW1)
* `show ip interface brief` (R1)
* Ping tests between devices in different VLANs

Successful ping results confirmed that:

* The trunk link between SW1 and R1 is operational
* Router subinterfaces are active
* Inter-VLAN routing is functioning correctly

Screenshots of verification outputs are available in the `/screenshots` directory.

---

## Notes

At this stage, communication between VLANs is unrestricted, as no access control policies have been applied.

This phase establishes Layer 3 connectivity across the network and prepares the environment for the introduction of DHCP and security controls in later phases.
