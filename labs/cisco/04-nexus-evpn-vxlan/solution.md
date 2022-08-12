# Cisco Nexus EVPN Lab: Solution
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

c-1-b1:
```
configure terminal
!
interface mgmt 0
   vrf member management
   ip addr 192.168.101.18/24
   ipv6 add fc00:192:168:101::18/64
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

c-1-b2:
```
configure terminal
!
interface mgmt 0
   vrf member management
   ip addr 192.168.101.19/24
   ipv6 add fc00:192:168:101::19/64
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

### Hostname and Domain
c-1-b1:
```
configure terminal
!
hostname c-1-b1
ip domain-name lab.karneliuk.com
!
```

c-1-b2:
```
configure terminal
!
hostname c-1-b2
ip domain-name lab.karneliuk.com
!
```

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

## Fabric part
### Interfaces
#### Fabric interaces
From now on all further configuation is done via SSH.

c-1-s1:
```
configure terminal
!
interface ethernet 1/1
   no switchport
   shutdown
!
interface ethernet 1/2
   no switchport
   shutdown
!
interface ethernet 1/3
   no switchport
   shutdown
!
interface ethernet 1/4
   no switchport
   ip address 10.0.0.0/31
   no shutdown
   load-interval 5
!
interface ethernet 1/5
   no switchport
   ip address 10.0.0.4/31
   no shutdown
   load-interval 5
!
interface ethernet 1/6
   no switchport
   ip address 10.0.0.8/31
   no shutdown
   load-interval 5
!
interface ethernet 1/7
   no switchport
   ip address 10.0.0.12/31
   no shutdown
   load-interval 5
!
interface ethernet 1/8
   no switchport
   ip address 10.0.0.16/31
   no shutdown
   load-interval 5
!
interface ethernet 1/9
   no switchport
   ip address 10.0.0.20/31
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
interface ethernet 1/1
   no switchport
   shutdown
!
interface ethernet 1/2
   no switchport
   shutdown
!
interface ethernet 1/3
   no switchport
   shutdown
!
interface ethernet 1/4
   no switchport
   ip address 10.0.0.2/31
   no shutdown
   load-interval 5
!
interface ethernet 1/5
   no switchport
   ip address 10.0.0.6/31
   no shutdown
   load-interval 5
!
interface ethernet 1/6
   no switchport
   ip address 10.0.0.10/31
   no shutdown
   load-interval 5
!
interface ethernet 1/7
   no switchport
   ip address 10.0.0.14/31
   no shutdown
   load-interval 5
!
interface ethernet 1/8
   no switchport
   ip address 10.0.0.18/31
   no shutdown
   load-interval 5
!
interface ethernet 1/9
   no switchport
   ip address 10.0.0.22/31
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

c-1-b1:
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
interface ethernet 1/5
   no switchport
   shutdown
!
interface loopback 0
   ip address 10.0.255.18/32
   ip address 10.0.254.101/32 secondary
   no shutdown
!
```

c-1-b2:
```
configure terminal
!
interface ethernet 1/1
   no switchport
   ip address 10.0.0.21/31
   no shutdown
   load-interval 5
!
interface ethernet 1/2
   no switchport
   ip address 10.0.0.23/31
   no shutdown
   load-interval 5
!
interface ethernet 1/5
   no switchport
   shutdown
!
interface loopback 0
   ip address 10.0.255.19/32
   ip address 10.0.254.101/32 secondary
   no shutdown
!
```

c-1-l1:
```
configure terminal
!
interface ethernet 1/1
   no switchport
   ip address 10.0.0.1/31
   no shutdown
   load-interval 5
!
interface ethernet 1/2
   no switchport
   ip address 10.0.0.3/31
   no shutdown
   load-interval 5
!
interface loopback 0
   ip address 10.0.255.30/32
   ip address 10.0.254.201/32 secondary
   no shutdown
!
```

c-1-l2:
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
interface loopback 0
   ip address 10.0.255.31/32
   ip address 10.0.254.201/32 secondary
   no shutdown
!
```

c-1-l3:
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
interface loopback 0
   ip address 10.0.255.32/32
   ip address 10.0.254.202/32 secondary
   no shutdown
!
```

c-1-l4:
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
interface loopback 0
   ip address 10.0.255.33/32
   ip address 10.0.254.202/32 secondary
   no shutdown
!
```

#### IX Port-channel for future peerlink
c-1-b1, c-1-b2, c-1-l1, c-1-l2, c-1-l3, c-1-l4:
```
configure terminal
!
feature lacp
!
interface eth1/3
   switchport
   switchport mode trunk
   channel-group 1 mode active
!
interface eth1/4
   switchport
   switchport mode trunk
   channel-group 1 mode active
!
```

#### IX VLAN over Port-channel
c-1-b1:
```
configure terminal
!
feature interface-vlan
!
vlan 2
   name ix_vlan_to_peer
!
interface Vlan 2
   ip address 10.0.0.28/31
   no shutdown
!
```

c-1-b2:
```
configure terminal
!
feature interface-vlan
!
vlan 2
   name ix_vlan_to_peer
!
interface Vlan 2
   ip address 10.0.0.29/31
   no shutdown
