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
    lo:
      addresses:
        - 127.0.0.1/8
        - ::1/128
        - 10.1.0.254/32
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
    lo:
      addresses:
      - 127.0.0.1/8
      - ::1/128
      - 10.1.0.254/32
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
        ip address 10.0.0.1/31
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
        ip address 10.0.0.0/31
        no shutdown
    !
    interface Ethernet 2
        ip address 10.0.0.2/31
        no shutdown
    !
    interface Ethernet 3
        ip address 10.0.0.4/31
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
        ip address 10.0.0.3/31
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
        ip address 10.0.0.5/31
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
    router-id 10.0.255.100
    bgp log-neighbor-changes
    !
    neighbor PG_SPINE password DC_PASS
    neighbor PG_SPINE send-community extended
    !
    neighbor 10.0.0.0 peer group PG_SPINE
    neighbor 10.0.0.0 remote-as 65002
    !
    address-family ipv4
        neighbor PG_SPINE activate 
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
    router-id 10.0.255.101
    bgp log-neighbor-changes
    !
    neighbor PG_LEAF password DC_PASS
    neighbor PG_LEAF send-community extended
    !
    neighbor 10.0.0.1 peer group PG_LEAF
    neighbor 10.0.0.1 remote-as 65001
    neighbor 10.0.0.3 peer group PG_LEAF
    neighbor 10.0.0.3 remote-as 65003
    neighbor 10.0.0.5 peer group PG_LEAF
    neighbor 10.0.0.5 remote-as 65004
    !
    address-family ipv4
        neighbor PG_LEAF activate 
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
    router-id 10.0.255.102
    bgp log-neighbor-changes
    !
    neighbor PG_SPINE password DC_PASS
    neighbor PG_SPINE send-community extended
    !
    neighbor 10.0.0.2 peer group PG_SPINE
    neighbor 10.0.0.2 remote-as 65002
    !
    address-family ipv4
        neighbor PG_SPINE activate 
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
    router-id 10.0.255.103
    bgp log-neighbor-changes
    !
    neighbor PG_SPINE password DC_PASS
    neighbor PG_SPINE send-community extended
    !
    neighbor 10.0.0.4 peer group PG_SPINE
    neighbor 10.0.0.4 remote-as 65002
    !
    address-family ipv4
        neighbor PG_SPINE activate 
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
            route-target export evpn 65000:1
            redistribute connected route-map RP_IPV4_CUSTOMER_PREFIXES
        !
    !
!
```

## Disable checksum offload on all Linux hosts
```
$ sudo ethtool -K ens19 tx off rx off
$ sudo ethtool -K eth1 tx off rx off
```

**Important**: That shall be done after each reboot

## Load Balancers
### Install Docker
c-3-lb1, c-3-lb2:
```
sudo apt-get update -y

sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release -y

sudo mkdir -p /etc/apt/keyrings

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update -y

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y
```

### Get Dockerized FRR
c-3-lb1, c-3-lb2:
```
mkdir frr && cd frr

tee docker-compose.yaml << __EOF__
---
version: "3.9"
services:
    frr:
        image: frrouting/frr
        restart: always
        network_mode: host
        volumes:
          - frr_config:/etc/frr
        privileged: true

volumes:
  frr_config:
    driver: local
...
__EOF__

sudo docker compose up -d
```

### Enable BGP daemon
c-3-lb1, c-3-lb2:
```
sudo sed -i 's/bgpd=no/bgpd=yes/' /var/lib/docker/volumes/frr_frr_config/_data/daemons

sudo docker compose restart
```


### Enable BFD daemon
c-3-lb1, c-3-lb2:
```
sudo sed -i 's/bfdd=no/bfdd=yes/' /var/lib/docker/volumes/frr_frr_config/_data/daemons

