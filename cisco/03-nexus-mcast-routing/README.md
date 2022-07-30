# Cisco Nexus Routing Multicast Lab
## Management
### Credentials
This configuration is done from console port for all devices:
```
         ---- System Admin Account Setup ----


Do you want to enforce secure password standard (yes/no) [y]: yes

  Enter the password for "admin": 
  Confirm the password for "admin": 

         ---- Basic System Configuration Dialog VDC: 1 ----

This setup utility will guide you through the basic configuration of
the system. Setup configures only enough connectivity for management
of the system.

Please register Cisco Nexus9000 Family devices promptly with your
supplier. Failure to register may affect response times for initial
service calls. Nexus9000 devices must be registered to receive 
entitled support services.

Press Enter at anytime to skip a dialog. Use ctrl-c at anytime
to skip the remaining dialogs.

 Would you like to enter the basic configuration dialog (yes/no): no
```

### IP addresses
This configuration is done from console port for all devices.

c-1-s1:
```
configure terminal
!
interface mgmt 0
   vrf member management
   ip addr 192.168.101.20/24
   ipv6 add fc00:192:168:101::20/64
   no shutdown
!
vrf context management
   ip route 0.0.0.0/0 192.168.101.1
   ipv6 route ::/0 fc00:192:168:101::1
!
!
copy running-config startup-config
!
```

c-1-s2:
```
configure terminal
!
interface mgmt 0
   vrf member management
   ip addr 192.168.101.21/24
   ipv6 add fc00:192:168:101::21/64
   no shutdown
!
vrf context management
   ip route 0.0.0.0/0 192.168.101.1
   ipv6 route ::/0 fc00:192:168:101::1
!
!
copy running-config startup-config
!
```

c-1-l1:
```
configure terminal
!
interface mgmt 0
   vrf member management
   ip addr 192.168.101.30/24
   ipv6 add fc00:192:168:101::30/64
   no shutdown
!
vrf context management
   ip route 0.0.0.0/0 192.168.101.1
   ipv6 route ::/0 fc00:192:168:101::1
!
!
copy running-config startup-config
!
```

c-1-l2:
```
configure terminal
!
interface mgmt 0
   vrf member management
   ip addr 192.168.101.31/24
   ipv6 add fc00:192:168:101::31/64
   no shutdown
!
vrf context management
   ip route 0.0.0.0/0 192.168.101.1
   ipv6 route ::/0 fc00:192:168:101::1
!
!
copy running-config startup-config
!
```

c-1-l3:
```
configure terminal
!
interface mgmt 0
   vrf member management
   ip addr 192.168.101.32/24
   ipv6 add fc00:192:168:101::32/64
   no shutdown
!
vrf context management
   ip route 0.0.0.0/0 192.168.101.1
   ipv6 route ::/0 fc00:192:168:101::1
!
!
copy running-config startup-config
!
```

c-1-l4:
```
configure terminal
!
interface mgmt 0
   vrf member management
   ip addr 192.168.101.33/24
   ipv6 add fc00:192:168:101::33/64
   no shutdown
!
vrf context management
   ip route 0.0.0.0/0 192.168.101.1
   ipv6 route ::/0 fc00:192:168:101::1
!
!
copy running-config startup-config
!
```

## Hostname and Domain
c-1-s1:
```
configure terminal
!
hostname c-1-s1
ip domain-name lab.karneliuk.com
!
```

c-1-s2:
```
configure terminal
!
hostname c-1-s2
ip domain-name lab.karneliuk.com
!
```

c-1-l1:
```
configure terminal
!
hostname c-1-l1
ip domain-name lab.karneliuk.com
!
```

c-1-l2:
```
configure terminal
!
hostname c-1-l2
ip domain-name lab.karneliuk.com
!
```

c-1-l3:
```
configure terminal
!
hostname c-1-l3
ip domain-name lab.karneliuk.com
!
```

c-1-l4:
```
configure terminal
!
hostname c-1-l4
ip domain-name lab.karneliuk.com
!
```

## IP Interfaces
### Core interaces
From now on all further configuation is done via SSH.

