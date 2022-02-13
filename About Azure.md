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







[How to Effectively Use Azure Management Groups, Subscriptions, and Resource Groups]: https://cloudacademy.com/blog/how-to-effectively-use-azure-management-groups-subscriptions-and-resource-groups/
