Alright AR — here comes the **fully detailed, brutally clear breakdown of STP (Spanning Tree Protocol)**.  
No sugarcoating. No half explanations. You’re getting the **real** version that CCNA expects and the logic behind how STP actually thinks.

I’ll include diagrams to help you visualize it properly.

---

# ✅ **WHAT IS STP? (Real Explanation)**

STP is a Layer 2 protocol whose ONLY job is:

### **👉 Prevent switching loops**

AND

### **👉 Keep one best path active while blocking all others**

Why?  
Because switches **flood broadcasts**.  
If you have two links between switches → broadcast never stops → **broadcast storm → network death**.

STP prevents this by:

- Choosing **one Root Bridge**
    
- Calculating **best path** to root
    
- Blocking extra links
    

---

# 🔥 STP MESSAGE USED → **BPDU**

Switches send a small packet called **BPDU** every 2 seconds.

BPDU contains:

- Root Bridge ID
    
- Sender Bridge ID
    
- Path Cost
    
- Timer values
    

STP decisions are based ONLY on BPDU comparison.

---

# 🔥 HOW STP MAKES DECISIONS

STP uses a strict decision logic:

### **1️⃣ Elect the Root Bridge**

### **2️⃣ Each non-root switch chooses its Root Port**

### **3️⃣ Each network segment chooses a Designated Port**

### **4️⃣ Any port that loses → becomes Blocked**

Let’s break them down properly.

---

# 🟥 **1. ROOT BRIDGE ELECTION — MOST IMPORTANT RULE**

STP picks the switch with the **lowest Bridge ID**.

Bridge ID =  
**Priority (default 32768) + MAC address**

Since all switches have same priority by default…

👉 **The switch with the lowest MAC becomes the Root Bridge.**

This usually means:  
**the oldest/cheapest switch accidentally becomes the boss.**

### To force STP Root Bridge:

```
spanning-tree vlan 1 priority 4096
```

Lower number = stronger.

---

# 🟦 **2. ROOT PORT (RP) – One per switch (except root)**

The Root Port is the port with the **best path (lowest cost)** into the Root Bridge.

If cost ties →  
use these tie-breakers in order:

1. Lowest **upstream** Bridge ID
    
2. Lowest **port cost**
    
3. Lowest **port ID**
    

---

# 🟩 **3. DESIGNATED PORT (DP) – One per segment**

For every link, the side with the **best path to root** becomes the Designated Port.

Other side becomes:

- **Root Port** (if best path)  
    or
    
- **Blocking** (if worse path)
    

---

# 🟨 **4. BLOCKED (NON-DESIGNATED PORT)**

Blocked ports DO NOT forward user traffic.  
But they STILL listen to BPDUs.

They** only move to forwarding if topology changes**.

---

# 🔥 STP PORT STATES

Classic 802.1D STP moves through 5 states:

|State|Meaning|
|---|---|
|**Disabled**|Admin down|
|**Blocking**|Listens BPDUs only|
|**Listening**|Builds STP topology|
|**Learning**|Learns MAC addresses|
|**Forwarding**|Normal traffic|
|**Broken (obsolete)**|Old version|

### Only 2 states forward traffic:

- Learning
    
- Forwarding
    

Listening/Blocking do NOT forward traffic.

---

# 🔥 STP TIMERS (Default)

STP uses 3 main timers:

|Timer|Default|Purpose|
|---|---|---|
|**Hello**|2 sec|BPDU send interval|
|**Forward Delay**|15 sec|Listening + Learning|
|**Max Age**|20 sec|BPDU expiration time|

With classic STP, convergence can take **50 seconds** total.  
This is why better versions exist.

---

# 🔥 STP COST VALUES

STP calculates the **best path** based on link speed:

|Link Speed|Cost|
|---|---|
|10 Mbps|100|
|100 Mbps|19|
|1 Gbps|4|
|10 Gbps|2|

Lower = better.

---

# 🔥 STP VERSIONS (Don’t mix these)

## 1️⃣ **STP (802.1D)** — Worst

- Oldest
    
- Slow convergence (50 seconds)
    

## 2️⃣ **RSTP (802.1w)** — Modern standard

- Converges in ~2 seconds
    
- Replaces Listening/Learning
    

Enable:

```
spanning-tree mode rapid-pvst
```

## 3️⃣ **PVST+** (Cisco proprietary)

- Runs one STP instance per VLAN
    
- Better load-balancing
    
- Works only on Cisco
    

Enable:

```
spanning-tree mode pvst
```

## 4️⃣ **Rapid-PVST+**

- Fast + per-VLAN
    
- Best version for Cisco networks
    

---

# 🔥 RSTP PORT ROLES (Modern)

RSTP improves STP with new roles:

- **Root Port (RP)**
    
- **Designated Port (DP)**
    
- **Alternate Port** (backup path)
    
- **Backup Port** (same segment backup)
    

These enable FAST transitions.

---

# 🔥 PORTFAST & BPDU GUARD (MUST KNOW FOR CCNA)

## ✔ PortFast

Use only for **end devices** (PC, printer).  
Skips STP states → immediate forwarding.

```
spanning-tree portfast
```

## ✔ BPDU Guard

If a PortFast port receives a BPDU → SHUTDOWN

```
spanning-tree bpduguard enable
```

This protects the STP topology from idiots plugging a switch into an access port.

---

# 🔥 HOW TO VERIFY STP

