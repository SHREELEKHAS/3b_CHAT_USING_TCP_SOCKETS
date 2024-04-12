## SHREE LEKHA.S 212223110052

# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.

## PROGRAM
```
client.py

import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)  # Create a TCP/IP socket
s.connect(('localhost', 8000))  # Connect to the server

while True:
    msg = input("Client > ")  # Input message from the client
    s.send(msg.encode())  # Send the message to the server
    if msg.lower() == 'exit':
        break
    print("Server > ", s.recv(1024).decode())  # Receive and print the response from the server

s.close()  # Close the connection


server.py
import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)  # Create a TCP/IP socket
s.bind(('localhost', 8000))  # Bind the socket to the address and port
s.listen(5)  # Listen for incoming connections, with a maximum backlog of 5

print("Server listening on port 8000...")

while True:
    c, addr = s.accept()  # Accept a new connection
    print("Connected to", addr)

    while True:
        client_message = c.recv(1024).decode()  # Receive data from the client
        if not client_message or client_message.lower() == 'exit':  # If no data is received or 'exit' command is received, break the loop
            break
        print("Received message:", client_message)

        c.sendall(client_message.encode())  # Send the received message back to the client

    print("Connection closed.")
    c.close()  # Close the connection



```
## PROGRAM:
![Screenshot 2024-04-12 094655](https://github.com/SHREELEKHAS/3b_CHAT_USING_TCP_SOCKETS/assets/149768910/514b317b-6891-4d38-b6fa-ffbbe8393dcc)



## OUTPUT
![Screenshot 2024-04-12 094620](https://github.com/SHREELEKHAS/3b_CHAT_USING_TCP_SOCKETS/assets/149768910/134e7d62-3514-4fb2-a280-d80c011bdf6b)


## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
