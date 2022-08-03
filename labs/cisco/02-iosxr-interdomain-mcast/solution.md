# Notes
## Manual cofiguration of Cisco IOS XR
### c-2-d1-pe1
```
hostname c-2-d1-pe1
domain name lab.karneliuk.com
vrf mgmt
 address-family ipv4 unicast
 !
 address-family ipv6 unicast
 !
!
interface MgmtEth0/0/CPU0/0
 vrf mgmt
 ipv4 address 192.168.101.50 255.255.255.0
 ipv6 address fc00:192:168:101::50/64
 no shutdown
!
router static
 vrf mgmt
  address-family ipv4 unicast
   0.0.0.0/0 192.168.101.1
  !
  address-family ipv6 unicast
   ::/0 fc00:192:168:101::1
  !
 !
!
end  
```

### c-2-d1-pe2
```
hostname c-2-d1-pe2
domain name lab.karneliuk.com
vrf mgmt
 address-family ipv4 unicast
 !
 address-family ipv6 unicast
 !
!
interface MgmtEth0/0/CPU0/0
 vrf mgmt
 ipv4 address 192.168.101.51 255.255.255.0
 ipv6 address fc00:192:168:101::51/64
 no shutdown
!
router static
 vrf mgmt
  address-family ipv4 unicast
   0.0.0.0/0 192.168.101.1
  !
  address-family ipv6 unicast
   ::/0 fc00:192:168:101::1
  !
 !
!
end  
```

### c-2-d1-pe3
```
hostname c-2-d1-pe3
domain name lab.karneliuk.com
vrf mgmt
 address-family ipv4 unicast
 !
 address-family ipv6 unicast
 !
!
interface MgmtEth0/0/CPU0/0
 vrf mgmt
 ipv4 address 192.168.101.52 255.255.255.0
 ipv6 address fc00:192:168:101::52/64
 no shutdown
!
router static
 vrf mgmt
  address-family ipv4 unicast
   0.0.0.0/0 192.168.101.1
  !
  address-family ipv6 unicast
   ::/0 fc00:192:168:101::1
  !
 !
!
end  
```

### c-2-d1-pe2
```
hostname c-2-d1-pe2
domain name lab.karneliuk.com
vrf mgmt
 address-family ipv4 unicast
 !
 address-family ipv6 unicast
 !
!
interface MgmtEth0/0/CPU0/0
 vrf mgmt
 ipv4 address 192.168.101.51 255.255.255.0
 ipv6 address fc00:192:168:101::51/64
 no shutdown
!
router static
 vrf mgmt
  address-family ipv4 unicast
   0.0.0.0/0 192.168.101.1
  !
  address-family ipv6 unicast
   ::/0 fc00:192:168:101::1
  !
 !
!
end  
```

### c-2-d1-pe4
```
hostname c-2-d1-pe4
domain name lab.karneliuk.com
vrf mgmt
 address-family ipv4 unicast
 !
 address-family ipv6 unicast
 !
!
interface MgmtEth0/0/CPU0/0
 vrf mgmt
 ipv4 address 192.168.101.53 255.255.255.0
 ipv6 address fc00:192:168:101::53/64
 no shutdown
!
router static
 vrf mgmt
  address-family ipv4 unicast
   0.0.0.0/0 192.168.101.1
  !
  address-family ipv6 unicast
   ::/0 fc00:192:168:101::1
  !
 !
!
end  
```

### c-2-d1-p1
```
hostname c-2-d1-p1
domain name lab.karneliuk.com
vrf mgmt
 address-family ipv4 unicast
 !
 address-family ipv6 unicast
 !
!
interface MgmtEth0/0/CPU0/0
 vrf mgmt
 ipv4 address 192.168.101.54 255.255.255.0
 ipv6 address fc00:192:168:101::54/64
 no shutdown
!
router static
 vrf mgmt
  address-family ipv4 unicast
   0.0.0.0/0 192.168.101.1
  !
  address-family ipv6 unicast
   ::/0 fc00:192:168:101::1
  !
 !
!
end  
```

### c-2-d2-pe1
```
hostname c-2-d2-pe1
domain name lab.karneliuk.com
vrf mgmt
 address-family ipv4 unicast
 !
 address-family ipv6 unicast
 !
!
interface MgmtEth0/0/CPU0/0
 vrf mgmt
 ipv4 address 192.168.101.60 255.255.255.0
 ipv6 address fc00:192:168:101::60/64
 no shutdown
!
router static
 vrf mgmt
  address-family ipv4 unicast
   0.0.0.0/0 192.168.101.1
  !
  address-family ipv6 unicast
   ::/0 fc00:192:168:101::1
  !
 !
!
end
```

