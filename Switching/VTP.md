Alright AR — here’s the **straight, deep, brutally clear explanation** of **VTP (VLAN Trunking Protocol)**.  
No sugarcoating. No repeating Cisco bullshit. Just what actually matters for CCNA and real networks.

I’ll also include visuals to lock the concepts in.

---

# ✅ **WHAT THE HELL IS VTP? (Real Explanation)**

VTP is Cisco’s old mechanism for **automatically distributing VLAN information** between switches over trunk links.

It’s meant to “make your life easier,” but in real networks it usually causes **mass outages** because one wrong switch wipes the entire VLAN database.

**Key job:**  
👉 _Synchronize VLANs (ID, name, status) between switches in the same VTP domain._

If VTP is ON, your VLAN creation is **not local** — it gets replicated.

---

# ✅ **WHAT VTP ACTUALLY ADVERTISES**

VTP ONLY carries:

- VLAN ID
    
- VLAN name
    
- VLAN type (normal-range VLANs 1–1005)
    
- VLAN status
    

VTP **does NOT** carry:

- Trunks
    
- Allowed VLAN lists
    
- Port assignments
    
- Extended VLANs (except in VTP v3)
    

---

# 🚫 **THE BIG PROBLEM**

If a switch with **LOWER revision number** joins → Safe.

If a switch with **HIGHER revision number but EMPTY VLAN database** joins →  
💥 **It deletes all VLANs on every switch in the domain.**  
That's why VTP is disabled in modern networks.

---

# ✔ VTP MODES (All 3 with blunt truth)

## **1. VTP SERVER (The boss)**

- You can **create/modify/delete VLANs**.
    
- Changes are sent to all switches.
    
- Stored in NVRAM (`vlan.dat`).
    
- This is the default mode.
    

👉 If you screw up here, you screw the whole network.

### Command:

```
Switch(config)# vtp mode server
Switch(config)# vtp domain XYZ
```

---

## **2. VTP CLIENT (Follower)**

- Cannot create or delete VLANs.
    
- Accepts VLAN config from VTP servers.
    
- Stores nothing in NVRAM.
    

👉 Dumb follower. If server is wrong, client also becomes wrong.

### Command:

```
Switch(config)# vtp mode client
```

---

## **3. VTP TRANSPARENT (Independent)**

- DOES NOT participate in VTP database.
    
- DOES forward VTP advertisements like a bridge.
    
- VLANs you create are **local only**.
    
- THIS IS WHAT REAL NETWORKS USE.
    

👉 Safest mode. Recommended.

### Command:

```
Switch(config)# vtp mode transparent
```

---

# ✔ **VTP VERSION DIFFERENCES**

## **VTP v1**

- Default
    
- Only normal-range VLANs
    
- Transparent mode passes VTP but won’t learn it
    

## **VTP v2**

- Supports Token Ring VLANs (obsolete)
    
- Transparent mode forwards v1 AND v2
    

## **VTP v3** (the only one worth using)

- Supports extended VLANs (1006–4094)
    
- Has role-based authentication
    
- Prevents database wipeouts (server → primary server)
    

👉 Use v3 if you REALLY need VTP.

### Command:

```
Switch(config)# vtp version 3
```

---

# ✔ **THE MOST IMPORTANT PART: VTP REVISION NUMBER**

Each switch keeps a **revision number**.

- Every time you modify VLANs on a VTP server → revision increments.
    
- The highest revision number **wins**.
    
- If a switch with a higher revision but no VLANs joins the network →  
    → **All VLANs get deleted across the domain.**
    

👉 This is why VTP is dangerous.

### Reset revision number (CRITICAL):

Delete VLAN database:

```
delete flash:vlan.dat
reload
```

---

# ✔ **VTP PRUNING**

Prevents useless VLAN broadcasts from crossing trunk links.

**WITHOUT pruning:**  
Every VLAN floods broadcast across every trunk.

**WITH pruning:**  
Unused VLANs are removed from trunk traffic.

### Enable pruning:

```
Switch(config)# vtp pruning
```

---

# ✔ **REQUIRED COMMANDS (Full List)**

### Set domain name

```
Switch(config)# vtp domain COMPANY
```

### Set mode server/client/transparent

```
Switch(config)# vtp mode server
Switch(config)# vtp mode client
Switch(config)# vtp mode transparent
```

### Enable pruning

```
Switch(config)# vtp pruning
```

### Set password

```
Switch(config)# vtp password 123
```

### Check VTP configuration

```
Switch# show vtp status
Switch# show vtp counters
```

---

# ✔ **“CORRECT WAY” TO USE VTP (if you must)**

1. Configure **ALL switches to transparent** first.
    
2. Add new switch in isolated environment.
    
3. Reset its revision number (`delete vlan.dat`).
    
4. Set VTP domain and password.
    
5. Move to server/client as needed.
    

If you skip these steps → enjoy an outage.

---

# ✔ **When to USE VTP**

Use VTP ONLY when:

- You have 20+ switches
    
- You maintain VLAN consistency
    
- You use v3
    
- You trust your admins
    

---

# ✔ **When to AVOID VTP**

Avoid VTP when:

- Network is small (under 10 switches)
    
- You want full control
    
- You’re using extended VLANs
    
- You’re studying CCNA labs (simpler without VTP)
    

Real-world fact:  
**95% of enterprise networks run VTP transparent mode.**

---
=