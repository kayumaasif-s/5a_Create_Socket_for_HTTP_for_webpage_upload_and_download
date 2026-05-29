# 5a_Create_Socket_for_HTTP_for_webpage_upload_and_download
## AIM :
To write a PYTHON program for socket for HTTP for web page upload and download
## Algorithm

1.Start the program.
<BR>
2.Get the frame size from the user
<BR>
3.To create the frame based on the user request.
<BR>
4.To send frames to server from the client side.
<BR>
5.If your frames reach the server it will send ACK signal to client otherwise it will send NACK signal to client.
<BR>
6.Stop the program
<BR>
## Program:
```
import socket

def download_file(host, port, filename):
    req = f"GET /{filename} HTTP/1.1\r\nHost: {host}\r\nConnection: close\r\n\r\n"
    
    with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
        s.connect((host, port))
        s.sendall(req.encode())
        response = b""
        while (data := s.recv(4096)):
            response += data

    body = response.split(b"\r\n\r\n", 1)[1]
    out = f"downloaded_{filename}"
    with open(out, "wb") as f:
        f.write(body)

    print(f"Downloaded as {out}")

if __name__ == "__main__":
    download_file("127.0.0.1", 8080, "example.txt")
```
## OUTPUT:
<img width="864" height="165" alt="WhatsApp Image 2026-05-29 at 1 16 55 PM" src="https://github.com/user-attachments/assets/062ec4c3-ea1a-460f-8154-e466591be9d0"/>
<img width="1238" height="178" alt="WhatsApp Image 2026-05-29 at 1 17 07 PM" src="https://github.com/user-attachments/assets/17b116e1-513c-4691-8bc7-61e7d9fd18b9"/>

## Result
Thus the socket for HTTP for web page upload and download created and Executed
