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
| PC1    | Fa0/0     | 1   | 192.168.1.11   | 255.255.255.0     |
| PC2    | Fa0/0     | 1   | 192.168.1.12   | 255.255.255.0     |
| PC3   | Fa0/0  | 1  | 192.168.2.13   | 255.255.255.0     |
| PC4   | Fa0/0  | 1   | 192.168.2.14   | 255.255.255.0     |
| SRV1   | Fa0/0  | 1   | 192.168.3.100   | 255.255.255.0     |
| R1   | Fa1/0  | 1   | 192.168.2.1   | 255.255.255.0     |
| R1   | Fa0/0  | 1   | 192.168.1.1   | 255.255.255.0     |
| R1   | S2/0  | 1   | 12.0.0.1   | 255.255.255.0     |

## Configuration Steps

### PC1 (ping to SRV1)

C:\>ping 192.168.3.100

<img width="480" alt="Captura de Pantalla 2025-04-29 a la(s) 21 04 04" src="https://github.com/user-attachments/assets/6863174e-6f7b-4fba-910a-be828b03c029" />

### PC4 (ping to SRV1)

C:\>ping 192.168.3.100

<img width="472" alt="Captura de Pantalla 2025-04-29 a la(s) 21 06 40" src="https://github.com/user-attachments/assets/2e6ec24c-c27f-482a-b7de-a1f6e9010eea" />

### R2 (configure the first ACL)

R2>enable

R2#conf t

R2(config)#access-list 1 permit 192.168.1.0 0.0.0.255

R2(config)#int f0/0

R2(config-if)#ip access-group 1 out

### PC4 (ping SRV1 to troubleshoot the first ACL)

C:\>ping 192.168.3.100

<img width="486" alt="Captura de Pantalla 2025-04-29 a la(s) 21 16 45" src="https://github.com/user-attachments/assets/aaf2ce01-de57-4d2c-a9fb-ea4baf219748" />

### R1 (configure the second ACL)


R1>enable

R1#conf t

R1(config)#access-list 1 deny host 192.168.2.14

R1(config)#access-list 1 permit any 

R1(config)#int f0/0

R1(config-if)#ip access-group 1 out

R1(config-if)#do sh access-lists

<img width="252" alt="Captura de Pantalla 2025-04-29 a la(s) 21 20 40" src="https://github.com/user-attachments/assets/c8f1d53e-c7d7-4ce4-b946-3bed1ce79952" />

### PC3 (ping subnet 192.168.1.0)

C:\>ping 192.168.1.12

<img width="484" alt="Captura de Pantalla 2025-04-29 a la(s) 21 30 21" src="https://github.com/user-attachments/assets/5595e895-9572-45e8-be9a-131128b4cbcb" />

### PC4 (ping subnet 192.168.1.0)

C:\>ping 192.168.1.12

<img width="494" alt="Captura de Pantalla 2025-04-29 a la(s) 21 33 47" src="https://github.com/user-attachments/assets/d8999e4f-33a7-450e-ac51-bc1173aefe3e" />

























