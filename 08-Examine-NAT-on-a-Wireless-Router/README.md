# Packet Tracer – Examine NAT on a Wireless Router

## Overview
This lab explores Network Address Translation (NAT) on a wireless router in Cisco Packet Tracer. It demonstrates how a router connects a private internal network to an external network and translates private IP addresses when traffic crosses the router.

## Objectives
- Examine NAT configuration on a wireless router.
- Connect four PCs to a wireless router using DHCP.
- Identify public and private IP addresses.
- Observe traffic crossing the network using NAT.
- Examine packet headers before and after address translation.

## Background
Network Address Translation (NAT) translates IP addresses between an internal network and an external network. Private IP addresses are commonly used within local networks and are not directly routable over the public Internet.

A wireless router can use NAT to translate the private source IP address of an internal device into its public-facing IP address when sending traffic to an external server. This allows multiple internal devices to share a public IP address.

## Network Topology

![NAT Wireless Router Topology](images/topology.png)

## Lab Procedure

### Part 1: Examine the External Network Configuration
1. Connect one PC to the wireless router using a straight-through cable.
2. Open the PC's **Desktop → IP Configuration** and select **DHCP**.
3. Record the default gateway address.
4. Open the browser and enter the gateway address.
5. Log in using the credentials specified in the lab instructions.
6. Open the router's **Status** page and locate the Internet connection IP address.
7. Determine whether the Internet-facing address is public or private.

![Public IP Address](images/01-public-ip-address.png)

### Part 2: Examine the Internal Network Configuration
1. Open the router's **Status → Local Network** section.
2. Record the internal network IP address.
3. Examine the DHCP server settings and the address range assigned to clients.
4. Determine whether the internal addresses are private or public.

![Private IP Address](images/02-private-ip-address.png)

### Part 3: Connect Four PCs
1. Connect four PCs to the wireless router using straight-through cables.
2. On each PC, open **Desktop → IP Configuration**.
3. Select **DHCP** to obtain an IP address automatically.
4. Use `ipconfig /all` in the Command Prompt to inspect the network configuration.
5. Confirm that the PCs receive private IP addresses.

![PC DHCP Configuration](images/03-pc-dhcp-configuration.png)

### Part 4: Observe NAT Translation
1. Switch to **Simulation Mode**.
2. Open **Edit Filters** and select TCP and HTTP under the Misc tab, as specified in the activity.
3. Select **Add Complex PDU**.
4. Click one of the PCs to set it as the source.
5. Set the application to **HTTP**.
6. Select the `cisc learn.nat.com` server shown in your activity as the destination. Use the exact server name displayed in Packet Tracer.
7. Set the source port to `1000` and the periodic interval to `120` seconds.
8. Click **Create PDU**, then click **Play** to observe the traffic.

![Simulation Event List](images/04-simulation-event-list.png)

### Part 5: Examine Packet Headers
1. Select an event in the Simulation Panel and open its PDU details.
2. Inspect the **Inbound PDU Details** and note the source and destination IP addresses.
3. Inspect the **Outbound PDU Details** and compare the addresses.
4. Observe how the source IP address changes when traffic crosses the router.
5. Examine other events to follow the translation process.
6. Click **Check Results** when finished.

![Inbound PDU Details](images/05-inbound-pdu-details.png)

![Outbound PDU Details](images/06-outbound-pdu-details.png)

## Key Concepts

- **NAT:** Translates IP addresses as traffic passes between networks.
- **Private IP address:** Used within a local network and not directly routable on the public Internet.
- **Public IP address:** Used for routing across the public Internet.
- **DHCP:** Automatically assigns IP configuration to network devices.
- **Inbound PDU:** Shows packet information entering a device.
- **Outbound PDU:** Shows packet information leaving a device.
- **Source address translation:** Changes the source IP address of outgoing traffic when NAT is applied.

## Results
The activity demonstrates the difference between internal private addressing and external addressing. It also shows how packet headers can be inspected to observe NAT translation as traffic passes through the wireless router.

## Conclusion
This lab provides practical experience with NAT, DHCP, and packet inspection in Cisco Packet Tracer. By comparing inbound and outbound PDU information, the effect of NAT on source IP addresses can be understood.

---

**Tool:** Cisco Packet Tracer  
**Lab:** Examine NAT on a Wireless Router
