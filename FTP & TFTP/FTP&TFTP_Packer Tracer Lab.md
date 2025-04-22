# FTP & TFTP Configuration

**Author:** Millioud NetLab  
**Date:** 22-04-2025

## Objectives

1. Configure the appropriate IP addresses on each device.
    Configure routing on the routers to allow full connectivity.

2. Use TFTP on R1 to retrieve the following file from SRV1:
    c2900-universalk9-mz.SPA.155-3.M4a.bin

3. Upgrade R1's OS and then delete the old file from flash.

4. Use FTP on R2 to retrieve the following file from SRV1:
    c2900-universalk9-mz.SPA.155-3.M4a.bin
    (FTP username: jeremy, password: ccna)
  **THE TRANSFER MAY TAKE ABOUT A MINUTE**

5. Upgrade R2's OS and then delete the old file from flash.

## Topology

<img width="798" alt="Captura de Pantalla 2025-04-22 a la(s) 19 10 31" src="https://github.com/user-attachments/assets/01d7bfce-616c-4b6d-8978-1119cc81cd52" />

## Devices Used

| Device         | Model        | Quantity |
|----------------|--------------|----------|
| Server1        | Server-PT         | 1        |
| Layer 2 Switch | 2960         | 1        |
| Router             | 2911      | 2        |

##  IP Addressing Table

| Device | Interface | VLAN | IP Address     | Subnet Mask       |
|--------|-----------|------|----------------|-------------------|
| Server1    | Fa0/0     | 1   | 10.0.0.1   | 255.255.255.0     |
| R1   | G0/1     | 1   | 10.0.0.254  | 255.255.255.0     |
| R1   | G0/0  | 1   | 192.168.12.1   | 255.255.255.252     |
| R2   | G0/0   | 1  | 192.168.12.2   | 255.255.255.252     |

## Configuration Steps

### Server 1 (.1)

config -> settings -> default gateway: 10.0.0.254 
config -> FastEthernet0 -> IPv4 address: 10.0.0.1 Netmask: 255.255.255.0

### Router 1 (.1)

R1>enable

R1#conf t

R1(config)#int g0/1

R1(config-if)#ip address 10.0.0.254 255.255.255.0

R1(config-if)#no shut

R1(config-if)#int g0/0

R1(config-if)#ip address 192.168.12.1 255.255.255.252

R1(config-if)#no shut

### Router 2 (.1)

R2>enable

R2#conf t

R2(config)#int g0/0

R2(config-if)#ip address 192.168.12.2 255.255.255.252

R2(config-if)#no shut

R2(config-if)#exit

R2(config)#ip route 10.0.0.0 255.255.255.0 192.168.12.1

### Router 1 (.2 and .3)

R1#copy tftp flash

Address or name of remote host []? 10.0.0.1

Source filename []? c2900-universalk9-mz.SPA.155-3.M4a.bin

Destination filename [c2900-universalk9-mz.SPA.155-3.M4a.bin]? 

R1#conf t

R1(config)#boot system flash:c2900-universalk9-mz.SPA.155-3.M4a.bin

R1(config)#exit

R1#write

R1#reload

R1#delete flash:c2900-universalk9-mz.SPA.151-4.M4.bin

### Router 2 (.4 and .5)

R2#conf t

R2(config)#ip ftp username jeremy

R2(config)#ip ftp password ccna

R2#copy ftp flash

Address or name of remote host []? 10.0.0.1

Source filename []? c2900-universalk9-mz.SPA.155-3.M4a.bin

Destination filename [c2900-universalk9-mz.SPA.155-3.M4a.bin]? 

R2#conf t

R2(config)#boot system flash:c2900-universalk9-mz.SPA.155-3.M4a.bin

R2(config)#exit

R2#write

R2#reload

R2#delete flash:c2900-universalk9-mz.SPA.155-3.M4a.bin

Delete filename [c2900-universalk9-mz.SPA.155-3.M4a.bin]?

Delete flash:/c2900-universalk9-mz.SPA.155-3.M4a.bin? [confirm]