### c-2-d2-pe2
```
hostname c-2-d2-pe2
domain name lab.karneliuk.com
vrf mgmt
 address-family ipv4 unicast
 !
 address-family ipv6 unicast
 !
!
interface MgmtEth0/0/CPU0/0
 vrf mgmt
 ipv4 address 192.168.101.61 255.255.255.0
 ipv6 address fc00:192:168:101::61/64
 no shutdown
!
router static
 vrf mgmt
  address-family ipv4 unicast
   0.0.0.0/0 192.168.101.1
  !
  address-family ipv6 unicast
   ::/0 fc00:192:168:101::1
  !
 !
!
end
```

### c-2-d2-pe3
```
hostname c-2-d2-pe3
domain name lab.karneliuk.com
vrf mgmt
 address-family ipv4 unicast
 !
 address-family ipv6 unicast
 !
!
interface MgmtEth0/0/CPU0/0
 vrf mgmt
 ipv4 address 192.168.101.62 255.255.255.0
 ipv6 address fc00:192:168:101::62/64
 no shutdown
!
router static
 vrf mgmt
  address-family ipv4 unicast
   0.0.0.0/0 192.168.101.1
  !
  address-family ipv6 unicast
   ::/0 fc00:192:168:101::1
  !
 !
!
end
```

### c-2-d2-p1
```
hostname c-2-d2-p1
domain name lab.karneliuk.com
vrf mgmt
 address-family ipv4 unicast
 !
 address-family ipv6 unicast
 !
!
interface MgmtEth0/0/CPU0/0
 vrf mgmt
 ipv4 address 192.168.101.63 255.255.255.0
 ipv6 address fc00:192:168:101::63/64
 no shutdown
!
router static
 vrf mgmt
  address-family ipv4 unicast
   0.0.0.0/0 192.168.101.1
  !
  address-family ipv6 unicast
   ::/0 fc00:192:168:101::1
  !
 !
!
end
```

## Enable SSH
### Downloaded PIE to Cisco IOS XR routers
```
copy tftp://192.168.101.1/xrvr-k9sec-x.pie-6.5.1.34I disk0: vrf mgmt
```

### Install the downloaded PIE
```
admin
install add disk0:/xrvr-k9sec-x.pie-6.5.1.34I
install activate disk0:xrvr-k9sec-x-6.5.1.34I
install commit
exit
```

### Generate SSH keys
```
crypto key generate rsa general-keys 
```

### Enable SSH server
```
conf t
ssh server v2
ssh server vrf mgmt
no ssh server vrf default
commit
```








# Configuration of DC1
## Interfaces
c-2-d1-pe1
```
interface Loopback0
 ipv4 address 10.0.255.1 255.255.255.254
 ipv6 address fc00:10:0:255::1/128
 no shutdown
!
interface GigabitEthernet0/0/0/1
 ipv4 address 10.0.0.2 255.255.255.254
 ipv6 address fc00:10::2/127
 no shutdown
!
interface GigabitEthernet0/0/0/2
 ipv4 address 100.64.0.0 255.255.255.254
 ipv6 address fc00:100:64::/127
 no shutdown
!
interface GigabitEthernet0/0/0/3
 ipv4 address 10.0.0.4 255.255.255.254
 ipv6 address fc00:10::4/127
 no shutdown
!
```

c-2-d1-pe2
```
interface GigabitEthernet0/0/0/0
 ipv4 address 10.0.0.1 255.255.255.254
 ipv6 address fc00:10::1/127
 no shutdown
!
interface GigabitEthernet0/0/0/1
 ipv4 address 10.0.0.6 255.255.255.254
 ipv6 address fc00:10::6/127
 no shutdown
!
interface GigabitEthernet0/0/0/2
 ipv4 address 100.64.0.2 255.255.255.254
 ipv6 address fc00:100:64::2/127
 no shutdown
!
int lo 0
 ipv4 address 10.0.255.2 255.255.255.254
 ipv6 address fc00:10:0:255::2/128
 no shutdown
!
```

c-2-d1-pe3
```
interface Loopback0
 ipv4 address 10.0.255.3 255.255.255.254
 ipv6 address fc00:10:0:255::3/128
 no shutdown
!
interface GigabitEthernet0/0/0/0
 ipv4 address 10.0.0.8 255.255.255.254
 ipv6 address fc00:10::8/127
 no shutdown
!
interface GigabitEthernet0/0/0/1
 ipv4 address 10.0.0.10 255.255.255.254
 ipv6 address fc00:10::10/127
 no shutdown
!
interface GigabitEthernet0/0/0/2
 ipv4 address 10.0.0.5 255.255.255.254
 ipv6 address fc00:10::5/127
 no shutdown
!
interface GigabitEthernet0/0/0/3
 ipv4 address 10.1.0.1 255.255.255.0
 ipv6 address fc00:10:1::1/64
 no shutdown
!
```

