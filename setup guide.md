# SETUP GUIDE (STEP-BY-STEP)

## 1. REQUIREMENTS
Install:
- Cisco Packet Tracer
- Wireshark (optional but recommended)


## 2. OPEN THE LAB FILE
Open:
lab_files/enterprise_network_base.pkt


## 3. DEVICE SETUP ORDER

### Step 1: Switch Setup
- Create VLANs (10, 20, 30, 40)
- Assign ports to VLANs
- Configure trunk port

### Step 2: Router Setup
- Configure router-on-a-stick
- Add subinterfaces for VLANs
- Assign IP addresses

### Step 3: DHCP Setup
- Configure DHCP pools for each VLAN

### Step 4: NAT Setup
- Configure inside/outside interfaces
- Enable PAT (overload)

### Step 5: Security Setup
- Apply ACL rules
- Enable port security
- Disable unused ports


## 4. TESTING CHECKLIST

✔ PCs receive IP addresses  
✔ VLAN communication works  
✔ Inter-VLAN routing works  
✔ Internet (ping 8.8.8.8) works  
✔ HR cannot access Finance  
✔ ACL rules are enforced  


## 5. OPTIONAL SECURITY LAB
- Simulate unauthorized access
- Observe traffic using Wireshark
