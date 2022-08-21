# Arista EOS + HAProxy + FRR + NGINX Lab
This lab aims to test High-available FRR setup leveraging 

## Management
### Credentails
all switches:
```
enable
!
configure terminal
!
username zthnat privilege 15 secret tanhtz0!
!
aaa authentication login default local
aaa authentication enable default none
!
copy running-config startup-config
!
```

### IP addresses (DC)
c-3-b1:
```
enable
!
configure terminal
    vrf instance mgmt 
    !
    ip routing 
    ip routing vrf mgmt
    !
    interface Management 1
        vrf mgmt
        ip address 192.168.101.100/24
        ipv6 add fc00:192:168:101::100/64
        no shut
    !
    ip route vrf mgmt 0.0.0.0 0.0.0.0 192.168.101.1
    ipv6 route vrf mgmt ::/0 fc00:192:168:101::1
!
copy running-config startup-config
!
```

c-3-s1:
```
enable
!
configure terminal
    vrf instance mgmt 
    !
    ip routing 
    ip routing vrf mgmt
    !
    interface Management 1
        vrf mgmt
        ip address 192.168.101.101/24
        ipv6 add fc00:192:168:101::101/64
        no shut
    !
    ip route vrf mgmt 0.0.0.0 0.0.0.0 192.168.101.1
    ipv6 route vrf mgmt ::/0 fc00:192:168:101::1
!
copy running-config startup-config
!
```

c-3-l1:
```
enable
!
configure terminal
    vrf instance mgmt 
    !
    ip routing 
    ip routing vrf mgmt
    !
    interface Management 1
        vrf mgmt
        ip address 192.168.101.102/24
        ipv6 add fc00:192:168:101::102/64
        no shut
    !
    ip route vrf mgmt 0.0.0.0 0.0.0.0 192.168.101.1
    ipv6 route vrf mgmt ::/0 fc00:192:168:101::1
!
copy running-config startup-config
!
```

c-3-l2:
```
enable
!
configure terminal
    vrf instance mgmt 
    !
    ip routing 
    ip routing vrf mgmt
    !
    interface Management 1
        vrf mgmt
        ip address 192.168.101.103/24
        ipv6 add fc00:192:168:101::103/64
        no shut
    !
    ip route vrf mgmt 0.0.0.0 0.0.0.0 192.168.101.1
    ipv6 route vrf mgmt ::/0 fc00:192:168:101::1
!
copy running-config startup-config
!
```

### Hostname and domain (DC)
c-3-b1:
```
enable
!
configure terminal
    hostname c-3-b1
    dns domain lab.karneliuk.com
!
copy running-config startup-config
!
```

c-3-s1:
```
enable
!
configure terminal
    hostname c-3-s1
    dns domain lab.karneliuk.com
!
copy running-config startup-config
!
```

c-3-l1:
```
enable
!
configure terminal
    hostname c-3-l1
    dns domain lab.karneliuk.com
!
copy running-config startup-config
!
```

c-3-l2:
```
enable
!
configure terminal
    hostname c-3-l2
    dns domain lab.karneliuk.com
!
copy running-config startup-config
!
```

### IP addresses (SF)
c-3-lb1:
```
$ sudo tee /etc/netplan/00-installer-config.yaml << __EOF__
# This is the network config written by 'subiquity'
network:
  ethernets:
    ens18:
      addresses:
      - 192.168.101.90/24
      routes:
        - to: default
          via: 192.168.101.1
      nameservers:
        addresses:
        - 9.9.9.9
        search: []
    ens19:
      addresses:
      - 10.1.0.1/31
      routes:
        - to: 10.0.0.0/8
          via: 10.1.0.0
      nameservers:
        addresses: []
        search: []
  version: 2
__EOF__

$ sudo netplan apply
```

c-3-lb2:
```
$ sudo tee /etc/netplan/00-installer-config.yaml << __EOF__
# This is the network config written by 'subiquity'
network:
  ethernets:
    ens18:
      addresses:
      - 192.168.101.91/24
      routes:
        - to: default
          via: 192.168.101.1
      nameservers:
        addresses:
        - 9.9.9.9
        search: []
    ens19:
      addresses:
      - 10.1.0.3/31
      routes:
        - to: 10.0.0.0/8
          via: 10.1.0.2
      nameservers:
        addresses: []
        search: []
  version: 2
__EOF__

$ sudo netplan apply
```

c-3-o1:
```
$ sudo tee /etc/netplan/00-installer-config.yaml << __EOF__
# This is the network config written by 'subiquity'
network:
  ethernets:
    ens18:
      addresses:
      - 192.168.101.92/24
      routes:
        - to: default
          via: 192.168.101.1
      nameservers:
        addresses:
        - 9.9.9.9
        search: []
    ens19:
      addresses:
      - 10.1.1.1/31
      routes:
        - to: 10.0.0.0/8
          via: 10.1.1.0
      nameservers:
        addresses: []
        search: []
  version: 2
__EOF__

$ sudo netplan apply
```