!
```

c-1-l1:
```
configure terminal
!
feature interface-vlan
!
vlan 2
   name ix_vlan_to_peer
!
interface Vlan 2
   ip address 10.0.0.24/31
   no shutdown
!
```

c-1-l2:
```
configure terminal
!
feature interface-vlan
!
vlan 2
   name ix_vlan_to_peer
!
interface Vlan 2
   ip address 10.0.0.25/31
   no shutdown
!
```

c-1-l3:
```
configure terminal
!
feature interface-vlan
!
vlan 2
   name ix_vlan_to_peer
!
interface Vlan 2
   ip address 10.0.0.26/31
   no shutdown
!
```

c-1-l4:
```
configure terminal
!
feature interface-vlan
!
vlan 2
   name ix_vlan_to_peer
!
interface Vlan 2
   ip address 10.0.0.27/31
   no shutdown
!
```

### VPC on leafs and borders
c-1-b1:
```
configure terminal
!
feature vpc
!
vpc domain 101
   peer-switch
   role priority 1
   peer-keepalive destination 192.168.101.19 source 192.168.101.18 vrf management
   peer-gateway
   auto-recovery
   fast-convergence
   ipv6 nd synchronize
   ip arp synchronize

!
interface port-channel 1
   vpc peer-link
!
```

c-1-b2:
```
configure terminal
!
feature vpc
!
vpc domain 101
   peer-switch
   role priority 1024
   peer-keepalive destination 192.168.101.18 source 192.168.101.19 vrf management
   peer-gateway
   auto-recovery
   fast-convergence
   ipv6 nd synchronize
   ip arp synchronize

!
interface port-channel 1
   vpc peer-link
!
```

c-1-l1:
```
configure terminal
!
feature vpc
!
vpc domain 201
   peer-switch
   role priority 1
   peer-keepalive destination 192.168.101.31 source 192.168.101.30 vrf management
   peer-gateway
   auto-recovery
   fast-convergence
   ipv6 nd synchronize
   ip arp synchronize

!
interface port-channel 1
   vpc peer-link
!
```

c-1-l2:
```
configure terminal
!
feature vpc
!
vpc domain 201
   peer-switch
   role priority 1024
   peer-keepalive destination 192.168.101.30 source 192.168.101.31 vrf management
   peer-gateway
   auto-recovery
   fast-convergence
   ipv6 nd synchronize
   ip arp synchronize

!
interface port-channel 1
   vpc peer-link
!
```

c-1-l3:
```
configure terminal
!
feature vpc
!
vpc domain 202
   peer-switch
   role priority 1
   peer-keepalive destination 192.168.101.33 source 192.168.101.32 vrf management
   peer-gateway
   auto-recovery
   fast-convergence
   ipv6 nd synchronize
   ip arp synchronize

!
interface port-channel 1
   vpc peer-link
!
```

c-1-l4:
```
configure terminal
!
feature vpc
!
vpc domain 202
   peer-switch
   role priority 1024
   peer-keepalive destination 192.168.101.32 source 192.168.101.33 vrf management
   peer-gateway
   auto-recovery
   fast-convergence
   ipv6 nd synchronize
   ip arp synchronize
!
interface port-channel 1
   vpc peer-link
!
```

### Fabric Routing
#### IGP
c-1-s1:
```
configure terminal
!
feature ospf
!
router ospf fabric
   router-id 10.0.255.20
   log-adjacency-changes detail
   !
   timers lsa-arrival 10
   timers throttle lsa 0 50 1000
   timers throttle spf 50 50 1000
!
interface Loopback 0-1
   ip router ospf fabric area 0.0.0.0
!
interface ethernet 1/4-9
   ip router ospf fabric area 0.0.0.0
   ip ospf network point-to-point
!
```

c-1-s2:
```
configure terminal
!
feature ospf
!
router ospf fabric
   router-id 10.0.255.21
   log-adjacency-changes detail
   !
   timers lsa-arrival 10
   timers throttle lsa 0 50 1000
   timers throttle spf 50 50 1000
!
interface Loopback 0-1
   ip router ospf fabric area 0.0.0.0
!
interface ethernet 1/4-9
   ip router ospf fabric area 0.0.0.0
   ip ospf network point-to-point
!
```

c-1-b1:
```
configure terminal
!
feature ospf
!
router ospf fabric
   router-id 10.0.255.18
   log-adjacency-changes detail
   !
   timers lsa-arrival 10
   timers throttle lsa 0 50 1000
   timers throttle spf 50 50 1000
!
interface Loopback 0
   ip router ospf fabric area 0.0.0.0
!
interface ethernet 1/1-2
   ip router ospf fabric area 0.0.0.0
   ip ospf network point-to-point
!
interface vlan 2
   ip router ospf fabric area 0.0.0.0
   ip ospf network point-to-point
!
```

c-1-b2:
```
configure terminal
!
feature ospf
!
router ospf fabric
   router-id 10.0.255.19
   log-adjacency-changes detail
   !
   timers lsa-arrival 10
   timers throttle lsa 0 50 1000
   timers throttle spf 50 50 1000
