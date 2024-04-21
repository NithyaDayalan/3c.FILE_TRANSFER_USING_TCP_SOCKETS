# 3c   CREATION FOR FILE TRANSFER USING TCP SOCKETS

## AIM :
To write a python program for creating File Transfer using TCP Sockets Links.
## ALGORITHM :
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM :
### CLIENT :
```
import socket

s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
    while True:
        print('receiving data...')
        data = s.recv(1024)
        print('data=%s' % (data,))
        if not data:
            break
        f.write(data)
print('Successfully got the file')
s.close()
print('connection closed')
```
### SERVER :
```
import socket 

port = 60000 
s = socket.socket() 
host = socket.gethostname() 
s.bind((host, port)) 
s.listen(5) 
print("Server listening...")
while True:
    conn, addr = s.accept() 
    print('Got connection from', addr)
    data = conn.recv(1024)
    print('Server received', repr(data))
    filename='mytext.txt'
    with open(filename, 'rb') as f:
        l = f.read(1024)
        while l:
            conn.send(l)
            print('Sent ', repr(l))
            l = f.read(1024)
    print('Done sending')
    conn.send('Thank you for connecting'.encode())
    conn.close()
```
## OUTPUT :
![image](https://github.com/NithyaDayalan/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/166380061/0f4d0324-5ca0-4bab-97fd-cc30be7490f2)

## RESULT :
Thus, the python program for creating File Transfer using TCP Sockets Links was successfully created and executed.