c-3-o2:
```
$ sudo tee /etc/netplan/00-installer-config.yaml << __EOF__
# This is the network config written by 'subiquity'
network:
  ethernets:
    ens18:
      addresses:
      - 192.168.101.93/24
      routes:
        - to: default
          via: 192.168.101.1
      nameservers:
        addresses:
        - 9.9.9.9
        search: []
    ens19:
      addresses:
      - 10.1.1.3/31
      routes:
        - to: 10.0.0.0/8
          via: 10.1.1.2
      nameservers:
        addresses: []
        search: []
  version: 2
__EOF__

$ sudo netplan apply
```

c-3-e1:
```
$ tee /etc/netplan/00-installer-config.yaml << __EOF__
# This is the network config written by 'subiquity'
network:
  ethernets:
    ens18:
    
      addresses:
      - 192.168.101.95/24
      routes:
        - to: default
          via: 192.168.101.1
      nameservers:
        addresses:
        - 9.9.9.9
        search: []
    ens19:
      addresses:
      - 10.2.0.1/31
      routes:
        - to: 10.0.0.0/8
          via: 10.2.0.0
      nameservers:
        addresses: []
        search: []
  version: 2
__EOF__

$ netplan apply
```

## Data Centre Fabric Configuration
### Make all interfaces routed by default
All switches:
```
enable
!
configure terminal
    switchport default mode routed
!
```

### Enable IPv6 routing
All switches:
```
enable
!
configure terminal
    ipv6 unicast-routing
!
```

### Core interaces
From now on all further configuation is done via SSH.

c-3-b1:
```
enable
!
configure terminal
    interface loopback 0
        ip address 10.0.255.100/32
        no shutdown
    !
    interface Ethernet 2
        ipv6 enable
        no shutdown
    !
!
```

c-3-s1:
```
enable
!
configure terminal
    interface loopback 0
        ip address 10.0.255.101/32
        no shutdown
    !
    interface Ethernet 1
        ipv6 enable
        no shutdown
    !
    interface Ethernet 2
        ipv6 enable
        no shutdown
    !
    interface Ethernet 3
        ipv6 enable
        no shutdown
    !
!
```

c-3-l1:
```
enable
!
configure terminal
    interface loopback 0
        ip address 10.0.255.102/32
        no shutdown
    !
    interface Ethernet 1
        ipv6 enable
        no shutdown
    !
!
```

c-3-l2:
```
enable
!
configure terminal
    interface loopback 0
        ip address 10.0.255.103/32
        no shutdown
    !
    interface Ethernet 1
        ipv6 enable
        no shutdown
    !
!
```

### Enable BGP multi-agent
All switches:
```
enable
!
configure terminal
    service routing protocols model multi-agent 
!
copy running-config startup-config
!
```

### Reboot switches
All swiches:
```
reload now
!
```

### BGP Core
c-3-b1:
```
enable
!
configure terminal
!
router bgp 65001
    bgp default ipv4-unicast transport ipv6 
    router-id 10.0.255.100
    bgp log-neighbor-changes
    !
    neighbor PG_SPINE remote-as 65002
    neighbor PG_SPINE password DC_PASS
    neighbor PG_SPINE send-community extended
    !
    neighbor interface ethernet 2 peer-group PG_SPINE remote-as 65002
    !
    address-family ipv4
        neighbor PG_SPINE activate 
        neighbor PG_SPINE next-hop address-family ipv6 originate
        network 10.0.255.100/32
    !
    address-family evpn
        neighbor PG_SPINE activate 
    !
!
```

c-3-s1:
```
enable
!
configure terminal
!
router bgp 65002
    bgp default ipv4-unicast transport ipv6 
    router-id 10.0.255.101
    bgp log-neighbor-changes
    !
    neighbor PG_LEAF password DC_PASS
    neighbor PG_LEAF send-community extended
    !
    neighbor interface ethernet 1 peer-group PG_LEAF remote-as 65001
    neighbor interface ethernet 2 peer-group PG_LEAF remote-as 65003
    neighbor interface ethernet 3 peer-group PG_LEAF remote-as 65004
    !
    address-family ipv4
        neighbor PG_LEAF activate 
        neighbor PG_LEAF next-hop address-family ipv6 originate
        network 10.0.255.101/32
    !
    address-family evpn
        neighbor PG_LEAF activate
        neighbor PG_LEAF next-hop-unchanged
    !
!
```

c-3-l1:
```
enable
!
configure terminal
!
router bgp 65003
    bgp default ipv4-unicast transport ipv6 
    router-id 10.0.255.102
    bgp log-neighbor-changes
    !
    neighbor PG_SPINE password DC_PASS
    neighbor PG_SPINE send-community extended
    !
    neighbor interface ethernet 1 peer-group PG_SPINE remote-as 65002
    !
    address-family ipv4
        neighbor PG_SPINE activate 
        neighbor PG_SPINE next-hop address-family ipv6 originate
        network 10.0.255.102/32
    !
    address-family evpn
        neighbor PG_SPINE activate
    !
!
```

