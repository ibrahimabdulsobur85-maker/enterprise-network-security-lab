

# DHCP CONFIGURATION
```bash

ip dhcp excluded-address 192.168.10.1 192.168.10.10
ip dhcp excluded-address 192.168.10.65 192.168.10.70
ip dhcp excluded-address 192.168.10.129 192.168.10.135
ip dhcp excluded-address 192.168.10.193 192.168.10.200

ip dhcp pool HR
network 192.168.10.0 255.255.255.192
default-router 192.168.10.1
dns-server 8.8.8.8

ip dhcp pool FINANCE
network 192.168.10.64 255.255.255.192
default-router 192.168.10.65
dns-server 8.8.8.8

ip dhcp pool IT
network 192.168.10.128 255.255.255.192
default-router 192.168.10.129
dns-server 8.8.8.8

ip dhcp pool SALES
network 192.168.10.192 255.255.255.192
default-router 192.168.10.193
dns-server 8.8.8.8
