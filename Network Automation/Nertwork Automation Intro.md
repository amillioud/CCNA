# Network Automation Introduction 

## What is network automation?
Automating repetitive network tasks using scripts or tools (e.g., Python, Ansible, Netmiko).

Traditionally, engineers manage devices one at a time by connecting to their CLI via SSH or Telnet. This model has some downsides when configuring large networks:

- Typos and other mistakes are common
- Time consuming and inefficient
- Difficult to standardize configurations

Network automation provides many benefits:

- Human error, such as typos, is reduced
- Networks become more scalable; allowing quicker deployments and network-wide troubleshooting
- *network-wide* policy compliance can be assured
- Efficiency reduces *operating expenses*

There are varios tools and methods than can be used to automate tasks in the network: SDN (Software defined networking), Ansible, Puppet, Python scripts, etc.

<img width="128" height="158" alt="image" src="https://github.com/user-attachments/assets/40a41d3b-1bd4-4b4e-91bb-38c2b4ec0134" />


<img width="285" height="100" alt="image" src="https://github.com/user-attachments/assets/d48dfb1d-49dd-4d11-ae7f-4b8b9bb72303" />


<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/990eb809-48d6-445d-8849-9646e906b0ec" />


## Logical planes

Functional layers that separate different types of tasks or responsabilities within a network device or architecture.

### Data Plane (Forwarding Plane)

Moves data packets (frames, packets) from one interface to another. Usually fast processes at the hardware level; using ASIC (application-specific integrated circuit).

- A router receives a message, looks for the most specific matching route in its routing table, and forwards it out of the appropiate interface to the next hop. Encapsulation and de-encapsulation of Layer 2 header. 

<img width="400" height="200" alt="image" src="https://github.com/user-attachments/assets/2f0cea85-1e38-4596-9a37-b0985a40b9e6" />

- A switch receives a message, looks at its destination MAC address, and it forwards it out of the appropiate interface (or floods it). Adding or removing 802.1q tags.

<img width="480" height="131" alt="image" src="https://github.com/user-attachments/assets/1558e418-0e9d-4e8e-8990-4fb4e6b7354a" />

- *Network address translation* (changing the source/destination ip addresses before forwarding).
- Deciding to block or forward messages based on *ACLs*, *port security* and other QoS parameters.

### Control Plane 

The way a device makes its forwarding decisions: routing table, MAC address table, ARP table, STP etc.

- The control plance controls what the data plane does, for example by building the routers´s routing table
- Performs overhead work

### Management Plane

Performs overhead work. However, it doesn´t directly affect the forwarding of messages in the data plane.

The management plane consists of protocols that are used to manage devices:

- *SSH/Telnet* used to connect to the CLI of a device
- *Syslog* used to keep logs of events that occur on the device
- *SNMP* used to monitor the operations of the device
- *NTP* used to maintain accurate time on the device

The operations of the management and control plane are usually managed by the *CPU*. Howeber, this is not desirable for data plane operations because CPU processing is "slow".
Instead, a specialized hardware ASIC (applicaation-specific integrated circuit) is used. ASICs are chips built for specific purposes. Using a *switch* as an example:

- When a frame is received, the ASIC (not the CPU) is responsible for the switching logic. The MAC addressable is stored in a kind of memory called *TCAM* (ternary content-addressable memory).
- The ASIC feeds the destination MAC address of the frame into the TCAM, which returns the matching MAC address table 










