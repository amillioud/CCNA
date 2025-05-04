# SYSLOG (lab 2)

**Author:** Millioud NetLab  
**Date:** 04-05-2025

## Objectives

1. Connect to R1's console port using PC2:
   
     -Shut down the G0/0 interface
   
     -After you receive a syslog message, re-enable the interface.

     -What is the severity level of the syslog messages?

     -Enable date and timestamps with milliseconds for logging messages

3. Configure an enable secret of 'ccna'

     -Then configure the VTY lines to allow Telnet and require a password of 'ccent' to connect

5. Telnet from PC1 to R1's G0/0 interface, then perform a 'no shutdown' on the unused G0/1 interface

     -Why does no syslog message appear?

     -Configure R1 so that logging/debug messages are displayed on the VTY lines

7. Configure synchronous logging on the console and VTY lines

8. Enable logging to the buffer, and configure the buffer size to 8192 bytes.

9. Enable logging to the syslog server SRV1.


## Topology 

<img width="520" alt="Captura de Pantalla 2025-05-04 a la(s) 14 00 59" src="https://github.com/user-attachments/assets/870fd5df-3d3d-487d-b10b-a66657967b8a" />

## Devices Used

| Device         | Model        | Quantity |
|----------------|--------------|----------|
| Switch         | 2960         | 1        |
| Router | 2911         | 1        |
| PC             | PC-PT      | 2        |
| Server             | Server-PT      | 1        |

## IP Addressing Table

| Device | Interface | VLAN | IP Address     | Subnet Mask       |
|--------|-----------|------|----------------|-------------------|
| PC1    | Fa0/0     | 1   | 192.168.1.12   | 255.255.255.0     |
| R1   | G0/0   | 1   | 192.168.1.1   | 255.255.255.0     |
| SRV1   | Fa0/0   | 1   | 192.168.20.1   | 255.255.255.0     |
| SW1   | Fa0/1, Fa0/2, G0/1   | 1   | na   | na     |

## Configuration Steps

### PC2 (.1)

R1>enable

R1#conf t

R1(config)#int g0/0

R1(config-if)#shutdown

<img width="690" alt="Captura de Pantalla 2025-05-04 a la(s) 14 08 03" src="https://github.com/user-attachments/assets/aeb3ca39-90bd-4dd3-97a6-b7fc2c965dba" />

R1(config-if)#no shutdown

<img width="689" alt="Captura de Pantalla 2025-05-04 a la(s) 14 08 48" src="https://github.com/user-attachments/assets/71c1f4e4-1acd-482a-9bd8-9732df281647" />

R1(config)#service timestamps log datetime msec

### PC2 (.2)

R1(config)#enable secret ccna 

R1(config)#line vty 0 15

R1(config-line)#password ccent 

R1(config-line)#login

R1(config-line)#transport input telnet

### PC1 (.3)

C:\>telnet 192.168.1.1

Password: ccnet

R1(config)#int g0/1

R1(config-if)#no shut

R1(config-if)# end

R1#terminal monitor

R1(config)#int g0/1

R1(config-if)#shutdown

<img width="664" alt="Captura de Pantalla 2025-05-04 a la(s) 15 08 04" src="https://github.com/user-attachments/assets/4da7f8b4-87c1-4436-a6d4-030a45c8e816" />

### PC1 (.4)

R1(config)#line console 0

R1(config-line)#logging synchronous

R1(config-line)#line vty 0 15

R1(config-line)#logging synchronous

### PC1 (.5)

R1(config)#logging buffered

R1(config)#do sh logging

<img width="594" alt="Captura de Pantalla 2025-05-04 a la(s) 17 12 59" src="https://github.com/user-attachments/assets/0fa19c8c-f9ff-45d2-986a-13b5e047855c" />

R1(config)#logging buffered 8192 

R1(config)#do sh logging

<img width="595" alt="Captura de Pantalla 2025-05-04 a la(s) 17 14 31" src="https://github.com/user-attachments/assets/f0522a6f-3d86-4cc7-a3bf-b0cb05035642" />

### PC1 (.6)

R1(config)#logging host 192.168.1.100

R1(config)#do show logging

<img width="609" alt="Captura de Pantalla 2025-05-04 a la(s) 17 18 38" src="https://github.com/user-attachments/assets/683b8eda-1938-4ac3-8f99-a48998298956" />
























