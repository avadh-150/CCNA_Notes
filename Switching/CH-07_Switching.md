
Layer 2 switching, often referred to simply as "switching" in the context of Cisco exam objectives unless specified otherwise, is the process of using the hardware address of devices on a Local Area Network (LAN) to **segment a network**. Layer 2 switches and bridges are faster than routers because they examine the frame's hardware addresses rather than looking at the Network layer header information when deciding whether to forward, flood, or drop the frame.

The reliance on Layer 2 switching has dramatically changed network design, allowing for the implementation of clean, cost-effective, and resilient internetworks.

## Core Functions of Layer 2 Switching

There are **three distinct functions** of Layer 2 switching that are essential to remember:

11. **Address Learning**.
12. **Forward/Filter Decisions** (Frame Switching and Frame Flooding).
13. **Loop Avoidance**.

### 1. Address Learning

Address learning is the process by which a Layer 2 switch remembers the source hardware address (MAC address) of every frame received on an interface.

- **MAC Database:** This information is entered into a database called the **forward/filter table** or **Content Addressable Memory (CAM) table**. Modern, fast switches use application-specific integrated circuits (ASICs) to build and maintain these tables.
- **Process:** When a switch is first powered on, the CAM table is empty. When a device transmits a frame, the switch receives it on an interface and immediately places the frame’s **source address** in the table, associating it with the precise interface where the frame was received.

### 2. Forward/Filter Decisions

Forward/filter decisions determine how a frame is handled based on the switch's learned addresses.

- **Frame Filtering (Forwarding):** When a frame arrives, the switch compares the destination hardware address to the MAC database. If the destination hardware address is known and listed in the database, the switch chooses the appropriate exit interface and sends the frame _only_ out of that port. This process is called **frame filtering** and preserves bandwidth on other network segments.
- **Frame Flooding (Initial Unknown):** If the destination hardware address is **not listed** in the MAC database, the switch has no choice but to **flood the frame** out of every active interface except the interface it was received on, in an attempt to locate the destination device.
- **Point-to-Point:** Once the destination device answers the flooded frame, the switch learns its location and places its MAC address into the database, enabling a **point-to-point connection** between the two devices for future frames.
- **Broadcasts:** If a host sends a broadcast on the LAN, the switch will, by default, flood the frame out of all active ports except the source port. The switch creates smaller collision domains, but it remains one large broadcast domain by default.
- **Aging:** If devices do not communicate again within a certain time period, the switch will flush their entries from the database to keep it current.

### 3. Loop Avoidance

Redundant links are often created between switches to prevent network failures. However, without proper schemes in place, these links can cause **network loops**.

Problems caused by network loops include:

- **Broadcast Storms:** Switches can flood broadcasts endlessly throughout the internetwork.
- **Multiple Frame Copies:** A device may receive duplicate copies of the same frame arriving from different segments simultaneously.
- **MAC Table Thrashing:** The switch's MAC address filter table can become confused, receiving the source device's MAC address from more than one link. The switch can get caught up constantly updating the table and fail to forward frames.

The **Spanning Tree Protocol (STP)** is used to prevent these problems and avoid network loops while still permitting network redundancy.

## Advantages of Layer 2 Switching

Layer 2 switching offers several key advantages over older technologies like hubs:

- **Dedicated Collision Domains:** Unlike hubs, switches create private, dedicated collision domains, providing **independent bandwidth exclusive on each port**.
- **Efficiency:** Layer 2 switching is highly efficient because no modification to the data packet takes place; the switch only reads the frame encapsulating the packet.
	- **Performance:** Advantages include **hardware-based bridging** (using ASICs), **wire speed**, **low latency**, and **low cost**.

## Layer 2 Security Features

Layer 2 switches can be secured using features like **Port Security**. Port security is used to restrict access to a switch based on MAC addresses, preventing unauthorized users from connecting devices (including hubs or access points) to a switch port.

Port security configurations include:

