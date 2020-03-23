# Networker Firewall Rules RH based Linux

Networker is using a portmapper which is listening on port 7937/tcp and open ports additional for communication.

As per Networker Security Guide the Networker Client rquires 

2 fixed listening ports 7937/tcp+udp and 7939/tcp.

2 ports in addition from the service port range.

2 optional ports in additon from the service port range are required if snapshot manegement services are required.

You must define the service port range for networker so that the ports open in the firewall match the ports used by the portmapper otherwise you will have connectivity issues.

You can set the service port range by issueing the nsrports command on the client:

```
[root@stm-lx-3 NW-helpers]# nsrports 7937-7942
Service ports: 7937-7942 
Connection ports: 0-0 
```

This directory currently contains the file nserexec.xml which are the firewall rules for the nw client.
I will add rules for storage node and server later.

You can install the rules by issuing the following command:

```
firewall-cmd --permanent --new-service-from-file=Documents/FW-nsrexecd.xml  --name=nsrexecd
```
