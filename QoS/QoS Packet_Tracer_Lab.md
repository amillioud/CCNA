# QoS
**Author:** Millioud NetLab  
**Date:** 13-05-2025

## Objectives

1. Mark HTTPS traffic as AF31
   
*--Provide minimum 10% bandwidth as a priority queue

2. Mark HTTP traffic as AF32

*--Provide minimum 10% bandwidth

3. Mark ICMP traffic as CS2

*--Provide minimum 5% bandwidth

4. Use simulation mode to view the DSCP markings of packets:

   -when pinging jeremysitlab.com from PC1

   -when accessing jeremysitlab.com from PC1 via HTTP

   -when accessing jeremysitlab.com from PC1 via HTTPS

## Topology

<img width="879" alt="Captura de Pantalla 2025-05-13 a la(s) 19 22 40" src="https://github.com/user-attachments/assets/e6c8c676-06f2-4d75-8250-74afc729d04f" />

## Devices Used

| Device         | Model        | Quantity |
|----------------|--------------|----------|
| PC       | PC-PT         | 1        |
| Layer 2 Switch | 2960         | 2       |
| Router             | ISR4331      | 2        |
| Server             | Server-PT      | 1        |

## IP Addressing Table

| Device | Interface | VLAN | IP Address     | Subnet Mask       |
|--------|-----------|------|----------------|-------------------|
| PC1    | Fa0/0     | 1   | 192.168.0.10   | 255.255.255.0     |
| R1    | G0/0/1     | 1   | 192.168.0.1   | 255.255.255.0     |
| R1   | G0/0/0  | 1  | 172.16.0.1   | 255.255.255.252     |
| R2   | G0/0/0   | 1   | 192.168.0.2   | 255.255.255.252     |
| R2   |   G0/0/1 | 1  | 10.0.0.1   | 255.255.255.0     |
| SRV1   |   G0/0/1 | 1  | 10.0.0.1   | 255.255.255.0     |

## Configuration Steps



















