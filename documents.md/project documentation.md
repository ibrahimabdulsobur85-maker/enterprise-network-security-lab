# ENTERPRISE NETWORK DESIGN & CYBERSECURITY PROJECT

## 1. PROJECT OVERVIEW

This project demonstrates the design, implementation, and security of an enterprise network using IP addressing, VLAN segmentation, routing, NAT, and cybersecurity controls.

It also extends into a cybersecurity lab by simulating attacks and analyzing network traffic using Wireshark.

---

## 2. OBJECTIVES

* Design a structured IP addressing scheme
* Implement VLAN-based network segmentation
* Configure inter-VLAN routing
* Enable DHCP for automatic IP assignment
* Implement NAT for internet access
* Apply security using ACLs and port security
* Simulate cyber attacks and apply mitigation
* Analyze network traffic using Wireshark

---

## 3. NETWORK DESIGN

### 3.1 Devices Used

* 1 Router (Main Router)
* 1 Switch (Layer 2)
* 1 ISP Router
* 1 Server (Internet simulation)
* 8 PCs (Users)
* 1 Attacker PC

---

### 3.2 Departments (VLANs)

| VLAN | Department | Ports   |
| ---- | ---------- | ------- |
| 10   | HR         | Fa0/1–2 |
| 20   | Finance    | Fa0/3–4 |
| 30   | IT         | Fa0/5–6 |
| 40   | Sales      | Fa0/7–8 |

---

## 4. IP ADDRESSING SCHEME

| VLAN | Network        | Subnet Mask     | Gateway        |
| ---- | -------------- | --------------- | -------------- |
| 10   | 192.168.10.0   | 255.255.255.192 | 192.168.10.1   |
| 20   | 192.168.10.64  | 255.255.255.192 | 192.168.10.65  |
| 30   | 192.168.10.128 | 255.255.255.192 | 192.168.10.129 |
| 40   | 192.168.10.192 | 255.255.255.192 | 192.168.10.193 |

---

## 5. IMPLEMENTATION

### 5.1 VLAN CONFIGURATION (SWITCH)

```bash
enable
configure terminal

vlan 10
name HR
vlan 20
name Finance
vlan 30
name IT
vlan 40
name Sales
```

### Assign Ports

```bash
interface range fa0/1-2
switchport mode access
switchport access vlan 10

interface range fa0/3-4
switchport mode access
switchport access vlan 20

interface range fa0/5-6
switchport mode access
switchport access vlan 30

interface range fa0/7-8
switchport mode access
switchport access vlan 40
```

### Trunk Port

```bash
interface g0/1
switchport mode trunk
```

---

### 5.2 INTER-VLAN ROUTING (ROUTER)

```bash
interface g0/0
no shutdown

interface g0/0.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.192

interface g0/0.20
encapsulation dot1Q 20
ip address 192.168.10.65 255.255.255.192

interface g0/0.30
encapsulation dot1Q 30
ip address 192.168.10.129 255.255.255.192

interface g0/0.40
encapsulation dot1Q 40
ip address 192.168.10.193 255.255.255.192
```

---

### 5.3 DHCP CONFIGURATION

```bash
ip dhcp pool HR
network 192.168.10.0 255.255.255.192
default-router 192.168.10.1

ip dhcp pool FINANCE
network 192.168.10.64 255.255.255.192
default-router 192.168.10.65

ip dhcp pool IT
network 192.168.10.128 255.255.255.192
default-router 192.168.10.129

ip dhcp pool SALES
network 192.168.10.192 255.255.255.192
default-router 192.168.10.193
```

---

## 6. INTERNET CONNECTIVITY (NAT)

### NAT Configuration

```bash
interface g0/0
ip nat inside

interface g0/1
ip nat outside

access-list 1 permit 192.168.10.0 0.0.0.255

ip nat inside source list 1 interface g0/1 overload

ip route 0.0.0.0 0.0.0.0 200.0.0.1
```

---

## 7. SECURITY IMPLEMENTATION

### 7.1 ACCESS CONTROL LIST (ACL)

Block HR from accessing Finance:

```bash
access-list 100 deny ip 192.168.10.0 0.0.0.63 192.168.10.64 0.0.0.63
access-list 100 permit ip any any

interface g0/0.10
ip access-group 100 in
```

---

### 7.2 FIREWALL SIMULATION

Block HTTP traffic:

```bash
access-list 110 deny tcp any any eq 80
access-list 110 permit ip any any

interface g0/1
ip access-group 110 out
```



### 7.3 PORT SECURITY

bash
interface range fa0/1-8
switchport port-security
switchport port-security maximum 2
switchport port-security violation restrict


### 7.4 DISABLE UNUSED PORTS

bash
interface range fa0/9-24
shutdown




## 8. CYBERSECURITY SIMULATION

### 8.1 Attack Scenarios

1. Unauthorized Access (HR → Finance)

   * Blocked using ACL

2. Port Scanning

   * Detected via unusual traffic patterns

3. DHCP Starvation (Conceptual)

   * Prevented using DHCP Snooping and Port Security


### 8.2 Security Strategy

| Threat              | Detection      | Mitigation        |
| ------------------- | -------------- | ----------------- |
| Unauthorized access | ACL logs       | VLAN segmentation |
| Port scanning       | Traffic spikes | Firewall rules    |
| DHCP attack         | IP exhaustion  | DHCP snooping     |

---

## 9. WIRESHARK ANALYSIS

### Filters Used

* ICMP Traffic:

```bash
icmp
```

* DNS Traffic:

```bash
dns
```

* SYN Scan Detection:

```bash
tcp.flags.syn == 1 and tcp.flags.ack == 0
```

* HTTP Traffic:

http


### Key Observations

* ICMP shows request/reply communication
* DNS resolves domain names to IP addresses
* SYN packets indicate possible scanning
* HTTP traffic is unencrypted (security risk)


## 10. TESTING & VERIFICATION

* DHCP assigns IP addresses correctly
* Devices communicate within VLAN
* Inter-VLAN routing works
* HR cannot access Finance
* IT can access all VLANs
* Internet access via NAT works



## 11. KEY LEARNINGS

* Importance of network segmentation
* Role of ACLs in security enforcement
* NAT enables internet access for private networks
* Traffic analysis helps detect threats
* Layered security improves network protection


## 12. CONCLUSION

This project demonstrates practical skills in networking and cybersecurity, including design, configuration, troubleshooting, and threat mitigation. It reflects real-world enterprise network implementation and security practices.


```bash
## 13. AUTHOR

Name: IBRAHIM ABDULSOBUR
Role: Network / Cybersecurity Student
Tools Used: Cisco Packet Tracer, Wireshark
