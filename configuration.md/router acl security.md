
# SECURITY (ACL FIREWALL SIMULATION)

```bash

# Block HR from Finance

access-list 100 deny ip 192.168.10.0 0.0.0.63 192.168.10.64 0.0.0.63
access-list 100 permit ip any any

interface g0/0.10
ip access-group 100 in


# HARDENING


no ip http server
no ip http secure-server
service password-encryption
