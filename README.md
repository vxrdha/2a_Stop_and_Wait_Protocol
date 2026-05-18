# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
## SERVER:
import socket

# Create socket
s = socket.socket()

# Bind host and port
s.bind(('localhost', 8000))

# Listen for client connection
s.listen(5)

print("Server is waiting for connection...")

# Accept connection
c, addr = s.accept()

print("Connected with", addr)

while True:
    # Receive data from client
    data = c.recv(1024).decode()

    if not data:
        break

    print("Client:", data)

    # Send acknowledgement
    c.send("Acknowledgement Received".encode())

# Close connection
c.close()
s.close()

## CLIENT:
import socket

# Create socket
s = socket.socket()

# Connect to server
s.connect(('localhost', 8000))

print("Connected to server")

while True:
    # Input from user
    msg = input("Enter a data: ")

    # Send data to server
    s.send(msg.encode())

    # Receive acknowledgement
    ack = s.recv(1024).decode()

    print("Server:", ack)

    # Exit condition
    if msg.lower() == "exit":
        break

# Close socket
s.close()

## OUTPUT
<img width="532" height="292" alt="Screenshot 2026-05-18 132009" src="https://github.com/user-attachments/assets/5c7a31b1-8aed-4ae7-aa32-ab1567a07ba6" />
<img width="534" height="287" alt="Screenshot 2026-05-18 131948" src="https://github.com/user-attachments/assets/4ac7d23b-880f-4d4b-b9be-5145f19a96d8" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
