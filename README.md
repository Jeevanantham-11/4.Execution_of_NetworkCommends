# 4.Execution_of_NetworkCommands
## AIM :
Use of Network commands in Real Time environment
## Software :
Command Prompt And Network Protocol Analyzer
## Procedure: 
To do this EXPERIMENT- follows these steps:

Students have to understand basic networking commands such as:
```
•tcpdump
```
```
•netstat
```
```
•ifconfig
```
```
•nslookup
```
```
•traceroute
```

Additionally, capture ping and traceroute PDUs using a network protocol analyzer.

This includes all commands related to network configuration, such as:

• Switching to privileged mode and normal mode

• Configuring router interfaces

• Saving the configuration to flash memory or permanent memory

This commands includes

• Configuring the Router commands

• General Commands to configure network

• Privileged Mode commands of a router 

• Router Processes & Statistics

• IP Commands

• Other IP Commands e.g. show ip route etc.
## Algorithm
Algorithm: Server Ping Program

1. Start the program.
2. Import socket and pythonping modules.
3. Create a socket.
4. Bind the socket to localhost and port 8000.
5. Listen for client connections.
6. Accept the client connection.
7. Receive hostname from the client.
8. If hostname is "exit", terminate the connection.
9. Ping the received hostname.
10. Send the ping result back to the client.
11. Close the connection.
12. Stop the program.

Algorithm: Client Ping Request Program

1. Start the program.
2. Import socket module.
3. Create a socket.
4. Connect to the server at localhost port 8000.
5. Ask the user to enter a hostname or IP address.
6. Send the hostname to the server.
7. Receive the ping result from the server.
8. Display the result.
9. If user enters "exit", close the connection.
10. Stop the program.

## Program
```
Server.py
```
```
import socket
from pythonping import ping

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("Server listening on port 8000...")
c, addr = s.accept()
print(f"Connection from {addr}")

while True:
    try:
        hostname = c.recv(1024).decode('utf-8')
        if not hostname or hostname.lower() == 'exit':
            print("Client disconnected.")
            break
        response = ping(hostname, verbose=False, count=4)
        c.send(str(response).encode('utf-8'))
    except Exception as e:
        c.send(f"Ping failed: {e}".encode('utf-8'))

c.close()
```
```
Client.py
```
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    ip = input("Enter the website you want to ping (or type 'exit' to quit): ")
    s.send(ip.encode('utf-8'))
    if ip.lower() == 'exit':
        break
    print(s.recv(4096).decode('utf-8'))

s.close()
```
## Output
## Server

![alt text](<Screenshot 2026-03-10 211608.png>)

## Client

![alt text](<Screenshot 2026-03-10 211554.png>)

```
traceroute
```
![alt text](<Screenshot 2026-03-12 112925.png>)

```
ipconfig
```
![alt text](<Screenshot 2026-03-12 112606.png>)
```
nslookup
```
![alt text](<Screenshot 2026-03-12 112736.png>)

```
netstat
```
![alt text](<Screenshot 2026-03-12 112520-1.png>)
## Result
Thus Execution of Network commands Performed 
