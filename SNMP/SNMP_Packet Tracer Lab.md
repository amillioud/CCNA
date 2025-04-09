# SNMP Packet Tracer Lab

**Author:** Millioud NetLab  
**Date:** 07-04-2025  

## Objectives


1. Configure the following SNMP communities on R1:
read-only: Cisco1
read/write: Cisco2

2. Use SNMP 'Get' messages via the MIB browser on PC1 to check the following:
-How long has R1 been running? (system uptime)
-What is the currently configured hostname on R1?
-How many interfaces does R1 have?
-What are those interfaces?

+check what other information you can learn about R1 via SNMP Get messages.
 
3. Use an SNMP 'Set' message from PC1 to change the hostname of R1.

## Topology 

<img width="527" alt="Captura de Pantalla 2025-04-07 a la(s) 20 22 58" src="https://github.com/user-attachments/assets/7dbdfdcb-061f-452d-a2e2-dd0f213619ed" />

## Devices Used


| Device         | Model        | Quantity |
|----------------|--------------|----------|
| Router         | 2911         | 1        |
| Switch  | 2960         | 1        |
| PC             | PC-PT     | 1        |

## IP Addressing Table

| Device | Interface | VLAN | IP Address     | Subnet Mask       |
|--------|-----------|------|----------------|-------------------|
| R1    | G0/0     | na   | 192.168.1.254   | 255.255.255.0     |
| PC1    | Fa0/0     | na   | 192.168.1.1   | 255.255.255.0     |

## Configuration Steps

### R1

R1(config)#snmp-server community Cisco1 ro

R1(config)#snmp-server community Cisco2 rw

### PC1

PC1 -> Desktop -> MIB Browser -> Address 192.168.1.254 

PC1 -> Desktop -> MIB Browser -> MIB tree -> .sysName (Operations: Set -> data type: octet string & value: R12) -> Ok
