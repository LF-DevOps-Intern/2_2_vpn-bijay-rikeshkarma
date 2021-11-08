# Research on IDS/ IPS
*Intrusion detection systems* (IDS) and *intrusion prevention systems* (IPS) constantly watch your network, identifying possible incidents and logging information about them, stopping the incidents, and reporting them to security administrators. In addition, some networks use IDS/IPS for identifying problems with security policies and deterring individuals from violating security policies. IDS/IPS have become a necessary addition to the security infrastructure of most organizations, precisely because they can stop attackers while they are gathering information about your network.  
There are many applications that provide IDS/IPS service and one of them is **Suricata**. 
## Suricata
Suricata is the leading independent open source threat detection engine. By combining intrusion detection (IDS), intrusion prevention (IPS), network security monitoring (NSM) and PCAP processing, Suricata can quickly identify, stop, and assess the most sophisticated attacks.

- Let's first install EPEL repositories using the following command:
  - `yum install epel-release`
- After installing epl-release check for these additional packages and install them if not available on your system: `gcc flex  bison zlib-devel  libdnet-devel libpcap-devel pcre-devel  et-devel tar make libnetfilter_queue-devel lua-devel PyYAML libmaxminddb-devel rustc cargo lz4-devel  libyaml-devel file-devel  jansson-devel nss-devel libcap-ng-devel`
- Install **Suricata** using:
  - `yum install suricata`
- Now we need to update the rules to get the Emerging Threats Open ruleset. As Suricata does not ship with rules by default we run the follwoing command:
  - `suricata-update`
- Configuring the network interface for suricata from the file `/etc/sysconfig/suricata` by editing the last line to:
  - `OPTIONS="-i enp0s3 --user suricata"`
  - [snapshot]()
- Starting the Suricata by using this command in the terminal:
  - `systemctl start suricata`
  - we can check the status to verify by:
    - `systemctl status suricata`
    - [snapshot]()
- Now lets add new sample rules, for this we navigate to `/usr/share/suricate/rules/` and nano the `test.rules` file in the directory.
  - Add the following line to the `test.rules` file:
    - `alert http any any -> any any (msg:"Do not read gossip during work"; content:"Scarlett"; nocase; classtype:policy-violation; sid:1; rev:1;)`
- Now we need to add the rules name in `/usr/share/suricata/rules/suricata.yaml`
  - append the following line under the rule-files:
    - `usr/share/suricata/rules/test.rules`
- Lastly we can see the events taking place on the system by tailing the suricata alert logs on suricata host by:
  - `tail -f /var/log/suricata/fast.log`  
  - [snapshot]()