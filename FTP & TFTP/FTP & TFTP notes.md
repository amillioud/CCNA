# FTP & TFTP

## FTP - File Transfer Protocol

### - What it is:
   A standard network protocol used to transfer files between a client and a server over a network (like the internet).

### - How it works:

- Uses TCP (Transmission Control Protocol) for reliable communication.

- Requires a username and password for access (though anonymous FTP also exists).

- Can be used via a command line (ftp command), web browser, or FTP client like FileZilla.

### Common use:
Uploading website files to a web server, downloading software or backups from a remote machine.

### Ports:

- Control connection: Port 21

- Data connection: Port 20 (in active mode)

## TFTP - Trivial File Transfer Protocol

### What it is: 

- A simpler, lightweight version of FTP, used for basic file transfers.

### How it works:

- Uses UDP (User Datagram Protocol) instead of TCP, so it's faster but less reliable.

- Does not require authentication – no username/password.

- Mostly used for transferring small files like firmware or configuration files.

### Common use:

Bootstrapping devices (e.g., routers or switches)

Transferring firmware to network devices

Network PXE (Preboot Execution Environment) booting

Port: Uses Port 69 (only used in the very first message of the client to the server; the server chooses a random source port for the following messages)

## FTP vs TFTP

<img width="782" alt="Captura de Pantalla 2025-04-13 a la(s) 18 27 32" src="https://github.com/user-attachments/assets/8fdc3cf4-b019-4746-b48e-0d0a18c9605f" />