c-1-s1:
```
configure terminal
!
interface ethernet 1/2 
   no switchport
   ip address 10.0.0.0/31
   no shutdown
   load-interval 5
!
interface ethernet 1/3
   no switchport
   ip address 10.0.0.2/31
   no shutdown
   load-interval 5
!
interface ethernet 1/4
   no switchport
   ip address 10.0.0.4/31
   no shutdown
   load-interval 5
!
interface ethernet 1/5
   no switchport
   ip address 10.0.0.8/31
   no shutdown
   load-interval 5
!
interface ethernet 1/6
   no switchport
   ip address 10.0.0.12/31
   no shutdown
   load-interval 5
!
interface ethernet 1/7
   no switchport
   ip address 10.0.0.16/31
   no shutdown
   load-interval 5
!
interface loopback 0
   ip address 10.0.255.20/32
   no shutdown
!
interface loopback 1
   ip address 10.0.254.1/32
   no shutdown
!
```

c-1-s1:
```
configure terminal
!
interface ethernet 1/2 
   no switchport
   ip address 10.0.0.1/31
   no shutdown
   load-interval 5
!
interface ethernet 1/3
   no switchport
   ip address 10.0.0.3/31
   no shutdown
   load-interval 5
!
interface ethernet 1/4
   no switchport
   ip address 10.0.0.6/31
   no shutdown
   load-interval 5
!
interface ethernet 1/5
   no switchport
   ip address 10.0.0.10/31
   no shutdown
   load-interval 5
!
interface ethernet 1/6
   no switchport
   ip address 10.0.0.14/31
   no shutdown
   load-interval 5
!
interface ethernet 1/7
   no switchport
   ip address 10.0.0.18/31
   no shutdown
   load-interval 5
!
interface loopback 0
   ip address 10.0.255.21/32
   no shutdown
!
interface loopback 1
   ip address 10.0.254.1/32
   no shutdown
!
```

c-1-l1:
```
configure terminal
!
interface ethernet 1/1 
   no switchport
   ip address 10.0.0.5/31
   no shutdown
   load-interval 5
!
interface ethernet 1/2
   no switchport
   ip address 10.0.0.7/31
   no shutdown
   load-interval 5
!
interface ethernet 1/3
   no switchport
   ip address 10.0.0.20/31
   no shutdown
   load-interval 5
!
interface ethernet 1/4
   no switchport
   ip address 10.12.0.0/31
   no shutdown
   load-interval 5
!
interface loopback 0
   ip address 10.0.255.30/32
   no shutdown
!
```

c-1-l2:
```
configure terminal
!
interface ethernet 1/1 
   no switchport
   ip address 10.0.0.9/31
   no shutdown
   load-interval 5
!
interface ethernet 1/2
   no switchport
   ip address 10.0.0.11/31
   no shutdown
   load-interval 5
!
interface ethernet 1/3
   no switchport
   ip address 10.0.0.21/31
   no shutdown
   load-interval 5
!
interface ethernet 1/4
   no switchport
   ip address 10.12.0.1/31
   no shutdown
   load-interval 5
!
interface loopback 0
   ip address 10.0.255.31/32
   no shutdown
!
```

c-1-l3:
```
configure terminal
!
interface ethernet 1/1 
   no switchport
   ip address 10.0.0.13/31
   no shutdown
   load-interval 5
!
interface ethernet 1/2
   no switchport
   ip address 10.0.0.15/31
   no shutdown
   load-interval 5
!
interface ethernet 1/3
   no switchport
   ip address 10.0.0.24/31
   no shutdown
   load-interval 5
!
interface ethernet 1/4
   no switchport
   ip address 10.34.0.0/31
   no shutdown
   load-interval 5
!
interface loopback 0
   ip address 10.0.255.32/32
   no shutdown
!
```

c-1-l4:
```
configure terminal
!
interface ethernet 1/1 
   no switchport
   ip address 10.0.0.17/31
   no shutdown
   load-interval 5
!
interface ethernet 1/2
   no switchport
   ip address 10.0.0.19/31
   no shutdown
   load-interval 5
!
interface ethernet 1/3
   no switchport
   ip address 10.0.0.25/31
   no shutdown
   load-interval 5
!
interface ethernet 1/4
   no switchport
   ip address 10.34.0.1/31
   no shutdown
   load-interval 5
!
interface loopback 0
   ip address 10.0.255.33/32
   no shutdown
!
```