c-2-d1-pe4
```
interface Loopback0
 ipv4 address 10.0.255.4 255.255.255.254
 ipv6 address fc00:10:0:255::4/128
 no shutdown
!
interface GigabitEthernet0/0/0/0
 ipv4 address 10.0.0.9 255.255.255.254
 ipv6 address fc00:10::9/127
 no shutdown
!
interface GigabitEthernet0/0/0/1
 ipv4 address 10.0.0.12 255.255.255.254
 ipv6 address fc00:10::12/127
 no shutdown
!
interface GigabitEthernet0/0/0/2
 ipv4 address 10.1.1.1 255.255.255.254
 ipv6 address fc00:10:1:1::1/64
 no shutdown
!
```

c-2-d1-p1
```
interface Loopback0
 ipv4 address 10.0.255.5 255.255.255.254
 ipv6 address fc00:10:0:255::5/128
 no shutdown
!
interface GigabitEthernet0/0/0/0
 ipv4 address 10.0.0.3 255.255.255.254
 ipv6 address fc00:10::3/127
 no shutdown
!
interface GigabitEthernet0/0/0/1
 ipv4 address 10.0.0.7 255.255.255.254
 ipv6 address fc00:10::7/127
 no shutdown
!
interface GigabitEthernet0/0/0/2
 ipv4 address 10.0.0.11 255.255.255.254
 ipv6 address fc00:10::11/127
 no shutdown
!
interface GigabitEthernet0/0/0/3
 ipv4 address 10.0.0.13 255.255.255.254
 ipv6 address fc00:10::13/127
 no shutdown
!
```

## CDP
All devices:
```
cdp
cdp log adjacency changes
cdp advertise v1
```

c-2-d1-pe1
```
interface GigabitEthernet0/0/0/0
 cdp
!
interface GigabitEthernet0/0/0/1
 cdp
!
interface GigabitEthernet0/0/0/2
 cdp
!
interface GigabitEthernet0/0/0/3
 cdp
!
```

c-2-d1-pe2
```
interface GigabitEthernet0/0/0/0
 cdp
!
interface GigabitEthernet0/0/0/1
 cdp
!
interface GigabitEthernet0/0/0/2
 cdp
!
```

c-2-d1-pe3
```
interface GigabitEthernet0/0/0/0
 cdp
!
interface GigabitEthernet0/0/0/1
 cdp
!
interface GigabitEthernet0/0/0/2
 cdp
!
```

c-2-d1-pe4
```
interface GigabitEthernet0/0/0/0
 cdp
!
interface GigabitEthernet0/0/0/1
 cdp
!
```

c-2-d1-pe1
```
interface GigabitEthernet0/0/0/0
 cdp
!
interface GigabitEthernet0/0/0/1
 cdp
!
interface GigabitEthernet0/0/0/2
 cdp
!
interface GigabitEthernet0/0/0/3
 cdp
!
```

c-2-d1-pe1
```
interface GigabitEthernet0/0/0/0
 cdp
!
interface GigabitEthernet0/0/0/1
 cdp
!
interface GigabitEthernet0/0/0/2
 cdp
!
interface GigabitEthernet0/0/0/3
 cdp
!
```

## IGP
### OSPFv2
c-2-d1-pe1
```
router ospf core-dc1
 log adjacency changes detail
 router-id 10.0.255.1
 auto-cost reference-bandwidth 100000
 area 0.0.0.0
  fast-reroute per-prefix ti-lfa enable
  interface Loopback0
   passive enable
  !
  interface GigabitEthernet0/0/0/0
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
  interface GigabitEthernet0/0/0/1
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
  interface GigabitEthernet0/0/0/3
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
 !
!
```

c-2-d1-pe2
```
router ospf core-dc1
 log adjacency changes detail
 router-id 10.0.255.2
 auto-cost reference-bandwidth 100000
 area 0.0.0.0
  fast-reroute per-prefix ti-lfa enable
  interface Loopback0
   passive enable
  !
  interface GigabitEthernet0/0/0/0
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
  interface GigabitEthernet0/0/0/1
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
 !
!
```

c-2-d1-pe3
```
router ospf core-dc1
 log adjacency changes detail
 router-id 10.0.255.3
 auto-cost reference-bandwidth 100000
 area 0.0.0.0
  fast-reroute per-prefix ti-lfa enable
  interface Loopback0
   passive enable
  !
  interface GigabitEthernet0/0/0/0
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
  interface GigabitEthernet0/0/0/1
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
  interface GigabitEthernet0/0/0/2
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
 !
 area 0.0.0.1
 !
 interface GigabitEthernet0/0/0/3
  passive
 !
!
```

