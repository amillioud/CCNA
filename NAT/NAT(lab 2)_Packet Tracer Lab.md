# Static NAT Configuration (lab 2)

**Author:** Millioud NetLab  
**Date:** 24-04-2025  

## Objectives

1. RIP has been configured so that R1 and R2 can reach their inside networks.  
    Why can't PC1, PC2, and PC3 successfully ping SRV1?
    (Hint: The serial connection between R1 and R2 is simulating the Internet with ACLs)

2. Configure static NAT on R1 to translate the address of PC1, PC2, and PC3 to 
    1.2.3.11, 1.2.3.12, and 1.2.3.13, respectively.

3. Attempt to ping SRV1 from each PC again.  Do the pings succeed?

## Topology

<img width="1040" alt="Captura de Pantalla 2025-04-24 a la(s) 18 59 16" src="https://github.com/user-attachments/assets/624e887f-f971-4d5e-ac6d-4f4361feb906" />

## Devices Used

| Device         | Model        | Quantity |
|----------------|--------------|----------|
| PC         | PC-PT         | 3        |
| Switch | 2960         | 2        |
| Router             | 2911      | 2        |
| Server             | Server-PT      | 1        |

## IP Addressing table 

| Device | Interface | VLAN | IP Address     | Subnet Mask       |
|--------|-----------|------|----------------|-------------------|
| PC1    | Fa0/0     | 1   | 192.168.1.11   | 255.255.255.0     |
| PC2    | Fa0/0     | 1  | 192.168.1.12   | 255.255.255.0     |
| PC3   | Fa0/0    | 1   | 192.168.1.13   | 255.255.255.0     |
| SW1    | G0/0     | 1  | 192.168.1.1   | 255.255.255.0     |
| SW1   | S0/3/0    | 1   | 1.2.3.1   | 255.255.255.0     |
| SW2    | G0/0     | 1  | 1.1.1.1  | 255.255.255.0     |
| SW2   | S0/3/0    | 1   | 1.2.3.2   | 255.255.255.0     |
| SRV1   | Fa0/0    | 1   | 1.2.3.100   | 255.255.255.0     |

## Configuration Steps

### R1 (.1)

R1>enable
R1#show ip access-lists

<img width="367" alt="Captura de Pantalla 2025-04-24 a la(s) 19 19 34" src="https://github.com/user-attachments/assets/168dbc07-1a60-4908-a69f-38cbe26e40c2" />




















