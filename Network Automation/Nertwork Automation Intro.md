# Network Automation Introductin 

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

- A router receives a message, looks for the most specific matching route in its routing table, and forwards it out of the appropiate interface to the next hop. 

<img width="400" height="200" alt="image" src="https://github.com/user-attachments/assets/2f0cea85-1e38-4596-9a37-b0985a40b9e6" />
