### Customer interfaces
c-1-l1:
```
configure terminal
!
vlan 10
   name c-1-h1
!
vlan 20
   name c-1-h2
!
feature interface-vlan
feature hsrp
!
interface Vlan 10
   ip address 10.12.10.2/24
   no shutdown
   !
   hsrp version 2
   hsrp 0 ipv4
      ip 10.12.10.1
      priority 110
      preempt
   !
!
interface Vlan 20
   ip address 10.12.20.2/24
   no shutdown
   !
   hsrp version 2
   hsrp 0 ipv4
      ip 10.12.20.1
      priority 110
      preempt
   !
!
interface eth1/5
   switchport
   switchport mode access
   switchport access vlan 10
   no shutdown
!
interface eth1/6
   switchport
   switchport mode access
   switchport access vlan 20
   no shutdown
!
interface eth1/7
   shutdown
!
```

c-1-l2:
```
configure terminal
!
vlan 30
   name c-1-h3
!
vlan 40
   name c-1-h4
!
feature interface-vlan
feature hsrp
!
interface Vlan 30
   ip address 10.12.30.2/24
   no shutdown
   !
   hsrp version 2
   hsrp 0 ipv4
      ip 10.12.30.1
      priority 100
      preempt
   !
!
interface Vlan 40
   ip address 10.12.40.2/24
   no shutdown
   !
   hsrp version 2
   hsrp 0 ipv4
      ip 10.12.40.1
      priority 110
      preempt
   !
!
interface eth1/5
   switchport
   switchport mode access
   switchport access vlan 40
   no shutdown
!
interface eth1/6
   shutdown
!
interface eth1/7
   switchport
   switchport mode access
   switchport access vlan 30
   no shutdown
!
```

c-1-l3:
```
configure terminal
!
vlan 10
   name c-1-h5
!
vlan 20
   name c-1-h6
!
feature interface-vlan
feature hsrp
!
interface Vlan 10
   ip address 10.34.10.2/24
   no shutdown
   !
   hsrp version 2
   hsrp 0 ipv4
      ip 10.34.10.1
      priority 110
      preempt
   !
!
interface Vlan 20
   ip address 10.34.20.2/24
   no shutdown
   !
   hsrp version 2
   hsrp 0 ipv4
      ip 10.34.20.1
      priority 110
      preempt
   !
!
interface eth1/5
   switchport
   switchport mode access
   switchport access vlan 10
   no shutdown
!
interface eth1/6
   switchport
   switchport mode access
   switchport access vlan 20
   no shutdown
!
interface eth1/7
   shutdown
!
```

c-1-l4:
```
configure terminal
!
vlan 30
   name c-1-h7
!
vlan 40
   name c-1-h8
!
feature interface-vlan
feature hsrp
!
interface Vlan 30
   ip address 10.34.30.2/24
   no shutdown
   !
   hsrp version 2
   hsrp 0 ipv4
      ip 10.34.30.1
      priority 100
      preempt
   !
!
interface Vlan 40
   ip address 10.34.40.2/24
   no shutdown
   !
   hsrp version 2
   hsrp 0 ipv4
      ip 10.34.40.1
      priority 110
      preempt
   !
!
interface eth1/5
   switchport
   switchport mode access
   switchport access vlan 40
   no shutdown
!
interface eth1/6
   shutdown
!
interface eth1/7
   switchport
   switchport mode access
   switchport access vlan 30
   no shutdown
!
```

## OSPF
### Core OSPF
c-1-s1:
```
configure terminal
!
feature ospf
!
router ospf core-dc
   log-adjacency-changes detail
   router-id 10.0.255.20
   timers throttle spf 50 50 1000
   timers throttle lsa 0 50 1000
!
interface loopback 0
   ip router ospf core-dc area 0.0.0.0 
!
interface loopback 1
   ip router ospf core-dc area 0.0.0.0 
!
interface ethernet 1/2
   ip router ospf core-dc area 0.0.0.0 
   ip ospf network point-to-point 
!
interface ethernet 1/3
   ip router ospf core-dc area 0.0.0.0 
   ip ospf network point-to-point 
!
interface ethernet 1/4
   ip router ospf core-dc area 0.0.0.0 
   ip ospf network point-to-point 
!
interface ethernet 1/5
   ip router ospf core-dc area 0.0.0.0 
   ip ospf network point-to-point 
!
interface ethernet 1/6
   ip router ospf core-dc area 0.0.0.0 
   ip ospf network point-to-point 
!
interface ethernet 1/7
   ip router ospf core-dc area 0.0.0.0 
   ip ospf network point-to-point 
!
```

