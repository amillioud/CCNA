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


































