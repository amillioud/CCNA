#  SSH Packet Tracer Lab

**Author:** Millioud NetLab  

**Date:** 11-04-2025  

##  Objectives

1.Connect Laptop1 to SW2's console port to perform the following configurations:

Host name: SW2

Enable secret: ccna

Username/PW: jeremy/ccna

VLAN1 SVI: 192.168.2.253/24

Default gateway: R2

2. Configure the following console line security settings on SW2:
   
Authentication: Local user

Exec timeout: 5 minutes

3. Configure SW2 for remote access via SSH:
   
Domain name: jeremysitlab.com

RSA key size: 2048 bits

Authentication: Local user

Exec timeout: 5 minutes

Protocols: SSH only

+Limit access to PC1 ONLY

## Topology

<img width="887" alt="Captura de Pantalla 2025-04-11 a la(s) 17 13 54" src="https://github.com/user-attachments/assets/279e1d6c-e639-48ea-a6e8-bfc6e3040087" />


## Devices Used

| Device         | Model        | Quantity |
|----------------|--------------|----------|
| Laptop         | Generic         | 1        |
| Switch  | 2960         | 2       |
| PC             | Generic      | 1        |
| Router | 2911      | 1        |

## IP Addressing table

| Device | Interface | VLAN | IP Address     | Subnet Mask       |
|--------|-----------|------|----------------|-------------------|
| Laptop    | RS 232     | na   | na | na     |
| Switch 2    | Console port    | na   | na  |na |
| Switch 2    | Console port    | 1   | 192.168.2.253  | 255.255.255.0 |
| Router 2   | G0/1   | 1   | 192.168.2.254  | 255.255.255.0 |
| Router 2   | G0/0    | 1   | 10.0.0.2  | 255.255.255.252 |
| Router 1   | G0/0    | 1   | 10.0.0.1  | 255.255.255.252 |
| Router 1   | G0/1    | 1   | 192.168.1.254 | 255.255.255.0 |
| PC 1   | F0/1    | 1   | 192.168.1.1 | 255.255.255.0 |


## Configuration Steps

### From Laptop 1 terminal 

Switch>enable

Switch#conf t

Switch(config)#hostname SW1

SW1(config)#enable secret ccna

SW1(config)#username jeremy secret ccna

SW1(config)#interface vlan 1

SW1(config-if)#ip address 192.168.2.253 255.255.255.0

SW1(config-if)#no shutdown

SW1(config-if)#exit

SW1(config)#ip default-gateway 192.168.2.254

SW1(config)#line 0

SW1(config-line)#login local

SW1(config-line)#exec-timeout 5 0

SW1(config)#access-list 1 permit host 192.168.1.1

SW1(config)#line vty 0 15

SW1(config-line)#login local

SW1(config-line)#exec-timeout 5 0

SW1(config-line)#transport input ssh

SW1(config-line)#access-class 1 in












