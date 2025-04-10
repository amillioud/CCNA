# Syslog Configuration Packet Tracer Lab

**Author:** Millioud NetLab  
**Date:** 10-04-2025  

## Objective

(R1 username: jeremy, PW: ccna, enable PW: ccna)

1. Connect to R1's console port using PC2:
   
     -Shut down the G0/0 interface
   
     -After you receive a syslog message, re-enable the interface.
   
     -What is the severity level of the syslog messages?
   
     -Enable timestamps for logging messages

3. Telnet from PC1 to R1's G0/0 interface
   
     -Enable the unused G0/1 interface
   
     -Enable logging to the VTY lines for the current session.

5. Enable logging to the buffer, and configure the buffer size to 8192 bytes.

6. Enable logging to the syslog server SRV1 with a level of 'debugging'.
 
## Topology

<img width="583" alt="Captura de Pantalla 2025-04-10 a la(s) 22 16 17" src="https://github.com/user-attachments/assets/d387e91c-1eb2-4659-9b17-18ba980b52fd" />

## Devices Used

| Device         | Model        | Quantity |
|----------------|--------------|----------|
| Switch 1         | 2960         | 1        |
| Router 1| 2911         | 1        |
| PC 1           | Generic      | 1        |
| PC 2           | Generic      | 1        |
| Server 1           | Generic      | 1        |

## IP Addressing Table

| Device | Interface | VLAN | IP Address     | Subnet Mask       |
|--------|-----------|------|----------------|-------------------|
| PC2    | console port   | na   | na  | na    |
| PC1    | F0/0   | 1   | 192.168.1.12  | 255.255.255.0    |
| R1    | G0/0   | 1   | 192.168.1.1  | 255.255.255.0    |
| SRV1    | G0/0   | 1   | 192.168.1.100  | 255.255.255.0    |

## Configuration Steps

### PC2 (from terminal)

Username: jeremy

Password: ccna

R1>enable

Password: ccna

R1#configure terminal

R1(config)#interface g0/0

R1(config-if)#shutdown

* R1(config-if)#
%LINK-5-CHANGED: Interface GigabitEthernet0/0, changed state to administratively down

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0, changed state to down *














