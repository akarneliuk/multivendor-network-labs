# Cisco Nexus Routing Unicast and Multicast Lab
This lab aims to master routing (unicast and multicast) technologies in Cisco Nexus.

## Covered Topics
- Unicast routing
  - Multi-area OSPF
  - Prefix aggregation on area borders
  - Authentication with key chain
- Multicast routing
  - PIMv4
  - IGMPv3
  - PIM neighbors authentication
  - Anycast RP for ASM
  - Phantom RP for BiDir ASM
  - SSM

## Success Criteria
- All hosts can reach each other over IP relying unicast routing
- All hosts can subscribe to multiacst groups and reach each other:
  - 238.0.0.0/23 for BiDir
  - 239.0.0.0/8 for ASM
  - 232.0.0.0/8 any source for SSM

## Main Considerations
- c-1-s1 and c-1-s2 shall form the Anycast RP with PIM
- c-1-s1 and c-1-s2 shall be deploying Phantom RP