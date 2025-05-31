# Dynamic ARP Inspection
**Author:** Millioud NetLab  
**Date:** 30-05-2025 

## Objectives

1. Configure R1 as a DHCP server.
    Exclude 192.168.1.1 - 192.168.1.9 from the pool
    Default gateway: R1

2. Configure DHCP snooping on SW1 and SW2.

3. Configure DAI on SW1 and SW2.
  -Enable all additional validation checks
  -Trust ports connected to a router or switch

## Topology

<img width="491" alt="Captura de Pantalla 2025-05-30 a la(s) 20 54 41" src="https://github.com/user-attachments/assets/682cb377-1fd4-4ba0-b767-29d8a65c3f8e" />


## Devices Used

| Device         | Model        | Quantity |
|----------------|--------------|----------|
| Router         | 2911         | 1        |
|  Switch | 2960         | 2       |
| PC             | PC-PT      | 3        |

## IP Addressing Table

| Device | Interface | VLAN | IP Address     | Subnet Mask       |
|--------|-----------|------|----------------|-------------------|
| R1     | G0/0      | 1    | 192.168.1.1    | 255.255.255.0     |

## Configuration Steps

### R1(.1)

R1>enable

R1#conf t

R1(config)#ip dhcp excluded-address 192.168.1.1 192.168.1.9

R1(config)#ip dhcp pool POOL1

R1(dhcp-config)#network 192.168.1.0 255.255.255.0

R1(dhcp-config)#default-router 192.168.1.1

### SW1 (.2)

SW1(config)#ip dhcp snooping 

SW1(config)#ip dhcp snooping vlan 1

SW1(config)#no ip dhcp snooping information option

SW1(config)#int range g0/1-2

SW1(config-if-range)#ip dhcp snooping trust

### SW2 (.2)

SW2(config)#ip dhcp snooping

SW2(config)#ip dhcp snooping vlan 1

SW2(config)#no ip dhcp snooping information option

SW2(config)#int g0/1

SW2(config-if)#ip dhcp snooping trust

### SW2 (.3)

SW2(config-if)#exit

SW2(config)#ip arp inspection vlan 1

SW2(config)#ip arp inspection validate src-mac ip dst-mac

SW2(config)#int g0/1

SW2(config-if)#ip arp inspection trust













