<H1 ALIGN=CENTER> SIMULATION ARP/RARP PROTOCOLS </H1>
<H3> NAME : SHRRUTHILAYA G </H3>
<H3> REGISTER NUMBER : 212221230097 </H3>
<H3>EXPERIMENT NO : 02 C </H3>
<H3>DATE  : 11.05.2024 </H3>

## AIM:
To implement python codes for the simulation of ARP/RARP protocols.
## PROCEDURE:
### CLIENT:
1. Start the program.
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
### SERVER:
1. Start the program.
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.

## PROGRAM:
### CLIENT:
```PYTHON
import socket
s = socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c, addr = s.accept()
address = {"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
    ip = c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
### SERVER:
```PYTHON
import socket
s = socket.socket()
s.connect(('localhost',8000))
while True:
    ip = input("Enter Logical address : ")
    s.send(ip.encode())
    print("MAC Address : ", s.recv(1024).decode())
```
## OUTPUT:
### CLIENT:
![Client](https://github.com/Shrruthilaya-Gangadaran/2c.ARP_RARP_PROTOCOLS/assets/93427705/d2077607-98ba-4731-b796-a1d29874244a)
### SERVER:
![Server](https://github.com/Shrruthilaya-Gangadaran/2c.ARP_RARP_PROTOCOLS/assets/93427705/8543a3f2-f396-4f8d-97f2-c58156cecf9d)
## RESULT:
Thus, simulation of ARP/RARP protocol is done successfully.