c-2-d1-pe4
```
router ospf core-dc1
 log adjacency changes detail
 router-id 10.0.255.4
 auto-cost reference-bandwidth 100000
 area 0.0.0.0
  fast-reroute per-prefix ti-lfa enable
  interface Loopback0
   passive enable
  !
  interface GigabitEthernet0/0/0/0
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
  interface GigabitEthernet0/0/0/1
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
 !
 area 0.0.0.2
 !
 interface GigabitEthernet0/0/0/2
  passive
 !
!
```

c-2-d1-p1
```
router ospf core-dc1
 log adjacency changes detail
 router-id 10.0.255.5
 auto-cost reference-bandwidth 100000
 area 0.0.0.0
  fast-reroute per-prefix ti-lfa enable
  interface Loopback0
   passive enable
  !
  interface GigabitEthernet0/0/0/0
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
  interface GigabitEthernet0/0/0/1
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
  interface GigabitEthernet0/0/0/2
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
  interface GigabitEthernet0/0/0/3
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
 !
!
```
#### Authentication
all:
```
key chain KC_OSPF_AUTH
 key 1
  accept-lifetime 00:00:00 january 01 2022 infinite
  key-string DC1_AUTH_KEY
  send-lifetime 00:00:00 january 01 2022 infinite
  cryptographic-algorithm HMAC-SHA-256
 !
!
```

all:
```
router ospf core-dc1
 area 0.0.0.0
  authentication keychain KC_OSPF_AUTH
 !
!
```

### OSPFv3
c-2-d1-pe1
```
router ospfv3 core-dc1
 log adjacency changes detail
 router-id 10.0.255.1
 auto-cost reference-bandwidth 100000
 area 0.0.0.0
  fast-reroute per-prefix
  interface Loopback0
   passive enable
  !
  interface GigabitEthernet0/0/0/0
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
  interface GigabitEthernet0/0/0/1
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
  interface GigabitEthernet0/0/0/3
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
 !
!
```

c-2-d1-pe2
```
router ospfv3 core-dc1
 log adjacency changes detail
 router-id 10.0.255.2
 auto-cost reference-bandwidth 100000
 area 0.0.0.0
  fast-reroute per-prefix
  interface Loopback0
   passive enable
  !
  interface GigabitEthernet0/0/0/0
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
  interface GigabitEthernet0/0/0/1
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
 !
!
```

c-2-d1-pe3
```
router ospfv3 core-dc1
 log adjacency changes detail
 router-id 10.0.255.3
 auto-cost reference-bandwidth 100000
 area 0.0.0.0
  fast-reroute per-prefix
  interface Loopback0
   passive enable
  !
  interface GigabitEthernet0/0/0/0
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
  interface GigabitEthernet0/0/0/1
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
  interface GigabitEthernet0/0/0/2
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
 !
 area 0.0.0.1
 !
 interface GigabitEthernet0/0/0/3
  passive
 !
!
```

c-2-d1-pe4
```
router ospfv3 core-dc1
 log adjacency changes detail
 router-id 10.0.255.4
 auto-cost reference-bandwidth 100000
 area 0.0.0.0
  fast-reroute per-prefix
  interface Loopback0
   passive enable
  !
  interface GigabitEthernet0/0/0/0
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
  interface GigabitEthernet0/0/0/1
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
 !
 area 0.0.0.2
 !
 interface GigabitEthernet0/0/0/2
  passive
 !
!
```

c-2-d1-p1
```
router ospfv3 core-dc1
 log adjacency changes detail
 router-id 10.0.255.5
 auto-cost reference-bandwidth 100000
 area 0.0.0.0
  fast-reroute per-prefix
  interface Loopback0
   passive enable
  !
  interface GigabitEthernet0/0/0/0
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
  interface GigabitEthernet0/0/0/1
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
  interface GigabitEthernet0/0/0/2
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
  interface GigabitEthernet0/0/0/3
   network point-to-point
   flood-reduction enable
   dead-interval 10
   hello-interval 3
  !
 !
!
```


## BGP
### iBGP
### eBGP
## Multicasting
### Enable Multcasting for IPv4
All routers:
```
multicast-routing
 address-family ipv4
  interface all enable
 !
!
multicast-routing
!
```

### PIMv4
All routers:
```
ipv4 access-list ACL_RP_MCAST
 10 permit ipv4 any 239.0.0.0/8
!
router pim
 address-family ipv4
  no rp-address 10.0.255.5
  rp-address 10.0.255.5 ACL_RP_MCAST
  log neighbor changes
 !
!
```

### PIMv4 BIDIR
All routers:
```
ipv4 access-list ACL_IPV4_RP_MCAST_BIDIR
 10 permit ipv4 any 238.0.0.0/8
!
router pim
 address-family ipv4
  rp-address 10.0.255.5 ACL_IPV4_RP_MCAST_BIDIR bidir
 !
!
```

### Enable Multcasting for IPv4
All routers:
```
multicast-routing
 address-family ipv6
  interface all enable
 !
!
multicast-routing
!
```

