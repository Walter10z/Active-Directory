# Active-Directory

![Draw io](https://github.com/Walter10z/Active-Directory/assets/102203609/bd410c60-a06e-4872-9866-e02df7f42841)

## Introduction

Throughout this project, I gained hands-on experience in setting up a Windows 10 virtual machine, a Windows Server 2022 instance, a Splunk server, and a Kali Linux machine for log collection purposes. Splunk was utilized to analyze the ingested logs, enabling the identification of incidents. This exercise provided valuable insights into both the SOC Analyst's and attacker's perspectives. Tasks involved installing resources, configuring networks, investigating logs, managing users in Active Directory, and executing hacking techniques.

## Technologies being used and other resources

  - VirtualBox
  - Windows 10 VM
  - Windows Server 2022 VM
  - Splunk Ubuntu 22.04 LTS VM
  - Kali Linux VM
  - Sysmon
  - Atomic Red Team
  - Crowbar
## After installing the resources 

I will deploy Sysmon and Splunk on both Windows virtual machines to gather comprehensive logs and facilitate in-depth investigation.


![4  Assign Splunk   Sysmon ADDC01](https://github.com/Walter10z/Active-Directory/assets/102203609/04c477ca-8082-4212-8913-662224ec1bc8)


Afterward, the installation of Active Directory was required for the Windows Server 2022.


![5  Add Active Directory](https://github.com/Walter10z/Active-Directory/assets/102203609/91ba52cf-0fb3-4b83-88b3-107264ff3121)


Following the addition of Active Directory, the next step was to include my Windows 10 VM into the local group I had established within AD.


![6  Connect windows 10 to AD](https://github.com/Walter10z/Active-Directory/assets/102203609/fc462d87-f60b-4dc9-a6f2-1c409baabe67)


Finally, I must install Kali Linux and configure its network settings to enable communication with the other VMs.


![7  Kali Linux Setup Connection](https://github.com/Walter10z/Active-Directory/assets/102203609/f0f04db7-7f26-4b7f-be46-13af4c024802)


## Attacking Tool Crowbar 
In this phase, the installation of Crowbar, a brute-force attack tool utilized by cybersecurity professionals, penetration testers, and malicious actors, was necessary. Upon downloading, I proceeded to unzip the file and configure the tool to execute a limited set of 20 brute-force attacks. 

![8  Kali Linux Crowbar](https://github.com/Walter10z/Active-Directory/assets/102203609/e42eac2d-5f53-4650-a02f-1c4c1b657af9)

After configuring my text file, I proceeded to test its functionality. Windows Server 2022, Windows 10, Splunk, and Kali Linux had to be operational. I conducted the attack on the Windows 10 VM using a user I had created in Active Directory, and then gathered the resulting logs in Splunk for investigation. 

![9  Brute Force in Jenny Smith](https://github.com/Walter10z/Active-Directory/assets/102203609/28e4e5ce-e5b4-4680-8f48-371fc8b47ffb)

## Investigating with Splunk
I delved into the logs to pinpoint the source of the brute-force attack. Using the search query index=endpoint jsmith EventCode=4625 in the search bar, I aimed to identify the failed logon attempts, helping to uncover the origin of the malicious attacker.

![10  Splunk Eventcode 4625](https://github.com/Walter10z/Active-Directory/assets/102203609/01370be4-5742-488b-86cd-c42db6bccc9d)

Next, I aimed to check for any successful logon attempts. I entered the following query into the search bar: index=endpoint, jsmith EventCode=4624.

![11  Splunk EventCode 4624](https://github.com/Walter10z/Active-Directory/assets/102203609/5b2dd180-f988-40f4-93bd-ac7c205a8950)

During the investigation, the attacker successfully executed a brute-force attack on the Windows 10 VM, gaining access via an RDP session. Analysis of the logs in Splunk revealed the initial stages of the attack, providing valuable IOCs for further in-depth investigation. This information will enable us to thoroughly examine the incident and devise an appropriate solution or determine if escalation is necessary.


## Atomic Red Team
Atomic Red Team is a framework designed to help organizations test their defenses against cybersecurity threats. Developed by Red Canary, Atomic Red Team provides a library of small, modular, and standardized test procedures, known as "atomic tests," which mimic the tactics, techniques, and procedures (TTPs) used by real attackers.

Installed Atomic Red Team in the Windows 10 machine to test it out 2 attacks. 

![12  Atomic Red Team Install](https://github.com/Walter10z/Active-Directory/assets/102203609/9004c14c-117a-4a9a-a3c7-167e613dcaaf)


![13  Atomic Test T1136 001](https://github.com/Walter10z/Active-Directory/assets/102203609/305c3816-b4e6-4d6c-b2f9-a4766ecfdafb)


![14  Atomic Test T1059 001](https://github.com/Walter10z/Active-Directory/assets/102203609/4f41742a-4f7d-4ac2-a8cc-caf2ffff918c)

## Lessons Learned

In this lab project, I gained a diverse skill set encompassing several tasks such as setting up multiple VMs, configuring network cards for each VM, assigning IP addresses, installing Active Directory, creating user accounts, executing a brute-force attack, and analyzing logs. The lab provided a visual understanding of both blue team and red team techniques. 


