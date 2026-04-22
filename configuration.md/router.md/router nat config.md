
# NAT CONFIGURATION

```bash

access-list 1 permit 192.168.10.0 0.0.0.255

interface g0/0
ip nat inside

interface g0/1
ip nat outside

ip nat inside source list 1 interface g0/1 overload

# Default route to ISP
ip route 0.0.0.0 0.0.0.0 200.0.0.1
