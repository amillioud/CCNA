# LAN Architectures
**Author:** Millioud NetLab  
**Date:** 08-06-2025  

---

## Objectives

Configure HSRP on DSW1/DSW2, and ensure sychronization with STP.

In VLAN 10:

-DSW1 is HSRP active/STP root

-DSW2 is HSRP standby/STP secondary root

In VLAN 20:

-DSW2 is HSRP active/STP root

-DSW1 is HSRP standby/STP secondary root

---

## Topology

<img width="564" alt="Captura de Pantalla 2025-06-08 a la(s) 17 26 55" src="https://github.com/user-attachments/assets/a361ead6-0907-4fe9-a9c1-00f1c54163c5" />

## Devices Used

| Device         | Model        | Quantity |
|----------------|--------------|----------|
| Switch         | 2960         | 2        |
| Layer 3 Switch | 3560         | 2        |
| PC             | PC-PT        | 3        |

## IP Addressing Table

| Device | Interface | VLAN | IP Address     | Subnet Mask       |
|--------|-----------|------|----------------|-------------------|
| PC1    | Fa0/0     | 10   | 10.0.10.10     | 255.255.255.0     |
| PC2    | Fa0/0     | 20   | 10.0.20.10     | 255.255.255.0     |
| DSW1   | VLAN 10   | 10   | 10.0.10.254    | 255.255.255.0     |
| DSW1   | VLAN 20   | 20   | 10.0.20.254    | 255.255.255.0     |
| DSW2   | VLAN 10   | 10   | 10.0.10.254    | 255.255.255.0     |
| DSW2   | VLAN 20   | 20   | 10.0.20.254    | 255.255.255.0     |

## Configuration Steps

### DSW1

DSW1#show standby brief

<img width="630" alt="Captura de Pantalla 2025-06-08 a la(s) 17 50 07" src="https://github.com/user-attachments/assets/61731d1d-91b5-4def-9804-3549a9d8c770" />

DSW1#show spanning-tree vlan 10

<img width="666" alt="Captura de Pantalla 2025-06-08 a la(s) 17 50 45" src="https://github.com/user-attachments/assets/2bdd3eed-2457-405c-afd0-c0d46c92e04a" />

DSW1#show spanning-tree vlan 20

<img width="655" alt="Captura de Pantalla 2025-06-08 a la(s) 17 51 38" src="https://github.com/user-attachments/assets/e32fd7d6-7141-436c-a4be-03b7ace28162" />

DSW1#configure terminal 

DSW1(config)#spanning-tree vlan 10 root primary

DSW1(config)#spanning-tree vlan 20 root secondary

DSW1(config)#do sh spanning-tree vlan 10

<img width="655" alt="Captura de Pantalla 2025-06-08 a la(s) 17 54 31" src="https://github.com/user-attachments/assets/78edf749-4fb4-4e4b-9b75-b23af55c1b9a" />

DSW1(config)#do sh spanning-tree vlan 20

<img width="664" alt="Captura de Pantalla 2025-06-08 a la(s) 17 55 59" src="https://github.com/user-attachments/assets/20ccca96-266f-400c-a292-560f51daa5e0" />

DSW1(config)#interface vlan 10

DSW1(config-if)#standby version 2

DSW1(config-if)#standby 10 ip 10.0.10.254

<img width="435" alt="Captura de Pantalla 2025-06-08 a la(s) 18 03 19" src="https://github.com/user-attachments/assets/786a8c2e-3b83-4a06-b7c1-48caf17efad2" />

DSW1(config-if)#standby 10 preempt

DSW1(config-if)#interface vlan 20

DSW1(config-if)#standby version 2

DSW1(config-if)#standby 20 ip 10.0.20.254

<img width="449" alt="Captura de Pantalla 2025-06-08 a la(s) 18 06 41" src="https://github.com/user-attachments/assets/3c6e9d87-2222-416f-8197-d813178c3195" />

DSW1(config-if)#standby priority 95

DSW1(config-if)#standby 20 preempt

### DSW2

DSW2(config)#spanning-tree vlan 10 root secondary

DSW2(config)#spanning-tree vlan 20 root primary

DSW2(config)#do sh spanning-tree vlan 20

<img width="655" alt="Captura de Pantalla 2025-06-08 a la(s) 18 14 28" src="https://github.com/user-attachments/assets/251702d4-a645-4c2e-a33d-fc8cf5761c16" />

DSW2(config)#do sh spanning-tree vlan 10

<img width="651" alt="Captura de Pantalla 2025-06-08 a la(s) 18 15 59" src="https://github.com/user-attachments/assets/3b6b4250-0e31-4adc-b3fe-fad9fbbdd1ad" />

DSW2(config)#interface vlan 10

DSW2(config-if)#standby version 2

DSW2(config-if)#standby 10 ip 10.0.10.254

<img width="491" alt="Captura de Pantalla 2025-06-08 a la(s) 18 32 01" src="https://github.com/user-attachments/assets/8ccb0530-9685-47b1-b789-38931bc00b6e" />

DSW2(config-if)#standby 10 priority 95

DSW2(config-if)#standby 10 preempt

DSW2(config-if)#interface vlan 20

DSW2(config-if)#standby version 2

DSW2(config-if)#standby 20 ip 10.0.20.254

<img width="489" alt="Captura de Pantalla 2025-06-08 a la(s) 18 37 17" src="https://github.com/user-attachments/assets/58767059-1294-4efe-8630-964f9b5bab8c" />

DSW2(config-if)#standby 20 priority 105 

DSW2(config-if)#standby 20 preempt

<img width="503" alt="Captura de Pantalla 2025-06-08 a la(s) 18 37 33" src="https://github.com/user-attachments/assets/3b4aa6d8-77d4-4212-a140-4214f4e9fcf9" />

DSW2(config-if)#do show standby brief

<img width="636" alt="Captura de Pantalla 2025-06-08 a la(s) 18 41 36" src="https://github.com/user-attachments/assets/eab60512-1edb-4339-8496-0832e9bb7e82" />

### DSW1

DSW1#show standby brief

<img width="654" alt="Captura de Pantalla 2025-06-08 a la(s) 18 44 08" src="https://github.com/user-attachments/assets/5e2dd4d5-efb3-4e3b-b3fb-68555c8dafec" />




























