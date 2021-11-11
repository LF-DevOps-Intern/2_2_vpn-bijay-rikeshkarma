# VPN and IDS/ IPS Assignment

- **Setup a VPN server in one vm. You can use openvpn for this purpose.**
  - [Question no. 1 (Answer)](https://github.com/LF-DevOps-Intern/2_2_vpn-bijay-rikeshkarma/tree/main/1)
    - **You should have two network interface one for wan and another for lan. You should setup vpn server which listens on wan interface and provides lan interfaces subnets ip address to the client which connects using openvpn client.**
      - [Question no. 1(a) (Answer)](https://github.com/LF-DevOps-Intern/2_2_vpn-bijay-rikeshkarma/tree/main/1/a)
    - **You should create certificates files for both server and client to connect to server and export client certificates to the client vm.**
      - [Question no. 1(b) (Answer)](https://github.com/LF-DevOps-Intern/2_2_vpn-bijay-rikeshkarma/tree/main/1/b)
- **Create another vm with installing openvpn client and you should create openvpn client connect file(with extension .ovpn) providing the certificates. You should be able to connect tothe vpn server and get ip address from lan subnet that you assigned in first vm.**
  - [Question no. 2 (Answer)](https://github.com/LF-DevOps-Intern/2_2_vpn-bijay-rikeshkarma/tree/main/2)
- **Research on IDS/IPS. There are many applications that provide IDS/IPS service. Find one of the opensource service and install it on the VM1 you created previously. Try to set up IDS which block some of the known vulnerabilities signature.**
  - [Question no. 3 (Answer)](https://github.com/LF-DevOps-Intern/2_2_vpn-bijay-rikeshkarma/tree/main/3)
