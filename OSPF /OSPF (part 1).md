# Pakcet Tracer Lab - OSPF (part 1) 

## 1. Lab Objectives

1. Configure the appropriate hostnames and IP addresses on each device.  Enable router interfaces.
    (You don't have to configure ISPR1)

2. Configure a loopback interface on each router (1.1.1.1/32 for R1, 2.2.2.2/32 for R2, etc.)

3. Configure OSPF on each router.
    Enable OSPF on each interface (including loopback interfaces).
    (Do not enable OSPF on R1's Internet link)
    Configure passive interfaces where appropriate (including loopback interfaces).

4. Configure R1 as an ASBR that advertises a default route in to the OSPF domain.

5. Check the routing tables of R2, R3, and R4.  What default route(s) were added?

## 2. Topology 

<img width="664" height="318" alt="Captura de Pantalla 2026-01-18 a la(s) 13 18 20" src="https://github.com/user-attachments/assets/a812a131-0b54-42c9-b8d8-1b24433ae8f2" />

## 3. Devices and Interfaces 

<img width="834" height="559" alt="Captura de Pantalla 2026-01-18 a la(s) 13 19 44" src="https://github.com/user-attachments/assets/02352479-b7d3-4c23-99c9-2197bffa893e" />

## 4. Configuration

### 4.1 R1


Router(config)#hostname R1

R1(config)#router ospf 1 

R1(config-router)#network 10.0.12.0 255.255.255.252 area 0

R1(config-router)#network 10.0.13.0 255.255.255.252 area 0

R1(config-router)#network 1.1.1.1 255.255.255.255 area 0

R1(config-router)#passive-interface l0

R1(config)#ip route 0.0.0.0 0.0.0.0 203.0.113.2

R1(config)#router ospf 1

R1(config-router)#default-information originate

### 4.2 R2

Router(config)#hostname R2

R2(config)#router ospf 1

R2(config-router)#network 10.0.12.0 255.255.255.252 area 0

R2(config-router)#network 10.0.24.0 255.255.255.252 area 0

R2(config-router)#network 2.2.2.2 255.255.255.255 area 0

R2(config-router)#passive-interface l0

### 4.3 R4

Router(config)#hostname R4

R4(config)#router ospf 1

R4(config-router)#network 192.168.4.0 255.255.255.0 area 0

R4(config-router)#network 10.0.24.0 255.255.255.252 area 0

R4(config-router)#network 10.0.34.0 255.255.255.252 area 0

R4(config-router)#network 4.4.4.4 255.255.255.255 area 0

R4(config-router)#passive-interface g0/0

R4(config-router)#passive-interface l0

### 4.4 R3

Router(config)#hostname R4

R3(config)#router ospf 1

R3(config-router)#network 10.0.34.0 255.255.255.252 area 0

R3(config-router)#network 10.0.13.0 255.255.255.252 area 0

R3(config-router)#network 3.3.3.3 255.255.255.255 area 0

R3(config-router)#passive-interface l0

### 4.5 PC1

Default-gateway: 192.168.4.254

IP-address/subnet mask: 192.168.4.1 255.255.255.0
