c-1-s2:
```
configure terminal
!
feature ospf
!
router ospf core-dc
   log-adjacency-changes detail
   router-id 10.0.255.21
   timers throttle spf 50 50 1000
   timers throttle lsa 0 50 1000
!
interface loopback 0
   ip router ospf core-dc area 0.0.0.0 
!
interface loopback 1
   ip router ospf core-dc area 0.0.0.0 
!
interface ethernet 1/2
   ip router ospf core-dc area 0.0.0.0 
   ip ospf network point-to-point 
!
interface ethernet 1/3
   ip router ospf core-dc area 0.0.0.0 
   ip ospf network point-to-point 
!
interface ethernet 1/4
   ip router ospf core-dc area 0.0.0.0 
   ip ospf network point-to-point 
!
interface ethernet 1/5
   ip router ospf core-dc area 0.0.0.0 
   ip ospf network point-to-point 
!
interface ethernet 1/6
   ip router ospf core-dc area 0.0.0.0 
   ip ospf network point-to-point 
!
interface ethernet 1/7
   ip router ospf core-dc area 0.0.0.0 
   ip ospf network point-to-point 
!
```

c-1-l1:
```
configure terminal
!
feature ospf
!
router ospf core-dc
   log-adjacency-changes detail
   router-id 10.0.255.30
   timers throttle spf 50 50 1000
   timers throttle lsa 0 50 1000
!
interface loopback 0
   ip router ospf core-dc area 0.0.0.0 
!
interface ethernet 1/1
   ip router ospf core-dc area 0.0.0.0 
   ip ospf network point-to-point 
!
interface ethernet 1/2
   ip router ospf core-dc area 0.0.0.0 
   ip ospf network point-to-point 
!
interface ethernet 1/3
   ip router ospf core-dc area 0.0.0.0 
   ip ospf network point-to-point 
!
interface ethernet 1/4
   ip router ospf core-dc area 0.0.0.12
   ip ospf network point-to-point 
!
```

c-1-l2:
```
configure terminal
!
feature ospf
!
router ospf core-dc
   log-adjacency-changes detail
   router-id 10.0.255.31
   timers throttle spf 50 50 1000
   timers throttle lsa 0 50 1000
!
interface loopback 0
   ip router ospf core-dc area 0.0.0.0 
!
interface ethernet 1/1
   ip router ospf core-dc area 0.0.0.0 
   ip ospf network point-to-point 
!
interface ethernet 1/2
   ip router ospf core-dc area 0.0.0.0 
   ip ospf network point-to-point 
!
interface ethernet 1/3
   ip router ospf core-dc area 0.0.0.0 
   ip ospf network point-to-point 
!
interface ethernet 1/4
   ip router ospf core-dc area 0.0.0.12
   ip ospf network point-to-point 
!
```

c-1-l3:
```
configure terminal
!
feature ospf
!
router ospf core-dc
   log-adjacency-changes detail
   router-id 10.0.255.32
   timers throttle spf 50 50 1000
   timers throttle lsa 0 50 1000
!
interface loopback 0
   ip router ospf core-dc area 0.0.0.0 
!
interface ethernet 1/1
   ip router ospf core-dc area 0.0.0.0 
   ip ospf network point-to-point 
!
interface ethernet 1/2
   ip router ospf core-dc area 0.0.0.0 
   ip ospf network point-to-point 
!
interface ethernet 1/3
   ip router ospf core-dc area 0.0.0.0 
   ip ospf network point-to-point 
!
interface ethernet 1/4
   ip router ospf core-dc area 0.0.0.34 
   ip ospf network point-to-point 
!
```