### PIMv6
All routers:
```
ipv6 access-list ACL_IPV6_RP_MCAST
 10 permit ipv6 any ff00:6:5001::/48
!
router pim
 address-family ipv6
  rp-address fc00:10:0:255::5 ACL_IPV6_RP_MCAST
  log neighbor changes
 !
!
```
### Apply Multicast Border
```
no ipv4 access-list ACL_IPV4_NO_PIM
ipv4 access-list ACL_IPV4_MCAST_BOUNDARY
 10 permit ipv4 any 237.0.0.0/8
 9999 deny ipv4 any any
!
multicast-routing
 address-family ipv4
  interface GigabitEthernet0/0/0/2
   boundary ACL_IPV4_MCAST_BOUNDARY
  !
 !
!
multicast-routing
!
```

### BGP

Both PE
```
prefix-set PS_IPV4_AS_65001_ROUTES
  10.0.0.0/8 le 24
end-set
!
route-policy RP_PERMIT_ANY
  pass
end-policy
!
route-policy RP_IPV4_AS_65001_PERMIT
  if destination in PS_IPV4_AS_65001_ROUTES then
    done
  else
    drop
  endif
end-policy
!
router bgp 65001
 address-family ipv4 unicast
  redistribute ospf core-dc1 route-policy RP_IPV4_AS_65001_PERMIT
  aggregate-address 10.0.0.0/8 summary-only
 !
!
```

PE1
```
router bgp 65001
 bgp router-id 10.0.255.1
 bgp log neighbor changes detail
 address-family ipv4 unicast
  additional-paths receive
  additional-paths send
 !
 neighbor 10.0.255.2
  remote-as 65001
  advertisement-interval 0
  password clear SUPER_65001_PASS
  update-source Loopback0
  address-family ipv4 unicast
   next-hop-self
  !
 !
 neighbor 100.64.0.1
  remote-as 65002
  advertisement-interval 0
  password clear INTER_ASS
  address-family ipv4 unicast
    route-policy RP_IPV4_AS_65001_PERMIT out
    route-policy RP_PERMIT_ANY in
  !
 !
!
```

PE2
```
router bgp 65001
 bgp router-id 10.0.255.2
 bgp log neighbor changes detail
 address-family ipv4 unicast
  additional-paths receive
  additional-paths send
 !
 neighbor 10.0.255.1
  remote-as 65001
  advertisement-interval 0
  password clear SUPER_65001_PASS
  update-source Loopback0
  address-family ipv4 unicast
   next-hop-self
  !
 !
 neighbor 100.64.0.3
  remote-as 65002
  advertisement-interval 0
  password clear INTER_ASS
  address-family ipv4 unicast
    route-policy RP_IPV4_AS_65001_PERMIT out
    route-policy RP_PERMIT_ANY in
  !
 !
!
```

PE1 and PE2
```
router ospf core-dc1
 default-information originate always
!
```

### MSDP
on P1
```
router msdp
 connect-source Loopback0
 originator-id Loopback0
 default-peer 20.0.255.4
 !
 peer 20.0.255.4
  password clear IIIAAABBB
  description RP_AS65002 
  keepalive 5 15
 !
!
```

on P1
```
ipv4 access-list ACL_IPV4_INTERDOMAIN_MCAST
 10 permit ipv4 any 237.0.0.0/8
 9999 deny ipv4 any any
!
router msdp
 sa-filter in list ACL_IPV4_INTERDOMAIN_MCAST
 sa-filter out list ACL_IPV4_INTERDOMAIN_MCAST
!
```


```
ipv4 access-list ACL_IPV4_MCAST_BOUNDARY
 10 permit ipv4 any 237.0.0.0 0.255.255.255
 20 permit ipv4 any 224.0.0.0 0.255.255.255
 9999 deny ipv4 any any
```

# Configuration of DC2
## Interfaces
c-2-d2-pe1
```
interface Loopback0
 ipv4 address 20.0.255.1 255.255.255.254
 ipv6 address fc00:20:0:255::1/128
 no shutdown
!
interface GigabitEthernet0/0/0/0
 ipv4 address 20.0.0.0 255.255.255.254
 ipv6 address fc00:20::0/127
 no shutdown
!
interface GigabitEthernet0/0/0/1
 ipv4 address 20.0.0.2 255.255.255.254
 ipv6 address fc00:20::2/127
 no shutdown
!
interface GigabitEthernet0/0/0/2
 ipv4 address 100.64.0.1 255.255.255.254
 ipv6 address fc00:100:64::1/127
 no shutdown
!
interface GigabitEthernet0/0/0/3
 ipv4 address 100.64.0.5 255.255.255.254
 ipv6 address fc00:100:64::5/127
 no shutdown
!
```