!
interface Loopback 0
   ip router ospf fabric area 0.0.0.0
!
interface ethernet 1/1-2
   ip router ospf fabric area 0.0.0.0
   ip ospf network point-to-point
!
interface vlan 2
   ip router ospf fabric area 0.0.0.0
   ip ospf network point-to-point
!
```

c-1-l1:
```
configure terminal
!
feature ospf
!
router ospf fabric
   router-id 10.0.255.30
   log-adjacency-changes detail
   !
   timers lsa-arrival 10
   timers throttle lsa 0 50 1000
   timers throttle spf 50 50 1000
!
interface Loopback 0
   ip router ospf fabric area 0.0.0.0
!
interface ethernet 1/1-2
   ip router ospf fabric area 0.0.0.0
   ip ospf network point-to-point
!
interface vlan 2
   ip router ospf fabric area 0.0.0.0
   ip ospf network point-to-point
!
```

c-1-l2:
```
configure terminal
!
feature ospf
!
router ospf fabric
   router-id 10.0.255.31
   log-adjacency-changes detail
   !
   timers lsa-arrival 10
   timers throttle lsa 0 50 1000
   timers throttle spf 50 50 1000
!
interface Loopback 0
   ip router ospf fabric area 0.0.0.0
!
interface ethernet 1/1-2
   ip router ospf fabric area 0.0.0.0
   ip ospf network point-to-point
!
interface vlan 2
   ip router ospf fabric area 0.0.0.0
   ip ospf network point-to-point
!
```

c-1-l3:
```
configure terminal
!
feature ospf
!
router ospf fabric
   router-id 10.0.255.32
   log-adjacency-changes detail
   !
   timers lsa-arrival 10
   timers throttle lsa 0 50 1000
   timers throttle spf 50 50 1000
!
interface Loopback 0
   ip router ospf fabric area 0.0.0.0
!
interface ethernet 1/1-2
   ip router ospf fabric area 0.0.0.0
   ip ospf network point-to-point
!
interface vlan 2
   ip router ospf fabric area 0.0.0.0
   ip ospf network point-to-point
!
```

c-1-l4:
```
configure terminal
!
feature ospf
!
router ospf fabric
   router-id 10.0.255.33
   log-adjacency-changes detail
   !
   timers lsa-arrival 10
   timers throttle lsa 0 50 1000
   timers throttle spf 50 50 1000
!
interface Loopback 0
   ip router ospf fabric area 0.0.0.0
!
interface ethernet 1/1-2
   ip router ospf fabric area 0.0.0.0
   ip ospf network point-to-point
!
interface vlan 2
   ip router ospf fabric area 0.0.0.0
   ip ospf network point-to-point
!
```

#### IGP Authentication
c-1-s1:
```
configure terminal
!
key chain KC_OSPF_AUTH
   key 0
      cryptographic-algorithm HMAC-SHA-256
      accept-lifetime 00:00:00 Aug 7 2022 infinite 
      send-lifetime 00:00:00 Aug 7 2022 infinite
      key-string SUPER_OSPF_PASS
!
router ospf fabric
   area 0.0.0.0 authentication message-digest
!
interface ethernet 1/4-9
   ip ospf authentication key-chain KC_OSPF_AUTH
!
```

c-1-s2:
```
configure terminal
!
key chain KC_OSPF_AUTH
   key 0
      cryptographic-algorithm HMAC-SHA-256
      accept-lifetime 00:00:00 Aug 7 2022 infinite 
      send-lifetime 00:00:00 Aug 7 2022 infinite
      key-string SUPER_OSPF_PASS
!
router ospf fabric
   area 0.0.0.0 authentication message-digest
!
interface ethernet 1/4-9
   ip ospf authentication key-chain KC_OSPF_AUTH
!
```


c-1-b1, c-1-b2, c-1-l1, c-1-l2, c-1-l3, c-1-l4:
```
configure terminal
!
key chain KC_OSPF_AUTH
   key 0
      cryptographic-algorithm HMAC-SHA-256
      accept-lifetime 00:00:00 Aug 6 2022 infinite 
      send-lifetime 00:00:00 Aug 6 2022 infinite
      key-string SUPER_OSPF_PASS
!
router ospf fabric
   area 0.0.0.0 authentication message-digest
!
interface ethernet 1/1-2
   ip ospf authentication key-chain KC_OSPF_AUTH
!
interface vlan 2
   ip ospf authentication key-chain KC_OSPF_AUTH
!
```

#### Multicast
c-1-s1, c-1-s2:
```
configure terminal
!
feature pim
!
ip pim log-neighbor-changes 
!
interface loopback 0-1
   ip pim sparse-mode
!
interface ethernet 1/4-9
   ip pim sparse-mode
!
ip prefix-list PL_IPV4_ASM_VTEP seq 10 permit 239.11.11.0/24
ip pim rp-address 10.0.254.1 prefix-list PL_IPV4_ASM_VTEP
!
ip pim anycast-rp 10.0.254.1 10.0.255.20
ip pim anycast-rp 10.0.254.1 10.0.255.21
!
```

c-1-b1, c-1-b2, c-1-l1, c-1-l2, c-1-l3, c-1-l4:
```
configure terminal
!
feature pim
!
ip pim log-neighbor-changes 
!
interface loopback 0
   ip pim sparse-mode
