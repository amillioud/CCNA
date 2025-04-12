# DHCP Packet Tracer Lab

**Author:** Millioud NetLab  
**Date:** 06-04-2025 

## Objectives

1. Configure the following DHCP pools on R2:
POOL1: 192.168.1.0/24 (reserve .1 to .10)
     DNS 8.8.8.8
     Domain: jeremysitlab.com
     Default Gateway: R1
POOL2: 192.168.2.0/24 (reserve .1 to .10)
     DNS 8.8.8.8
     Domain: jeremysitlab.com
     Default Gateway: R2
POOL3: 203.0.113.0/30 (reserve .1)

2. Configure R1's G0/0 interface as a DHCP client.

3. Configure R1 as a DHCP relay agent for the 192.168.1.0/24 subnet.
 
4. Use the CLI of PC1 and PC2 to make them request an IP address 
    from their DHCP server.

## Topology

<img width="591" alt="Captura de Pantalla 2025-04-06 a la(s) 13 16 15" src="https://github.com/user-attachments/assets/3244058d-e763-41a8-949d-7f125bfc96de" />

## Devices Used


| Device         | Model        | Quantity |
|----------------|--------------|----------|
| Router         | 2911         | 2        |
| Switch         | 2960         | 2        |
| PC         | PC-PT         | 2        |

## IP Addressing Table

| Device | Interface | VLAN | IP Address     | Subnet Mask       |
|--------|-----------|------|----------------|-------------------|
| PC2    | Fa0/0     | na   | na   | 255.255.255.0     |
| PC1    | Fa0/0     | na   | na   | 255.255.255.0     |
| R1    | g0/0     | na   | 203.0.113.1   | 255.255.255.252     |
| R1    | g0/1     | na   | 192.168.2.1   | 255.255.255.0     |
| R1    | g0/0     | na   | 203.0.113.2   | 255.255.255.252     |
| R1    | g0/1     | na   | 192.168.1.1   | 255.255.255.0     |

## Configuration Steps

### Router 2 (1.)

R2>enable

R2#show ip dhcp binding

R2(config)#ip dhcp excluded-address 192.168.1.1 192.168.1.10

R2(config)#ip dhcp pool POOL1

R2(dhcp-config)#network 192.168.1.0 255.255.255.0

R2(dhcp-config)#dns-server 8.8.8.8

R2(dhcp-config)#domain-name jeremysitlab.com

R2(dhcp-config)#default-router 192.168.1.1

R2(config)#ip dhcp excluded-address 192.168.2.1 192.168.2.10

R2(dhcp-config)#ip dhcp pool POOL2

R2(dhcp-config)#network 192.168.2.0 255.255.255.0

R2(dhcp-config)#dns-server 8.8.8.8

R2(dhcp-config)#domain-name jeremysitlab.com

R2(dhcp-config)#default-router 192.168.2.1

R2(config)#ip dhcp excluded-address 203.0.113.1

R2(dhcp-config)#ip dhcp pool POOL3

R2(dhcp-config)#network 203.0.113.0 255.255.255.252

### Router 1 (2.)

R1>enable

R1#conf t

R1(config)#int g0/0

R1(config-if)#ip address dhcp

R1(config-if)#no shut

### Router 1 (3.)

R1(config-if)#int g0/1

R1(config-if)#ip helper-address 192.168.1.1

### PC 1 / PC 2 (4.)

C:\>ipconfig /renew
