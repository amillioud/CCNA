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

### 5. R1

Router>enable
Router#configure terminal
Router(config)#hostname R1
R1(config)#interface range g3/0,g0/0,f1/0
R1(config-if-range)#no shutdown
R1(config-if-range)#interface g3/0
R1(config-if)#ip address 203.0.113.1 255.255.255.252
R1(config-if)#interface g0/0
R1(config-if)#ip address 10.0.12.1 255.255.255.252
R1(config-if)#interface f1/0
R1(config-if)#ip address 10.0.13.1 255.255.255.252



