!
interface ethernet 1/1-2
   ip pim sparse-mode
!
interface Vlan 2
   ip pim sparse-mode
!
ip prefix-list PL_IPV4_ASM_VTEP seq 10 permit 239.11.11.0/24
ip pim rp-address 10.0.254.1 prefix-list PL_IPV4_ASM_VTEP
!
```

#### Multicast Authentication
c-1-s1, c-1-s2:
```
configure terminal
!
interface ethernet 1/4-9
   ip pim hello-authentication ah-md5 MCAST_AUTH
!
```

c-1-b1, c-1-b2, c-1-l1, c-1-l2, c-1-l3, c-1-l4:
```
configure terminal
!
interface ethernet 1/1-2
   ip pim hello-authentication ah-md5 MCAST_AUTH
!
interface Vlan 2
   ip pim hello-authentication ah-md5 MCAST_AUTH
!
```

#### Enable EVPN Control plane
On all devices:
```
configure terminal
!
nv overlay evpn
!
```

#### BGP for EVPN
c-1-s1:
```
configure terminal
!
feature bgp
!
router bgp 65000
   router-id 10.0.255.20
   log-neighbor-changes
   !
   template peer-session TPS_IBGP_EVPN_VTEPS
      update-source loopback 0
      password BGP_AUTH_1
   !
   template peer-policy TPP_IBGP_EVPN_VTEPS
      send-community
      send-community extended
      route-reflector-client
   !
   template peer TP_IBGP_EVPN_VTEPS
      inherit peer-session TPS_IBGP_EVPN_VTEPS
      address-family l2vpn evpn
         inherit peer-policy TPP_IBGP_EVPN_VTEPS 1
      !
   !
   neighbor 10.0.255.18 remote-as 65000
      inherit peer TP_IBGP_EVPN_VTEPS
   !
   neighbor 10.0.255.19 remote-as 65000
      inherit peer TP_IBGP_EVPN_VTEPS
   !
   neighbor 10.0.255.30 remote-as 65000
      inherit peer TP_IBGP_EVPN_VTEPS
   !
   neighbor 10.0.255.31 remote-as 65000
      inherit peer TP_IBGP_EVPN_VTEPS
   !
   neighbor 10.0.255.32 remote-as 65000
      inherit peer TP_IBGP_EVPN_VTEPS
   !
   neighbor 10.0.255.33 remote-as 65000
      inherit peer TP_IBGP_EVPN_VTEPS
   !
!
```

c-1-s1:
```
configure terminal
!
feature bgp
!
router bgp 65000
   router-id 10.0.255.21
   log-neighbor-changes
   !
   template peer-session TPS_IBGP_EVPN_VTEPS
      update-source loopback 0
      password BGP_AUTH_1
   !
   template peer-policy TPP_IBGP_EVPN_VTEPS
      send-community
      send-community extended
      route-reflector-client
   !
   template peer TP_IBGP_EVPN_VTEPS
      inherit peer-session TPS_IBGP_EVPN_VTEPS
      address-family l2vpn evpn
         inherit peer-policy TPP_IBGP_EVPN_VTEPS 1
      !
   !
   neighbor 10.0.255.18 remote-as 65000
      inherit peer TP_IBGP_EVPN_VTEPS
   !
   neighbor 10.0.255.19 remote-as 65000
      inherit peer TP_IBGP_EVPN_VTEPS
   !
   neighbor 10.0.255.30 remote-as 65000
      inherit peer TP_IBGP_EVPN_VTEPS
   !
   neighbor 10.0.255.31 remote-as 65000
      inherit peer TP_IBGP_EVPN_VTEPS
   !
   neighbor 10.0.255.32 remote-as 65000
      inherit peer TP_IBGP_EVPN_VTEPS
   !
   neighbor 10.0.255.33 remote-as 65000
      inherit peer TP_IBGP_EVPN_VTEPS
   !
!
```

c-1-b1:
```
configure terminal
!
feature bgp
!
router bgp 65000
   router-id 10.0.255.18
   log-neighbor-changes
   !
   template peer-session TPS_IBGP_EVPN_RR
      update-source loopback 0
      password BGP_AUTH_1
   !
   template peer-policy TPP_IBGP_EVPN_RR
      send-community
      send-community extended
      next-hop-self
   !
   template peer TP_IBGP_EVPN_RR
      inherit peer-session TPS_IBGP_EVPN_RR
      address-family l2vpn evpn
         inherit peer-policy TPP_IBGP_EVPN_RR 1
      !
   !
   neighbor 10.0.255.20 remote-as 65000
      inherit peer TP_IBGP_EVPN_RR
   !
   neighbor 10.0.255.21 remote-as 65000
      inherit peer TP_IBGP_EVPN_RR
   !
