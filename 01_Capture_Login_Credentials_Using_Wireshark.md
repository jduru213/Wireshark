## Capture Login Credentials Using Wireshark & Netsniff-ng in Kali Linux
Welcome to a hands-on exploration of capturing login credentials using Wireshark and Netsniff-ng  in Kali Linux! In this lab project, I will guide you through the step-by-step process of scanning, filtering, and capturing credentials within my network.


## Step 1: Initiation of Netsniff-ng 

### What is a .pcap file and why are we creating one?

The binary file format known as ".pcap" (Packet Capture) stores network packet data obtained during network traffic analysis.

We are creating one solely because the .pcap file facilitates replay and simulation for testing and troubleshooting network issues, and serves educational purposes by providing real-world scenarios for learning about network security.  

# Here is the command to initialize netsniff
 ```bash
netsniff-ng --in eth0 --out <yourfilename>.pcap
   ```
![image](https://github.com/jduru213/Wireshark-HomeLabs/assets/112328773/7f94ff87-ceb0-476a-96fc-c1e6283ded1f)
![image](https://github.com/jduru213/Wireshark-HomeLabs/assets/112328773/bd91d307-51d0-4fc2-bbf6-da252dfd2d2f)


## Step 2: Web navigation to Vulnweb.com 

### What is Vulweb.com & why are we using it?

Vulweb.com is an educational platform that helps users learn about web application security and vulnerabilities. Its goal is to provide individuals with practical experience and knowledge in the field of web application security allowing users to enhance their abilities in discovering and exploiting

While Netsniff is running in the background, open your web browser on Kali: 

- Search Vulnweb.com and click on the Acuforum URL
  
![image](https://github.com/jduru213/Wireshark-HomeLabs/assets/112328773/7f3d9731-f583-4ab6-ae89-295708fbe294)


## Step 3: Login 
- Once you click on the Acuforum URL, you should be navigated to a page. At the top of the page click the "login" tab
  
![image](https://github.com/jduru213/Wireshark-HomeLabs/assets/112328773/8cb33f77-6097-44d9-b3bf-fe8ef2b16f86)
![image](https://github.com/jduru213/Wireshark-HomeLabs/assets/112328773/0ade0a5b-64b3-47ac-bf14-b011832d26c3)

- Once you get to the login page, type in any username or password of your choice
  P.S If it says invalid login that's fine, we are just trying to capture the credentials
  
![image](https://github.com/jduru213/Wireshark-HomeLabs/assets/112328773/8570d6b7-80e6-4903-8839-6932c67cb5e2)


## Step 4: Configuring Wireshark and open .pcap file 
-  Now, stop capturing packets by clicking Ctrl + C and see how many packets you generated

-  Generated 2704 packets
  
  ![image](https://github.com/jduru213/Wireshark-HomeLabs/assets/112328773/96051a91-eac6-4fbe-a03b-d546e0589092)

-  Go back to your Kali linux terminal run the "ls" command and find your .pcap file
  
 ![image](https://github.com/jduru213/Wireshark-HomeLabs/assets/112328773/217fa474-9e23-4d75-afb7-cfc04a936678)


-  Run Wireshark by typing in "Wireshark" in your Kali terminal:
  
  ![image](https://github.com/jduru213/Wireshark-HomeLabs/assets/112328773/e5a3b83b-a0ca-4500-919d-5f09121ab8e2)
  ![image](https://github.com/jduru213/Wireshark-HomeLabs/assets/112328773/9d56626f-98b8-4a73-8168-7a29916d187d)


- Next, when wireshark is open Go to File → Open → \home\kali directory → <yourfilenaem>.pcap file → Open or simply type in your file name in the "Files of type" search bar 
  ![image](https://github.com/jduru213/Wireshark-HomeLabs/assets/112328773/90479ceb-203c-4729-aae4-76b5c11b40ab)

- Now you have a full representation, of all the packets
![image](https://github.com/jduru213/Wireshark-HomeLabs/assets/112328773/f9e3d198-6185-43d3-b415-d83278e87212)


## Step 5: Filtering Packets for credentials
We must filter HTTP packets by typing “HTTP” to find the intercepted password and username. The packet we are searching for is a POST request. A POST request is an HTTP method used for sending data to a server to create or update a resource on said server

P.S Most websites will not transfer data through HTTP since it is unencrypted and therefore insecure, this is solely for practice purposes to learn how to filter and analyze your network 

- First, let's type in "HTTP" in the search bar to filter out the network protocol
  ![image](https://github.com/jduru213/Wireshark-HomeLabs/assets/112328773/6662a79a-9696-4e46-bb66-619fd3dd1730)
  
- Now, double-click the packet to open 
  
  ![image](https://github.com/jduru213/Wireshark-HomeLabs/assets/112328773/3b40e100-b4c9-45fa-b818-06ee75a2ae0a)
  
- Lastly, scroll to the very bottom where it says HTML form URL encoded and find the form item saying "tfUName" & "tfUPass"  

![image](https://github.com/jduru213/Wireshark-HomeLabs/assets/112328773/dc3f56f2-6dc0-4c5f-93d3-39157c7e353c)

To wrap it up, this project illuminates the vulnerabilities associated with unprotected communication routes, which I actively conducted. Through my investigation into the collection of login credentials in Kali Linux, I have identified possible hazards utilizing programs like Wireshark and NetSNIFF. The lesson highlights how critical it is to put strong cybersecurity safeguards in place as soon as possible to protect sensitive data, including encryption and close monitoring.
