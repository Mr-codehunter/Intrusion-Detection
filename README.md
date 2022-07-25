# *Intrusion Detection System*

## Intruders
- The most common threat to security is the attack by the intruder. Intruders are often referred to as hackers and are the most harmful factors contributing to the vulnerability of security. 
- Intruders breach the privacy of users and aim at stealing the confidential information of the users.

## Types
- Masquerader
- Misfeasor
- Clandestine User

## Intrusion Detection Platform
![IDP](https://www.threatstack.com/wp-content/uploads/2017/11/intrusion-detection-platform-diagram-caption-1-971x1024.png)

## Functions of Detection System
- Identifies All Attacks
- Helps Reduce Risk Over Time
- Alerts on Anomalous Behavior
- Maintains Compliance and so on.

## Tools for intrusion detection system
- ***CrowdStrike Falcon***

A cloud-based endpoint protection platform that includes threat hunting. It is not a Open Source tool.

- ***Snort***

It is provided by Cisco Systems and free to use, leading network-based intrusion detection system software.

- ***Suricata***

Network-based intrusion detection system software that operates at the application layer for greater visibility.

- ***OSSEC***

Excellent host-based intrusion detection system that is free to use.

- ***Zeek***

Network monitor and network-based intrusion prevention system.

## Difference between Snort and Suricata

Snort|Suricata|
-----|--------|
Snort is single thread.|Suricata is Multithreaded.|
It uses one CPU at a time.|It uses Multiple CPU ar a time.|

## Installation and configuration of Snort

We can install snort on ubuntu22.04LTS using following commands:

***Step 1 update***

```
sudo apt update
```

***Step 2 Install Snort***

```
sudo apt-get install snort -y
```
```
Click Ok for the configuration
```

***Step 3 Go to the snort directory***

```
cd /etc/snort/
ls -l
```
***Step 4 Backup of snort.conf file***

```
sudo cp snort.conf snort.conf.back
ls -l
```
***Step 5 Create a another configuration file***

```
sudo cp snort.conf test1_snort.conf
ls -l
```
```
ipvar HOME_NET any
ipvar HOME_NET <your ip address>
```
Save the file using ctrl+S and CTRL+X 

***Step 6 now check file is configured or not***

```
sudo snort -T -i wlp2s0 -c /etc/snort/test1_snort.conf
```
#### T - use for testing mode

output

```
Snort successfully validated the configuration!
Snort exiting
```
***Step 7 set COnfiguration Rules***

- ICMP detection Rule

```
cd /etc/snort/rules/
ls -l
```
```
sudo nano local.rules
```
paste it

```
alert icmp any any -> $HOME_NET any (msg:"ICMP Test"; sid:1000001; rev:1;)
```
****Step 8 check rule is configured or not***

```
sudo snort -T -i wlp2s0 -c /etc/snort/test1_snort.conf
sudo snort -A console -q -i wlp2s0 -c /etc/snort/test1_snort.conf
```
#### -A - it is used print output in the console.

#### -q - it will shows only limited or related information not shows lot of imformation.

#### -i - it is used for interfaces like- etn0, wlp2s0 etc.

#### -c - it is used to open configuration file.

- FTP Connection Detection Rule
- FTP Connection Failed Rule

## References

- https://www.geeksforgeeks.org/intruders-in-network-security/
- https://www.geeksforgeeks.org/intrusion-detection-system-ids/
- https://www.comparitech.com/net-admin/network-intrusion-detection-tools/
- https://www.comparitech.com/net-admin/snort-cheat-sheet/
- https://cybersecurity.att.com/blogs/security-essentials/open-source-intrusion-detection-tools-a-quick-overview#:~:text=Multi%2DThreaded%20%2D%20Snort%20runs%20with,cpu%2Fcores%20you%20have%20available.


