# Security Analysis – Enterprise Network Security Lab

## 1. Overview
This document explains the security design, threats considered, implemented controls, and evaluation of the enterprise network. The goal is to demonstrate practical cybersecurity awareness in a segmented corporate network environment.


## 2. Security Objectives
The network security design was built to achieve the following:

- Prevent unauthorized access between departments  
- Enforce least privilege communication rules  
- Protect internal network from external threats  
- Reduce attack surface through segmentation  
- Monitor and analyze suspicious traffic behavior  


## 3. Threat Model Considered

### 3.1 Unauthorized Access (Lateral Movement)
Attackers or internal users attempting to access restricted departmental resources (e.g., HR → Finance).

### 3.2 Port Scanning
Reconnaissance attempts to discover open ports and services within the network.

### 3.3 DHCP-Based Attacks (Conceptual)
Exhaustion or spoofing of DHCP services to disrupt IP allocation.

### 3.4 External Network Attacks
Traffic from untrusted networks attempting to access internal systems.


## 4. Implemented Security Controls

### 4.1 VLAN Segmentation
Each department is isolated into separate VLANs:

- VLAN 10: HR  
- VLAN 20: Finance  
- VLAN 30: IT  
- VLAN 40: Sales  

✔ Benefit: Limits broadcast domains and prevents unrestricted access between departments.


### 4.2 Access Control Lists (ACLs)
Extended ACLs were implemented to enforce communication rules.

Example:
- HR is denied access to Finance network
- All other necessary traffic is permitted

✔ Benefit: Enforces policy-based access control at the network layer.


### 4.3 NAT (Network Address Translation)
NAT overload (PAT) was used to allow internal devices access to external networks.

✔ Benefit:
- Hides internal IP structure
- Reduces exposure of private addresses to external networks
  

### 4.4 Port Security
Switch port security was configured to limit device connections per port.

✔ Configuration includes:
- Maximum MAC address limit
- Violation mode set to restrict

✔ Benefit:
- Prevents unauthorized device connections
- Reduces risk of rogue devices on the network


### 4.5 Disabled Unused Ports
Unused switch ports were shut down.

✔ Benefit:
- Reduces attack surface
- Prevents unauthorized physical connections


## 5. Attack Simulation Summary

### 5.1 Unauthorized Access Attempt
- Attempt: HR accessing Finance resources  
- Result: Blocked by ACL rules  

### 5.2 Port Scanning Simulation
- Attempt: Multiple connection requests to different services  
- Result: Detected via traffic pattern analysis  

### 5.3 DHCP Attack (Conceptual)
- Risk: IP exhaustion through fake requests  
- Mitigation: Port security + DHCP control mechanisms  


## 6. Traffic Analysis (Wireshark Observation)

Using Wireshark, the following traffic behaviors were analyzed:

- ICMP traffic confirms connectivity (ping tests)
- DNS traffic shows domain resolution processes
- TCP SYN packets indicate connection attempts
- HTTP traffic is unencrypted and exposes data risk

✔ Insight: Unencrypted protocols should be replaced with secure alternatives like HTTPS.



## 7. Security Evaluation

| Security Layer | Status | Effectiveness |
|----------------|--------|--------------|
| VLAN Segmentation | Implemented | High |
| ACL Filtering | Implemented | High |
| NAT Protection | Implemented | Medium |
| Port Security | Implemented | High |
| Traffic Monitoring | Simulated | Medium |


## 8. Limitations

- No dedicated firewall appliance used  
- No IDS/IPS system integrated  
- No centralized logging (SIEM) implemented  
- Attack simulation is limited to Packet Tracer capabilities  


## 9. Future Improvements

- Deploy firewall (e.g., ASA or Palo Alto simulation)  
- Implement IDS/IPS monitoring  
- Add SIEM system (Splunk concept)  
- Enable VPN for remote access  
- Implement real-time log analysis  


## 10. Conclusion

This network demonstrates a layered security approach combining segmentation, access control, and traffic monitoring. It provides a foundational model for enterprise-level cybersecurity and network engineering practices.
