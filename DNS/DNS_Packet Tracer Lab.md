#  DNS Configuration
**Author:** Millioud NetLab  
**Date:** 27-05-2025

## Objectives 

1. Configure the following DHCP pool on R1:
   1pool:
     Network: 192.168.1.0/24
     Default gateway: 192.168.1.1
     Excluded address range: 192.168.1.1 - 192.168.1.10

2. From PC1, attempt to ping SRV1 by IP address, then by name.  Does either fail?

3. Add 20.0.0.100 as a DNS server to the 1pool DHCP pool.

4. From PC1, ping SRV1 and SRV2 by name.  Do the pings succeed?

5. On SW1, attempt to ping SRV1 by IP address and by name.  

6. On SW1, manually specify R1 as the default gateway and DNS1 as the DNS server, then attempt the pings again.

## Topology 

<img width="460" alt="Captura de Pantalla 2025-05-27 a la(s) 17 48 55" src="https://github.com/user-attachments/assets/964e8ef9-aded-4899-ad3f-0fc256162876" />

## Devices Used

| Device         | Model        | Quantity |
|----------------|--------------|----------|
| Switch         | 2960-24TT         | 3        |
| Router | 2911         | 1        |
| PC             | PT-PC      | 2        |
| Server             | PT-Server      | 3        |

## IP Addressing Table

| Device | Interface | VLAN | IP Address     | Subnet Mask       |
|--------|-----------|------|----------------|-------------------|
| PC1    | Fa0/0     | 1   | 169.254.28.120   | 255.255.0.0     |
| PC2    | Fa0/0     | 1   | 169.254.195.124  | 255.255.0.0     |
| SW1   | VLAN 1   | 1   | 192.168.1.2   | 255.255.255.0     |
| SW2   | VLAN 1   | 1   | 10.0.0.2  | 255.255.255.0     |
| SW3   | VLAN 1   | 1   | 20.0.0.2   | 255.255.255.0     |
| DNS1   | VLAN 1   | 1   | 20.0.0.100   | 255.255.255.0     |
| SRV1   | VLAN 1   | 1   | 20.0.0.101   | 255.255.255.0     |
| SRV2   | VLAN 1   | 1   | 20.0.0.102   | 255.255.255.0     |
| R1   | VLAN 1   | 1   | 20.0.0.102   | 255.255.255.0     |

## Configuration Steps

R1 (.1)

R1>enable

R1#configure terminal

R1(config)#ip dhcp excluded-address 192.168.1.1 192.168.1.10

R1(config)#ip dhcp pool 1pool

R1(dhcp-config)#network 192.168.1.0 255.255.255.0

R1(dhcp-config)#default-router 192.168.1.1

PC (.2)

C:\>ping 10.0.0.101

<img width="493" alt="Captura de Pantalla 2025-05-27 a la(s) 18 25 22" src="https://github.com/user-attachments/assets/563a6915-2f28-476f-a6c7-cc202df689eb" />

C:\>ping SRV1

<img width="637" alt="Captura de Pantalla 2025-05-27 a la(s) 18 25 48" src="https://github.com/user-attachments/assets/64ed7f86-2c92-4f58-8d2e-3395a8bb7b98" />

R1 (.3)

R1(dhcp-config)#dns-server 20.0.0.100

PC1 (.4)

C:\>ipconfig /release

<img width="368" alt="Captura de Pantalla 2025-05-27 a la(s) 18 32 40" src="https://github.com/user-attachments/assets/7d456912-926c-4a6b-8141-abd1a5a09a65" />

C:\>ipconfig /renew

<img width="411" alt="Captura de Pantalla 2025-05-27 a la(s) 18 32 59" src="https://github.com/user-attachments/assets/e032cd19-1ca9-4560-b3ce-62c3e48d7459" />

C:\>ping srv1

<img width="484" alt="Captura de Pantalla 2025-05-27 a la(s) 18 35 10" src="https://github.com/user-attachments/assets/7d1daa5b-1265-4864-8f13-52334aa9f95d" />

C:\>ping srv2

<img width="487" alt="Captura de Pantalla 2025-05-27 a la(s) 18 39 20" src="https://github.com/user-attachments/assets/fd40e9be-8281-4d50-b07b-bdf566298e2a" />

SW1 (.5)

SW1#ping 10.0.0.101

<img width="577" alt="Captura de Pantalla 2025-05-27 a la(s) 18 49 20" src="https://github.com/user-attachments/assets/df36be58-a901-4450-8d69-c80e06d3ffad" />

SW1#ping srv1

<img width="471" alt="Captura de Pantalla 2025-05-27 a la(s) 18 49 59" src="https://github.com/user-attachments/assets/5db4ac09-3e53-419e-83d0-5f5eceb4bd22" />

SW1 (.6)

SW1(config)#ip default-gateway 192.168.1.1

SW1(config)#ip name-server 20.0.0.0

SW1(config)#do ping srv1

<img width="588" alt="Captura de Pantalla 2025-05-27 a la(s) 19 00 27" src="https://github.com/user-attachments/assets/32ae52d6-f1ea-4c11-9602-f3ffc23ced60" />

SW1(config)#do ping srv2

<img width="583" alt="Captura de Pantalla 2025-05-27 a la(s) 19 01 00" src="https://github.com/user-attachments/assets/0e3fff3e-705b-44f9-8f47-f131a7dbc12c" />
