!
```

c-1-b2:
```
configure terminal
!
feature bgp
!
router bgp 65000
   router-id 10.0.255.19
   log-neighbor-changes
   !
   template peer-session TPS_IBGP_EVPN_RR
      update-source loopback 0
      password BGP_AUTH_1
   !
   template peer-policy TPP_IBGP_EVPN_RR
      send-community
      send-community extended
      next-hop-self
   !
   template peer TP_IBGP_EVPN_RR
      inherit peer-session TPS_IBGP_EVPN_RR
      address-family l2vpn evpn
         inherit peer-policy TPP_IBGP_EVPN_RR 1
      !
   !
   neighbor 10.0.255.20 remote-as 65000
      inherit peer TP_IBGP_EVPN_RR
   !
   neighbor 10.0.255.21 remote-as 65000
      inherit peer TP_IBGP_EVPN_RR
   !
!
```

c-1-l1:
```
configure terminal
!
feature bgp
!
router bgp 65000
   router-id 10.0.255.30
   log-neighbor-changes
   !
   template peer-session TPS_IBGP_EVPN_RR
      update-source loopback 0
      password BGP_AUTH_1
   !
   template peer-policy TPP_IBGP_EVPN_RR
      send-community
      send-community extended
      next-hop-self
   !
   template peer TP_IBGP_EVPN_RR
      inherit peer-session TPS_IBGP_EVPN_RR
      address-family l2vpn evpn
         inherit peer-policy TPP_IBGP_EVPN_RR 1
      !
   !
   neighbor 10.0.255.20 remote-as 65000
      inherit peer TP_IBGP_EVPN_RR
   !
   neighbor 10.0.255.21 remote-as 65000
      inherit peer TP_IBGP_EVPN_RR
   !
!
```

c-1-l2:
```
configure terminal
!
feature bgp
!
router bgp 65000
   router-id 10.0.255.31
   log-neighbor-changes
   !
   template peer-session TPS_IBGP_EVPN_RR
      update-source loopback 0
      password BGP_AUTH_1
   !
   template peer-policy TPP_IBGP_EVPN_RR
      send-community
      send-community extended
      next-hop-self
   !
   template peer TP_IBGP_EVPN_RR
      inherit peer-session TPS_IBGP_EVPN_RR
      address-family l2vpn evpn
         inherit peer-policy TPP_IBGP_EVPN_RR 1
      !
   !
   neighbor 10.0.255.20 remote-as 65000
      inherit peer TP_IBGP_EVPN_RR
   !
   neighbor 10.0.255.21 remote-as 65000
      inherit peer TP_IBGP_EVPN_RR
   !
!
```

c-1-l3:
```
configure terminal
!
feature bgp
!
router bgp 65000
   router-id 10.0.255.32
   log-neighbor-changes
   !
   template peer-session TPS_IBGP_EVPN_RR
      update-source loopback 0
      password BGP_AUTH_1
   !
   template peer-policy TPP_IBGP_EVPN_RR
      send-community
      send-community extended
      next-hop-self
   !
   template peer TP_IBGP_EVPN_RR
      inherit peer-session TPS_IBGP_EVPN_RR
      address-family l2vpn evpn
         inherit peer-policy TPP_IBGP_EVPN_RR 1
      !
   !
   neighbor 10.0.255.20 remote-as 65000
      inherit peer TP_IBGP_EVPN_RR
   !
   neighbor 10.0.255.21 remote-as 65000
      inherit peer TP_IBGP_EVPN_RR
   !
!
```

c-1-l4:
```
configure terminal
!
feature bgp
!
router bgp 65000
   router-id 10.0.255.33
   log-neighbor-changes
   !
   template peer-session TPS_IBGP_EVPN_RR
      update-source loopback 0
      password BGP_AUTH_1
   !
   template peer-policy TPP_IBGP_EVPN_RR
      send-community
      send-community extended
      next-hop-self
   !
   template peer TP_IBGP_EVPN_RR
      inherit peer-session TPS_IBGP_EVPN_RR
      address-family l2vpn evpn
         inherit peer-policy TPP_IBGP_EVPN_RR 1
      !
   !
   neighbor 10.0.255.20 remote-as 65000
      inherit peer TP_IBGP_EVPN_RR
   !
   neighbor 10.0.255.21 remote-as 65000
      inherit peer TP_IBGP_EVPN_RR
   !
!
```

### VTEP configuration
#### General configuration and VTEP
c-1-b1, c-1-b2, c-1-l1, c-1-l2, c-1-l3, c-1-l4:
```
configure terminal
!
feature vn-segment-vlan-based
feature nv overlay
fabric forwarding anycast-gateway-mac 0000.5e.1234
!
interface nve1  
   no shutdown
   source-interface loopback0
   host-reachability protocol bgp
!
```

#### Advertise-PIP and Virtual-MAC for Anycst VTEP (vPC)
c-1-b1, c-1-b2, c-1-l1, c-1-l2, c-1-l3, c-1-l4:
```
configure terminal
!
interface nve1  
   advertise virtual-rmac
!
router bgp 65000
   address-family l2vpn evpn
      advertise-pip
   !
