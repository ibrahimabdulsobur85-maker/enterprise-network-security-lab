


## CORE ROUTER CONFIGURATION
# Enterprise Network Security Lab


```bash

enable
configure terminal

hostname CORE-ROUTER
no ip domain-lookup


# INTERFACES


interface g0/0
no shutdown

interface g0/1
no shutdown


# INTER-VLAN ROUTING


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
