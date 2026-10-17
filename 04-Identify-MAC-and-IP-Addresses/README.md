# Packet Tracer – Identify MAC and IP Addresses

## Overview

This Cisco Packet Tracer lab demonstrates how MAC addresses and IPv4 addresses are used when devices communicate over a network. Using Simulation Mode, we inspect the details of Protocol Data Units (PDUs) as they travel between devices on the same local network and between devices on different networks.

## Objectives

- Gather PDU information for local network communication.
- Gather PDU information for remote network communication.
- Identify source and destination MAC addresses.
- Identify source and destination IPv4 addresses.
- Understand how switches and routers handle Ethernet frames and IP packets.

## Tools and Technologies

- Cisco Packet Tracer
- IPv4 addressing
- Ethernet and MAC addressing
- ICMP (`ping`)
- Simulation Mode
- OSI model

## Network Topology

### Part 1: Local Network Communication

The first topology contains two PCs on the same local network, connected through a switch. The activity uses PC `172.16.31.3` to ping PC `172.16.31.2`.

![Local network topology](images/topology.png)

### Part 2: Remote Network Communication

The second topology contains devices on different IP networks connected through switches, an access point, and a router. The activity uses PC `172.16.31.3` to ping the remote host `10.10.10.2`.

![Remote network topology](images/topology.png)

## Part 1: Gather PDU Information for Local Network Communication

### Procedure

1. Open PC `172.16.31.3` and launch Command Prompt.
2. Run the command:

   ```text
   ping 172.16.31.2
   ```

3. Switch to **Simulation Mode** and repeat the ping command.
4. Select the PDU envelope that appears beside the source PC.
5. Inspect the **OSI Model** and **Outbound PDU Details** tabs.
6. Record the source and destination MAC and IPv4 addresses.
7. Use **Capture / Forward** to follow the PDU through the switch until it reaches the destination.

### Observations

For local communication, the source and destination PCs belong to the same IP network. The source sends an Ethernet frame addressed to the destination PC's MAC address. The switch forwards the frame toward the correct port.

The IPv4 source and destination addresses identify the two communicating PCs. Because the destination is on the same local network, the source does not need to send the frame to the default gateway.

**Example addressing from the activity:**

| Field | Value |
|---|---|
| Source IPv4 address | `172.16.31.3` |
| Destination IPv4 address | `172.16.31.2` |
| Source MAC address | Record from Packet Tracer |
| Destination MAC address | Record from Packet Tracer |

![Local PDU details](images/local-pdu-details.png)

![Local PDU observations](images/local-pdu-table.png)

## Part 2: Gather PDU Information for Remote Network Communication

### Procedure

1. Return to the Command Prompt on PC `172.16.31.3`.
2. Run the command:

   ```text
   ping 10.10.10.2
   ```

3. Switch to **Simulation Mode** and repeat the command.
4. Select the PDU and inspect its source and destination MAC and IPv4 addresses.
5. Use **Capture / Forward** to follow the PDU as it passes through the switch and router.
6. Record the addressing information for the inbound and outbound PDUs at the router.
7. Continue following the PDU toward the destination and observe the echo reply returning to the source.

### Observations

For remote communication, the destination belongs to a different IP network. The source sends the Ethernet frame to the MAC address of its default gateway. The router examines the destination IP address and forwards the packet toward the remote network.

As the packet moves between networks, the source and destination MAC addresses change for each Ethernet link. The source and destination IPv4 addresses generally remain the same from the original sender to the final destination, unless a feature such as NAT modifies them.

For the initial packet from PC `172.16.31.3` to host `10.10.10.2`, the IP addressing is:

| Field | Value |
|---|---|
| Source IPv4 address | `172.16.31.3` |
| Destination IPv4 address | `10.10.10.2` |
| Destination MAC on the first link | MAC address of the default gateway interface |
| MAC addresses on later links | Depend on the devices on each link |

![Remote PDU details](images/remote-pdu-details.png)

![Remote PDU observations](images/remote-pdu-table.png)

## Key Concepts Learned

- **MAC address:** A Layer 2 address used to deliver Ethernet frames across a local link.
- **IPv4 address:** A Layer 3 logical address used to identify source and destination hosts across IP networks.
- **Switch:** Forwards Ethernet frames within a LAN using MAC address information.
- **Router:** Connects different IP networks and forwards packets based on IP routing information.
- **ICMP:** A protocol used by `ping` to send echo requests and receive echo replies.
- **Simulation Mode:** Allows the movement and details of PDUs to be inspected step by step.
- **Local communication:** The frame is addressed to the destination device's MAC address.
- **Remote communication:** The first Ethernet frame is addressed to the default gateway's MAC address.

## Conclusion

This lab demonstrates the difference between MAC addressing and IPv4 addressing during local and remote communication. By examining PDUs in Packet Tracer Simulation Mode, we can observe how switches forward frames within a LAN and how routers forward packets between networks. This helps explain the role of Layer 2 and Layer 3 addressing in computer networking.

## Skills Practiced

- Using the `ping` command
- Inspecting PDUs in Simulation Mode
- Identifying MAC and IPv4 addresses
- Observing switch and router forwarding
- Comparing local and remote network communication
