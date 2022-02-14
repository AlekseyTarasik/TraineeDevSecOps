## Microsoft Azure and Google Cloud Platform


In this task, I need to create a virtual network using Azure or Google Cloud Platform.

I decided to understand the microsoft product in connection with my future career growth.

The purpose of this project is to study the creation and work with the Azure cloud platform, create an Azure virtual private network scheme, and write explanatory documentation for my scheme.

To create my virtual network scheme, I followed the following principles:
#### 1) One VPC per needed Environment

  We need a minimum of two VPCs - one for Test and one for Prod.
  * Prod: Production - just the most trusted and skilled should have access here.
  * Test: Test environment should be as close as possible to Prod but it should be able to break at any time without anyone complaining.
  
  Why do I use only two? Because I'm creating a small schema for a small application. And because we should never mix Prod and Test objects.

#### 2) Have a good naming standard and keep it implemented

  I apply this principle, for example, for subnet signatures - "nw-prod-if-web"
  
#### 3) One FW per network (NW) and one FW per server (SRV)

  In each AZ I have subnets that I use SG_NW to access. In each subnet I have a server or multiple servers that use NSG_SRV. Network Security Group - very close to a standard stateful FW. Then we use one to protect the NW (nsg_nw) and one to protect the server (nsg_srv).

#### 4) Group the same type of services on its own NW

  In my scheme, I group various services of the same type at the subnet level.
  
#### 5) Separate internet-facing (if) services from non-internet-facing (nif)

  It is also important to divide the services into connected to the Internet and disconnected from the Internet. This is necessary for additional security of some services and routing of local networks.

#### 6) Use IPv6 in all NW and to all services
  
  IPv6 eliminates the possibility of private address conflicts, and also optimizes multicast routing. IPv6 has a simpler header format, which makes routing easier and more efficient. It also improves the quality of services (QoS). IPv6 has built-in authentication and privacy protection, as well as flexible options with support for extensions.
  
#### 7) Let the IP number tell you where you are

  With a smart numbering principle of the IP number ranges the IP number you find on a server can give you information both on what region you are in, if what type of environment the VPC handles and on what NW you are.
  
  In my virtual network, I chose the private ipv4 range as /16. In subnets, I used the /24 range. And for ipv6 I chose the range as /48. In subnets I used the range /64.
 
## About my scheme

  In my scheme, the whole chain starts with the Internet. To connect to the cloud, you need to go through the DNS layer.
Azure DNS uses a global network of name servers to provide a fast response to DNS queries. A random distribution network service is used, so DNS requests are automatically routed to the nearest domain name servers, which ensures maximum performance.
I also want to note that DNS names need to be delimited, for example, intranet.domain.com for Prod, but test-intranet.domain.com for Test.

The Local Network Gateway is designed to manage web application traffic. 

The application gateway is able to make routing decisions based on additional HTTP request attributes, such as URI paths. 

In the scheme, the Local Network Gateway sends a request to the Prod version or to the Test version.
Further on the diagram you can see the branching into two networks. The first network is Prod, the second is Test.


Consider the Prod branch.
Local Network Gateway is followed by Load balancer (external) for public IP addresses and Application Gateway.

In my case, Load balancer (external) is designed to determine the load on Availability Zones and send the received request to one of the AZ.

Azure Application Gateway provides application-level routing and load balancing services which let you build a scalable and highly-available web front end in Azure.

Application Gateway can be used for:
1) WAF as an option
2) HTTP(S) round-robin load balancing
3) cookie-based session affinity
4) SSL (TLS really) offloading with optional TLS re-encryption to the backend
5) URL-based and multi-site routing, diagnostics, and monitoring
6) HTTP to HTTPS redirection
7) WebSocket support
8) SSL policies

Next, I separate Prod into 2 Availability Zones for build High-Availability (HA) services. I think that two zones are enough for my application. 

Each AZ is connected to the internet via NAT.
I have the following subnets:
1) nw-prod-if-web
2) nw-prod-if-app
3) nw-prod-nif-coop
4) nw-prod-nif-infrasec
5) nw-prod-nif-db

From the interesting things here, you can see that for access to nw-prod-nif-coop, I use nw-prod-nif-infrasec in order to increase security. 

Also, the database in the first AZ and the second AZ have a connection. This is done for fault tolerance. If the "master" database has problems (disabled), then using asynchronous replication technology, some of the latest data is sent to the "standby" database and the project is connected to another database.

On Prod, the database versions are connected to the Azure Storage service to send logs and dumps.

Azure Network Security Groups (NSGs) is a network security service to refine traffic from and to Azure VNet. It is an OSI layer 3 & 4 network security service. An Azure NSG comprises of several security rules that users can allow or deny. These rules are evaluated based on the 5-tuple hash. This 5-tuple hash takes values from the source IP address, source port number, destination IP address, destination port number, and protocol type in use. You can associate Network Security Groups with a VNet or a VM network interface.
Azure Firewall allows you to mask the source and destination network addresses while NSG doesn’t.

![fw-vs-nsg2](https://user-images.githubusercontent.com/91851663/153874308-ca791948-2a3e-4500-9086-6f47c7a1c64e.png)

Various useful links to guides for creating virtual networks in microsoft azure:

* [Create a virtual network using the Azure portal]
* [Create a virtual network using PowerShell]
* [Create a virtual network using the Azure CLI]
* [Create a virtual network - Resource Manager template]
* [Filter network traffic]
* [Route network traffic]
* [Restrict network access to resources]
* [Connect virtual networks]



[Create a virtual network using the Azure portal]: https://docs.microsoft.com/en-us/azure/virtual-network/quick-create-portal
[Create a virtual network using PowerShell]: https://docs.microsoft.com/en-us/azure/virtual-network/quick-create-powershell
[Create a virtual network using the Azure CLI]: https://docs.microsoft.com/en-us/azure/virtual-network/quick-create-cli
[Create a virtual network - Resource Manager template]: https://docs.microsoft.com/en-us/azure/virtual-network/quick-create-template
[Filter network traffic]: https://docs.microsoft.com/en-us/azure/virtual-network/tutorial-filter-network-traffic
[Route network traffic]: https://docs.microsoft.com/en-us/azure/virtual-network/tutorial-create-route-table-portal
[Restrict network access to resources]: https://docs.microsoft.com/en-us/azure/virtual-network/tutorial-restrict-network-access-to-resources
[Connect virtual networks]: https://docs.microsoft.com/en-us/azure/virtual-network/tutorial-connect-virtual-networks-portal