- **Prerequisite:** The port must be configured as an ==access port== (`switchport mode access`) before port security can be enabled (`switchport port-security`).
- **Maximum Addresses:** Limiting the number of MAC addresses that can associate with a port (==default maximum is 1==).
- **Violation Modes:** Setting penalties for security violations:
    - **Shutdown (Default):** The interface is immediately put into an **error-disabled state** (`Secure-shutdown` or `err-disabled`), requiring a manual `shutdown` followed by `no shutdown` to re-enable. This mode alerts the administrator via SNMP.
    - **Restrict:** Drops packets from unknown sources after the maximum limit is met, but does not shut down the port. This mode generates a log message and sends an **SNMP trap**.
    - **Protect:** Drops packets from unknown sources until the maximum is reduced, but does **not** generate an alert (like an SNMP trap).
- **Sticky MAC:** Using the `switchport port-security mac-address sticky` command allows the switch to dynamically learn addresses and save them as static entries in the running configuration.

Layer 2 switching works similarly to a sorting office (the switch) where postal workers (the ASICs) look only at the immediate address labels (MAC addresses) on the outside of the package (the frame) to decide which specific sorting bin (the destination port) to put it in, rather than opening the package to read the contents inside (the Network layer header) to figure out the ultimate destination. If they don't know the recipient's bin yet, they send copies to every sorting station (flooding) until the recipient responds, establishing a direct route for the future.

## I. Basic Administrative and Management Commands

These commands handle access, device identification, and configuration saving:

| Command Syntax                 | Purpose                                      | Example / Usage                                 |
| :----------------------------- | :------------------------------------------- | :---------------------------------------------- |
| **`en`** or **`enable`**       | Enters privileged EXEC mode.                 | `Switch>en`                                     |
| **`config t`**                 | Enters global configuration mode.            | `Switch#config t`                               |
| **`hostname [name]`**          | Sets the device hostname.                    | `Switch(config)#hostname S1`                    |
| **`enable secret [password]`** | Sets the encrypted privileged EXEC password. | `S1(config)#enable secret todd`                 |
| **`banner motd #[text]#`**     | Sets the Message of the Day banner.          | `S1(config)#banner motd #this is my S1 switch#` |
| **`line con 0`**               | Configures console access.                   | `S1(config-if)#line con 0`                      |
| **`line vty 0 15`**            | Configures remote (Telnet/SSH) access.       | `S1(config-line)#line vty 0 15`                 |
| **`password [password]`**      | Sets a password for a line.                  | `S1(config-line)#password console`              |
| **`login`**                    | Enables password checking on a line.         | `S1(config-line)#login`                         |
| **`copy run start`**           | Saves the running configuration.             | `S1#copy run start`                             |

## II. Interface and IP Configuration Commands

These commands configure physical and logical interfaces, and IP addressing for in-band management:

| Command Syntax                | Purpose                                            | Example / Usage                                                           |
| :---------------------------- | :------------------------------------------------- | :------------------------------------------------------------------------ |
| **`int [interface]`**         | Enters interface configuration mode.               | `S1(config)#int f0/15`                                                    |
| **`int range [range]`**       | Enters configuration mode for multiple interfaces. | `S3(config)#int range f0/3-4`                                             |
| **`description [text]`**      | Provides a description for an interface.           | `S1(config-if)#description 1st connection to S3`                          |
| **`int vlan 1`**              | Configures the default management interface.       | `S1(config-line)#int vlan 1`                                              |
| **`ip address [ip] [mask]`**  | Assigns an IP address to the management VLAN.      | `S1(config-if)#ip address 192.168.10.17 255.255.255.240`                  |
| **`no shut`**                 | Activates the interface (often needed for VLAN 1). | `S1(config-if)#no shut`                                                   |
| **`ip default-gateway [ip]`** | Sets the default gateway for remote management.    | `S3(config)#ip default-gateway 192.168.10.30`                             |
| **`shutdown`**                | Administratively disables an interface.            | `S3(config-if)# shutdown` (used to manually reset an error-disabled port) |

