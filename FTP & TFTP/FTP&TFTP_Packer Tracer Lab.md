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

















