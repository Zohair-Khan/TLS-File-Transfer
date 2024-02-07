# TLS File Transfer Application
This is a secure file transfer application implementing TLS encryption to transfer files from a client to a host, written in Python.

## Included Files:
- `server/`
    - `TLSFileXferServer.py` : Server side of an secure file transfer application implementing TLS/TCP.          
        - Handles files sent from clients and saves them to the working directory.
        - Implements TLS encryption over a TCP connection.
- `client/`
    - `TLSFileXferClient.py` : Client side of an secure file transfer application implementing TLS/TCP.        
        - Sends files to a directed server.
        - Implements TLS encryption over a TCP connection.
    - `sample.txt`
    - `mountain-lake.jpg`      


## Requirements:
- Python installed
- OpenSSL installed

## Generating TLS Keys and Certificate:
1. Run the following command to generate a private key (`key.pem`) and a public certificate (`cert.pem`):

    ```
    openssl req -newkey rsa:2048 -new -nodes -x509 -days 3650 -keyout key.pem -out cert.pem
    ```

2. Fill in the required information:
    - 2 Letter Country Code
    - State or Province Name
    - City Name
    - Organization Name
    - Organizational Unit Name
    - Host Name
    - Email Address
3. In the directory where you ran the command, you should find your private key (`key.pem`) and your public certificate (`cert.pem`).

## Running the TLSFileXfer server:
1. Place your generated `key.pem` and `cert.pem` files in the same directory as `TLSFileXferServer.py`.
2. Run `TLSFileXferServer.py`. The program requires command-line arguments that specify the file transfer server's IP address/hostname and port. The port number must be between 1024 and 65535. The command format is:

    ```
    TLSFileXferServer.py <server_host> <server_port>
    ```

    For instance: 

    ```
    python3 TLSFileXferServer.py localhost 9999
    ```

3. Files received from clients connected to the server will appear in the same directory as `TLSFileXferServer.py`.

## Running the NetFileXfer client:
1. Run `TLSFileXferClient.py`. The program requires command-line arguments that specify the file transfer server's IP address/hostname and port. The port number must be between 1024 and 65535. The command format is:

    ```
    TLSFileXferClient.py <server_host> <server_port> <file_path>
    ```

    For instance: 

    ```
    python3 TLSFileXferClient.py localhost 9999 sample.txt
    ```

    where `sample.txt` is in the same directory as `NetFileXferClient.py`.

2. The client will confirm that it connected to the server, send the file to the server, then disconnect from the server.