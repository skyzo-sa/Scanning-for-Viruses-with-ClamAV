# Linux Lab – Scanning for Viruses with ClamAV 
## Objective

The objective of this script is to block incoming network traffic from a list of specified IP addresses using the iptables firewall in Linux. It automates the process of applying IP-based traffic restrictions for network security purposes.

### Job Skills Learned

- Linux System Administration
- Managing firewall rules using iptables.
- Bash Shell Scripting
- Using loops and conditional commands.
- Network Security and Access Control
- Automation and Efficiency


### Tools Used

- Linux Terminal Command Line Interface (CLI)
- Bash Shell
- iptables (Firewall)
- Networking Commands: ping, ifconfig
- VMware Tools: Linux VM

*Ref: Diagram:



### STEPS


# installing clamav
`sudo apt install && sudo apt install clamav clamav-daemon`
![image](https://github.com/user-attachments/assets/0112d559-0646-41bb-a5db-5a854ae6caa7)
![image](https://github.com/user-attachments/assets/b6f53824-7acd-4468-898e-1ddf0fb341da)
 
 
 
# checking the status
`systemctl status clamav-freshclam`
![image](https://github.com/user-attachments/assets/701f07dd-0af8-419c-b0d5-e0566c39a820)
 
`systemctl status clamav-daemon`
![image](https://github.com/user-attachments/assets/eb1935ac-72f0-4609-8fe2-6858f12dfcd0)
 
 
# starting the clamav daemon
`systemctl start clamav-daemon`
![image](https://github.com/user-attachments/assets/fd6ee0cf-cffb-4bf9-bf43-bc3fee3306f5)
 
 
# enabling the daemon to start and boot
`systemctl enable clamav-daemon`
![image](https://github.com/user-attachments/assets/9f667c17-cd21-4624-b5df-e2e388004b97)
 
 
# getting a test virus
`wget www.eicar.org/download/eicar.com`
![image](https://github.com/user-attachments/assets/56dd5cb3-edd3-429c-84ab-f64da459d503)
 
 
# scanning a directory using clamdscan
`clamdscan --fdpass /root/`
![image](https://github.com/user-attachments/assets/e7b22e2e-a414-4aca-a1fa-31ccfb8e821f)
  

# moving found viruses to a quarantine directory
`clamdscan --move=/quarantine --fdpass /root`
![image](https://github.com/user-attachments/assets/73413874-bb03-48b8-a305-9bd8ee52d056)
 
## Ensure the quarantine directory exists:
`If /quarantine does not exist, create it first:
sudo mkdir -p /quarantine
sudo chmod 777 /quarantine  # Adjust permissions as needed`
![image](https://github.com/user-attachments/assets/c42c5db8-9ab7-46a2-811d-992e79c063f2)
 

 
# scanning a directory using clamscan
`clamscan --recursive /etc`
![image](https://github.com/user-attachments/assets/6f0210e8-06ca-4c90-9ea8-ea00ac42f1aa)
![image](https://github.com/user-attachments/assets/74294a34-45ab-4dfc-a25a-69caf132d8dd)
![image](https://github.com/user-attachments/assets/702c10bf-5997-4b3a-991d-b8f86f7383e1)
 
 
 
`clamscan --recursive --infected /quarantine`
![image](https://github.com/user-attachments/assets/9571b3c2-e03c-4913-8d52-fa3b3eb117fc)
![image](https://github.com/user-attachments/assets/85350237-c856-409c-8e12-bd1a851dde1e)
 
 

`clamscan --recursive --infected --remove /quarantine/`
![image](https://github.com/user-attachments/assets/42c4f6c2-ac68-4836-9677-e8c100f4ff16)
 
