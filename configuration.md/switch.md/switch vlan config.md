
# VLAN PORT ASSIGNMENT
```bash

# HR Department
interface range fa0/1-2
switchport mode access
switchport access vlan 10
description HR_DEPARTMENT

# Finance Department
interface range fa0/3-4
switchport mode access
switchport access vlan 20
description FINANCE_DEPARTMENT

# IT Department
interface range fa0/5-6
switchport mode access
switchport access vlan 30
description IT_DEPARTMENT

# Sales Department
interface range fa0/7-8
switchport mode access
switchport access vlan 40
description SALES_DEPARTMENT
