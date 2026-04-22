
# CORE SWITCH CONFIGURATION
# Enterprise Network Security Lab
```bash

enable
configure terminal

hostname CORE-SWITCH
no ip domain-lookup


# VLAN CREATION


vlan 10
name HR

vlan 20
name FINANCE

vlan 30
name IT

vlan 40
name SALES

do write

exit
