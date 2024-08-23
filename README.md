# brittnia11
Cybersecurity Incident Reports

# Table of contents

1. [Cybersecurity incident report network traffic analysis](#one)
2. [Analyze network attacks using Wireshark](#two)
3. [Apply OS hardening techniques](#three)

-------
# Cybersecurity incident report network traffic analysis <a name="one">
# Part 1: Provide a summary of the problem found in the DNS and ICMP traffic log.
The UDP protocol reveals that: That the port is unreachable

This is based on the results of the network analysis, which show that the ICMP echo reply returned the error message: “udp port 53 unreachable.” 

The port noted in the error message is used for: Port 53 is typically associated with DNS protocol communication.

The most likely issue is: The DNS server is unreachable, likely due to a DoS attack against the DNS server.

# Part 2: Explain your analysis of the data and provide at least one cause of the incident.
Time incident occurred: 1:23 PM

Explain how the IT team became aware of the incident: “Several customers of clients reported that they were not able to access the client company website www.yummyrecipesforme.com, and saw the error “destination port unreachable” after waiting for the page to load.”

Explain the actions taken by the IT department to investigate the incident: “It is necessary to inspect network traffic and data to determine network-related issues. We’ll need to load a network analyzer tool, conduct packet sniffing tests using  tcpdump, and attempt to load the webpage again. ”

Note key findings of the IT department's investigation (i.e., details related to the port affected, DNS server, etc.): 
-DNS server is down or traffic to port 53 is blocked by firewall > check firewall settings to see if any recent changes have been made to its configuration(i.e. Block network traffic). IF this is found to be true we may opt to block the port to stop or prevent an attack.

Note a likely cause of the incident:
-Server may be experiencing downtime due to a successful DoS “Denial of service attack” or a misconfig (i.e. firewall) that blocked port 53..

-------
# Analyze network attacks using Wireshark <a name="two">
# Section 1: Identify the type of attack that may have caused this network interruption
One potential explanation for the website’s connection timeout error message is a DoS attack. The logs show that the web server stops responding after it is overloaded with SYN packet requests. This event could be a type of DoS attack called SYN flooding.

# Section 2: Explain how the attack is causing the website malfunction
When the website visitors try to establish a connection with the web server, a three-way handshake occurs using the TCP protocol. The handshake consists of three steps: 

	•	A SYN packet is sent from the source to the destination, requesting to connect.
	•	The destination replies to the source with a SYN-ACK packet to accept the connection request. The destination will reserve resources for the source to connect.
	•	A final ACK packet is sent from the source to the destination acknowledging the permission to connect. 

In the case of a SYN flood attack, a malicious actor will send a large number of SYN packets all at once, which overwhelms the server’s available resources to reserve for the connection. When this happens, there are no server resources left for legitimate TCP connection requests. 

The logs indicate that the web server has become overwhelmed and is unable to process the visitors’ SYN requests. The server is unable to open a new connection to new visitors who receive a connection timeout message.

-------
# Apply OS hardening techniques <a name="three">
# Section 1: Identify the network protocol involved in the incident
The protocol involved in the incident is the Hypertext transfer protocol (HTTP). Since the issue was with accessing the web server for yummyrecipesforme.com, we know that requests to web servers for web pages involve http traffic. 

Also, when we ran tcpdump and accessed the yummyrecipesforme.com website the corresponding tcpdump log file showed the usage of the http protocol when contacting the . The malicious file is observed being transported to the users’ computers using the HTTP protocol at the application layer.

# Section 2: Document the incident
Several customers contacted the website’s helpdesk stating that when they visited the website, they were prompted to download and run a file that contained access to new recipes. Their personal computers have been operating slowly ever since. The website owner tried logging into the web server but noticed they were locked out of their account.

The cybersecurity analyst used a sandbox environment to open the website without impacting the company network. Then, the analyst ran tcpdump to capture the network traffic packets produced by interacting with the website. The analyst was prompted to download a file claiming it would provide access to free recipes, accepted the download and ran it. The browser then redirected the analyst to a fake website (greatrecipesforme.com). 

The cybersecurity analyst inspected the tcpdump log and observed that the browser initially requested the IP address for the yummyrecipesforme.com website. Once the connection with the website was established over the HTTP protocol, the analyst recalled downloading and executing the file. The logs showed a sudden change in network traffic as the browser requested a new IP address for the greatrecipesforme.com URL. The network traffic was then rerouted to the new IP address for the greatrecipesforme.com website. 

The senior cybersecurity professional analyzed the source code for the websites and the downloaded file. The analyst discovered that an attacker had manipulated the website to add code that prompted the users to download a malicious file disguised as a browser update. Since the website owner stated that they had been locked out of their administrator account, the team believes the attacker used a brute force attack to access the account and change the admin password. The execution of the malicious file compromised the end users’ computers. 

# Section 3: Recommend one remediation for brute force attacks
One security measure the team plans to implement to protect against brute force attacks is to disallow previous passwords from being used. Since the vulnerability that lead to this attack was the attacker’s ability to use a default password to log in, it’s important that we prevent any old passwords such as default passwords from being used to reset the password. Another supportive measure is to require more frequent password updates, so in case any unauthorized person becomes aware of the password, they are less likely to be able to use that password if the password is updated sooner than later. Finally, another helpful solution is to implement two-factor authentication (2FA). 

2FA requires authentication via a password and also by confirming a one-time passcode (OTP) sent to either their email or phone. Once the user confirms their identity through their login credentials and the OTP, they will gain access to the system. Any malicious actor that attempts a brute force attack will not likely gain access to the system because it requires additional authentication. 






