# Create certificates files for both server and client to connect to server and export client certificates to the client vm.
- Install easy-rsa first to create certificates using the command:  
  [`yum install easy-rsa`]()
  - making a new directory for easy-rsa to store the certificates, keys:
    - mkdir -p /etc/openvpn/easy-rsa/keys 
      - *p*- make required directories 
    - cp -rf /usr/share/easy-rsa/2.0/* /etc/openvpn/easy-rsa  
      - *r*- copy recursively
      - *f*- force this/ accept
      - [snapshot]()
    - change the variables file in the easy-rsa folder  
      `nano /etc/openvpn/easy-rsa/vars`
      - edit as per requirement
        - [edited file snapshot for example]()
    - now we build the security of our server security certificates and keys. while on the */etc/openvpn/easy-rsa*, we use following commands:
      - `source ./vars`
        - to build our certificate of authority
      - `./clean-all`
        - clean if any keys are already existing
      - `/build-ca`
        - signing our server and client's certificates
      - `./build-key-server $( hostname )`
        - add our host name to the script file
      - `./build-dh`
        - building our *diffie-hellman*
        - hashing function to exchange keys securely over the internet or over a network
    - now we copy the server certificates and keys to the openvpn folder using the command:
      - `cd /etc/openvpn/easy-rsa/keys`
      - `cp ca.crt localhost.localdomain.crt localhost.localdomain.key dh2048.pem /etc/openvpn`

## Generating Client Keys
- to build the client keys we navigate to `/etc/openvpn/easy-rsa` and run the command
  - `source ./vars`
  - `./build-key client`
- now change the directory to `keys` folder and verify myclient keys, we should see `myclient.crt myclient.key`.
- to export client certificates to the client vm we can use flash drive, email or SSH/SCP client like Filezilla. 
  - lets send the file via cURL
    - navigate to the `/etc/openvpn/easy-rsa/keys`
    - use the following command:
      - `curl --upload-file ./myclient.crt https://transfer.sh`  