## III. Port Security Configuration Commands

Port security restricts switch access based on MAC addresses. The port must be an access port first.

| Command Syntax                                    | Purpose                                                                     | Example / Usage                                                                          |
| :------------------------------------------------ | :-------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------- |
| **`switchport mode access`**                      | Makes the port an access port (prerequisite).                               | `Switch(config-if)#switchport mode access`                                               |
| **`switchport port-security`**                    | **Enables** port security on the interface.                                 | `Switch(config-if)#switchport port-security`                                             |
| **`switchport port-security maximum [value]`**    | Sets the maximum number of allowed secure MAC addresses (default is 1).     | `Switch(config-if)#switchport port-security maximum 1`                                   |
| **`switchport port-security violation [mode]`**   | Sets the action when a violation occurs.                                    | `Switch(config-if)#switchport port-security violation shutdown` (Sets the default mode). |
| **`switchport port-security violation restrict`** | Sets violation to drop frames and alert via SNMP.                           | `S3(config-if-range)#switchport port-security violation restrict`                        |
| **`switchport port-security mac-address [mac]`**  | Statically defines an authorized MAC address.                               | `Switch(config-if)#switchport port-security mac-address aa.bb.cc.dd.ee.ff`               |
| **`switchport port-security mac-address sticky`** | Converts dynamically learned addresses into static, running-config entries. | `Switch(config-if)#switchport port-security mac-address sticky`                          |

## IV. Verification and Monitoring Commands

These commands are used to check connectivity, status, and Layer 2 table entries:

| Command Syntax                                           | Purpose                                                         | Example / Usage                                      |
| :------------------------------------------------------- | :-------------------------------------------------------------- | :--------------------------------------------------- |
| **`show running-config`** (or `sh run`)                  | Displays the current configuration.                             | Used to get a great overview of the device.          |
| **`show interface vlan 1`** (or `sh int vlan 1`)         | Verifies the status and IP address of the management interface. | `S3#sh int vlan 1`                                   |
| **`show ip interface brief`**                            | Provides a summary of interface status and IP address.          | Used to check interface status.                      |
| **`show ip arp`**                                        | Displays the ARP table (IP to MAC mappings).                    | `S3#sh ip arp`                                       |
| **`show mac address-table`** (or `sh mac address-table`) | Displays the forward/filter table (CAM table).                  | `S3#sh mac address-table`                            |
| **`show port-security interface [interface]`**           | Verifies detailed port security configuration and status.       | `S3(config-if-range)#do show port-security int f0/3` |
| **`ping [ip address]`**                                  | Tests connectivity.                                             | `S2#ping 192.168.10.17`                              |

## V. Static MAC Address Table Commands

These commands directly manipulate the MAC address table:

| Command Syntax                                                   | Purpose                                                    | Example / Usage                                                       |
| :--------------------------------------------------------------- | :--------------------------------------------------------- | :-------------------------------------------------------------------- |
| **`mac address-table static [mac] vlan [vlan] int [interface]`** | Manually sets a static MAC address entry in the CAM table. | `S3(config)#mac address-table static aaaa.bbbb.cccc vlan 1 int fa0/7` |

---

### Example of Command Usage in Context:

To secure a port (Fa0/3) to only allow a single MAC address, ensure it is in access mode, and set it to the default maximum of 1, while changing the violation mode from the default (`shutdown`) to `restrict`:

```
Switch#config t
Switch(config)#int fa0/3
Switch(config-if)#switchport mode access
Switch(config-if)#switchport port-security
Switch(config-if)#switchport port-security maximum 10
Switch(config-if)#switchport port-security violation restrict
Switch(config-if)#switchport port-security mac-address aa.bb.cc.dd.ee.ff
```

The commands show how to use `switchport mode access` as a prerequisite, `switchport port-security` to enable the feature (setting the maximum to 1 by default), `switchport port-security violation restrict` to change the penalty, and `switchport port-security mac-address` to set an authorized static MAC address.

![[Swiching Chapter.png]]