### Check STP mode:

```
show spanning-tree summary
```

### Check STP details:

```
show spanning-tree
```

### Check port role:

```
show spanning-tree interface fa0/1
```

Outputs show:

- Designated/Root/Alternate
    
- Port state (FWD/BLOCK)
    
- Cost
    
- Priority
    

---

# 🔥 EXACT LOGIC STP USES (EXAM CRITICAL)

1. Elect **Root Bridge**
    
2. On every switch, elect **Root Port**
    
3. On every segment, elect **Designated Port**
    
4. Anything else → **Blocking**
    

This never changes.

---

# 🧠 REAL-WORLD STP RULES (Brutal Truth)

1. **Never let STP auto-elect the root.**  
    You ALWAYS set it manually.
    
2. **Make your core/distribution switches the root.**
    
3. **Use Rapid-PVST or MST, NOT legacy STP.**
    
4. **Enable BPDU Guard on all access ports.**
    
5. **Implement EtherChannel to avoid blocked links.**
    
Alright AR — here’s the **complete, no-bullshit, full STP command list** you actually need for CCNA and real networking.  
Not half-baked theory — this is the **entire command arsenal**.

---

# 🔥 **STP – ALL COMMANDS (EVERY MODE, EVERY CHECK, EVERY CONFIG)**

Below is EVERYTHING you can configure or verify in STP:

---

# ✅ **1. SHOW COMMANDS (READ THESE FIRST)**

These show the actual STP state, ports, timers, root, and priorities.

```
show spanning-tree
show spanning-tree vlan <vlan-id>
show spanning-tree summary
show spanning-tree root
show spanning-tree interface <int>
show spanning-tree detail
show spanning-tree inconsistentports
show spanning-tree mst
show spanning-tree mst configuration
```

These are used 99% of the time when troubleshooting.

---

# ✅ **2. SET BRIDGE PRIORITY (ROOT ELECTION)**

If you want to make a switch the root, do this:

```
spanning-tree vlan <vlan-id> priority <0 | 4096 | 8192 | ... | 61440>
```

Or the lazy way (recommended):

```
spanning-tree vlan <vlan-id> root primary
spanning-tree vlan <vlan-id> root secondary
```

**Primary** = lowest priority  
**Secondary** = second lowest

---

# ✅ **3. SET STP MODE**

## **Per-VLAN STP (PVST+)**

```
spanning-tree mode pvst
```

## **Rapid STP (RSTP / Rapid-PVST+)**

```
spanning-tree mode rapid-pvst
```

## **Multiple STP (MST)**

```
spanning-tree mode mst
```

---

# ✅ **4. INTERFACE-LEVEL STP COMMANDS**

## **Enable/Disable STP on a Port**

```
spanning-tree portfast
no spanning-tree portfast
```

## **Portfast on trunk**

```
spanning-tree portfast trunk
```

## **BPDU Guard**

```
spanning-tree bpduguard enable
spanning-tree bpduguard disable
```

## **BPDU Filter**

```
spanning-tree bpdufilter enable
spanning-tree bpdufilter disable
```

## **Enable globally**

```
spanning-tree portfast default
spanning-tree bpduguard default
```

---

# 🎯 **5. STP PROTECTION FEATURES (REAL-WORLD)**

## **Root Guard**

Stops someone from becoming the root switch.

```
spanning-tree guard root
```

## **Loop Guard**

Prevents unidirectional link loops.

```
spanning-tree guard loop
```

## **UDLD (not STP but used with STP)**

```
udld aggressive
```

---

# ✅ **6. UplinkFast / BackboneFast (Legacy but in CCNA)**

Rare today, but still in syllabus.

### **UplinkFast (access switch failover)**

```
spanning-tree uplinkfast
```

### **BackboneFast (faster indirect failure detection)**

```
spanning-tree backbonefast
```

---

# ✅ **7. STP TIMERS**

### **Set Hello Time**

```
spanning-tree vlan <vlan-id> hello-time <seconds>
```

### **Set Forward-Time**

```
spanning-tree vlan <vlan-id> forward-time <seconds>
```

### **Set Max-Age**

```
spanning-tree vlan <vlan-id> max-age <seconds>
```

⚠ Don’t touch these unless you know EXACTLY what you’re doing.

---

# ✅ **8. MST REGION CONFIGURATION (FULL SET)**

```
spanning-tree mst configuration
 name MYREGION
 revision 1
 instance 1 vlan 10,20,30
 instance 2 vlan 40-60
 exit
```

Verify:

```
show spanning-tree mst
show spanning-tree mst configuration
```

---

# 🚀 **9. DISABLE STP on VLAN (NOT RECOMMENDED)**

```
no spanning-tree vlan <vlan-id>
```

If you do this without knowing what you're doing → you deserve the network loop.

---

# 🧠 REAL-WORLD SUMMARY (CUT THE BULLSHIT)

**Most important STP commands you’ll use daily:**

```
show spanning-tree
show spanning-tree vlan 10
show spanning-tree root
spanning-tree vlan 10 root primary
spanning-tree mode rapid-pvst
spanning-tree portfast
spanning-tree bpduguard enable
spanning-tree guard root
```

Everything else is extras.

---

# Want a full **STP LAB**?

I can give you:

- 3-switch topology
    
- Root selection
    
- Blocking/forwarding verification
    
- Portfast + BPDU Guard test  
    Just say **“STP lab”**.