c-1-l4:
```
configure terminal
!
feature ospf
!
router ospf core-dc
   log-adjacency-changes detail
   router-id 10.0.255.33
   timers throttle spf 50 50 1000
   timers throttle lsa 0 50 1000
!
interface loopback 0
   ip router ospf core-dc area 0.0.0.0 
!
interface ethernet 1/1
   ip router ospf core-dc area 0.0.0.0 
   ip ospf network point-to-point 
!
interface ethernet 1/2
   ip router ospf core-dc area 0.0.0.0 
   ip ospf network point-to-point 
!
interface ethernet 1/3
   ip router ospf core-dc area 0.0.0.0 
   ip ospf network point-to-point 
!
interface ethernet 1/4
   ip router ospf core-dc area 0.0.0.34
   ip ospf network point-to-point 
!
```

### Core OSPF Authentication
All spines:
```
configure terminal
!
key chain KC_OSPF_CORE_DC
  key 0
    key-string SUPER_SECRET_PASSWORD
    accept-lifetime 00:00:00 Jul 29 2022  infinite
    send-lifetime 00:00:00 Jul 29 2022  infinite
    cryptographic-algorithm HMAC-SHA-256
!
router ospf core-dc
    area 0.0.0.0 authentication message-digest
!
interface eth 1/2
    ip ospf authentication key-chain KC_OSPF_CORE_DC
!
interface eth 1/3
    ip ospf authentication key-chain KC_OSPF_CORE_DC
!
interface eth 1/4
    ip ospf authentication key-chain KC_OSPF_CORE_DC
!
interface eth 1/5
    ip ospf authentication key-chain KC_OSPF_CORE_DC
!
interface eth 1/6
    ip ospf authentication key-chain KC_OSPF_CORE_DC
!
interface eth 1/7
    ip ospf authentication key-chain KC_OSPF_CORE_DC
!
```

leafs 1-2:
```
configure terminal
!
key chain KC_OSPF_CORE_DC
  key 0
    key-string SUPER_SECRET_PASSWORD
    accept-lifetime 00:00:00 Jul 29 2022  infinite
    send-lifetime 00:00:00 Jul 29 2022  infinite
    cryptographic-algorithm HMAC-SHA-256
!
router ospf core-dc
    area 0.0.0.0 authentication message-digest
    area 0.0.0.12 authentication message-digest
!
interface eth 1/1
    ip ospf authentication key-chain KC_OSPF_CORE_DC
!
interface eth 1/2
    ip ospf authentication key-chain KC_OSPF_CORE_DC
!
interface eth 1/3
    ip ospf authentication key-chain KC_OSPF_CORE_DC
!
interface eth 1/4
    ip ospf authentication key-chain KC_OSPF_CORE_DC
!
```

leafs 3-4:
```
configure terminal
!
key chain KC_OSPF_CORE_DC
  key 0
    key-string SUPER_SECRET_PASSWORD
    accept-lifetime 00:00:00 Jul 29 2022  infinite
    send-lifetime 00:00:00 Jul 29 2022  infinite
    cryptographic-algorithm HMAC-SHA-256
!
router ospf core-dc
    area 0.0.0.0 authentication message-digest
    area 0.0.0.34 authentication message-digest
!
interface eth 1/1
    ip ospf authentication key-chain KC_OSPF_CORE_DC
!
interface eth 1/2
    ip ospf authentication key-chain KC_OSPF_CORE_DC
!
interface eth 1/3
    ip ospf authentication key-chain KC_OSPF_CORE_DC
!
interface eth 1/4
    ip ospf authentication key-chain KC_OSPF_CORE_DC
!
```

### Customer-facing OSPF
c-1-l1:
```
configure terminal
!
router ospf core-dc
   area 0.0.0.12 range 10.12.0.0/16
!
interface vlan 10
   ip ospf passive-interface
   ip router ospf core-dc area 0.0.0.12
!
interface vlan 20
   ip ospf passive-interface
   ip router ospf core-dc area 0.0.0.12
!
```

c-1-l2:
```
configure terminal
!
router ospf core-dc
   area 0.0.0.12 range 10.12.0.0/16
!
interface vlan 30
   ip ospf passive-interface
   ip router ospf core-dc area 0.0.0.12
!
interface vlan 40
   ip ospf passive-interface
   ip router ospf core-dc area 0.0.0.12
!
```

