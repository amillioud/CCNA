# Extended Access Control Lists (lab 2)
**Author:** Millioud NetLab  
**Date:** [05-05-2025]  

## Objectives

Configure extended ACLs to achieve the following requirements:
---only PC1 can access SRV1
---only hosts on the 192.168.2.0/24 network can access SRV2

## Topology 

<img width="750" alt="Captura de Pantalla 2025-05-01 a la(s) 16 06 24" src="https://github.com/user-attachments/assets/10a4749d-fe88-4b73-8643-ac4201fe1b36" />

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
| PC1    | Fa0/0     | 1   | 192.168.1.11   | 255.255.255.0     |
| PC2    | Fa0/0     | 1   | 192.168.1.12   | 255.255.255.0     |
| PC3   | Fa0/0  | 1  | 192.168.2.13   | 255.255.255.0     |
| PC4   | Fa0/0  | 1   | 192.168.2.14   | 255.255.255.0     |
| SRV1   | Fa0/0  | 1   | 192.168.3.100   | 255.255.255.0     |
| R1   | Fa1/0  | 1   | 192.168.2.1   | 255.255.255.0     |
| R1   | Fa0/0  | 1   | 192.168.1.1   | 255.255.255.0     |
| R1   | S2/0  | 1   | 12.0.0.1   | 255.255.255.0     |

## Configurations Steps

### R1

R1>enable

R1#conf t

R1(config)#ip access-list extended pc1

R1(config-ext-nacl)#permit ip host 192.168.1.11 192.168.3.100 0.0.0.255

R1(config-ext-nacl)#do sh access-lists

<img width="475" alt="Captura de Pantalla 2025-05-01 a la(s) 16 14 41" src="https://github.com/user-attachments/assets/215858ad-aa67-49f3-9588-0e583777124c" />

R1(config-ext-nacl)#exit

R1(config)#int f0/0

R1(config-if)#ip access-group pc1 in

### PC1

ping 192.168.3.100

<img width="477" alt="Captura de Pantalla 2025-05-01 a la(s) 16 17 27" src="https://github.com/user-attachments/assets/3a5fb39e-50b1-4640-ae06-66516cda2087" />

### PC2

ping 192.168.3.100

<img width="490" alt="Captura de Pantalla 2025-05-01 a la(s) 16 18 28" src="https://github.com/user-attachments/assets/3fd4848e-f009-40db-917b-083acb3cb25c" />

### R1

R1(config)#ip access-list extended network1

R1(config-ext-nacl)#permit ip 192.168.2.0 0.0.0.255 192.168.3.101 0.0.0.255

R1(config-ext-nacl)#int s2/0

R1(config-if)#ip access-group network1 out

### PC1

ping 192.168.3.101

<img width="490" alt="Captura de Pantalla 2025-05-01 a la(s) 16 24 07" src="https://github.com/user-attachments/assets/828cf11f-6113-476c-9f03-c633374a907e" />

### PC3

ping 192.168.3.101

<img width="483" alt="Captura de Pantalla 2025-05-01 a la(s) 16 24 55" src="https://github.com/user-attachments/assets/0210e73f-a94e-4b21-b0b7-5b1d0b04aa54" />

















