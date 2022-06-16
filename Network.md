# Network Forensic Analysis Report

_TODO_ Complete this report as you complete the Network Activity on Day 3 of class.

## Time Thieves 
You must inspect your traffic capture to answer the following questions:

1. What is the domain name of the users' custom site?
    ***frank-n-ted-dc.frank-n-ted.com***
    ![](Images/1.png)
2. What is the IP address of the Domain Controller (DC) of the AD network?
    ***10.6.12.12***
     ![](Images/2.png)
3. What is the name of the malware downloaded to the 10.6.12.203 machine?
   - Once you have found the file, export it to your Kali machine's desktop.
   ***june11.dll***
    ![](Images/3.png)
4. Upload the file to [VirusTotal.com](https://www.virustotal.com/gui/). 
5. What kind of malware is this classified as?
   ***Trojan***
    ![](Images/4.png)
---

## Vulnerable Windows Machine

1. Find the following information about the infected Windows machine:
    - Host name: ***Rotterdam-PC***
    - IP address: ***172.16.4.205***
    - MAC address: ***00:59:07:b0:63:a4***
    ![](Images/2.1.png)
2. What is the username of the Windows user whose computer is infected?
    - ***matthijs.devries***
    ![](Images/2.2.png)
3. What are the IP addresses used in the actual infection traffic?
    - ***172.16.4.205 was the machine that was being infected***
    - ***185.243.115.84 sent many empty gif to the infected machine***
    - ***166.62.111.64 was also sending high volumes of packets during the capture***
    ![](Images/2.3.png)
    ![](Images/2.3.2.png)
4. As a bonus, retrieve the desktop background of the Windows host.
    ![](Images/4.png)
