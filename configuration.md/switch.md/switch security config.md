
# SWITCH SECURITY CONFIGURATION


# Port Security (Prevent unauthorized devices)
interface range fa0/1-8
switchport port-security
switchport port-security maximum 2
switchport port-security mac-address sticky
switchport port-security violation restrict

# Disable unused ports
interface range fa0/9-24
shutdown
description UNUSED_PORTS

# Prevent VLAN hopping attacks (trunk hardening)
interface g0/1
switchport mode trunk
switchport trunk allowed vlan 10,20,30,40