c-1-l3:
```
configure terminal
!
router ospf core-dc
   area 0.0.0.34 range 10.34.0.0/16
!
interface vlan 10
   ip ospf passive-interface
   ip router ospf core-dc area 0.0.0.34
!
interface vlan 20
   ip ospf passive-interface
   ip router ospf core-dc area 0.0.0.34
!
```

c-1-l4:
```
configure terminal
!
router ospf core-dc
   area 0.0.0.34 range 10.34.0.0/16
!
interface vlan 30
   ip ospf passive-interface
   ip router ospf core-dc area 0.0.0.34
!
interface vlan 40
   ip ospf passive-interface
   ip router ospf core-dc area 0.0.0.34
!
```

## Multicasting
### IGMP
c-1-l1:
```
configure terminal
!
interface vlan 10
   ip igmp version 3
!
interface vlan 20
   ip igmp version 3
!
```

c-1-l2:
```
configure terminal
!
interface vlan 30
   ip igmp version 3
!
interface vlan 40
   ip igmp version 3
!
```

c-1-l3:
```
configure terminal
!
interface vlan 10
   ip igmp version 3
!
interface vlan 20
   ip igmp version 3
!
```

c-1-l4:
```
configure terminal
!
interface vlan 30
   ip igmp version 3
!
interface vlan 40
   ip igmp version 3
!
```

### PIM
c-1-s1:
```
configure terminal
!
feature pim
!
ip pim log-neighbor-changes
!
interface ethernet 1/2
   ip pim sparse-mode
!
interface ethernet 1/3
   ip pim sparse-mode
!
interface ethernet 1/4
   ip pim sparse-mode
!
interface ethernet 1/5
   ip pim sparse-mode
!
interface ethernet 1/6
   ip pim sparse-mode
!
interface ethernet 1/7
   ip pim sparse-mode
!
interface loopback 0
   ip pim sparse-mode
!
interface loopback 1
   ip pim sparse-mode
!
```

c-1-s2:
```
configure terminal
!
feature pim
!
ip pim log-neighbor-changes
!
interface ethernet 1/2
   ip pim sparse-mode
!
interface ethernet 1/3
   ip pim sparse-mode
!
interface ethernet 1/4
   ip pim sparse-mode
!
interface ethernet 1/5
   ip pim sparse-mode
!
interface ethernet 1/6
   ip pim sparse-mode
!
interface ethernet 1/7
   ip pim sparse-mode
!
interface loopback 0
   ip pim sparse-mode
!
interface loopback 1
   ip pim sparse-mode
!
```

c-1-l1:
```
configure terminal
!
feature pim
!
ip pim log-neighbor-changes
!
interface ethernet 1/1
   ip pim sparse-mode
!
interface ethernet 1/2
   ip pim sparse-mode
!
interface ethernet 1/3
   ip pim sparse-mode
!
interface ethernet 1/4
   ip pim sparse-mode
!
interface vlan 10
   ip pim sparse-mode
   ip pim passive
!
interface vlan 20
   ip pim sparse-mode
   ip pim passive
!
```

c-1-l2:
```
configure terminal
!
feature pim
!
ip pim log-neighbor-changes
!
interface ethernet 1/1
   ip pim sparse-mode
!
interface ethernet 1/2
   ip pim sparse-mode
!
interface ethernet 1/3
   ip pim sparse-mode
!
interface ethernet 1/4
   ip pim sparse-mode
!
interface vlan 30
   ip pim sparse-mode
   ip pim passive
!
interface vlan 40
   ip pim sparse-mode
   ip pim passive
!
```

c-1-l3:
```
configure terminal
!
feature pim
!
ip pim log-neighbor-changes
!
interface ethernet 1/1
   ip pim sparse-mode
!
interface ethernet 1/2
   ip pim sparse-mode
!
interface ethernet 1/3
   ip pim sparse-mode
!
interface ethernet 1/4
   ip pim sparse-mode
!
interface vlan 10
   ip pim sparse-mode
   ip pim passive
!
interface vlan 20
   ip pim sparse-mode
   ip pim passive
!
```