sudo docker compose restart
```

### Configure BGP between LB and DC Fabric
#### LB side
**c-3-lb1 is active LB, c-3-lb2 is a passive one.**

c-3-lb1:
```
sudo docker container exec -it  frr-frr-1 vtysh
!
! Config is done inside FRR application inside the container
!
configure terminal
    ip prefix-list PL_IPV4_VIP seq 10 permit 10.1.0.254/32
    !
    route-map RP_IPV4_ADVERTISE_VIP permit 10
        match ip address prefix-list PL_IPV4_VIP
    !
    route-map RP_IPV4_ADVERTISE_VIP deny 9999
    !
    ip prefix-list PL_IPV4_DEF_ROUTE seq 10 permit 0.0.0.0/0
    !
    route-map RP_IPV4_RECIEVE_DEF permit 10
        match ip address prefix-list PL_IPV4_DEF_ROUTE
    !
    route-map RP_IPV4_RECIEVE_DEF deny 9999
    !
    router bgp 65100
        bgp router-id 10.1.0.1
        bgp log-neighbor-changes
        !
        neighbor 10.1.0.0 remote-as 65003
        neighbor 10.1.0.0 bfd
        !
        address-family ipv4 unicast
            network 10.1.0.254/32
            !
            neighbor 10.1.0.0 activate
            neighbor 10.1.0.0 route-map RP_IPV4_ADVERTISE_VIP out
            neighbor 10.1.0.0 route-map RP_IPV4_RECIEVE_DEF in
        !
!
```

c-3-lb2:
```
sudo docker container exec -it  frr-frr-1 vtysh
!
! Config is done inside FRR application inside the container
!
configure terminal
    ip prefix-list PL_IPV4_VIP seq 10 permit 10.1.0.254/32
    !
    route-map RP_IPV4_ADVERTISE_VIP permit 10
        match ip address prefix-list PL_IPV4_VIP
        set as-path prepend 65100 65100 65100 65100 65100
    !
    route-map RP_IPV4_ADVERTISE_VIP deny 9999
    !
    ip prefix-list PL_IPV4_DEF_ROUTE seq 10 permit 0.0.0.0/0
    !
    route-map RP_IPV4_RECIEVE_DEF permit 10
        match ip address prefix-list PL_IPV4_DEF_ROUTE
    !
    route-map RP_IPV4_RECIEVE_DEF deny 9999
    !
    router bgp 65100
        bgp router-id 10.1.0.3
        bgp log-neighbor-changes
        !
        neighbor 10.1.0.2 remote-as 65004
        neighbor 10.1.0.2 bfd
        !
        address-family ipv4 unicast
            network 10.1.0.254/32
            !
            neighbor 10.1.0.2 activate
            neighbor 10.1.0.2 route-map RP_IPV4_ADVERTISE_VIP out
            neighbor 10.1.0.2 route-map RP_IPV4_RECIEVE_DEF in
        !
!
```

#### DC Fabric fabric
c-3-l1:
```
enable
!
configure terminal
    router bgp 65003
        vrf CUST_1
            neighbor 10.1.0.1 remote-as 65100
            !
            address-family ipv4
                neighbor 10.1.0.1 activate
                neighbor 10.1.0.1 default-originate always
            !
        !
    !
!
```

c-3-l2:
```
enable
!
configure terminal
    router bgp 65004
        vrf CUST_1
            neighbor 10.1.0.3 remote-as 65100
            !
            address-family ipv4
                neighbor 10.1.0.3 activate
                neighbor 10.1.0.3 default-originate always
            !
        !
    !
!
```

### Get Dockerized HAProxy
c-3-lb1, c-3-lb2:
```
mkdir haproxy && cd haproxy

tee docker-compose.yaml << __EOF__
---
version: "3.9"
services:
    haproxy:
        image: haproxy
        restart: always
        network_mode: host
        volumes:
          - ./config/haproxy.cfg:/usr/local/etc/haproxy/haproxy.cfg:ro
          - ./ssl:/etc/ssl
...
__EOF__
```

### Create self-signed certifiacte
c-3-lb1, c-3-lb2:
```
mkdir ssl
openssl req -x509 -newkey rsa:4096 -keyout ssl/key.pem -out ssl/cert.pem -sha256 -days 365 -nodes -subj '/CN=test-website.lab.karneliuk.com'
cat ssl/cert.pem  ssl/key.pem > ssl/joined.pem
```

### Configure LB
c-3-lb1, c-3-lb2:
```
mkdir config

