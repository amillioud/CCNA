# Static NAT Configuration
**Author:** Millioud NetLab  
**Date:** 23-04-2025

## Objectives

1. Attempt to ping from PC1 to 8.8.8.8.  Does the ping work?

2. Configure static NAT on R1.
   
   > Configure the appropriate inside/outside interfaces
   
   > Map the IP addresses of PC1, PC2, and PC3 to 100.0.0.x/24

4. Ping 8.8.8.8 from PC1 again.  Does the ping work?

5. Ping google.com from each PC, and then check the NAT translations on R1.

6. Clear the NAT translations on R1.  Which entries remain?

## Topology

<img width="875" alt="Captura de Pantalla 2025-04-23 a la(s) 18 56 23" src="https://github.com/user-attachments/assets/a2110b27-b076-49e4-86c5-e855d63f7bba" />

## Devices Used

| Device         | Model        | Quantity |
|----------------|--------------|----------|
| PC         | PC-PT         | 3        |
| Switch | 2960         | 1        |
| Router             | 2911      | 2        |
| Server             | Server-PT      | 1        |

## IP Addressing Table

| Device | Interface | VLAN | IP Address     | Subnet Mask       |
|--------|-----------|------|----------------|-------------------|
| PC1    | Fa0/0     | 1   | 172.16.0.1  | 255.255.255.0     |
| PC2    | Fa0/0     | 1   | 172.16.0.2   | 255.255.255.0     |
| PC3   | Fa0/0  | 1   | 172.16.0.3   | 255.255.255.0     |
| R1   | G0/0  | 1   | 203.0.113.1   | 255.255.255.252     |
| R1   | G0/1   | 1   | 172.16.0.254   | 255.255.255.0     |
| INTERNET*   | G0/0   | 1   | 203.0.113.2   | 255.255.255.252     |
| INTERNET*   | G0/1   | 1   | 8.8.8.1   | 255.255.255.0     |
| SRV1   | G0/0   | na   | 8.8.8.8   | 255.255.255.0     |

## Configuration Steps

### PC1 (.1)

command prompt -> ping 8.8.8.8

### R1 (.2)

R1>enable

R1#conf t

R1(config)#int g0/1

R1(config-if)#ip nat inside

R1(config-if)#int g0/0

R1(config-if)#ip nat outside

R1(config-if)#exit

R1(config)#ip nat inside source static 172.16.0.1 100.0.0.1

R1(config)#ip nat inside source static 172.16.0.1 100.0.0.2

R1(config)#ip nat inside source static 172.16.0.1 100.0.0.3

### PC1 (.3)

command prompt -> ping 8.8.8.8

<img width="481" alt="Captura de Pantalla 2025-04-23 a la(s) 19 25 15" src="https://github.com/user-attachments/assets/47e57ea2-f760-493d-a209-dee2743582d9" />

### PC1, PC2 and PC3 (.4)

command prompt -> google.com

### R1 (.4)

R1#sh ip nat translations

<img width="677" alt="Captura de Pantalla 2025-04-23 a la(s) 19 33 02" src="https://github.com/user-attachments/assets/de11e31e-70a8-4c51-b2a5-7a6e07b1d0a4" />


### R1 (.5)

R1#clear ip nat translation *

R1#sh ip nat translations

<img width="666" alt="Captura de Pantalla 2025-04-23 a la(s) 19 34 31" src="https://github.com/user-attachments/assets/cc1a3cf3-8974-41eb-a268-1f08040c9a21" />
