c-2-d2-pe2
```
interface GigabitEthernet0/0/0/0
 ipv4 address 20.0.0.1 255.255.255.254
 ipv6 address fc00:20::1/127
 no shutdown
!
interface GigabitEthernet0/0/0/1
 ipv4 address 20.0.0.4 255.255.255.254
 ipv6 address fc00:20::4/127
 no shutdown
!
interface GigabitEthernet0/0/0/2
 ipv4 address 100.64.0.3 255.255.255.254
 ipv6 address fc00:100:64::3/127
 no shutdown
!
interface GigabitEthernet0/0/0/3
 ipv4 address 100.64.0.7 255.255.255.254
 ipv6 address fc00:100:64::7/127
 no shutdown
!
int lo 0
 ipv4 address 20.0.255.2 255.255.255.254
 ipv6 address fc00:20:0:255::2/128
 no shutdown
!
```

c-2-d2-pe3
```
interface Loopback0
 ipv4 address 20.0.255.3 255.255.255.254
 ipv6 address fc00:20:0:255::3/128
 no shutdown
!
interface GigabitEthernet0/0/0/0
 ipv4 address 20.0.0.6 255.255.255.254
 ipv6 address fc00:20::6/127
 no shutdown
!
interface GigabitEthernet0/0/0/1
 ipv4 address 20.1.0.1 255.255.255.0
 ipv6 address fc00:20:1::1/64
 no shutdown
!
```

c-2-d2-p1
```
interface Loopback0
 ipv4 address 20.0.255.4 255.255.255.254
 ipv6 address fc00:20:0:255::4/128
 no shutdown
!
interface GigabitEthernet0/0/0/0
 ipv4 address 20.0.0.3 255.255.255.254
 ipv6 address fc00:20::3/127
 no shutdown
!
interface GigabitEthernet0/0/0/1
 ipv4 address 20.0.0.5 255.255.255.254
 ipv6 address fc00:20::5/127
 no shutdown
!
interface GigabitEthernet0/0/0/2
 ipv4 address 20.0.0.7 255.255.255.254
 ipv6 address fc00:20::7/127
 no shutdown
!
```

## CDP
All devices:
```
cdp
cdp log adjacency changes
cdp advertise v1
```

c-2-d2-pe1
```
interface GigabitEthernet0/0/0/0
 cdp
!
interface GigabitEthernet0/0/0/1
 cdp
!
interface GigabitEthernet0/0/0/2
 cdp
!
interface GigabitEthernet0/0/0/3
 cdp
!
```

c-2-d2-pe2
```
interface GigabitEthernet0/0/0/0
 cdp
!
interface GigabitEthernet0/0/0/1
 cdp
!
interface GigabitEthernet0/0/0/2
 cdp
!
interface GigabitEthernet0/0/0/2
 cdp
!
```

c-2-d2-pe3
```
interface GigabitEthernet0/0/0/0
 cdp
!
interface GigabitEthernet0/0/0/1
 cdp
!
```

c-2-d2-p1
```
interface GigabitEthernet0/0/0/0
 cdp
!
interface GigabitEthernet0/0/0/1
 cdp
!
interface GigabitEthernet0/0/0/2
 cdp
!
```

## IGP
### ISIS
c-2-d2-pe1
```
router isis code-dc2
 is-type level-2-only
 net 49.0000.0200.0025.5001.00
 log adjacency changes
 address-family ipv4 unicast
  metric-style wide
  ispf
  spf-interval maximum-wait 1000 initial-wait 50 secondary-wait 50
 !
 address-family ipv6 unicast
  metric-style wide
  ispf
  spf-interval maximum-wait 1000 initial-wait 50 secondary-wait 50
 !
 interface Loopback0
  passive
  address-family ipv4 unicast
  !
  address-family ipv6 unicast
  !
 !
 interface GigabitEthernet0/0/0/0
  point-to-point
  address-family ipv4 unicast
  !
  address-family ipv6 unicast
  !
 !
 interface GigabitEthernet0/0/0/1
  point-to-point
  address-family ipv4 unicast
  !
  address-family ipv6 unicast
  !
 !
!         
```

c-2-d2-pe2
```
router isis code-dc2
 is-type level-2-only
 net 49.0000.0200.0025.5002.00
 log adjacency changes
 address-family ipv4 unicast
  metric-style wide
  ispf
  spf-interval maximum-wait 1000 initial-wait 50 secondary-wait 50
 !
 address-family ipv6 unicast
  metric-style wide
  ispf
  spf-interval maximum-wait 1000 initial-wait 50 secondary-wait 50
 !
 interface Loopback0
  passive
  address-family ipv4 unicast
  !
  address-family ipv6 unicast
  !
 !
 interface GigabitEthernet0/0/0/0
  point-to-point
  address-family ipv4 unicast
  !
  address-family ipv6 unicast
  !
 !
 interface GigabitEthernet0/0/0/1
  point-to-point
  address-family ipv4 unicast
  !
  address-family ipv6 unicast
  !
 !
!         
```

