# Voice VLANs

**Author:** Millioud NetLab  
**Date:** 03-05-2025

## Objectives 

**Telephony configurations (not relevant to the CCNA) have been pre-configured on R1**

1. Configure SW1's interfaces in the appropriate VLANs.

2. Configure ROAS for the connection between SW1 and R1.

3. In simulation mode, ping PC2 from PC1.
    Is the traffic tagged with a VLAN ID?

4. In simulation mode, call PH1 from PH2.  Is the traffic tagged with a VLAN ID?

## Topology 

<img width="917" alt="Captura de Pantalla 2025-05-03 a la(s) 23 52 37" src="https://github.com/user-attachments/assets/1789ba20-07fe-4b84-8d5f-9528efc281b2" />


## Devices Used

| Device         | Model        | Quantity |
|----------------|--------------|----------|
| IP Phone         | 7960         | 2        |
| Layer 3 Switch | 3560         | 1        |
| PC             | PC-PT      | 2        |

## IP Addressing Table

| Device | Interface | VLAN | IP Address     | Subnet Mask       |
|--------|-----------|------|----------------|-------------------|
| PC1    | Fa0/0     | 1   | 192.168.10.11   | 255.255.255.0     |
| PC2    | Fa0/0     | 1   | 192.168.20.12   | 255.255.255.0     |


## Configuration Steps

### Switch 1 (.1)

SW1>enable

SW1#conf t

SW1(config)#int range g1/0/2-g1/0/3

SW1(config-if-range)#switchport mode access

SW1(config-if-range)#switchport access vlan 10

SW1(config-if-range)#switchport voice vlan 20

SW1(config-if-range)#do sh vlan br

<img width="680" alt="Captura de Pantalla 2025-05-04 a la(s) 0 04 42" src="https://github.com/user-attachments/assets/534fb48e-7fc9-40ac-bc3a-b9fc48ac53a6" />

### Switch 1 (.2)

SW1(config-if-range)#int g1/0/1

SW1(config-if)#switchport mode trunk

SW1(config-if)#switchport trunk allowed vlan 10,20

### Router 1 (.2)

R1>enable

R1#conf t

R1(config)#int f0/0

R1(config-if)#no shutdown

R1(config-if)#int f0/0.10

R1(config-subif)#encapsulation dot1q 10

R1(config-subif)#ip address 192.168.10.1 255.255.255.0

R1(config-subif)#int f0/0.20

R1(config-subif)#encapsulation dot1q 20

R1(config-subif)#ip address 192.168.20.1 255.255.255.0

### PC1 (.3)

ping 192.168.10.12

<img width="474" alt="Captura de Pantalla 2025-05-04 a la(s) 0 19 36" src="https://github.com/user-attachments/assets/70be00f0-03d5-4e6e-a482-d6f3a7dcd5c0" />

<img width="797" alt="Captura de Pantalla 2025-05-04 a la(s) 0 21 46" src="https://github.com/user-attachments/assets/99a0104f-5b31-411d-943d-688137213111" />

Phone 1 (.4)

dial 2010

<img width="1071" alt="Captura de Pantalla 2025-05-04 a la(s) 0 32 31" src="https://github.com/user-attachments/assets/6bced437-a083-495e-9acb-c177d916cdec" />