!
```

#### Change ACL TCAM for ARP supression
c-1-b1, c-1-b2, c-1-l1, c-1-l2, c-1-l3, c-1-l4:
```
configure terminal
!
hardware access-list tcam region arp-ether 256 double-wide
!
```

## Services part
### Customer 1
#### VRF
c-1-b1, c-1-b2, c-1-l1, c-1-l2, c-1-l3, c-1-l4:
```
configure terminal
!
vrf context VRF_SERVICE_CUST_1
   vni 901001
   rd auto
   address-family ipv4 unicast
      route-target both auto
      route-target both auto evpn
   !
   address-family ipv6 unicast
      route-target both auto
      route-target both auto evpn
   !
!
```
#### Core-facing VLAN
c-1-b1, c-1-b2, c-1-l1, c-1-l2, c-1-l3, c-1-l4:
```
configure terminal
!
vlan 1001
   name core_svi_vrf_service_cust_1
   vn-segment 901001
!
```

#### Core-facing SVI
c-1-b1, c-1-b2, c-1-l1, c-1-l2, c-1-l3, c-1-l4:
```
configure terminal
!
interface vlan1001
   no shutdown
   vrf member VRF_SERVICE_CUST_1
   ip forward
   no ip redirects
   ipv6 address use-link-local-only
   no ipv6 redirects
!
```

#### User-facing VLAN
c-1-l1, c-1-l2, c-1-l3, c-1-l4:
```
configure terminal
!
vlan 10
   name user_svi_1_vrf_service_cust_1
   vn-segment 100010
!
vlan 20
   name user_svi_2_vrf_service_cust_1
   vn-segment 100020
!
```

#### User-facing SVI
c-1-l1, c-1-l2, c-1-l3, c-1-l4:
```
configure terminal
!
interface vlan10
   no shutdown
   vrf member VRF_SERVICE_CUST_1
   ip address 192.168.10.1/24 tag 10
   ipv6 address fc00:192:168:10::1/64 tag 10
   fabric forwarding mode anycast-gateway
!
interface vlan20
   no shutdown
   vrf member VRF_SERVICE_CUST_1
   ip address 192.168.20.1/24 tag 10
   ipv6 address fc00:192:168:20::1/64 tag 10
   fabric forwarding mode anycast-gateway
!
```

#### User-facing physical interfaces
c-1-l1:
```
configure terminal
!
interface ethernet 1/5
   switchport
   switchport mode access
   switchport access vlan 10
   no shutdown
!
interface ethernet 1/6
   switchport
   switchport mode access
   switchport access vlan 10
   channel-group 2002 mode active
!
interface port-channel 2002
   vpc 2002
!
interface ethernet 1/7
   switchport
   switchport mode access
   switchport access vlan 20
   channel-group 2003 mode active
!
interface port-channel 2003
   vpc 2003
!
```

c-1-l2:
```
configure terminal
!
interface ethernet 1/6
   switchport
   switchport mode access
   switchport access vlan 10
   channel-group 2002 mode active
!
interface port-channel 2002
   vpc 2002
!
interface ethernet 1/7
   switchport
   switchport mode access
   switchport access vlan 20
   channel-group 2003 mode active
!
interface port-channel 2003
   vpc 2003
!
```

c-1-l3:
```
configure terminal
!
interface ethernet 1/5
   switchport
   switchport mode access
   switchport access vlan 10
   no shutdown
!
interface ethernet 1/6
   switchport
   switchport mode access
   switchport access vlan 20
   channel-group 2006 mode active
!
interface port-channel 2006
   vpc 2006
!
```

c-1-l4:
```
configure terminal
!
interface ethernet 1/5
   switchport
   switchport mode access
   switchport access vlan 20
   no shutdown
!
interface ethernet 1/6
   switchport
   switchport mode access
   switchport access vlan 20
   channel-group 2006 mode active
!
interface port-channel 2006
   vpc 2006
!
```

#### Map VNIs to VTEP
c-1-l1, c-1-l2, c-1-l3, c-1-l4:
```
configure terminal
!
interface nve1
   member vni 901001 associate-vrf
   !
   member vni 100010 mcast-group 239.11.11.10
   !
   member vni 100020 mcast-group 239.11.11.20
   !
!
```

c-1-b1, c-1-b2:
```
configure terminal
!
interface nve1
   member vni 901001 associate-vrf
   !
!
```

#### BGP
c-1-l1, c-1-l2, c-1-l3, c-1-l4:
```
configure terminal
!
route-map RP_REDISTRIBUTE_IN_EVPN_VRF permit 10
  match tag 10
!
router bgp 65000
   vrf VRF_SERVICE_CUST_1
      address-family ipv4 unicast
         redistribute direct route-map RP_REDISTRIBUTE_IN_EVPN_VRF
!
```

### Customer 2
#### VRF
c-1-b1, c-1-b2, c-1-l1, c-1-l2, c-1-l3, c-1-l4:
```
configure terminal
!
vrf context VRF_SERVICE_CUST_2
   vni 901002
   rd auto
   address-family ipv4 unicast
      route-target both auto
      route-target both auto evpn
   !
   address-family ipv6 unicast
      route-target both auto
      route-target both auto evpn
   !
!
```
#### Core-facing VLAN
c-1-b1, c-1-b2, c-1-l1, c-1-l2, c-1-l3, c-1-l4:
```
configure terminal
!
vlan 1002
   name core_svi_vrf_service_cust_2s
   vn-segment 901002
