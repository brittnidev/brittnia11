# brittnia11
cybersecurity Incident Reports

# Table of contents

1. [Cybersecurity incident report network traffic analysis](#one)

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




