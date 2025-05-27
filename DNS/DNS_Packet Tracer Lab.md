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