c-3-l2:
```
enable
!
configure terminal
!
router bgp 65004
    bgp default ipv4-unicast transport ipv6 
    router-id 10.0.255.103
    bgp log-neighbor-changes
    !
    neighbor PG_SPINE password DC_PASS
    neighbor PG_SPINE send-community extended
    !
    neighbor interface ethernet 1 peer-group PG_SPINE remote-as 65002
    !
    address-family ipv4
        neighbor PG_SPINE activate 
        neighbor PG_SPINE next-hop address-family ipv6 originate
        network 10.0.255.103/32
    !
    address-family evpn
        neighbor PG_SPINE activate
    !
!
```

### VXLAN interfaces
c-3-b1, c-3-l1, c-3-l2:
```
enable
!
configure terminal
    !
    interface vxlan 1
        vxlan source-interface loopback 0
        vxlan udp-port 4789
    !
!
```

## Customer services configuration
### Customer VRF
c-3-b1, c-3-l1, c-3-l2:
```
enable
!
configure terminal
    !
    vrf instance CUST_1
    !
    ip routing vrf CUST_1
    !
!
``` 

### MAP L3 VNI to VXLAN
c-3-b1, c-3-l1, c-3-l2:
```
enable
!
configure terminal
    !
    interface vxlan 1
        vxlan vrf CUST_1 vni 10001
    !
!
``` 

### Customer interfaces
c-3-b1:
```
enable
!
configure terminal
    !
    interface Ethernet 1
        vrf CUST_1
        ip address 10.2.0.0/31
        no shutdown
    !
!
```

c-3-l1:
```
enable
!
configure terminal
    !
    interface Ethernet 2
        vrf CUST_1
        ip address 10.1.0.0/31
        no shutdown
    !
    interface Ethernet 3
        vrf CUST_1
        ip address 10.1.1.0/31
        no shutdown
    !
!
```

c-3-l2:
```
enable
!
configure terminal
    !
    interface Ethernet 2
        vrf CUST_1
        ip address 10.1.0.2/31
        no shutdown
    !
    interface Ethernet 3
        vrf CUST_1
        ip address 10.1.1.2/31
        no shutdown
    !
!
```

### BGP User prefixes
c-3-b1:
```
enable
!
configure terminal
    !
    ip prefix-list PL_IPV4_CUSTOMER_PREFIXES seq 10 deny 10.0.0.0/16 le 32 
    ip prefix-list PL_IPV4_CUSTOMER_PREFIXES seq 20 permit 10.0.0.0/8 le 32
    !
    route-map RP_IPV4_CUSTOMER_PREFIXES per 10
        match ip address prefix-list PL_IPV4_CUSTOMER_PREFIXES
    !
    route-map RP_IPV4_CUSTOMER_PREFIXES deny 9999
    !
    router bgp 65001
        vrf CUST_1
            rd 65000:1
            route-target import evpn 65000:1
            route-target export 65000:1
            route-target export evpn 65000:1
            redistribute connected route-map RP_IPV4_CUSTOMER_PREFIXES
        !
    !
!
```

c-3-l1:
```
enable
!
configure terminal
    !
    ip prefix-list PL_IPV4_CUSTOMER_PREFIXES seq 10 deny 10.0.0.0/16 le 32 
    ip prefix-list PL_IPV4_CUSTOMER_PREFIXES seq 20 permit 10.0.0.0/8 le 32
    !
    route-map RP_IPV4_CUSTOMER_PREFIXES per 10
        match ip address prefix-list PL_IPV4_CUSTOMER_PREFIXES
    !
    route-map RP_IPV4_CUSTOMER_PREFIXES deny 9999
    !
    router bgp 65003
        vrf CUST_1
            rd 65000:1
            route-target import evpn 65000:1
            route-target export 65000:1
            route-target export evpn 65000:1
            redistribute connected route-map RP_IPV4_CUSTOMER_PREFIXES
        !
    !
!
```

c-3-l2:
```
enable
!
configure terminal
    !
    ip prefix-list PL_IPV4_CUSTOMER_PREFIXES seq 10 deny 10.0.0.0/16 le 32 
    ip prefix-list PL_IPV4_CUSTOMER_PREFIXES seq 20 permit 10.0.0.0/8 le 32
    !
    route-map RP_IPV4_CUSTOMER_PREFIXES per 10
        match ip address prefix-list PL_IPV4_CUSTOMER_PREFIXES
    !
    route-map RP_IPV4_CUSTOMER_PREFIXES deny 9999
    !
    router bgp 65004
        vrf CUST_1
            rd 65000:1
            route-target import evpn 65000:1
            route-target export 65000:1
            route-target export evpn 65000:1
            redistribute connected route-map RP_IPV4_CUSTOMER_PREFIXES
        !
    !
!
```