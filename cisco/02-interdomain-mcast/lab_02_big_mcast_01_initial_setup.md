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