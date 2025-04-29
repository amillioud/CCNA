# Standard ACLs (lab 2)

**Author:** Millioud NetLab  

**Date:** 29-04-2025

## Objective

Configure standard ACLs to achieve the following requirements:

---only computers in the 192.168.1.0/24 network can access SRV1

---PC4 cannot communicate with the 192.168.1.0/24 network.

## Topology

<img width="1132" alt="Captura de Pantalla 2025-04-29 a la(s) 20 44 29" src="https://github.com/user-attachments/assets/896dbd1c-660b-49eb-9332-8bcf9f67fd86" />

## Devices Used

| Device         | Model        | Quantity |
|----------------|--------------|----------|
| PC         | PC-PT         | 4        |
| Switch | 2960         | 3        |
| Router             | Router-PT      | 2        |
| Server             | Server-PT      | 1        |

##  IP Addressing Table

| Device | Interface | VLAN | IP Address     | Subnet Mask       |
|--------|-----------|------|----------------|-------------------|
| PC1    | Fa0/0     | 10   | 192.168.10.2   | 255.255.255.0     |
| PC2    | Fa0/0     | 20   | 192.168.20.2   | 255.255.255.0     |
| L3SW   | VLAN 10   | 10   | 192.168.10.1   | 255.255.255.0     |
| L3SW   | VLAN 20   | 20   | 192.168.20.1   | 255.255.255.0     |



























