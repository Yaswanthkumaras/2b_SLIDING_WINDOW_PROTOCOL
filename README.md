# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
### Client :
```python
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
    while(i<len(l)):
            st+=s
            c.send(str(l[i:st]).encode())
            ack=c.recv(1024).decode()
            if ack:
                print(ack)
                i+=s
```
### Server :
```python
import socket

s = socket.socket()
s.connect(('localhost', 8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())
```
## OUPUT
### Client :
![Screenshot 2024-02-28 160755](https://github.com/Raja8334/2b_SLIDING_WINDOW_PROTOCOL/assets/120719634/b101347c-68f2-44fd-8557-933a0832ea38)
### Server :
![Screenshot 2024-02-28 160803](https://github.com/Raja8334/2b_SLIDING_WINDOW_PROTOCOL/assets/120719634/00863c6e-d29d-441e-88a6-00ff9f06d55c)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
