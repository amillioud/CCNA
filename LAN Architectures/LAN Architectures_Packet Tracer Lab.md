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

























