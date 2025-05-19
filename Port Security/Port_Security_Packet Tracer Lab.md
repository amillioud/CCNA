# Port Security
**Author:** Millioud NetLab  
**Date:** 19-05-2025

##  Objective

1. Configure port security on the following interfaces:
   
#SW1 F0/1, F0/2, F0/3#

Violation mode: Shutdown

Maximum addresses: 1

Sticky learning: Disabled

Aging time: 1 hour

#SW2 G0/1#

Violation mode: Restrict

Maximum addresses: 4

Sticky learning: Enabled

2. Trigger port security violations on SW1 and SW2 (for example by 

    connecting another PC) and observe the actions taken by each switch.

## Topology

<img width="727" alt="Captura de Pantalla 2025-05-19 a la(s) 17 10 20" src="https://github.com/user-attachments/assets/b7b08c3a-e51d-475d-9e89-3ac098c5a5ad" />

## Devices Used

| Device         | Model        | Quantity |
|----------------|--------------|----------|
| Switch         | 2960         | 2        |
| R1             | 2911         | 1        |
| PC             | PC-PT        | 3        |

## IP Addressing Table

| Device | Interface | VLAN | IP Address     | Subnet Mask       |
|--------|-----------|------|----------------|-------------------|
| PC1    | Fa0/1     | na   |  10.0.0.1   | 255.255.255.0     |
| PC2    | Fa0/2     | na   |  10.0.0.2    | 255.255.255.0     |
| PC3    | Fa0/3     | na   |  10.0.0.3     | 255.255.255.0     |
| SW1    | VLAN 1 (G0/1)    | na   | 10.0.0.10      | 255.255.255.0     |
| R1     | G0/1    | na   | 10.0.0.254     | 255.255.255.0     |

## Configuration Steps

SW1 (.1)

SW1>enable

SW1#configure terminal

SW1(config)#int range f0/1, f0/2, f0/3

SW1(config-if-range)#switchport port-security aging time 60

SW1(config-if-range)#do sh port-security int f0/1

<img width="392" alt="Captura de Pantalla 2025-05-19 a la(s) 17 44 35" src="https://github.com/user-attachments/assets/2be4f14e-cfa5-467e-bc4a-a65af216f8ba" />

SW2 (.1)

SW2>enable

SW2#configure terminal

SW2(config)#interface g0/1

SW2(config-if)#switchport mode access

SW2(config-if)#switchport port-security

SW2(config-if)#switchport port-security violation restrict

SW2(config-if)#switchport port-security maximum 4

SW2(config-if)#switchport port-security mac-address sticky

SW2(config-if)#do sh port-security int g0/1

<img width="387" alt="Captura de Pantalla 2025-05-19 a la(s) 17 51 54" src="https://github.com/user-attachments/assets/bed8f013-9275-43ad-863d-88e675838eea" />

PC 1, 2, 3 (.1)

Ping 10.0.0.254

SW2 (.1)

SW2(config-if)#do sh port-security int g0/1

<img width="381" alt="Captura de Pantalla 2025-05-19 a la(s) 17 53 38" src="https://github.com/user-attachments/assets/11432536-e4df-45c2-8005-9abd83b89931" />

SW2(config-if)#do sh mac address-table

<img width="377" alt="Captura de Pantalla 2025-05-19 a la(s) 17 55 57" src="https://github.com/user-attachments/assets/7f1c0a9e-aa1b-4b40-8666-6a110a9cf3a8" />

SW1 (.2)

SW1(config)#int vlan 1

SW1(config-if)#ip address 10.0.0.10 255.255.255.0

SW1(config-if)#no shutdown

SW1(config-if)#do ping 10.0.0.254

<img width="571" alt="Captura de Pantalla 2025-05-19 a la(s) 17 58 26" src="https://github.com/user-attachments/assets/dcaae1db-a6cc-47f7-bb56-064459e20b48" />

SW2 (.2)

SW2(config-if)#do sh port-security int g0/1

<img width="386" alt="Captura de Pantalla 2025-05-19 a la(s) 17 59 35" src="https://github.com/user-attachments/assets/558db1f6-52e8-4241-a58d-059a62d91e7a" />

PC1 (.2)

<img width="539" alt="Captura de Pantalla 2025-05-19 a la(s) 18 01 17" src="https://github.com/user-attachments/assets/940377c1-89b6-4109-bcee-74b8139d45c5" />

<img width="542" alt="Captura de Pantalla 2025-05-19 a la(s) 18 01 30" src="https://github.com/user-attachments/assets/193cc07a-301d-4e5c-afb1-bd623e872ee8" />

Ping 10.0.0.254

SW1 (.2)

SW1(config-if)#do show port-security int f0/1

<img width="383" alt="Captura de Pantalla 2025-05-19 a la(s) 18 03 21" src="https://github.com/user-attachments/assets/5ad64d72-f343-4d43-b43d-05ad1006f139" />

<img width="494" alt="Captura de Pantalla 2025-05-19 a la(s) 18 03 41" src="https://github.com/user-attachments/assets/725ca320-ac36-46e6-88e7-5511c60cf8f4" />































   
