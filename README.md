# brittnia11
cybersecurity Incident Reports

# Table of contents

1. [Cybersecurity incident report network traffic analysis](#one)
2. [Analyze network attacks using Wireshark](#two)

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




