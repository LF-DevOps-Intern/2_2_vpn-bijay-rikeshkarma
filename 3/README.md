# Research on IDS/ IPS
*Intrusion detection systems* (IDS) and *intrusion prevention systems* (IPS) constantly watch your network, identifying possible incidents and logging information about them, stopping the incidents, and reporting them to security administrators. In addition, some networks use IDS/IPS for identifying problems with security policies and deterring individuals from violating security policies. IDS/IPS have become a necessary addition to the security infrastructure of most organizations, precisely because they can stop attackers while they are gathering information about your network.  
There are many applications that provide IDS/IPS service and one of them is **Snort**. 
## Snort
Snort is one of the best known and widely used *network intrusion detection systems* (NIDS). It has been called one of the *most important open-source projects of all time*.
Snort is a free open source network intrusion detection system and intrusion prevention system created by Sourcefire. Snort is now developed by Cisco, which purchased Sourcefire in 2013.

- Let's first install EPEL repositories using the following command:
  - `yum install epel-release`
- After installing epl-release check for these additional packages and install them if not available on your system: `gcc flex  bison zlib  libdnet-devel`