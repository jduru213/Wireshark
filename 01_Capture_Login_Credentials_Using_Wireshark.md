## Capture Login Credentials Using Wireshark & Netsniff-ng in Kali Linux
Welcome to a hands-on exploration of capturing login credentials using Wireshark and Netsniff-ng  in Kali Linux! In this lab project, I will guide you through the step-by-step process of scanning, filtering, and capturing credentials within my network.

## Getting Started 


- 
- Download https://www.kali.org/

## Step 1: Initiation of Netsniff-ng 

What is a .pcap file and whay are we creating one?

The binary file format known as ".pcap" (Packet Capture) is used to store network packet data that is obtained during network traffic analysis.

The reason in which we are creating one is soley due to the fact that the .pcap file facilitates replay and simulation for testing, troubleshooting network issues, and serves educational purposes by providing real-world scenarios for learning about network security.  

Here is the command to intinitialize netsniff
 ```bash
netsniff-ng --in eth0 --out <yourfilename>.pcap
   ```
![image](https://github.com/jduru213/Wireshark-HomeLabs/assets/112328773/7f94ff87-ceb0-476a-96fc-c1e6283ded1f)

## Step 2: Web navigation to Vulnweb.com 

What is Vulweb.com & why are we using it?

Vulweb.com is an educational platform that helps users learn about web application security and vulnerabilities. Its goal is to provide individuals with practical experience and knowledge in the field of web application security allowing users to enhance their abilities in discovering and exploiting

- Search Vulnweb.com and click on the Acuforum URL
- [image]

## Step 3: Login 
- Once you click on the Acuforum URL, you should be navigated to a page. At the top of the page click the "login" tab
[image]

- Once you get to the login page, type in any username or password of your choice
  P.S If it says invalid login that's fine, we are just trying to capture the credentials  
[image]

## Step 4: Configuring Wireshark and open .pcap file 
-  Now, stop capturing packets by clicking Ctrl + C and see how many packets you generated
  [image]
-  Go back to your Kali linux terminal run the "ls" command and find your .pcap file
  [image]
-  Run Wireshark by typing in "Wireshark" in your kali terminal  
  [image]
- Next, when wireshark is open Go to File → Open → \home\kali directory → <yourfilenaem>.pcap file → Open
  [image]
- Now you have a full representation, of all the packets
  [image]

## Step 5: Filtering Packets for credentials
To find the password and username that were intercepted, we must filter HTTP packets by typing “http”. The packet we are searching for is a POST request. A POST request is an HTTP method used for sending data to a server for the purpose of creating or updating a resource on said server

P.S Most websites will not trafer data throgh http, this is solely for practice purposes to learn how to filter and analyze your network 