tee config/haproxy.cfg << __EOF__
global
    maxconn 4096
    log /dev/log local0

defaults
    timeout connect 5s
    timeout client 30s
    timeout server 30s
    retries 3
    log global
    mode http
    option httplog
    maxconn 3000

frontend webservers_vip
    bind 10.1.0.254:8080
    bind 10.1.0.254:8443 ssl crt /etc/ssl/joined.pem
    http-request redirect location https://10.1.0.254:8443 unless { ssl_fc }
    default_backend webservers_origin

backend webservers_origin
    balance roundrobin
    server c-3-o1 10.1.1.1:8080 check
    server c-3-o2 10.1.1.3:8080 check
__EOF__
```

### Launch LB
c-3-lb1, c-3-lb2:
```
sudo docker compose up -d
```

### Validation of LB
c-3-lb1, c-3-lb2:
```
sudo docker container logs haproxy-haproxy-1
[NOTICE]   (1) : New worker (8) forked
[NOTICE]   (1) : Loading success.
[WARNING]  (8) : Server webservers_origin/c-3-o1 is DOWN, reason: Layer4 timeout, check duration: 2002ms. 1 active and 0 backup servers left. 0 sessions active, 0 requeued, 0 remaining in queue.
[ALERT]    (8) : sendmsg()/writev() failed in logger #1: No such file or directory (errno=2)
[WARNING]  (8) : Server webservers_origin/c-3-o2 is DOWN, reason: Layer4 timeout, check duration: 2002ms. 0 active and 0 backup servers left. 0 sessions active, 0 requeued, 0 remaining in queue.
[ALERT]    (8) : backend 'webservers_origin' has no server available!
```

## Origin Webserver
### Install Docker
c-3-o1, c-3-o2:
```
sudo apt-get update -y

sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release -y

sudo mkdir -p /etc/apt/keyrings

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update -y

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y
```

### Get Dockerized nginx
c-3-o1, c-3-o2:
```
mkdir nginx && cd nginx

tee docker-compose.yaml << __EOF__
---
version: "3.9"
services:
    web:
        image: nginx
        restart: always
        ports:
          - 8080:80
        volumes:
          - ./config:/etc/nginx/conf.d
          - ./content:/tmp/content
...
__EOF__

sudo docker compose up -d
```

### Create custom web service
c-3-o1, c-3-o2:
```
mkdir config content

tee config/karneliuk_service.conf << __EOF__
server {
    listen       80;
    listen  [::]:80;
    server_name  localhost;

    location / {
        root   /tmp/content;
        index  index.html index.htm;
    }
}
__EOF__

