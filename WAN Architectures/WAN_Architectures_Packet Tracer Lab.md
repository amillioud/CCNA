# WAN Architectures
**Author:** Millioud NetLab  
**Date:** 1-06-2025

## Objectives

1. Configure a GRE tunnel to connect R1 and R2.

2. Configure OSPF on the tunnel interfaces of R1 and R2,
   
    to allow PC1 and PC2 to communicate.

## Topology

<img width="702" alt="Captura de Pantalla 2025-06-11 a la(s) 9 57 37" src="https://github.com/user-attachments/assets/e2ff7447-84af-41d3-8737-4e4c0c7b5ac4" />

## Devices Used

| Device         | Model        | Quantity |
|----------------|--------------|----------|
| Switch         | 2960         | 2        |
| Router         | 2911         | 4        |
| PC             | PC_PT        | 2        |

## IP Addressing Table

| Device | Interface | VLAN | IP Address     | Subnet Mask       |
|--------|-----------|------|----------------|-------------------|
| PC1    | Fa0/0     | 1    | 10.0.1.100     | 255.255.255.0     |
| PC2    | Fa0/0     | 1    | 10.0.2.100     | 255.255.255.0     |
| R1     | g0/0      | 1    | 10.0.1.1       | 255.255.255.0     |
| R1     | g0/0/0    | 1    | 100.0.0.2      | 255.255.255.252   |
| R2     | g0/0      | 1    | 10.0.2.1       | 255.255.255.0     |
| R2     | g0/0/0    | 1    | 200.0.0.2      | 255.255.255.252   |
| SPR1   | g0/0      | 1    | 10.0.0.1       | 255.255.255.0     |
| SPR1   | g0/0/0    | 1    | 100.0.0.1      | 255.255.255.252   |
| SPR2   | g0/0      | 1    | 10.0.0.2       | 255.255.255.0     |
| SPR2   | g0/0/0    | 1    | 200.0.0.1      | 255.255.255.252   |

## Configuration steps

### R1 (.1)

R1>enable

R1#configure terminal 

R1(config-if)#tunnel source g0/0/0

R1(config-if)#tunnel destination 200.0.0.2


R1(config-if)#ip address 192.168.1.1 255.255.255.252

R1(config-if)#do show ip interface brief

<img width="673" alt="Captura de Pantalla 2025-06-11 a la(s) 10 27 31" src="https://github.com/user-attachments/assets/b3861bb6-d76b-4db4-90d8-043f40be2158" />

### R2 (.1)

R2>enable

R2#configure terminal 

R2(config-if)#tunnel source g0/0/0

R2(config-if)#tunnel destination 100.0.0.2

R2(config-if)#ip address 192.168.1.2 255.255.255.252

R2(config-if)#do show ip interface brief

<img width="683" alt="Captura de Pantalla 2025-06-11 a la(s) 10 30 03" src="https://github.com/user-attachments/assets/1b3073ae-bb32-42f6-b1f8-8cc9d97c862b" />

R2(config-if)#ip route 0.0.0.0 0.0.0.0 200.0.0.1

<img width="552" alt="Captura de Pantalla 2025-06-11 a la(s) 10 32 35" src="https://github.com/user-attachments/assets/867aed2a-6ae6-43ba-82f3-db9b48f1af34" />

### R1 (.1)

R1(config)#ip route 0.0.0.0 0.0.0.0 100.0.0.1

R1(config-if)#do ping 192.168.1.2

<img width="585" alt="Captura de Pantalla 2025-06-11 a la(s) 10 42 23" src="https://github.com/user-attachments/assets/514afd05-8880-4f66-82f8-c595326f8559" />

### R1 (.2)

R1(config)#router ospf 1

R1(config-router)#network 192.168.1.1 0.0.0.0 area 0

R1(config-router)#network 10.0.0.1 0.0.0.0 area 0

R1(config-router)#passive-interface g0/0

### R2 (.2)

R2(config-router)#network 192.168.1.2 0.0.0.0 area 0

R2(config-router)#network 10.0.2.1 0.0.0.0 area 0

R2(config-router)#passive-interface g0/0

R2(config-router)#do show ip route

<img width="545" alt="Captura de Pantalla 2025-06-11 a la(s) 10 49 01" src="https://github.com/user-attachments/assets/5a1a381a-8b56-4477-bcd1-fd899d9be294" />

### PC1

<img width="415" alt="Captura de Pantalla 2025-06-11 a la(s) 11 23 05" src="https://github.com/user-attachments/assets/d39e8ad3-2ecc-4c46-be89-cccecd3c1359" />
















































