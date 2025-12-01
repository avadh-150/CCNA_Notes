VLANs (Virtual Local Area Networks) are a fundamental technology used to manage and segment networks, particularly in modern switched environments.

### Definition and Purpose of VLANs

A VLAN is defined as a **logical grouping of network users and resources** connected to administratively defined ports on a switch.

1. **Breaking Up Broadcast Domains:** By default, Layer 2 switches break up collision domains, but they leave the network as one large broadcast domain. VLANs provide the solution to break up broadcast domains in a pure switched internetwork.
2. **Network Segmentation:** Creating VLANs allows administrators to create smaller broadcast domains within a Layer 2 switched internetwork by assigning different switch ports to service different subnetworks. A VLAN functions like its own subnet or broadcast domain.
3. **Frame Handling:** Frames broadcast onto the network are only switched between the ports logically grouped within the same VLAN. Hosts in a specific VLAN cannot communicate with hosts that are members of another VLAN by default. Communication between VLANs requires a Layer 3 device, such as a router or Inter-VLAN Routing (IVR).
4. **Logical Separation:** VLANs allow for logical separation of hosts, even though they may be physically connected to the same switch. VLANs provide a grouping of users by function, independent of their physical or geographic locations.

### Benefits of Using VLANs

VLANs solve many problems associated with flat Layer 2 switched networks, which, by default, allow all users to see all devices and suffer from excessive broadcasts.

Key advantages include:

- **Broadcast Control:** VLANs greatly enhance network management by increasing the number of broadcast domains while simultaneously decreasing the size of those domains. This containment prevents broadcasts and broadcast storms caused by faulty equipment or inadequate segmentation from propagating throughout the entire internetwork.
- **Enhanced Security:** VLANs greatly enhance network security. By creating multiple broadcast groups, an administrator gains total control over each port and user. A group of users requiring high security can be put into their own VLAN, preventing users outside that VLAN from communicating with them.
- **Flexibility:** Network adds, moves, and changes are easily achieved simply by configuring a port into the appropriate VLAN.

### VLAN Port Types

Switch ports are Layer 2 interfaces that can be associated with a physical port belonging to only one VLAN if it is an access port, or all VLANs if it is a trunk port.

1. **Access Ports:** An access port belongs to and carries traffic for only a **single VLAN**. Traffic is both received and sent in native formats, meaning there is **no VLAN tagging** applied. Any device attached to an access link is unaware of the VLAN membership, assuming it is simply part of a broadcast domain.
    
    - **Voice Access Ports:** An exception to the single-VLAN rule is the voice VLAN (formerly auxiliary VLAN), which allows a second VLAN to be added to an access port for voice traffic. This setup permits both a phone and a PC device to connect to one switch port while residing in separate VLANs.
2. **Trunk Ports:** A trunk link is a point-to-point connection—often between two switches, a switch and a router, or a switch and a server—that is capable of carrying the traffic of **multiple VLANs** simultaneously (typically up to 1,001, or 4,094 if extended VLANs are considered). Trunking is the primary method used to allow VLANs to span multiple connected switches.
    

### Frame Tagging and Identification

When VLANs span more than one connected switch, a method is needed for each switch to track the users and frames as they travel through the switch fabric (a group of switches sharing the same VLAN information). This is achieved through **frame tagging**.

- **Frame Tagging:** Frame tagging uniquely assigns a user-defined VLAN ID to each frame. Switches use this identification to determine which frames belong to which VLANs.
- **Tagging Process:** When a frame enters the switch fabric, the switch identifies the VLAN ID from the tag. If the frame reaches an exit determined to be an access link matching the frame’s VLAN ID, the switch removes the VLAN identifier before forwarding the frame to the destination device.

**VLAN Identification Methods**

There are two primary trunking methods for VLAN identification:

1. **Inter-Switch Link (ISL):** This is a Cisco proprietary method that explicitly tags VLAN information onto an Ethernet frame by encapsulating the data frame with a new header and performing a new cyclic redundancy check (CRC). Although some Cisco switches still support ISL, Cisco has shifted toward using only 802.1q.
2. **IEEE 802.1q:** This is the **IEEE standard method** used for frame tagging. Unlike ISL, 802.1q inserts an 802.1q field (containing a 12-bit VLAN ID) into the existing frame. If trunking occurs between a Cisco switch and a different brand of switch, 802.1q must be used.
    - **Native VLAN:** When using 802.1q, all traffic for the native VLAN is **untagged**. The trunk port is assigned a default Port VLAN ID (PVID) for this VLAN (VLAN 1 by default), upon which all untagged traffic travels.

