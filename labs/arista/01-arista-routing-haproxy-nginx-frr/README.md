# Open Source Load Balacning lab
This lab aims to master skills in the load balancing with the following products involved:
- FRR for routing on load balancer
- HAProxy for load balancing on load balancer
- NGINX as origin web server
- Arista as DC fabric platform

## Covered Topics
- Unicast routing
  - eBGP for underlay routing for DC fabric
  - eBGP for overlay EVPN routing
  - L3 VNI and VRF for a tenant traffic
  - EVPN/VXLAN for tenant traffic
  - all configurations are done on Arista EOS platform
- Infrastructure
  - Ubuntu 22.04 (Jammy Jellyfish) for load balancers and origin web servers
  - Docker for containerization
- Load balancing
  - HTTP mode
  - One-arm with session termination
  - HAProxy 2.64
  - Routing at load balancers are implemted with FRRouting levearging BGP peering with DC fabric within tenant VRF
  - Active/passive is acheived via route policy with AS_PATH prepending
- Origin web-server
  - NGINX with a statc html webpage

## Success Criteria
- From c-3-e1 it is possible to query VIP at LB and get response.
```
root@c-3-e1:~# curl -X GET http://10.1.0.254:8080
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
- The service shall be further provided even if one of LBs and/or one of origin servers are down.
- You shall be able to see the request in logs at web origin server:
```
aaa@c-3-o1:~/nginx$ sudo docker container logs nginx-web-1
!
! OUTPUT IS TRUNCATED FOR BREVITY
!
10.1.0.1 - - [21/Aug/2022:13:45:09 +0000] "GET / HTTP/1.1" 200 447 "-" "curl/7.68.0" "-"
```