c-2-d2-pe3
```
router isis code-dc2
 is-type level-2-only
 net 49.0000.0200.0025.5003.00
 log adjacency changes
 address-family ipv4 unicast
  metric-style wide
  ispf
  spf-interval maximum-wait 1000 initial-wait 50 secondary-wait 50
 !
 address-family ipv6 unicast
  metric-style wide
  ispf
  spf-interval maximum-wait 1000 initial-wait 50 secondary-wait 50
 !
 interface Loopback0
  passive
  address-family ipv4 unicast
  !
  address-family ipv6 unicast
  !
 !
 interface GigabitEthernet0/0/0/0
  point-to-point
  address-family ipv4 unicast
  !
  address-family ipv6 unicast
  !
 !
 interface GigabitEthernet0/0/0/1
  passive
  address-family ipv4 unicast
  !
  address-family ipv6 unicast
  !
 !
!
```

c-2-d2-pe3
```
router isis code-dc2
 is-type level-2-only
 net 49.0000.0200.0025.5004.00
 log adjacency changes
 address-family ipv4 unicast
  metric-style wide
  ispf
  spf-interval maximum-wait 1000 initial-wait 50 secondary-wait 50
 !
 address-family ipv6 unicast
  metric-style wide
  ispf
  spf-interval maximum-wait 1000 initial-wait 50 secondary-wait 50
 !
 interface Loopback0
  passive
  address-family ipv4 unicast
  !
  address-family ipv6 unicast
  !
 !
 interface GigabitEthernet0/0/0/0
  point-to-point
  address-family ipv4 unicast
  !
  address-family ipv6 unicast
  !
 !
 interface GigabitEthernet0/0/0/1
  point-to-point
  address-family ipv4 unicast
  !
  address-family ipv6 unicast
  !
 !
 interface GigabitEthernet0/0/0/2
  point-to-point
  address-family ipv4 unicast
  !
  address-family ipv6 unicast
  !
 !
!
```

#### Authentication
all:
```
key chain KC_ISIS_AUTH
 key 1
  accept-lifetime 00:00:00 january 01 2022 infinite
  key-string DC1_AUTH_KEY
  send-lifetime 00:00:00 january 01 2022 infinite
  cryptographic-algorithm HMAC-SHA-256
 !
!
```

all:
```
router isis code-dc2
 lsp-password keychain KC_ISIS_AUTH
 interface GigabitEthernet0/0/0/0
  hello-password keychain KC_ISIS_AUTH
 !
 interface GigabitEthernet0/0/0/1
  hello-password keychain KC_ISIS_AUTH
 !
 interface GigabitEthernet0/0/0/2
  hello-password keychain KC_ISIS_AUTH
 !
!
```

## Multicasting
### Enable Multcasting for IPv4
All routers:
```
multicast-routing
 address-family ipv4
  interface all enable
 !
!
multicast-routing
!
```

### PIMv4
on pe1 and pe2:
```
ipv4 access-list ACL_IPV4_DENY_PIM_NEIGH
 10 deny ipv4 any any
!
router pim
 address-family ipv4
  log neighbor changes
  interface GigabitEthernet0/0/0/0
   no neighbor-filter
  !
  interface GigabitEthernet0/0/0/2
   bsr-border
   no neighbor-filter
  !
  interface GigabitEthernet0/0/0/3
   bsr-border
   no neighbor-filter
  !
 !
!
```

### PIMv4 - BSR
p1:
```
ipv4 access-list ACL_IPV4_RP_MCAST
 10 permit ipv4 any 237.0.0.0/8
 20 permit ipv4 any 239.0.0.0/8
!
router pim
 address-family ipv4
  log neighbor changes
  bsr candidate-bsr 20.0.255.4 hash-mask-len 30 priority 1
  bsr candidate-rp 20.0.255.4 group-list ACL_IPV4_RP_MCAST priority 192 interval 60
 !
!
```

### PIMv4 BIDIR
All routers:
```
ipv4 access-list ACL_IPV4_RP_MCAST_BIDIR
 10 permit ipv4 any 238.0.0.0/8
!
router pim
 address-family ipv4
  bsr candidate-rp 20.0.255.4 group-list ACL_IPV4_RP_MCAST_BIDIR priority 192 interval 60 bidir
 !
!
```

### Apply Multicast Border
```
ipv4 access-list ACL_IPV4_MCAST_BOUNDARY
 10 permit ipv4 any 237.0.0.0/8
 9999 deny ipv4 any any
!
multicast-routing
 address-family ipv4
  interface GigabitEthernet0/0/0/2
   boundary ACL_IPV4_MCAST_BOUNDARY
  !
  interface GigabitEthernet0/0/0/3
   boundary ACL_IPV4_MCAST_BOUNDARY
  !
 !
!
multicast-routing
!
```