tee content/index.html << __EOF__
<html>
<head>
<title>Best Automation Trainings at Karneliuk.com</title>
</head>
<body>
<h1>Test worker</h1>
<p>Enroll to <a href="http://training.karneliuk.com/">Network Automation Trainings</a>.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
__EOF__
```

### Launch NGINX

### Permit ip forwarding on origin servers
c-3-o1, c-3-o2:
```
sudo sed -i 's/#net.ipv4.ip_forward=1/net.ipv4.ip_forward=1/' /etc/sysctl.conf
sudo sysctl -p
```

### Validation of origin
c-3-o1:
```
sudo docker container ls
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS                                   NAMES
db5e6c846aa4   nginx     "/docker-entrypoint.…"   22 minutes ago   Up 22 minutes   0.0.0.0:8080->80/tcp, :::8080->80/tcp   nginx-web-1
```

c-3-o1:
```
sudo docker container logs nginx-web-1
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2022/08/21 13:00:47 [notice] 1#1: using the "epoll" event method
2022/08/21 13:00:47 [notice] 1#1: nginx/1.23.1
2022/08/21 13:00:47 [notice] 1#1: built by gcc 10.2.1 20210110 (Debian 10.2.1-6) 
2022/08/21 13:00:47 [notice] 1#1: OS: Linux 5.15.0-46-generic
2022/08/21 13:00:47 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2022/08/21 13:00:47 [notice] 1#1: start worker processes
2022/08/21 13:00:47 [notice] 1#1: start worker process 31
2022/08/21 13:00:47 [notice] 1#1: start worker process 32
10.1.1.1 - - [21/Aug/2022:13:11:32 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/7.81.0" "-"
10.1.1.1 - - [21/Aug/2022:13:12:07 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/7.81.0" "-"
10.1.1.1 - - [21/Aug/2022:13:15:08 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/7.81.0" "-"
10.1.0.1 - - [21/Aug/2022:13:18:00 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/7.81.0" "-"
10.1.0.1 - - [21/Aug/2022:13:18:59 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/7.68.0" "-"
10.1.0.1 - - [21/Aug/2022:13:19:01 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/7.68.0" "-"
10.1.0.1 - - [21/Aug/2022:13:20:20 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/7.68.0" "-"
10.1.0.1 - - [21/Aug/2022:13:20:42 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/7.81.0" "-"
10.1.0.1 - - [21/Aug/2022:13:20:44 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/7.68.0" "-"
10.1.0.1 - - [21/Aug/2022:13:22:30 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/7.68.0" "-"
10.1.0.1 - - [21/Aug/2022:13:22:31 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/7.68.0" "-"
10.1.0.1 - - [21/Aug/2022:13:22:32 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/7.68.0" "-"
10.1.0.1 - - [21/Aug/2022:13:22:32 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/7.68.0" "-"
10.1.0.1 - - [21/Aug/2022:13:22:33 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/7.68.0" "-"
10.1.0.1 - - [21/Aug/2022:13:22:33 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/7.68.0" "-"
```

c-3-o2:
```
sudo docker container ls
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS         PORTS                                   NAMES
8d369b38fd23   nginx     "/docker-entrypoint.…"   3 minutes ago   Up 3 minutes   0.0.0.0:8080->80/tcp, :::8080->80/tcp   nginx-web-1
```

c-3-o2:
```
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2022/08/21 13:21:20 [notice] 1#1: using the "epoll" event method
2022/08/21 13:21:20 [notice] 1#1: nginx/1.23.1
2022/08/21 13:21:20 [notice] 1#1: built by gcc 10.2.1 20210110 (Debian 10.2.1-6) 
2022/08/21 13:21:20 [notice] 1#1: OS: Linux 5.15.0-46-generic
2022/08/21 13:21:20 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2022/08/21 13:21:20 [notice] 1#1: start worker processes
2022/08/21 13:21:20 [notice] 1#1: start worker process 30
2022/08/21 13:21:20 [notice] 1#1: start worker process 31
10.1.0.1 - - [21/Aug/2022:13:22:30 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/7.68.0" "-"
10.1.0.1 - - [21/Aug/2022:13:22:31 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/7.68.0" "-"
10.1.0.1 - - [21/Aug/2022:13:22:32 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/7.68.0" "-"
10.1.0.1 - - [21/Aug/2022:13:22:32 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/7.68.0" "-"
10.1.0.1 - - [21/Aug/2022:13:22:33 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/7.68.0" "-"
10.1.0.1 - - [21/Aug/2022:13:22:33 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/7.68.0" "-"
```

### Validation of LB
c-3-lb1, c-3-lb2:
```
sudo docker container logs haproxy-haproxy-1
!
! Output is truncated for brevity
!
[WARNING]  (8) : Server webservers_origin/c-3-o1 is UP, reason: Layer4 check passed, check duration: 13ms. 1 active and 0 backup servers online. 0 sessions requeued, 0 total in queue.
[WARNING]  (8) : Server webservers_origin/c-3-o2 is UP, reason: Layer4 check passed, check duration: 14ms. 2 active and 0 backup servers online. 0 sessions requeued, 0 total in queue.

```

## End-to-end test
c-3-e1:
```
# curl -X GET http://10.1.0.254:8080
<html>
<head>
<title>Best Automation Trainings at Karneliuk.com</title>
</head>
<body>
<h1>Test worker</h1>
<p>Enroll to <a href="http://training.karneliuk.com/">Network Automation Trainings</a>.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```