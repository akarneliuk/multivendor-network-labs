# Cisco Nexus EVPN Lab
This lab aims to master EVPN VXLAN knowledge for intra-DC traffic as long as the External VRF connectivity

## Covered Topics
- Unicast routing
  - Single-area OSPF
  - Authentication with key chain
  - iBGP for L2VPN EVPN within the DC
  - eBGP for IPV4 UNICAST and IPV6 UNICAST for integration with DCI
- Multicast routing
  - PIMv4
  - Anycast RP for ASM for VNI BUM traffic
- EVPN VXLAN
  - L2VNI (multiple per VRF)
  - L3VNI (one per VRF)
  - Anycast VTEP for leafs
- L2
  - VPC domanis for leaf pairs
  - VPC to multihomed servers
  - VPC orphan ports for single-homed servers
- Optional topics:
  - Route leaking between VRFs

## Success Criteria
- All hosts can reach each other over IP relying unicast routing within VRF (between VRFs if optional task is done)
- hosts with VRF having External VRF connectivity can reach host over DCI
- All L2VNIs mapped to individual multicast groups
- spines act as Anycast RP with PIM
- spines act as BGP RR for iBGP routes
- VPC domains between leafs and borders are properly formed
- VPCs to servers are properly formed and forward traffic correctly

## Main Considerations
- c-1-s1 and c-1-s2 shall form the Anycast RP with PIM
- c-1-s1 and c-1-s2 shall be deploying Phantom RP