###
PE routers
```
ipv4 access-list ACL_IPV4_NO_PIM
 10 deny pim any any
 9999 permit ipv4 any any
!
interface GigabitEthernet0/0/0/2
 ipv4 access-group ACL_IPV4_NO_PIM ingress
 ipv4 access-group ACL_IPV4_NO_PIM egress
!
interface GigabitEthernet0/0/0/3
 ipv4 access-group ACL_IPV4_NO_PIM ingress
 ipv4 access-group ACL_IPV4_NO_PIM egress
!
```


## BGP
### iBGP
P1
```
router bgp 65002
 bgp router-id 20.0.255.4
 bgp log neighbor changes detail
 address-family ipv4 unicast
  additional-paths receive
  additional-paths send
 !
 af-group AF_IPV4_UNI_65002_RR_CLIENTS address-family ipv4 unicast
  route-reflector-client
 !
 session-group SG_65000_RR_CLIENTS
  remote-as 65002
  advertisement-interval 0
  password clear SUPER_65002_PASS
  update-source Loopback0
 !
 neighbor 20.0.255.1
  use session-group SG_65000_RR_CLIENTS
  address-family ipv4 unicast
   use af-group AF_IPV4_UNI_65002_RR_CLIENTS
  !
 !
 neighbor 20.0.255.2
  use session-group SG_65000_RR_CLIENTS
  address-family ipv4 unicast
   use af-group AF_IPV4_UNI_65002_RR_CLIENTS
  !
 !
 neighbor 20.0.255.3
  use session-group SG_65000_RR_CLIENTS
  address-family ipv4 unicast
   use af-group AF_IPV4_UNI_65002_RR_CLIENTS
  !
 !
!
```

PE1
```
router bgp 65002
 bgp router-id 20.0.255.1
 bgp log neighbor changes detail
 address-family ipv4 unicast
  additional-paths receive
  additional-paths send
 !
 neighbor 20.0.255.2
  remote-as 65002
  advertisement-interval 0
  password clear SUPER_65002_PASS
  update-source Loopback0
  address-family ipv4 unicast
   next-hop-self
  !
 !
 neighbor 100.64.0.0
  remote-as 65001
  advertisement-interval 0
  password clear INTER_ASS
  address-family ipv4 unicast
    route-policy RP_IPV4_AS_65000_PERMIT out
    route-policy RP_PERMIT_ANY in
  !
 !
!
```

PE2
```
router bgp 65002
 bgp router-id 20.0.255.2
 bgp log neighbor changes detail
 address-family ipv4 unicast
  additional-paths receive
  additional-paths send
 !
 neighbor 20.0.255.1
  remote-as 65002
  advertisement-interval 0
  password clear SUPER_65002_PASS
  update-source Loopback0
  address-family ipv4 unicast
   next-hop-self
  !
 !
 neighbor 100.64.0.2
  remote-as 65001
  advertisement-interval 0
  password clear INTER_ASS
  address-family ipv4 unicast
    route-policy RP_IPV4_AS_65000_PERMIT out
    route-policy RP_PERMIT_ANY in
  !
 !
!
```

Both PE
```
prefix-set PS_IPV4_AS_65002_ROUTES
  20.0.0.0/8 le 24
end-set
!
route-policy RP_PERMIT_ANY
  pass
end-policy
!
route-policy RP_IPV4_AS_65000_PERMIT
  if destination in PS_IPV4_AS_65002_ROUTES then
    done
  else
    drop
  endif
end-policy
!
router bgp 65002
 address-family ipv4 unicast
  redistribute isis code-dc2 route-policy RP_IPV4_AS_65000_PERMIT
  aggregate-address 20.0.0.0/8 summary-only
 !
!
```

Both PE
```
route-policy RP_BGP_TO_ISIS
  if destination in PS_IPV4_AS_65002_ROUTES then
    drop
  else
    done
  endif
end-policy
!
router isis code-dc2
 address-family ipv4 unicast
  redistribute bgp 65002 level-2 route-policy RP_BGP_TO_ISIS
 !
!
```

### MSDP
on P1
```
router msdp
 connect-source Loopback0
 originator-id Loopback0
 default-peer 10.0.255.5
 !
 peer 10.0.255.5
  password clear IIIAAABBB
  description RP_AS65001
  keepalive 5 15
 !
!
```

on P1
```
ipv4 access-list ACL_IPV4_INTERDOMAIN_MCAST
 10 permit ipv4 any 237.0.0.0/8
 9999 deny ipv4 any any
!
router msdp
 sa-filter in list ACL_IPV4_INTERDOMAIN_MCAST
 sa-filter out list ACL_IPV4_INTERDOMAIN_MCAST
!
```