# Create a openvpn client connect configuration file used to connect to the server

- created a text file myclient.ovpn using `touch myclient.ovpn` in the same directory as the files received from the server machine/ VM.
- add the following lines which helps to connect to the server and this also provides the certificates:  
    _client  
    dev tun  
    proto udp  
    remote 192.168.254.131 1194 udp   
    topology subnet
    pull	
    ca ca.crt  
    cert myclient.crt  
    key myclient.key  
    user nobody  
    group nogroup
_
- On the server, first VM(CentOS) enable to forward packets through its network interface
  - use sysctl to allow IP packet forwarding. Add the following line to the _sysctl.conf_ file
    - `nano /etc/sysctl.conf`
      -  *net.ipv4.ip_forward = 1*
    - `sysctl -p` 
- enable OpenVPN pam authentication module to add user authentication
  - using the OpenVPN auth-pam module the OpenVPN server can authenticate using the Linux system users. For this we need to create a PAM service file using the following commands:
    - `touch /etc/pam.d/openvpn`
    - `nano /etc/pam.d/openvpn`
  - then we need to add the following two lines to the file:
    - *auth required  pam_unix.so shadow  nodelay*
    - *account required pam_unix.so*
- Now restart the OpenVPN server
  - `systemctl stop openvpn@server.service`
  - `systemctl start openvpn@server.service`
  - `systemctl status openvpn@server.service`

# Install and configure OpenVPN on client's machine/ VM2.
- install openvpn-client on VM2(Ubuntu) using the command:
  - `sudo apt install openvpn`
- connect the VM2 to the server/ VM1 using the command:
  - `sudo openvpn --config client.ovpn`
- After this OpenVPN will be running in the terminal window.