!
```

#### Core-facing SVI
c-1-b1, c-1-b2, c-1-l1, c-1-l2, c-1-l3, c-1-l4:
```
configure terminal
!
interface vlan1002
   no shutdown
   vrf member VRF_SERVICE_CUST_2
   ip forward
   no ip redirects
   ipv6 address use-link-local-only
   no ipv6 redirects
!
```

#### User-facing VLAN
c-1-l1, c-1-l2, c-1-l3, c-1-l4:
```
configure terminal
!
vlan 30
   name user_svi_1_vrf_service_cust_2
   vn-segment 100030
!
```

#### User-facing SVI
c-1-l1, c-1-l2, c-1-l3, c-1-l4:
```
configure terminal
!
interface vlan30
   no shutdown
   vrf member VRF_SERVICE_CUST_2
   ip address 192.168.30.1/24 tag 10
   ipv6 address fc00:192:168:30::1/64 tag 10
   fabric forwarding mode anycast-gateway
!
```

#### User-facing physical interfaces
c-1-l2:
```
configure terminal
!
interface ethernet 1/5
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
interface ethernet 1/7
   switchport
   switchport mode access
   switchport access vlan 30
   channel-group 2007 mode active
!
interface port-channel 2007
   vpc 2007
!
```

c-1-l4:
```
configure terminal
!
interface ethernet 1/7
   switchport
   switchport mode access
   switchport access vlan 30
   channel-group 2007 mode active
!
interface port-channel 2007
   vpc 2007
!
```

#### Map VNIs to VTEP
c-1-l1, c-1-l2, c-1-l3, c-1-l4:
```
configure terminal
!
interface nve1
   member vni 901002 associate-vrf
   !
   member vni 100030 mcast-group 239.11.11.30
   !
!
```

c-1-b1, c-1-b2:
```
configure terminal
!
interface nve1
   member vni 901002 associate-vrf
   !
!
```

#### BGP
c-1-l1, c-1-l2, c-1-l3, c-1-l4:
```
configure terminal
!
router bgp 65000
   vrf VRF_SERVICE_CUST_2
      address-family ipv4 unicast
         redistribute direct route-map RP_REDISTRIBUTE_IN_EVPN_VRF
!
```

### VRF Leaking
c-1-l1, c-1-l2, c-1-l3, c-1-l4:
```
configure terminal
!
vrf context VRF_SERVICE_CUST_1
   address-family ipv4 unicast
      route-target import 65000:901002
   !
!
vrf context VRF_SERVICE_CUST_2
   address-family ipv4 unicast
      route-target import 65000:901001
   !
!
```

## Connection to external network
### Physical link on DC side
c-1-b1:
```
configure terminal
!
interface ethernet 1/5
   no swhitchport
   no shutdown
!
interface ethernet 1/5.10
   encapsulation dot1q 10
   vrf member VRF_SERVICE_CUST_1
   ip address 169.254.0.0/31
   ipv6 address fc00:169:254::/127
   no shutdown
!
```

c-1-b2:
```
configure terminal
!
interface ethernet 1/5
   no switchport
   no shutdown
!
interface ethernet 1/5.10
   encapsulation dot1q 10
   vrf member VRF_SERVICE_CUST_1
   ip address 169.254.0.2/31
   ipv6 address fc00:169:254::2/127
   no shutdown
!
```

### VRF on the PE side
c-1-g1:
```
configure terminal
!
vrf definition VRF_SERVICE_CUST_1
   rd 65001:1
   address-family ipv4 unicast
      route-target both 65001:1
   !
   address-family ipv6 unicast
      route-target both 65001:1
   !
!
```


### Physical links on the PE side
c-1-g1:
```
configure terminal
!
interface GigabitEthernet 5
   load-interval 30
   no shutdown
   cdp enable
!
interface GigabitEthernet 5.10
   encapsulation dot1q 10
   vrf forwarding VRF_SERVICE_CUST_1
   ip address 169.254.0.1 255.255.255.254
   ipv6 address fc00:169:254::1/127
   no shutdown
!
interface GigabitEthernet 6
   load-interval 30
   no shutdown
   cdp enable
!
interface GigabitEthernet 6.10
   encapsulation dot1q 10
   vrf forwarding VRF_SERVICE_CUST_1
   ip address 169.254.0.3 255.255.255.254
   ipv6 address fc00:169:254::3/127
   no shutdown
!
interface GigabitEthernet4
   vrf forwarding VRF_SERVICE_CUST_1
   ip address 192.168.254.1 255.255.255.0
   negotiation auto
   ipv6 address FC00:192:168:254::1/64
!
```

### Route-policy for BGP (DC side)
c-1-b1, c-1-b2:
```
configure terminal
!
ip prefix-list PL_IPV4_AS65000_ROUTES seq 10 permit 192.168.0.0/16 le 24
ipv6 prefix-list PL_IPV6_AS65000_ROUTES seq 10 permit fc00:192:168::/48 le 64
!
route-map RP_IPV4_BGP_EXPORT permit 10
   match ip address prefix-list PL_IPV4_AS65000_ROUTES
   set community 65000:100