c-1-l4:
```
configure terminal
!
feature pim
!
ip pim log-neighbor-changes
!
interface ethernet 1/1
   ip pim sparse-mode
!
interface ethernet 1/2
   ip pim sparse-mode
!
interface ethernet 1/3
   ip pim sparse-mode
!
interface ethernet 1/4
   ip pim sparse-mode
!
interface vlan 30
   ip pim sparse-mode
   ip pim passive
!
interface vlan 40
   ip pim sparse-mode
   ip pim passive
!
```

### PIM Authentication
All spines:
```
configure terminal
!
interface ethernet 1/2
   ip pim hello-authentication ah-md5 SUPER_MSEC
!
interface ethernet 1/3
   ip pim hello-authentication ah-md5 SUPER_MSEC
!
interface ethernet 1/4
   ip pim hello-authentication ah-md5 SUPER_MSEC
!
interface ethernet 1/5
   ip pim hello-authentication ah-md5 SUPER_MSEC
!
interface ethernet 1/6
   ip pim hello-authentication ah-md5 SUPER_MSEC
!
interface ethernet 1/7
   ip pim hello-authentication ah-md5 SUPER_MSEC
!
```

All leafs:
```
configure terminal
!
interface ethernet 1/1
   ip pim hello-authentication ah-md5 SUPER_MSEC
!
interface ethernet 1/2
   ip pim hello-authentication ah-md5 SUPER_MSEC
!
interface ethernet 1/3
   ip pim hello-authentication ah-md5 SUPER_MSEC
!
interface ethernet 1/4
   ip pim hello-authentication ah-md5 SUPER_MSEC
!
```

#### PIM ASM
All devices:
```
configure terminal
!
ip prefix-list PL_IPV4_MCAST_ASM seq 10 permit 239.0.0.0/8
!
ip pim rp-address 10.0.254.1 prefix-list PL_IPV4_MCAST_ASM 
!
```

c-1-s1:
```
configure terminal
!
ip pim anycast-rp 10.0.254.1 10.0.255.20
!
```

c-1-s2:
```
configure terminal
!
ip pim anycast-rp 10.0.254.1 10.0.255.21
!
```

#### PIM BIDIR (Phantom RP)
All devices:
```
configure terminal
!
ip prefix-list PL_IPV4_MCAST_BIDIR_1 seq 10 permit 238.0.0.0/24
ip prefix-list PL_IPV4_MCAST_BIDIR_2 seq 10 permit 238.0.1.0/24
!
ip pim rp-address 10.0.254.4 prefix-list PL_IPV4_MCAST_BIDIR_1 bidir
ip pim rp-address 10.0.254.8 prefix-list PL_IPV4_MCAST_BIDIR_2 bidir
!
```

c-1-s1:
```
configure terminal
!
interface loopback 2
    ip address 10.0.254.5/31
    ip pim sparse-mode
    no shutdown
    ip router ospf core-dc area 0.0.0.0
    ip ospf advertise-subnet
!
interface loopback 3
    ip address 10.0.254.9/30
    ip pim sparse-mode
    no shutdown
    ip router ospf core-dc area 0.0.0.0
    ip ospf advertise-subnet
!
```

c-1-s2:
```
configure terminal
!
interface loopback 2
    ip address 10.0.254.5/30
    ip pim sparse-mode
    no shutdown
    ip router ospf core-dc area 0.0.0.0
    ip ospf advertise-subnet
!
interface loopback 3
    ip address 10.0.254.9/31
    ip pim sparse-mode
    no shutdown
    ip router ospf core-dc area 0.0.0.0
    ip ospf advertise-subnet
!
```

#### PIM SSM
No config is needed


## Errors faced
On the configuration of PIM-BIDIR
```
c-1-s2(config)# 2022 Jul 30 21:22:56 c-1-s2 %VSHD-5-VSHD_SYSLOG_CONFIG_I: Configured from vty by admin on 192.168.101.1@pts/3 (message repeated 1 time)
2022 Jul 30 21:22:56 c-1-s2 %IPFIB-SLOT1-2-FIB_MCAST_BIDIR_ACL_MISSING: mcast-bidir TCAM region not carved on unit: 0 or failed init. Use 'hardware profile tcam resource template <custom template> ref-template nfe(T2)/nfe2(TH)' 'mcast_bidir 256.''Apply the service-template'
```