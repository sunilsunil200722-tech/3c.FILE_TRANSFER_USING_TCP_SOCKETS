# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.


## PROGRAM

### server code:
```
import socket

# Create socket
server = socket.socket()

# Bind IP and port
server.bind(("127.0.0.1", 5555))

# Listen for client
server.listen(1)

print("Server waiting for connection...")

# Accept client
client, addr = server.accept()

print("Connected to:", addr)

# Ask filename
filename = input("Enter file name to send: ")

# Open and send file
with open(filename, "rb") as file:
    data = file.read()
    client.send(data)

print("File sent successfully")

# Close connections
client.close()
server.close()
```

### client code:
```
import socket

# Create socket
client = socket.socket()

# Connect to server
client.connect(("127.0.0.1", 5555))

# Save file name
save_name = input("Enter name to save file: ")

# Receive data
data = client.recv(1000000)

# Save file
with open(save_name, "wb") as file:
    file.write(data)

print("File received successfully")

# Close connection
client.close()
```

## OUPUT

## server output:
<img width="1233" height="693" alt="Screenshot 2026-11-18 083258" src="https://github.com/user-attachments/assets/8e1caecc-56fd-488b-9f30-187d4d4e9316" />

## client output:
<img width="1235" height="698" alt="Screenshot 2026-11-18 083337" src="https://github.com/user-attachments/assets/652a9473-c0c0-443d-b3e2-b398098d34ac" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
