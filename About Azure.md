# Azure

#### What is Azure Resource Manager?
Azure Resource Manager is at the core of Microsoft Azure. It serves as an essential component of Azure deployment and provides a unified management layer regardless of the tool set used. Whether you use the Azure website, Azure CLI, Azure Powershell, or one of the many other methods for managing Azure resources, your commands all utilize Azure Resource Manager.

#### Understanding the Resource Manager Hierarchy
The Azure Resource Manager model uses four levels, or “scopes.” The following diagram provides an example of each of these scopes.

![scope-levels](https://user-images.githubusercontent.com/91851663/153774859-74ef5fba-f4d9-41f4-9652-dd2a51092865.png)

#### Azure Management Groups
##### What is a management group?
An Azure Management group is logical containers that allow Azure Administrators to manage access, policy, and compliance across multiple Azure Subscriptions en masse. Management groups allow you to build an Azure Subscription tree that can be used with several other Azure service, including Azure Policy and Azure Role Based Access Control. Azure Management Groups provide flexibility for organizing policy, access control, and compliance across multiple subscriptions. We can nest Azure Management Groups up to six levels deep for efficient management of resources.

Power of management groups is when you use them to model your organization. Azure Subscriptions can be grouped based on a need for common roles assigned along with Azure Policies and initiatives.

##### Organizing with management groups
Azure Management Groups provide a level of organization above Azure Subscriptions. If your company has more than one or two Azure Subscriptions, you will want to actively control access, policies, and compliance for those subscriptions. All subscription objects within a management group receives a copy of the role-based access control and policy settings applied to the management group. 

##### Limitations of management groups
A management group cannot contain an Azure Resource. It can only contain other management groups or subscriptions.


#### Azure Subscriptions
##### What is an Azure Subscription?
An Azure Subscription can be defined in many ways, but at its simplest a subscription refers to the logical entity that provides entitlement to deploy and consume Azure resources.

Microsoft’s definition of a subscription is “an agreement with Microsoft to use one or more Microsoft cloud platforms or services, for which charges accrue based on either a per-user license fee or on cloud-based resource consumption.”

##### How do subscriptions work?
Azure Subscriptions, at their core, are simple constructs. An Azure Subscription can be used in multiple ways to organize and store Azure resources, and to organize resources in containers.

##### Types of subscriptions
There are a large number of ways to create a subscription with Microsoft Azure, I am going to attempt to list the most prevalent.
* Enterprise Agreement (EA) – an Enterprise Agreement is a volume licensing program offered by Microsoft. The Enterprise Agreement most often is seen in larger organizations with 500 or more users, and is a three year contract with Microsoft.
* Pay as you go – Pay as you go is the second most common subscription type. Typically, the business will place a credit card file. Though rare, occasionally a client will pay by invoice.
* Free Trial – Anyone can sign up for a Free Trial of Azure, which is good for 30 days. The free trial subscription includes $200 of Azure spend credits. A free trial is converted to Pay once a credit card is placed on file.
* Cloud Solutions Partner (CSP) – CSP subscriptions are purchased through a Microsoft partner.

##### Subscription limitations
Azure has a large number of limitations per subscription, which are often referred to as “quotas”. Many (but not all) of the subscription limits can be raised by opening an online customer support request with Microsoft. Even so, all limits have a maximum value. Once you reach a maximum value, the only way to overcome it is multiple subscriptions.

#### Azure Resource Groups
##### What is a resource group?
Resource groups are the lowest level of organizational scope, and are the level that contains almost all Azure Resources. Azure Resources Groups are logical collections of virtual machines, app services, storage accounts, virtual networks, web apps, Azure SQL databases, etc. Resource groups can be utilized to subdivide resources by application or environment, among the many options.

Azure Resource Groups are a useful tool for Role-Based Access Control (RBAC). This will allow you to grant user access at the group level. Resource Groups can also simplify reporting and billing.

A resource group is a container that holds related resources for an Azure solution. The resource group can include all the resources for the solution, or only those resources that you want to manage as a group. You decide how you want to allocate resources to resource groups based on what makes the most sense for your organization. Generally, add resources that share the same lifecycle to the same resource group so you can easily deploy, update, and delete them as a group.

The resource group stores metadata about the resources. Therefore, when you specify a location for the resource group, you are specifying where that metadata is stored. For compliance reasons, you may need to ensure that your data is stored in a particular region.

Resource Groups in Azure is the approach to group the collection of resources that helps for easy maintenance of the Resources for example easy monitoring, automatic provisioning, etc. This is the main Purpose of the ResourceGroups.

A Resource Group in Azure is nothing but a logical container where you are creating your Azure resources. That holds all your Azure Resources. A resource group created in a specific region can contain the resources created in the other regions. There is no restriction on that.

#### Azure Region
##### What is an Azure Region?
Simply put, an Azure Region is a set of Datacenters that are connected through a dedicated low-latency network. How many datacenters does a region contain. Well, we do not have a fixed number. It varies. There are regions of different sizes. A Region could be made up of just 1 dataceneter or multiple datacenters. The point is, an Azure Region is a group of one or more Azure Datacenters. At the momenе Azure has more than 60 regions worldwide.

![azure-regions-explained](https://user-images.githubusercontent.com/91851663/153851258-b3bb96b1-76ad-4dee-8fbc-af9de1536d81.jpg)

You have the flexibility to deploy your applications and data to any Azure region you want. You can even deploy across multiple regions to deliver cross-region resiliency.

#### Virtual Network
##### Why use an Azure Virtual network?
Azure virtual network enables Azure resources to securely communicate with each other, the internet, and on-premises networks. Key scenarios that you can accomplish with a virtual network include - communication of Azure resources with the internet, communication between Azure resources, communication with on-premises resources, filtering network traffic, routing network traffic, and integration with Azure services.

#### Communicate between Azure resources
Azure resources communicate securely with each other in one of the following ways:

* Through a virtual network: You can deploy VMs, and several other types of Azure resources to a virtual network, such as Azure App Service Environments, the Azure Kubernetes Service (AKS), and Azure Virtual Machine Scale Sets. 
* Through a virtual network service endpoint: Extend your virtual network private address space and the identity of your virtual network to Azure service resources, such as Azure Storage accounts and Azure SQL Database, over a direct connection. Service endpoints allow you to secure your critical Azure service resources to only a virtual network. 
* Through VNet Peering: You can connect virtual networks to each other, enabling resources in either virtual network to communicate with each other, using virtual network peering. The virtual networks you connect can be in the same, or different, Azure regions.

#### Communicate with on-premises resources
You can connect your on-premises computers and networks to a virtual network using any combination of the following options:

* Point-to-site virtual private network (VPN): Established between a virtual network and a single computer in your network. Each computer that wants to establish connectivity with a virtual network must configure its connection. The communication between your computer and a virtual network is sent through an encrypted tunnel over the internet.
* Site-to-site VPN: Established between your on-premises VPN device and an Azure VPN Gateway that is deployed in a virtual network. This connection type enables any on-premises resource that you authorize to access a virtual network. The communication between your on-premises VPN device and an Azure VPN gateway is sent through an encrypted tunnel over the internet.
* Azure ExpressRoute: Established between your network and Azure, through an ExpressRoute partner. This connection is private. Traffic does not go over the internet. 

#### Filter network traffic
You can filter network traffic between subnets using either or both of the following options:

* Network security groups: Network security groups and application security groups can contain multiple inbound and outbound security rules that enable you to filter traffic to and from resources by source and destination IP address, port, and protocol.
* Network virtual appliances: A network virtual appliance is a VM that performs a network function, such as a firewall, WAN optimization, or other network function.

#### Route network traffic
Azure routes traffic between subnets, connected virtual networks, on-premises networks, and the Internet, by default. You can implement either or both of the following options to override the default routes Azure creates:

* Route tables: You can create custom route tables with routes that control where traffic is routed to for each subnet.
* Border gateway protocol (BGP) routes: If you connect your virtual network to your on-premises network using an Azure VPN Gateway or ExpressRoute connection, you can propagate your on-premises BGP routes to your virtual networks.


[How to Effectively Use Azure Management Groups, Subscriptions, and Resource Groups]: https://cloudacademy.com/blog/how-to-effectively-use-azure-management-groups-subscriptions-and-resource-groups/