---

VLANs function similarly to how a large office building might use separate mail slots for different departments even though all mail arrives at the same mailroom (the switch). Each department (VLAN) only receives mail addressed to them (broadcasts contained), and if someone needs to send mail between departments, it must go through an intermediary (the router or Layer 3 switch) to be properly sorted and directed.
Alright AR, here’s the **straight, no-nonsense answer** you asked for:

You said: **“give the all command with example”**  
And your PDF is clearly **Chapter 8 – VLANs and Inter-VLAN Routing**.  
So I’ll give you **EVERY important command from this chapter WITH examples**, clean and complete.  
No fluff. No spoon-feeding. Just the real stuff you actually use in CCNA labs.  
(Everything is pulled straight from your file **CH8.pdf** )

---

# ✅ **1. VLAN CREATION COMMANDS**

### **Create VLAN**

```
S1(config)# vlan 10
S1(config-vlan)# name SALES
```

### **Show VLANs**

```
S1# show vlan brief
```

### **Delete VLAN**

```
S1(config)# no vlan 10
```

---

# ✅ **2. ASSIGN PORTS TO VLAN (ACCESS PORTS)**

### **Set Port as Access**

```
S3(config)# interface fa0/3
S3(config-if)# switchport mode access
S3(config-if)# switchport access vlan 3
```

### **Add Voice VLAN**

```
S3(config-if)# switchport voice vlan 5
```

---

# ✅ **3. TRUNK PORT CONFIGURATION**

### **Set Trunk on 2960 (only dot1q)**

```
S1(config)# interface fa0/15
S1(config-if)# switchport mode trunk
```

### **Set Trunk on 3560 (supports ISL & dot1q)**

```
S1(config)# interface fa0/15
S1(config-if)# switchport trunk encapsulation dot1q
S1(config-if)# switchport mode trunk
```

### **Verify Trunk**

```
S1# show interfaces trunk
```

### **Check Switchport Mode**

```
S1# show interfaces fa0/15 switchport
```

---

# ✅ **4. TRUNK VLAN CONTROL**

### **Allow ONLY specific VLANs**

```
S1(config-if)# switchport trunk allowed vlan 4,6,12,15
```

### **Remove VLANs from trunk**

```
S1(config-if)# switchport trunk allowed vlan remove 4-8
```

### **Reset trunk allowed to default**

```
S1(config-if)# switchport trunk allowed vlan all
```

---

# ✅ **5. CHANGE NATIVE VLAN**

```
S1(config-if)# switchport trunk native vlan 4
```

⚠️ If mismatch: you’ll get CDP warning  

### **Restore original**

```
S1(config-if)# no switchport trunk native vlan
```

---

# ✅ **6. INTER-VLAN ROUTING (ROUTER-ON-A-STICK)**

### **Create subinterface for VLAN 2**

```
ISR(config)# interface fa0/0.2
ISR(config-subif)# encapsulation dot1Q 2
ISR(config-subif)# ip address 192.168.10.17 255.255.255.240
```

### **Subinterface for VLAN 3**

```
ISR(config)# interface fa0/0.3
ISR(config-subif)# encapsulation dot1Q 3
ISR(config-subif)# ip address 192.168.10.33 255.255.255.240
```

### **Enable main physical interface**

```
ISR(config)# interface fa0/0
ISR(config-if)# no shutdown
```

---

# ✅ **7. VLAN INTERFACE (SVI) ON LAYER 3 SWITCH**

### **Enable routing**

```
S1(config)# ip routing
```

### **Create SVI for VLAN 10**

```
S1(config)# interface vlan 10
S1(config-if)# ip address 192.168.10.1 255.255.255.0
```

### **Create SVI for VLAN 20**

```
S1(config)# interface vlan 20
S1(config-if)# ip address 192.168.20.1 255.255.255.0
```

---

# ✅ **8. ASSIGN IP ADDRESS TO SWITCH (MANAGEMENT VLAN)**

```
2960(config)# interface vlan 1
2960(config-if)# ip address 192.168.10.2 255.255.255.0
2960(config-if)# no shutdown
2960(config)# ip default-gateway 192.168.10.1
```

---

# ✅ **9. DTP MODES**

Commands:

```
switchport mode access
switchport mode trunk
switchport mode dynamic auto
switchport mode dynamic desirable
switchport nonegotiate
```

---

