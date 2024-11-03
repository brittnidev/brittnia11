# brittnia11
Cybersecurity Incident Reports

# Table of contents

1. [Cybersecurity incident report network traffic analysis](#one)
2. [Analyze network attacks using Wireshark](#two)
3. [Apply OS hardening techniques](#three)
4. [Analysis of network hardening](#four)
5. [Use the NIST Cybersecurity Framework to respond to a security incident](#five)
6. [Use Linux commands to manage file permissions](#six)

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

-------
# Analysis of network hardening <a name="four">
You are a security analyst working for a social media organization. The organization recently experienced a major data breach, which compromised the safety of their customers’ personal information, such as names and addresses. Your organization wants to implement strong network hardening practices that can be performed consistently to prevent attacks and breaches in the future. 

# Part 1: Select up to three hardening tools and methods to implement (https://s.craft.me/3eTPLYSptlgdAx)
1. Implementing multi-factor authentication (MFA)
2. Setting and enforcing strong password policies
3. Performing firewall maintenance regularly

MFA requires users to use more than one way to identify and verify their credentials before accessing an application. Some MFA methods include fingerprint scans, ID cards, pin numbers, and passwords.

Password policies can be refined to include rules regarding password length, a list of acceptable characters, and a disclaimer to discourage password sharing. They can also include rules surrounding unsuccessful login attempts, such as the user loses access to the network after five unsuccessful attempts. Firewall maintenance entails checking and updating security configurations regularly to stay ahead of potential threats.
# Part 2: Explain your recommendations
Implementing multi-factor authentication (MFA) enhances security by requiring more than just a password for access. This additional layer makes it harder for malicious actors to breach a network through brute force or similar attacks, as they must overcome multiple authentication methods. MFA also discourages password sharing, since anyone receiving a shared password would still need the extra authentication, making such sharing less effective.

Establishing a robust password policy is crucial for strengthening network security. Measures like locking accounts after a specific number of failed login attempts can thwart brute force attacks. Increasing password complexity, mandating regular updates, and prohibiting password reuse further hinder unauthorized access.

Regular maintenance of firewalls is essential. Network administrators should ensure that firewall rules align with current standards for permitted and restricted traffic. Any suspicious traffic sources should be added to a denial list. Firewall rules must be promptly updated following any security incidents, particularly those that permit dubious traffic into the network, to safeguard against various DoS and DDoS attacks.

-------
# Use the NIST Cybersecurity Framework to respond to a security incident <a name="five">
You are a cybersecurity analyst working for a multimedia company that offers web design services, graphic design, and social media marketing solutions to small businesses. Your organization recently experienced a DDoS attack, which compromised the internal network for two hours until it was resolved.

During the attack, your organization’s network services suddenly stopped responding due to an incoming flood of ICMP packets. Normal internal network traffic could not access any network resources. The incident management team responded by blocking incoming ICMP packets, stopping all non-critical network services offline, and restoring critical network services. 

The company’s cybersecurity team then investigated the security event. They found that a malicious actor had sent a flood of ICMP pings into the company’s network through an unconfigured firewall. This vulnerability allowed the malicious attacker to overwhelm the company’s network through a distributed denial of service (DDoS) attack. 

# To address this security event, the network security team implemented:
	• 	A new firewall rule to limit the rate of incoming ICMP packets
	• 	Source IP address verification on the firewall to check for spoofed IP addresses on incoming ICMP packets
	• 	Network monitoring software to detect abnormal traffic patterns
	• 	An IDS/IPS system to filter out some ICMP traffic based on suspicious characteristics

As a cybersecurity analyst, you are tasked with using this security event to create a plan to improve your company’s network security, following the National Institute of Standards and Technology (NIST) Cybersecurity Framework (CSF). You will use the CSF to help you navigate through the different steps of analyzing this cybersecurity event and integrate your analysis into a general security strategy. We have broken the analysis into different parts in the template below. You can explore them here:

	• 	**Identify** security risks through regular audits of internal networks, systems, devices, and access privileges to identify potential gaps in security.
	• 	**Protect** internal assets through the implementation of policies, procedures, training and tools that help mitigate cybersecurity threats.
	• 	**Detect** potential security incidents and improve monitoring capabilities to increase the speed and efficiency of detections.
	• 	**Respond** to contain, neutralize, and analyze security incidents; implement improvements to the security process.
 	• 	**Recover** affected systems to normal operation and restore systems data and/or assets that have been affected by an incident.


# Incident report analysis
- **Identify** Our organization recently faced a DDoS attack that disrupted the internal network for two hours. During this incident, network services became unresponsive due to an overwhelming influx of ICMP packets, preventing normal internal traffic from accessing network resources. The issue was resolved after the two-hour period.

- **Protect** The incident management team conducted an audit of the systems, devices, and access policies related to the attack to identify security gaps. They discovered that a malicious attacker had obtained an intern's login credentials, which were then used to access data from our customer database. Preliminary findings indicate that some customer data was deleted from the database.

- **Detect** The team has introduced new authentication policies to safeguard against future attacks, including multi-factor authentication (MFA), limiting login attempts to three, and providing training for all employees on securing their login credentials. Furthermore, we will establish a new firewall configuration and invest in an intrusion prevention system (IPS).

- **Respond** To detect unauthorized access attempts in the future, the team will utilize a firewall logging tool and an intrusion detection system (IDS) to monitor all incoming internet traffic.

- **Recover** The team has disabled the intern's network account and provided training to interns and employees on securing their login credentials moving forward. Upper management has been notified of this incident and will reach out to our customers via mail to inform them about the data breach. Additionally, management will contact law enforcement and other relevant organizations as mandated by local laws.
  
-------
# Manage files with Linux commands <a name="six">
- use the content of (https://docs.google.com/document/d/1F3-8XQZsNagSzTkJwFzOGY5OHbGbMRtlb8GbmXE_gCc/template/preview?resourcekey=0-UUEu0EyFFvMf0SAipcel6w) document to determine the current permissions.

# Project Description: Describe the command you can use to check permissions 
- This Linux project involves working with file and directory permissions using the provided directory structure "/home/researcher2/projects." Tasks include checking file and directory details, describing the permissions string, changing file permissions, changing permissions on a hidden file, and changing directory permissions.

# Check File and Directory Details
```
ls -la /home/researcher2/projects
```