route-map RP_IPV4_BGP_EXPORT deny 9999
!
route-map RP_IPV6_BGP_EXPORT permit 10
   match ip address prefix-list PL_IPV6_AS65000_ROUTES
   set community 65000:100
route-map RP_IPV6_BGP_EXPORT deny 9999
!
route-map RP_IPV4_BGP_IMPORT permit 10
!
route-map RP_IPV6_BGP_IMPORT permit 10
!
```

### BGP Option-A (DC side)
c-1-b1:
```
configure terminal
!
router bgp 65000
   !
   vrf VRF_SERVICE_CUST_1
      log-neighbor-changes
      !
      neighbor 169.254.0.1 remote-as 65001
         password inter_as
         address-family ipv4 unicast
            send-community
            route-map RP_IPV4_BGP_EXPORT out
            route-map RP_IPV4_BGP_IMPORT in
         !
      !
      neighbor fc00:169:254::1 remote-as 65001
         password inter_as
         address-family ipv6 unicast
            send-community
            route-map RP_IPV6_BGP_EXPORT out
            route-map RP_IPV6_BGP_IMPORT in
         !
      !
   !
!
```

c-1-b2:
```
configure terminal
!
router bgp 65000
   !
   vrf VRF_SERVICE_CUST_1
      log-neighbor-changes
      !
      neighbor 169.254.0.3 remote-as 65001
         password inter_as
         address-family ipv4 unicast
            send-community
            route-map RP_IPV4_BGP_EXPORT out
            route-map RP_IPV4_BGP_IMPORT in
         !
      !
      neighbor fc00:169:254::3 remote-as 65001
         password inter_as
         address-family ipv6 unicast
            send-community
            route-map RP_IPV6_BGP_EXPORT out
            route-map RP_IPV6_BGP_IMPORT in
         !
      !
   !
!
```

### Route-policy for BGP (PE side)
c-1-g1:
```
configure terminal
!
ip prefix-list PL_IPV4_AS65001_ROUTES seq 10 permit 192.168.254.0/24
ipv6 prefix-list PL_IPV6_AS65001_ROUTES seq 10 permit fc00:192:168:254::/64
!
route-map RP_IPV4_BGP_EXPORT permit 10
   match ip address prefix-list PL_IPV4_AS65001_ROUTES
   set community 65001:100
route-map RP_IPV4_BGP_EXPORT deny 9999
!
route-map RP_IPV6_BGP_EXPORT permit 10
   match ip address prefix-list PL_IPV6_AS65001_ROUTES
   set community 65001:100
route-map RP_IPV6_BGP_EXPORT deny 9999
!
ip as-path access-list 1 permit ^65000$
!
route-map RP_IPV4_BGP_IMPORT permit 10
   match as-path 1
route-map RP_IPV4_BGP_IMPORT deny 9999
!
route-map RP_IPV6_BGP_IMPORT permit 10
   match as-path 1
route-map RP_IPV6_BGP_IMPORT deny 9999
!
```
### BGP Option-A (PE side)
c-1-g1:
```
configure terminal
!
router bgp 65001
   bgp router-id 192.168.255.130
   bgp log-neighbor-changes
   !
   address-family ipv4 unicast vrf VRF_SERVICE_CUST_1
      neighbor 169.254.0.0 remote-as 65000
      neighbor 169.254.0.0 password inter_as
      neighbor 169.254.0.0 send-community
      neighbor 169.254.0.0 route-map RP_IPV4_BGP_EXPORT out
      neighbor 169.254.0.0 route-map RP_IPV4_BGP_IMPORT in
      !
      neighbor 169.254.0.2 remote-as 65000
      neighbor 169.254.0.2 password inter_as
      neighbor 169.254.0.2 send-community
      neighbor 169.254.0.2 route-map RP_IPV4_BGP_EXPORT out
      neighbor 169.254.0.2 route-map RP_IPV4_BGP_IMPORT in
      !
      redistribute connected route-map RP_IPV4_BGP_EXPORT
   !
   address-family ipv6 unicast vrf VRF_SERVICE_CUST_1
      neighbor fc00:169:254:: remote-as 65000
      neighbor fc00:169:254:: password inter_as
      neighbor fc00:169:254:: send-community
      neighbor fc00:169:254:: route-map RP_IPV6_BGP_EXPORT out
      neighbor fc00:169:254:: route-map RP_IPV6_BGP_IMPORT in
      !
      neighbor fc00:169:254::2 remote-as 65000
      neighbor fc00:169:254::2 password inter_as
      neighbor fc00:169:254::2 send-community
      neighbor fc00:169:254::2 route-map RP_IPV6_BGP_EXPORT out
      neighbor fc00:169:254::2 route-map RP_IPV6_BGP_IMPORT in
      !
      redistribute connected route-map RP_IPV6_BGP_EXPORT
   !
!
```

#### BGP ecmp for leafs
c-1-l[1-4]:
```
configure terminal
!
router bgp 65000
   vrf VRF_SERVICE_CUST_1
      address-family ipv4 unicast
         advertise l2vpn evpn
         maximum-paths 2
         maximum-paths ibgp 2
      !
   !
!
```