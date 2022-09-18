# AZ-104 Microsoft Azure Administrator Exam. Materials, Tips, Hints.

## ARM. Azure Resource Manager. Quick Start Templates

* Quick start Templates could be found here: https://azure.microsoft.com/en-us/resources/templates/

## Azure Virtual Machines

<details>
<summary>Create Azure VM with auto-generated and stored SSH keys</summary>

> az vm create \
    --resource-group YOUR_RESOURCE_GROUP \
    --name SampleVM2 \
    --image UbuntuLTS \
    --admin-username azureuser \
    --generate-ssh-keys \

</details>  

## Azure Active Directory, Azure Active Directory Domain Services (AD DS)

<details>
<summary>Azure Active Directory. Features. Plans</summary>

![image](https://user-images.githubusercontent.com/4239376/187085417-662708e0-87eb-445c-b6d0-aaea1e0fdc98.png)

</details>

<details>
<summary>Azure Active Directory VS Active Directory Domain Services</summary>

![image](https://user-images.githubusercontent.com/4239376/187085204-f65f3882-d2c3-4369-ab04-b8fbf65cb190.png)

Azure Active Directory is different
* Although Azure AD has many similarities to AD DS, there are also many differences. It is important to realize that using Azure AD is different from deploying an Active Directory domain controller on an Azure virtual machine and adding it to your on-premises domain. Here are some characteristics of Azure AD that make it different.

1. Identity solution. Azure AD is primarily an identity solution, and it is designed for Internet-based applications by using HTTP and HTTPS communications.
REST API Querying. Because Azure AD is HTTP/HTTPS based, it cannot be queried through LDAP. Instead, Azure AD uses the REST API over HTTP and HTTPS.
2. Communication Protocols. Because Azure AD is HTTP/HTTPS based, it does not use Kerberos authentication. Instead, it uses HTTP and HTTPS protocols such as SAML, WS-Federation, and OpenID Connect for authentication (and OAuth for authorization).
3. Federation Services. Azure AD includes federation services, and many third-party services (such as Facebook).
4. Flat structure. Azure AD users and groups are created in a flat structure, and there are no Organizational Units (OUs) or Group Policy Objects (GPOs).
</details>

<details>
<summary>Azure Active Directory Join</summary>

  Azure AD Join is designed to provide access to organizational apps and resources and to simplify Windows deployments of work-owned devices. AD Join has these benefits.  
  Azure Active Directory (Azure AD) enables single sign-on to devices, apps, and services from anywhere. IT administrators must ensure corporate assets are protected and that devices meet standards for security and compliance.  
  ![image](https://user-images.githubusercontent.com/4239376/187085477-db312954-4af1-49b3-877c-ea64fa03f245.png)

  ### Azure AD Join benefits:
* Single-Sign-On (SSO) to your Azure-managed SaaS apps and services. Your users won't have additional authentication prompts when accessing work resources. The SSO functionality is available even when users are not connected to the domain network.
* Enterprise state roaming of user settings across joined devices. With Windows 10, users gain the ability to securely synchronize their user settings and application settings data to the cloud. This reduces the time to configure a new device.
* Access to Microsoft Store for Business using an Azure AD account. Your users can choose from an inventory of applications pre-selected by the organization.
* Windows Hello support for secure and convenient access to work resources.
* Restriction of access to apps from only devices that meet compliance policy.
* Seamless access to on-premise resources when the device has line of sight to the on-premises domain controller.

  ### Connection options:
* Registering a device to Azure AD enables you to manage a device’s identity. Azure AD device registration provides the device with an identity that is used to authenticate the device when a user signs-in to Azure AD. You can use the identity to enable or disable a device.
* Joining a device is an extension to registering a device. Joining provides the benefits of registering and changes the local state of a device. Changing the local state enables your users to sign-in to a device using an organizational work or school account instead of a personal account.
  
</details>

<details>
<summary>Azure Roles. Azure Roles vs Azure Directory roles</summary>

![image](https://user-images.githubusercontent.com/4239376/187094387-e7732727-4847-419a-a3f9-af31cefd071a.png)
![image](https://user-images.githubusercontent.com/4239376/187094390-944ae973-6a22-4828-904d-a9cee7afc8a8.png)
1. Actions
2. NoActions
3. DataActions

* Classic subscription administrator roles
* Azure role-based access control (RBAC) roles
* Azure Active Directory (Azure AD) administrator roles

![image](https://user-images.githubusercontent.com/4239376/187094377-029444cf-0bf9-4ae6-88cd-e906a6c11db9.png)

### The following diagram illustrates how Azure AD Admin roles are different from Azure RBAC roles. 
Azure AD Admin roles are used to manage resources in Azure AD, such as users, groups, and domains. Azure RBAC roles provide more fine-grained access management to Azure resources.

![image](https://user-images.githubusercontent.com/4239376/187094494-02376152-8d06-41ad-87e6-c6ebba533793.png)

</details>

## Azure Container Instance (ACI). Azure Kubernetes Service (AKS)

<details>
<summary>Azure Container Instance</summary>

### Intro:
The top-level resource in Azure Container Instances is the container group. A container group is a collection of containers that get scheduled on the same host machine. The containers in a container group share a lifecycle, resources, local network, and storage volumes. It's similar in concept to a pod in Kubernetes.

![image](https://user-images.githubusercontent.com/4239376/188326890-ee3cf8a5-cb0e-44ff-a508-7b4ddb002994.png)
![image](https://user-images.githubusercontent.com/4239376/188326898-b7259ee3-83e1-4db8-983f-cbb2c3b77b92.png)

### An example container group:
* Is scheduled on a single host machine.
* Is assigned a DNS name label.
* Exposes a single public IP address, with one exposed port.
* Consists of two containers. One container listens on port 80, while the other listens on port 1433.
* Includes two Azure file shares as volume mounts, and each container mounts one of the shares locally.

### Resource allocation
Azure Container Instances allocates resources such as CPUs, memory, and optionally GPUs to a multi-container group by adding the resource requests of the instances in the group. Taking CPU resources as an example, if you create a container group with two container instances, each requesting one CPU, then the container group is allocated 2 CPUs.

### Common scenarios
* Multi-container groups are useful in cases where you want to divide a single functional task into a small number of container images. These images can then be delivered by different teams and have separate resource requirements. Example usage could include:

* A container serving a web application and a container pulling the latest content from source control.
* An application container and a logging container. The logging container collects the logs and metrics output by the main application and writes them to long-term storage.
* An application container and a monitoring container. The monitoring container periodically makes a request to the application to ensure that it's running and responding correctly, and raises an alert if it's not.
* A front-end container and a back-end container. The front end might serve a web application, with the back end running a service to retrieve data.

</details>

<details>
<summary>Azure Container Instance vs Azure Kubernetes Service</summary>

ACI is easier, lightweight solution to run your containerized instances. AKS is more about handling complex scenarios when you need to manage a series of pods, containers in them and so on.

</details>

<details>
<summary>Azure Kubernetes Service</summary>

## The standard container management runtime focuses on managing individual containers. If you want to scale a complex system with multiple containers working together, this scenario becomes challenging. To make the management process easier, it's common to use a container management platform, such as Kubernetes.
  
![image](https://user-images.githubusercontent.com/4239376/188499804-71c3d4d6-81de-481d-97fc-9764aef4d2a3.png)
  
* Pools are groups of nodes with identical configurations.

* Nodes are individual virtual machines running containerized applications.

* Pods are a single instance of an application. A pod can contain multiple containers.

* Container is a lightweight and portable executable image that contains software and all of its dependencies.

* Deployment has one or more identical pods managed by Kubernetes.

* Manifest is the YAML file describing a deployment.

## Kubernetes Cluster
  
![image](https://user-images.githubusercontent.com/4239376/188499954-766b2e58-98dd-4a8f-b58c-97f8b9f07bc4.png)

### A Kubernetes cluster is divided into two components:

Azure-managed nodes, which provide the core Kubernetes services and orchestration of application workloads.
Customer-managed nodes that run your application workloads.
  
### Azure-managed node

When you create an AKS cluster, a cluster node is automatically created and configured. This node is provided as a managed Azure resource abstracted from the user. You pay only for running agent nodes
  
### Nodes and node pools
To run your applications and supporting services, you need a Kubernetes node. An AKS cluster contains one or more nodes (Azure Virtual Machines) that run the Kubernetes node components and the container runtime.
  
* The kubelet is the Kubernetes agent that processes the orchestration requests from the Azure-managed node, and scheduling of running the requested containers. 
* Virtual networking is handled by the kube-proxy on each node. The proxy routes network traffic and manages IP addressing for services and pods.
* The container runtime is the component that allows containerized applications to run and interact with additional resources such as the virtual network and storage. AKS clusters using Kubernetes version 1.19 node pools and greater use containerd as its container runtime. AKS clusters using Kubernetes prior to v1.19 for node pools use Moby (upstream docker) as its container runtime.
  
Nodes of the same configuration are grouped together into node pools. A Kubernetes cluster contains one or more node pools. The initial number of nodes and size are defined when you create an AKS cluster, which creates a default node pool. This default node pool in AKS contains the underlying VMs that run your agent nodes.

### Ingress Controller
  In Kubernetes, Services logically group pods to allow for direct access via an IP address or DNS name and on a specific port. You can also distribute traffic using a load balancer. More complex routing of application traffic can also be achieved with Ingress Controllers. Security and filtering of the network traffic for pods is possible with Kubernetes network policies.
  
### Pods
Kubernetes uses pods to run an instance of your application. A pod represents a single instance of your application. Pods typically have a 1:1 mapping with a container, although there are advanced scenarios where a pod might contain multiple containers. These multi-container pods are scheduled together on the same node, and allow containers to share related resources.
  
</details>

<details>
<summary>Azure Kubernetes Service. Persistent Volumes. Volume, Persistent Volume, Storage Classes, Volume Claims</summary>
  
![image](https://user-images.githubusercontent.com/4239376/188500754-d6adcacf-d378-4f7b-875c-f2758d999d3e.png)  
## Applications that run in Azure Kubernetes Service (AKS) may need to store and retrieve data. 
  
  For some application workloads, this data storage can use local, fast storage on the node that is no longer needed when the pods are deleted. Other application workloads may require storage that persists on more regular data volumes within the Azure platform. Multiple pods may need to share the same data volumes, or reattach data volumes if the pod is rescheduled on a different node. Finally, you may need to inject sensitive data or application configuration information into pods.
  
* Volumes
* Persistent volumes
* Storage classes
* Persistent volume claims
  
### Volumes
Applications often need to be able to store and retrieve data. As Kubernetes typically treats individual pods as ephemeral, disposable resources, different approaches are available for applications use and persist data as necessary. A volume represents a way to store, retrieve, and persist data across pods and through the application lifecycle.  
  
Traditional volumes to store and retrieve data are created as Kubernetes resources backed by Azure Storage. You can manually create these data volumes to be assigned to pods directly, or have Kubernetes automatically create them. These data volumes can use Azure Disks or Azure Files:  
  
* Azure Disks can be used to create a Kubernetes DataDisk resource. Disks can use Azure Premium storage, backed by high-performance SSDs, or Azure Standard storage, backed by regular HDDs. For most production and development workloads, use Premium storage. Azure Disks are mounted as ReadWriteOnce, so are only available to a single node. For storage volumes that can be accessed by multiple nodes simultaneously, use Azure Files.
* Azure Files can be used to mount an SMB 3.0 share backed by an Azure Storage account to pods. Files let you share data across multiple nodes and pods. Files can use Azure Standard storage backed by regular HDDs, or Azure Premium storage, backed by high-performance SSDs.
 
### Persistent volumes
Volumes are defined and created as part of the pod lifecycle only exist until the pod is deleted. Pods often expect their storage to remain if a pod is rescheduled on a different host during a maintenance event, especially in StatefulSets. A persistent volume (PV) is a storage resource created and managed by the Kubernetes API that can exist beyond the lifetime of an individual pod.  
  
Azure Disks or Files are used to provide the PersistentVolume. As noted in the previous section on Volumes, the choice of Disks or Files is often determined by the need for concurrent access to the data or the performance tier.  
  
A PersistentVolume can be statically created by a cluster administrator, or dynamically created by the Kubernetes API server. If a pod is scheduled and requests storage that is not currently available, Kubernetes can create the underlying Azure Disk or Files storage and attach it to the pod. Dynamic provisioning uses a StorageClass to identify what type of Azure storage needs to be created.  
   
### Storage classes
To define different tiers of storage, such as Premium and Standard, you can create a StorageClass. The StorageClass also defines the reclaimPolicy. This reclaimPolicy controls the behavior of the underlying Azure storage resource when the pod is deleted and the persistent volume may no longer be required. The underlying storage resource can be deleted, or retained for use with a future pod.
  
**In AKS, four initial StorageClasses are created for cluster using the in-tree storage plugins:**

* default - Uses Azure StandardSSD storage to create a Managed Disk. The reclaim policy ensures that the underlying Azure Disk is deleted when the persistent volume that used it is deleted.
* managed-premium - Uses Azure Premium storage to create a Managed Disk. The reclaim policy again ensures that the underlying Azure Disk is deleted when the persistent volume that used it is deleted.
* azurefile - Uses Azure Standard storage to create an Azure File Share. The reclaim policy ensures that the underlying Azure File Share is deleted when the persistent volume that used it is deleted.
* azurefile-premium - Uses Azure Premium storage to create an Azure File Share. The reclaim policy ensures that the underlying Azure File Share is deleted when the persistent volume that used it is deleted.
  
  If no StorageClass is specified for a persistent volume, the default StorageClass is used. Take care when requesting persistent volumes so that they use the appropriate storage you need. You can create a StorageClass for additional needs using kubectl.
  
### Persistent volume claims
A PersistentVolumeClaim requests either Disk or File storage of a particular StorageClass, access mode, and size. The Kubernetes API server can dynamically provision the underlying storage resource in Azure if there is no existing resource to fulfill the claim based on the defined StorageClass. The pod definition includes the volume mount once the volume has been connected to the pod.

**A PersistentVolume is bound to a PersistentVolumeClaim once an available storage resource has been assigned to the pod requesting it. There is a 1:1 mapping of persistent volumes to claims.**
  
</details> 

<details>
<summary>AKS scaling. Manual Scaling. Automatic Scale-out Scale-in. Not Enough Resources</summary>

  ![image](https://user-images.githubusercontent.com/4239376/188501775-da85b625-2e80-42cc-91f8-7ebeb8959850.png)

## As you run applications in Azure Kubernetes Service (AKS), you may need to increase or decrease the amount of compute resources. 
As the number of application instances you need change, the number of underlying Kubernetes nodes may also need to change.
  
  
### Manually scale pods or nodes
  You can manually scale replicas (pods) and nodes to test how your application responds to a change in available resources and state. Manually scaling resources also lets you define a set amount of resources to use to maintain a fixed cost, such as the number of nodes. To manually scale, you define the replica or node count, and the Kubernetes API schedules creating new pods or draining nodes.
  
### Horizontal pod autoscaler (checks the Metrics API every 30 seconds)
  Kubernetes uses the horizontal pod autoscaler (HPA) to monitor the resource demand and automatically scale the number of replicas. By default, the horizontal pod autoscaler checks the Metrics API every 30 seconds for any required changes in replica count. When changes are required, the number of replicas is increased or decreased accordingly. Horizontal pod autoscaler works with AKS clusters that have deployed the Metrics Server for Kubernetes 1.8+.

  When you configure the horizontal pod autoscaler for a given deployment, you define the minimum and maximum number of replicas that can run. You also define the metric to monitor and base any scaling decisions on, such as CPU usage.
  
### Cooldown of scaling events
  As the horizontal pod autoscaler checks the Metrics API every 30 seconds, previous scale events may not have successfully completed before another check is made. This behavior could cause the horizontal pod autoscaler to change the number of replicas before the previous scale event has been able to receive application workload and the resource demands to adjust accordingly.

  To minimize these race events, cooldown or delay values can be set. These values define how long the horizontal pod autoscaler must wait after a scale event before another scale event can be triggered. This behavior allows the new replica count to take effect and the Metrics API reflect the distributed workload. By default, the delay on scale up events is 3 minutes, and the delay on scale down events is 5 minutes.
  
  You may need to tune these cooldown values. The default cooldown values may give the impression that the horizontal pod autoscaler isn't scaling the replica count quickly enough. For example, to more quickly increase the number of replicas in use, reduce the --horizontal-pod-autoscaler-upscale-delay when you create your horizontal pod autoscaler definitions using kubectl.
  
### Cluster autoscaler
To respond to changing pod demands, Kubernetes has a cluster autoscaler that adjusts the number of nodes based on the requested compute resources in the node pool. By default, the cluster autoscaler checks the API server every 10 seconds for any required changes in node count. If the cluster autoscale determines that a change is required, the number of nodes in your AKS cluster is increased or decreased accordingly. The cluster autoscaler works with RBAC-enabled AKS clusters that run Kubernetes 1.10.x or higher.

Cluster autoscaler is typically used alongside the horizontal pod autoscaler. When combined, the horizontal pod autoscaler increases or decreases the number of pods based on application demand, and the cluster autoscaler adjusts the number of nodes as needed to run those additional pods accordingly.
  
### Scale out events (IF NOT ENOUGH NODE RESOURCES)
If a node does not have sufficient compute resources to run a requested pod, that pod cannot progress through the scheduling process. The pod cannot start unless other compute resources are available within the node pool.
  
  When the cluster autoscaler notices pods that cannot be scheduled due to node pool resource constraints, the number of nodes within the node pool is increased to provide the extra compute resources. When those additional nodes are successfully deployed and available for use within the node pool, the pods are then scheduled to run on them.
  
* If your application needs to scale rapidly, some pods may remain in a state waiting to be scheduled until the new nodes deployed by the cluster autoscaler can accept the scheduled pods. For applications that have high burst demands, you can scale with virtual nodes and Azure Container Instances.
  
### Scale in events
The cluster autoscaler also monitors the pod scheduling status for nodes that have not recently received new scheduling requests. This scenario indicates that the node pool has more compute resources than are required, and that the number of nodes can be decreased.

A node that passes a threshold for no longer being needed for 10 minutes by default is scheduled for deletion. When this situation occurs, pods are scheduled to run on other nodes within the node pool, and the cluster autoscaler decreases the number of nodes.
  
</details>

<details>
<summary>AKS scaling into ACI</summary>
  
  ![image](https://user-images.githubusercontent.com/4239376/188502805-09e66102-c7ab-49e8-9e4d-a708d2cf8561.png)

  To rapidly scale your AKS cluster, you can integrate with Azure Container Instances (ACI). Kubernetes has built-in components to scale the replica and node count. However, if your application needs to rapidly scale, the horizontal pod autoscaler may schedule more pods than can be provided by the existing compute resources in the node pool. If configured, this scenario would then trigger the cluster autoscaler to deploy additional nodes in the node pool. It may take a few minutes for those nodes to successfully provision.

* ACI lets you quickly deploy container instances without more infrastructure overhead. When you connect with AKS, ACI becomes a secured, logical extension of your AKS cluster. The Virtual Kubelet component is installed in your AKS cluster that presents ACI as a virtual Kubernetes node. Kubernetes can then schedule pods that run as ACI instances through virtual nodes, not as pods on VM nodes directly in your AKS cluster.
  
</details>

# AKS. Q&A:
2. The infrastructure team is configuring networking for the Azure Kubernetes service. Which of the following services would be best for internal-only applications that support other workloads within the cluster?

**LoadBalancer**

**ClusterIP**
That's correct. ClusterIP creates an internal IP address for use within the AKS cluster. This is good for internal-only applications that support other workloads within the cluster.

**NodePort**
That's incorrect. NodePort creates a port mapping on the underlying node that allows the application to be accessed directly with the node IP address and port.

# Network. Private Links. ExpressRoute. Firewall. Other network-related topics (ASG, NSG, DNS, VNet, VPN Gateway)

<details>
<summary>Networks. Private links. ExpressRoute. Firewall (NAT, Application Rules, Network rules)</summary>
  Private links - could organize access between your private network and Azure resource.  Could be created once network created.  
  ExpressRoute - Azure - on-premise connection. 
  
## Firewall
    
![image](https://user-images.githubusercontent.com/4239376/188989290-6bde02fd-2cb8-47e3-91db-11670291e7f3.png)
    
### Topology
  It's recommended to use a hub-spoke network topology when deploying a firewall.

![image](https://user-images.githubusercontent.com/4239376/188988384-1b7a72b7-c469-49fd-b862-272adc8c22fa.png)
    
* The hub is a virtual network in Azure that acts as a central point of connectivity to your on-premises network.
* The spokes are virtual networks that peer with the hub, and can be used to isolate workloads.
* Traffic flows between the on-premises datacenter and the hub through an ExpressRoute or VPN gateway connection.

## Azure Firewall Features
    * Built-in high availability.  load balancers aren't required.
    * Availability Zones. Azure Firewall can be configured during deployment to span multiple Availability Zones for increased availability.
    * Network traffic filtering rules. You can centrally create allow or deny network filtering rules by source and destination IP address, port, and protocol. 
    * Threat intelligence. to alert and deny traffic from/to known malicious IP addresses and domains. The IP addresses and domains are sourced from the Microsoft Threat Intelligence feed.
    * Azure Monitor - built-in

## Azure Firewall combinations
    
![image](https://user-images.githubusercontent.com/4239376/188989451-ea20e496-b26c-472c-bd09-5dfd4fb32b97.png)

* Could be combines with Bastion (RDP\SSH traffic protection to your VMs)
* Could work together with VPN Gateway (Entry point from on-premise DC)

## Azure Firewall rules

![image](https://user-images.githubusercontent.com/4239376/188990044-04cca4c2-5ecb-4cf2-914d-8aa03fd86f01.png)

</details>  

<details>
<summary>Service Endpoint. Service Endpoint vs Private Link</summary>

A virtual network service endpoint provides the identity of your virtual network to the Azure service. Once service endpoints are enabled in your virtual network, you can secure Azure service resources to your virtual network by adding a virtual network rule to the resources.
    
![image](https://user-images.githubusercontent.com/4239376/189526580-ff10eb7f-3e4c-45fd-8f98-ae23c18baf07.png)

## Compare with Private link

Private Link is a newer solution than Service Endpoints.  
See alse here: https://samcogan.com/service-endpoints-and-private-link-whats-the-difference/
![image](https://user-images.githubusercontent.com/4239376/189526610-af2494b9-6289-4fd9-b9f7-2c6348e13773.png)

The key difference between Private Link and Service Endpoints is that with Private Link you are injecting the multi-tenant PaaS resource into your virtual network. With Service Endpoints, traffic still left you vNet and hit the public endpoint of the PaaS resource, with Private Link the PaaS resource sits within your vNet and gets a private IP on your vNet. When you send traffic to the PaaS resource, it does not leave the virtual network.

## Private Link case

![image](https://user-images.githubusercontent.com/4239376/189526704-f1432613-af85-4ccb-9e3b-1e2e5b59d3ac.png)

* Private connectivity to services on Azure. Traffic remains on the Microsoft network, with no public internet access. Connect privately to services running in other Azure regions. Private Link is global and has no regional restrictions.
* Integration with on-premises and peered networks. Access private endpoints over private peering or VPN tunnels from on-premises or peered virtual networks. Microsoft hosts the traffic, so you don’t need to set up public peering or use the internet to migrate your workloads to the cloud.
* Protection against data exfiltration for Azure resources. Use Private Link to map private endpoints to Azure PaaS resources. When there is a security incident within your network, only the mapped resource would be accessible, eliminating the threat of data exfiltration.
* Services delivered directly to your customers’ virtual networks. Privately consume Azure PaaS, Microsoft partner, and your own services in your virtual networks on Azure. Private Link works across Azure Active Directory (Azure AD) tenants to help unify your experience across services. Send, approve, or reject requests directly, without permissions or role-based access controls.
    
</details>

<details>
<summary>NSG. Network Security Group. DMZ</summary>

## NSG

You can limit network traffic to resources in a virtual network using a network security group (NSG). A network security group contains a list of security rules that allow or deny inbound or outbound network traffic. An NSG can be associated to a subnet or a network interface. A network security group can be associated multiple times.

There are three default inbound security rules.  

![image](https://user-images.githubusercontent.com/4239376/189196019-03aa54d1-7b1b-4583-85ce-72aa6c41add2.png)

There are three default outbound security rules.  

![image](https://user-images.githubusercontent.com/4239376/189196054-42265689-d63b-41bd-8b54-234c4478e3e1.png)

You can add more rules by specifying:

* Name
* Priority
* Port
* Protocol (Any, TCP, UDP)
*Source (Any, IP Addresses, Service tag)
* Destination (Any, IP Addresses, Virtual Network)
* Action (Allow or Deny)

## Example:

![image](https://user-images.githubusercontent.com/4239376/189196512-62f8f17f-c23f-471a-9547-1ceaa11fe995.png)

In the above example, if there was incoming traffic on port 80, you would need to have the NSG at the subnet level ALLOW port 80. You would also need another N S G with an ALLOW rule on port 80 at the NIC level.

</details>

<details>
<summary>VNet Virtual network peering. Global Peering. Vnet Peering. Connect on-premise and Azure resources not exposing the traffic to the internet. VPN Gateway vs Vnet peernig</summary>


**Create network:**    
    
> az network vnet create \
    --resource-group <YOUR_RESOURCE_GROUP> \
    --name SalesVNet \
    --address-prefixes 10.1.0.0/16 \
    --subnet-name <SUBNET_NAME> \
    --subnet-prefixes 10.1.1.0/24 \
    --location northeurope
    
**Create peering connection:**
> az network vnet peering create \
    --name <FROM_SUBNET_TO_SUBNET_NAME>
    --remote-vnet <FIRST_SUBNET_NAME> \
    --resource-group <RESOURCE_GROUP_OF_DESTINATION_SUBNET> \
    --vnet-name <SECOND_SUBNET_NAME> \
    --allow-vnet-access  
    
**Show list of established connections:**
> az network vnet peering list \
    --resource-group <RESOURCE_GROUP_ID> \
    --vnet-name <YOUR_NETWORK> \
    --query "[].{Name:name, Resource:resourceGroup, PeeringState:peeringState, AllowVnetAccess:allowVirtualNetworkAccess}"\
    --output table
    
Several business units have identified services in these virtual networks that need to communicate with each other. You need to enable this connectivity, but you don't want to expose these services to the internet. You also want to keep the integration as simple as possible.

![image](https://user-images.githubusercontent.com/4239376/189206782-c6cef64a-ce76-4135-b5e2-945fa6bde316.png)

## How to create
    
![image](https://user-images.githubusercontent.com/4239376/189207616-60a3f1f6-2b99-49ee-8a9e-25cf8d40c9e7.png)

1. Create two virtual networks.
2. Peer the virtual networks.
  Optional:  
3. Create virtual machines in each virtual network.
4. Test the communication between the virtual machines.    
    
### Advantages

* Private. Network traffic between peered virtual networks is private. Traffic between the virtual networks is kept on the Microsoft backbone network. No public Internet, gateways, or encryption is required in the communication between the virtual networks.
* Performance. A low-latency, high-bandwidth connection between resources in different virtual networks.
* Communication. The ability for resources in one virtual network to communicate with resources in a different virtual network, once the virtual networks are peered.
* Seamless. The ability to transfer data across Azure subscriptions, deployment models, and across Azure regions.
* No disruption. No downtime to resources in either virtual network when creating the peering, or after the peering is created.

![image](https://user-images.githubusercontent.com/4239376/189206979-5a706e1f-9be9-484b-97cd-71e0f8ef524a.png)

## VNet is non-transitive
    
VNet Peering is nontransitive. When you establish VNet peering between VNet1 and VNet2 and between VNet2 and VNet3, VNet peering capabilities do not apply between VNet1 and VNet3.
    
* Implement a multi-level hub and spoke architecture.
* Overcome the limit on the number of VNet peerings per virtual network.
  
![image](https://user-images.githubusercontent.com/4239376/189208010-a12b91d1-20f3-4d92-b663-c607e6e7e382.png)

## VNet Global Peering vs Virtual Network Peering

* Virtual network peering connects virtual networks in the same Azure region, such as two virtual networks in North Europe.
* Global virtual network peering connects virtual networks that are in different Azure regions, such as a virtual network in North Europe and a virtual network in West Europe.

## Vnet Peering Usecases

* Cross-subscription virtual network peering. You can use virtual network peering even when both virtual networks are in different subscriptions. This set up might be necessary for mergers and acquisitions or to connect virtual networks in subscriptions that different departments manage. Virtual networks can be in different subscriptions, and the subscriptions can use the same or different Azure Active Directory tenants.

* Gateway transit. You can connect to your on-premises network from a peered virtual network if you enable gateways transit from a virtual network that has a VPN gateway. 

* Overlapping address spaces. IP address spaces of connected networks within Azure, between Azure and your on-premises network can't overlap. 
![image](https://user-images.githubusercontent.com/4239376/190232252-14f36ff7-24d3-4537-8f99-b0dcc1b16433.png)


## VPN Gateway vs VNet peering

* A VPN gateway is a specific type of VNet gateway that is used to send traffic between an Azure virtual network and an on-premises location over the public internet. You can also use a VPN gateway to send traffic between VNets. Each VNet can have only one VPN gateway.
    
[https://azure.microsoft.com/en-us/blog/vnet-peering-and-vpn-gateways/](https://azure.microsoft.com/en-us/blog/vnet-peering-and-vpn-gateways/)

![image](https://user-images.githubusercontent.com/4239376/189207302-17f68f0d-4423-4621-bcbf-efc941a74e0f.png)
    
![image](https://user-images.githubusercontent.com/4239376/189207320-54d54ddc-4047-4d2f-8f63-2972c3b57a82.png)

    
## Which is best for you?

While we offer two ways to connect VNets, based on your specific scenario and needs, you might want to pick one over the other.

* VNet Peering provides a low latency, high bandwidth connection useful in scenarios such as cross-region data replication and database failover scenarios. Since traffic is completely private and remains on the Microsoft backbone, customers with strict data policies prefer to use VNet Peering as public internet is not involved. Since there is no gateway in the path, there are no extra hops, ensuring low latency connections.

* VPN Gateways provide a limited bandwidth connection and is useful in scenarios where encryption is needed, but bandwidth restrictions are tolerable. In these scenarios, customers are also not as latency-sensitive.
    
# Q & A
    
1. Which of the following allows peered virtual networks to share the gateway and get access to resources?
* Gateway transit
    
2. Virtual network peering is successfully established when the peering status for both virtual network peerings shows which status?
* Connected
    
</details>

<details>
<summary>VPN Gateway. SKU. Configurations. Connect to VPN Gateway network</summary>

![image](https://user-images.githubusercontent.com/4239376/189523382-b5983f25-9185-4b72-b3f6-cee2b93fe86b.png)

**A VPN gateway is a specific type of virtual network gateway that is used to send encrypted traffic between an Azure virtual network and an on-premises location over the public Internet. You also use a VPN gateway to send encrypted traffic between Azure virtual networks over the Microsoft network.**

* Site-to-site connections connect on-premises datacenters to Azure virtual networks
* VNet-to-VNet connections connect Azure virtual networks (custom)
* Point-to-site (User VPN) connections connect individual devices to Azure virtual networks

![image](https://user-images.githubusercontent.com/4239376/189523400-ffa6ac9d-6b80-4ffc-aaa7-e27ce9517294.png)

## VPN Gateway vs VNet peering

* A VPN gateway is a specific type of VNet gateway that is used to send traffic between an Azure virtual network and an on-premises location over the public internet. You can also use a VPN gateway to send traffic between VNets. Each VNet can have only one VPN gateway.
    
## VPN Gateway creation
    
* Before creating a virtual network gateway for your virtual network, you first need to create the gateway subnet. The gateway subnet contains the IP addresses that are used by the virtual network gateway. If possible, it's best to create a gateway subnet by using a CIDR block of /28 or /27 to provide enough IP addresses to accommodate future configuration requirements.

* When you create your gateway subnet, gateway VMs are deployed to the gateway subnet and configured with the required VPN gateway settings. Never deploy other resources (for example, additional VMs) to the gateway subnet. The gateway subnet must be named GatewaySubnet. 
    
## VPN Types. Route-based vs Policy-based

  VPN type. Route based or Policy based. Most VPN types are Route-based. The type of VPN you choose depends on the make and model of your VPN device, and the kind of VPN connection you intend to create. Typical route-based gateway scenarios include point-to-site, inter-virtual network, or multiple site-to-site connections. Route-based is also selected when you coexist with an ExpressRoute gateway or if you need to use IKEv2. Policy-based gateways support only IKEv1.

## SKU Types

  Use the drop-down to select a gateway SKU. Your choice will affect the number of tunnels you can have and the aggregate throughput benchmark. The benchmark is based on measurements of multiple tunnels aggregated through a single gateway. It is not a guaranteed throughput due to Internet traffic conditions and your application behaviors.
  
Generations:   
* Generation1 
* Generation2. 

  You cannot change generations or SKUs across generations. Basic and VpnGw1 SKUs are only supported in Generation1. VpnGw4 and VpnGw5 SKUs are only supported in Generation2.
 
![image](https://user-images.githubusercontent.com/4239376/189523479-56aa01b6-e6ee-4be9-b490-e7cd193adb58.png)

## VPN Gateway Type. Route-based VPNs vs Policy-based

* Route-based VPNs. Route-based VPNs use routes in the IP forwarding or routing table to direct packets into their corresponding tunnel interfaces. The tunnel interfaces then encrypt or decrypt the packets in and out of the tunnels. The policy (or traffic selector) for Route-based VPNs are configured as any-to-any (or wild cards).

* Policy-based VPNs. Policy-based VPNs encrypt and direct packets through IPsec tunnels based on the IPsec policies configured with the combinations of address prefixes between your on-premises network and the Azure VNet. The policy (or traffic selector) is defined as an access list in the VPN device configuration. When using a Policy-based VPN, keep in mind the following limitations:

Extra details:  

* Policy-Based VPNs can only be used on the Basic gateway SKU and is not compatible with other gateway SKUs.
* You can have only one tunnel when using a Policy-based VPN.
* You can only use Policy-based VPNs for S2S connections, and only for certain configurations. Most VPN Gateway configurations require a Route-based VPN.
  
## Connect to VPN Network
    
### Prerequisites
Set up the on-premises VPN gateway and decive you are going to use connecting to VPN Gateway in Azure.

    To configure your VPN device, you will need:

* A shared key. The same shared key that you specify when creating the VPN connection.
* The public IP address of your VPN gateway. The IP address can be new or existing.
    
![image](https://user-images.githubusercontent.com/4239376/189523759-ba5f4aef-d802-4629-9ab5-bd31f3991a97.png)
   
* Name. Enter a name for your connection.
* Connection type. Select Site-to-Site (IPSec) from the drop-down.
* Shared key (PSK). In this field, enter a shared key for your connection. You can generate or create this key yourself. In a site-to-site connection, the key you use is the same for your on-premises device and your virtual network gateway connection.
    
</details>

<details>
<summary>VPN. High-availability (HA) scenarios. Active - standby vs Active - active</summary>
    
![image](https://user-images.githubusercontent.com/4239376/189523923-39e51b49-1e0f-4b28-9abf-13cee3b4b673.png)
![image](https://user-images.githubusercontent.com/4239376/189523932-a6fa3ae7-b62d-4fa2-845f-8e6eab6ee3cb.png)
   
</details>

<details>
<summary>VPN. ExpressRoute + Site-to-site vpn as a failover path. ExpressRoute vs VPN Gateway.</summary>
  
![image](https://user-images.githubusercontent.com/4239376/189525781-39ac2fae-7379-4375-82c2-0336d8c62746.png)
    
## Consideration between options
![image](https://user-images.githubusercontent.com/4239376/189525862-2bc3b9ac-140c-447c-814f-eb85070c30dc.png)
    
</details>

<details>
<summary>Virtual WAN. WAN Types</summary>
  
Azure Virtual WAN is a networking service that provides optimized and automated branch connectivity to, and through, Azure. Azure regions serve as hubs that you can choose to connect your branches to. You use the Azure backbone to connect branches and enjoy branch-to-VNet connectivity.
    
Azure Virtual WAN brings together many Azure cloud connectivity services such as site-to-site VPN, User VPN (point-to-site), and ExpressRoute into a single operational interface. 
    
![image](https://user-images.githubusercontent.com/4239376/189525905-aa8eeaf7-73c7-4874-9524-8c1b8f87dd96.png)

## WAN Types
![image](https://user-images.githubusercontent.com/4239376/189525921-50d488af-b03f-44e6-9211-ab2489a36faf.png)

    
</details>

<details>
<summary>ASG. Application Security Group. Advantages. Example</summary>

## ASG

Application Security Groups (ASGs) ) logically group virtual machines by workload and define network security rules based on those groups. ASGs work in the same way as NSGs but provide an application-centric way of looking at your infrastructure.

## Example: 

![image](https://user-images.githubusercontent.com/4239376/189197524-fb66aa41-5de5-4332-990b-007f954edcf8.png)

* Let’s consider a usage case for an online retailer. In this scenario, it's important to control the network traffic to the application virtual machines. Here are the requirements.

* Shoppers access the company’s product catalog hosted on Web Servers. The Web Servers must be accessible from the internet over HTTP port 80 and HTTPS port 443.

* Inventory information is located on Database Servers. The Database Servers must be accessible over port 1433. Only the Web Servers should have access to the Database Servers.

### Answer:

For this scenario, we would:

Create an ASG (WebASG) that groups the Web Servers. Create another ASG (DBASG) that groups the Database Servers. Assign the corresponding server NICs to each ASG.  
Inside the NSG, create following rules:  

* Priority: 100, allow access from the internet to WebASG with port 80 and 443.
* Priority: 110, allow access from WebASG to DBASG with port 1433.
* Priority: 120, deny access from anywhere to DBASG with port 1433.

## ASG Advantages

* The configuration doesn’t require specific IP addresses. It would be difficult to specify IP addresses because of the number of servers and because the IP addresses could change. You also don't need to arrange the servers into a specific subnet.

* This configuration doesn't require multiple rule sets. You don't need to create a separate rule for each VM. You can dynamically apply new rules to ASG. New security rules are automatically applied to all the VMs in the Application Security Group.

* The configuration is easy to maintain and understand since is based on workload usage.


</details>

<details>
<summary>DNS. Custom Domain names. DNS zones. DNS record sets. TTL. Private DNS zones</summary>

When you create an Azure subscription, an Azure AD domain is automatically created. This instance of the domain has an initial domain name in the form domainname.onmicrosoft.com. 
    
## Information about domain names

* You must be a global administrator to perform domain management tasks. The global administrator is the user who created the subscription.  
* Domain names in Azure AD are globally unique. When one Azure AD directory has verified a domain name, other directories can't use that name.  
* Before a custom domain name can be used by Azure AD, the custom domain name must be added to your directory and verified.  

## Domain name verification
    
After adding the custom domain name, you must verify ownership of the domain name. Verification is performed by adding a DNS record. The DNS record can be MX or TXT. Once the DNS record is added, Azure will query the DNS domain for the presence of the record. This could take several minutes or several hours. When Azure verifies the presence of the DNS record, it will then add the domain name to the subscription.
    
## DNS Zones

* A DNS zone hosts the DNS records for a domain. So, to start hosting your domain in Azure DNS, you need to create a DNS zone for that domain name. Each DNS record for your domain is then created inside this DNS zone.
    
* To delegate your domain to Azure DNS, you first need to know the name server names for your zone. Each time a DNS zone is created Azure DNS allocates name servers from a pool. Once the Name Servers are assigned, Azure DNS automatically creates authoritative NS records in your zone.
    
![image](https://user-images.githubusercontent.com/4239376/189201476-c950dec5-ccb9-40ff-ad99-7de85f2bd18e.png)

## Child Domains
    
  If you want to set up a separate child zone, you can delegate a subdomain in Azure DNS. For example, after configuring contoso.com in Azure DNS, you could configure a separate child zone for partners.contoso.com.

  Setting up a subdomain follows the same process as typical delegation. The only difference is that NS records must be created in the parent zone contoso.com in Azure DNS, rather than in the domain registrar.
    
    
## DNS Record Sets
    
It's important to understand the difference between DNS record sets and individual DNS records. A record set is a collection of records in a zone that have the same name and are the same type.
    
![image](https://user-images.githubusercontent.com/4239376/189202149-0d2e01a8-83e3-4796-a28b-564edb83bc2a.png)

* A record set cannot contain two identical records. Empty record sets (with zero records) can be created, but do not appear on the Azure DNS name servers. Record sets of type CNAME can contain one record at most.
    
* The Add record set page will change depending on the type of record you select. For an A record, you will need the TTL (Time to Live) and IP address. The time to live, or TTL, specifies how long each record is cached by clients before being requeried.
    
![image](https://user-images.githubusercontent.com/4239376/189202362-e375ea41-af6f-4115-8089-9a74cb634eaf.png)

## Private DNS zones

When using private DNS zones, you can use your own custom domain names rather than the Azure-provided names. Using custom domain names helps you to tailor your virtual network architecture to best suit your organization's needs. It provides name resolution for virtual machines (VMs) within a virtual network and between virtual networks. Additionally, you can configure zones names with a split-horizon view, which allows a private and a public DNS zone to share the name.
    
![image](https://user-images.githubusercontent.com/4239376/189202579-9440d2a9-a961-4470-b38c-3c0d146277df.png)
    
## Azure private DNS benefits
    
* Removes the need for custom DNS solutions. Previously, many customers created custom DNS solutions to manage DNS zones in their virtual network. You can now perform DNS zone management by using the native Azure infrastructure. This removes the burden of creating and managing custom DNS solutions.
* Use all common DNS records types. Azure DNS supports A, AAAA, CNAME, MX, PTR, SOA, SRV, and TXT records.
* Automatic hostname record management. Along with hosting your custom DNS records, Azure automatically maintains hostname records for the VMs in the specified virtual networks. In this scenario, you can optimize the domain names you use without needing to create custom DNS solutions or modify applications.
* Hostname resolution between virtual networks. Unlike Azure-provided host names, private DNS zones can be shared between virtual networks. This capability simplifies cross-network and service-discovery scenarios, such as virtual network peering.
* Familiar tools and user experience. To reduce the learning curve, this new offering uses well-established Azure DNS tools (PowerShell, Azure Resource Manager templates, and the REST API).
* Split-horizon DNS support. With Azure DNS, you can create zones with the same name that resolve to different answers from within a virtual network and from the public internet. A typical scenario for split-horizon DNS is to provide a dedicated version of a service for use inside your virtual network.
* Available in all Azure regions. The Azure DNS private zones feature is available in all Azure regions in the Azure public cloud.
    
    
### Private DNS. Scenario 1: Name resolution scoped to a single virtual network

![image](https://user-images.githubusercontent.com/4239376/189202934-3b8c5c15-cff8-4302-b6d6-ed74931a6409.png)

  In this scenario, you have a virtual network and resources in Azure, including virtual machines (VMs). You want to resolve the resources from within the virtual network via a specific domain name (DNS zone). You also need the name resolution to be private and not accessible from the internet. Furthermore, for the VMs within the VNET, you need Azure to automatically register them into the DNS zone.

  In the above diagram, VNET1 contains two VMs (VM1 and VM2). Each VM has a private IP address. When you create a Private Zone (contoso.lab) and link it to VNet1, Azure DNS will automatically create two A records in the zone if you enable auto registration in the link configuration. DNS queries from VM1 to resolve VM2.contoso.lab will receive a DNS response that contains the Private IP of VM2. And, a Reverse DNS query (PTR) for the Private IP of VM1 (10.0.0.4) issued from VM2 will receive a DNS response that contains the FQDN of VM1, as expected.
    
### Scenario 2: Name resolution for multiple networks    
    
![image](https://user-images.githubusercontent.com/4239376/189203157-41fb8499-4584-44fb-9227-d9ae421d8e96.png)
    
  Name resolution across multiple virtual networks is probably the most common usage for DNS private zones. The following diagram shows a simple version of this scenario where there are only two virtual networks - VNet1 and VNet2.
    
* VNet1 is designated as a Registration virtual network and VNET2 is designated as a Resolution virtual network.
* The intent is for both virtual networks to share a common zone contoso.lab.
* The Resolution and Registration virtual networks are linked to the zone.
* DNS records for the Registration VNet VMs are automatically created. You can manually add DNS records for VMs in the Resolution virtual network.
    
#### In this configuration:

* DNS queries across the virtual networks are resolved. A DNS query from a VM in the Resolution VNet, for a VM in the Registration VNet, will receive a DNS response containing the Private IP of VM.
* Reverse DNS queries are scoped to the same virtual network. A Reverse DNS (PTR) query from a VM in the Resolution virtual network, for a VM in the Registration VNet, will receive a DNS response containing the NXDOMAIN of the VM. But, a reverse DNS query from a VM in the Resolution VNet, for a VM in the same VNet, will receive the FQDN.
    
# Q & A
    
1. Azure Private DNS allows which of the following?
    
* Lets organizations manage and resolve domain names in a virtual network without adding a custom DNS solution.
Correct. Azure Private DNS manages and resolves domain names in a virtual network without adding a custom DNS solution.

2. Which of the following best summarizes the purpose of Azure DNS?
* Manages and hosts the registered domain and associated records.
Correct. Azure DNS hosts the registered domains. Administrators can control and configure the domain records, like A, CNAME, MX, and set up alias records.

3. What type of DNS record should be created to map one or more IP addresses against a single domain?

* A or AAAA
Correct. The A or AAAA record maps an IP address to a domain. Multiple IP addresses are known as a record set.

</details>

<details>
<summary>User-defined routes (UDR). System routes.</summary>

## initial scheme
Azure uses system routes to direct network traffic between virtual machines, on-premises networks, and the Internet. 
![image](https://user-images.githubusercontent.com/4239376/189526414-ea3e491a-307d-4d27-864b-70dcd591caf2.png)

## User-defined routes when you want to customize behavior
![image](https://user-images.githubusercontent.com/4239376/189526460-3577f026-ee04-400a-b26c-2c89fcc55d58.png)

</details>

<details>
<summary>Network Watcher. Visualize Network Topology</summary>

* Regional service
* Network Watcher provides tools to monitor, diagnose, view metrics, and enable or disable logs for resources in an Azure virtual network. 
* Verify IP Flow: Quickly diagnose connectivity issues from or to the internet and from or to the on-premises environment.
> When you deploy a VM, Azure applies several default security rules to the VM. These rules allow or deny traffic to or from the VM. You might override Azure's default rules or create additional rules. At some point, a VM may become unable to communicate with other resources, because of a security rule.

![image](https://user-images.githubusercontent.com/4239376/189740671-1ab02cc6-1682-47c9-b179-adf3579c4426.png)

* Next Hop: To determine if traffic is being directed to the intended destination by showing the next hop. This will help determine if networking routing is correctly configured.

* Visualize Network Topology

![image](https://user-images.githubusercontent.com/4239376/189740739-f288ee2d-2941-469f-b6a1-51d488208095.png)


</details>

# Load Balancing. Application Gateway. Load Balancer. Front Door

<details>
<summary>Azure Application Gateway. Front Door</summary>

# Application Gateway. Features
    
![image](https://user-images.githubusercontent.com/4239376/189547356-3fc92ea8-6f3d-41b8-8ce1-b9e9a6241bff.png)

The Application Gateway uses application layer routing. Application layer routing routes traffic to a pool of web servers based on the URL of a request. The back-end pool can include Azure virtual machines, Azure virtual machine scale sets, Azure App Service, and even on-premises servers.
    
* Support for the HTTP, HTTPS, HTTP/2 and WebSocket protocols.
* A web application firewall to protect against web application vulnerabilities.
* End-to-end request encryption.
* Autoscaling, to dynamically adjust capacity as your web traffic load change.
    
Can work together with WAF
    
![image](https://user-images.githubusercontent.com/4239376/189547415-429e43d0-9c2d-4a51-8185-aabc75bae9f3.png)

# Applicateion Gateway Inside
    
![image](https://user-images.githubusercontent.com/4239376/189547549-0307f644-1a95-4116-be5b-64122e18536f.png)

![image](https://user-images.githubusercontent.com/4239376/189547556-eccd0a5e-56b1-4a30-a69b-16602303b48e.png)

![image](https://user-images.githubusercontent.com/4239376/189547561-2967a0ed-37a5-47e0-92af-694ed1f264f5.png)

    
## Application Gateway Routing. Multiple Site routing. Path-based routing
 
### Multiple Site Routing:
    
![image](https://user-images.githubusercontent.com/4239376/189547439-32e11095-6a41-426c-9cc2-729d7fa40e62.png)

Multiple site routing configures more than one web application on the same application gateway instance. In a multi-site configuration, you register multiple DNS names (CNAMEs) for the IP address of the Application Gateway, specifying the name of each site. 
    
### Path-based routing
    
![image](https://user-images.githubusercontent.com/4239376/189547486-94c2c524-0b51-4291-a477-0cb0caac14de.png)

Path-based routing sends requests with different URL paths to different pools of back-end servers. For example, you could direct requests with the path /video/* to a back-end pool containing servers that are optimized to handle video streaming, and direct /images/* requests to a pool of servers that handle image retrieval.
    
# Front Door. Features
    
Azure Front Door supports dynamic site acceleration (DSA), TLS/SSL offloading and end to end TLS, Web Application Firewall, cookie-based session affinity, url path-based routing, free certificates and multiple domain management, and others.

# Application gateway vs Front Door
While both Front Door and Application Gateway are layer 7 (HTTP/HTTPS) load balancers, the primary difference is that Front Door is a non-regional service whereas Application Gateway is a regional service. While Front Door can load balance between your different scale units/clusters/stamp units across regions, Application Gateway allows you to load balance between your VMs/containers etc. that is within the scale unit.
    
</details>

# BACKUP Services: Site Recovery. Azure Backups. Managed Disks Snapshots

![image](https://user-images.githubusercontent.com/4239376/189547585-7bd8bb00-468d-4ae4-b3b8-1be016a58260.png)

<details>
<summary>Snapshots. Managed Disks Snapshots. Recovery Services Vault</summary>

![image](https://user-images.githubusercontent.com/4239376/189546975-e0d74a97-682a-402d-9e9e-6e2e4c711b8b.png)
    
![image](https://user-images.githubusercontent.com/4239376/189547008-eb8088ed-71db-47fc-9d0b-73a48a60072b.png)

</details>

<details>
<summary>Azure Backup. Azure Backup Server</summary>

![image](https://user-images.githubusercontent.com/4239376/189547050-8ba535c0-9b7f-48f9-8ce8-5e376d109b07.png)

An Azure backup job consists of two phases. First, a virtual machine snapshot is taken. Second, the virtual machine snapshot is transferred to the Azure Recovery Services vault.

## Azure Backup vs Azure Backup Server

**AZURE BACKUP AGENT - Also known as MARS. You may find it under "On-premises file and folder backups" section**
    
![image](https://user-images.githubusercontent.com/4239376/189547139-ea301353-d323-43e8-b58f-f16e933a58f4.png)


</details>

<details>
<summary>Azure Site Recovery</summary>

Site Recovery helps ensure business continuity by keeping business apps and workloads running during outages. Site Recovery replicates workloads running on physical and virtual machines (VMs) from a primary site to a secondary location. When an outage occurs at your primary site, you fail over to secondary location, and access apps from there. After the primary location is running again, you can fall back to it.

![image](https://docs.microsoft.com/en-us/training/wwl-azure/configure-virtual-machine-backups/media/site-recovery-scenarios-388c71fd.png)

## Scenarios

* Replicate Azure VMs from one Azure region to another.
* Replicate on-premises VMware VMs, Hyper-V VMs, physical servers (Windows and Linux), Azure Stack VMs to Azure.
* Replicate AWS Windows instances to Azure.
* Replicate on-premises VMware VMs, Hyper-V VMs managed by System Center VMM, and physical servers to a secondary site.

## Features

* Using Site Recovery, you can set up and manage replication, failover, and failback from a single location in the Azure portal.
* Replication to Azure eliminates the cost and complexity of maintaining a secondary datacenter.
* Site Recovery orchestrates replication without intercepting application data. When you replicate to Azure, data is stored in Azure storage, with the resilience that it provides. When failover occurs, Azure VMs are created, based on the replicated data.
* Site Recovery provides continuous replication for Azure VMs and VMware VMs, and replication frequency as low as 30 seconds for Hyper-V.
* You can replicate using recovery points with application-consistent snapshots. These snapshots capture disk data, all data in memory, and all transactions in process.
* You can run planned failovers for expected outages with zero-data loss, or unplanned failovers with minimal data loss (depending on replication frequency) for unexpected disasters. You can easily fall back to your primary site when it's available again.
* Site Recovery integrates with Azure for simple application network management, including reserving IP addresses, configuring load-balancers, and integrating Azure * * Traffic Manager for efficient network switchovers.

</details>
    
<details>
<summary>Recovery Services vault</summary>
    
Recovery Services vaults store backup data for various Azure services such as IaaS VMs (Linux or Windows) and Azure SQL databases. Recovery Services vaults support System Center DPM, Windows Server, Azure Backup Server, and other services. Recovery Services vaults make it easy to organize your backup data, while minimizing management overhead.
    
![image](https://user-images.githubusercontent.com/4239376/190237732-f37b6acb-0271-4c20-b413-5985b6198b38.png)

## Recovery Services Vault

**Recovery Services vault** is a storage entity in Azure that houses data. The data is typically copies of data, or configuration information for virtual machines (VMs), workloads, servers, or workstations. You can use Recovery Services vaults to hold backup data for various Azure services such as IaaS VMs (Linux or Windows) and Azure SQL databases. Recovery Services vaults support System Center DPM, Windows Server, Azure Backup Server, and more. Recovery Services vaults make it easy to organize your backup data, while minimizing management overhead.  

**Can be used to backup on-premises virtual machines including: Hyper-V, VMware, System State, and Bare Metal Recovery.**

![image](https://user-images.githubusercontent.com/4239376/189547107-f1187c07-ebba-4863-847b-43b78113a6cb.png)
    
</details>
    
<details>
<summary>On-premises file and folder backups</summary>

![image](https://user-images.githubusercontent.com/4239376/190238182-331dfcf4-c1bf-484f-ae29-e5153e321986.png)

1. Create the recovery services vault. Within your Azure subscription, you will need to create a recovery services vault for the backups.
2. Download the agent and credential file. The recovery services vault provides a link to download the Azure Backup Agent. The Backup Agent will be installed on the local machine. There is also a credentials file that is required during the installation of the agent. You must have the latest version of the agent. Versions of the agent below 2.0.9083.0 must be upgraded by uninstalling and reinstalling the agent.
3. Install and register agent. The installer provides a wizard to configure the installation location, proxy server, and passphrase information. The downloaded credential file will be used to register the agent.
4. Configure the backup. Use the agent to create a backup policy including when to backup, what to backup, how long to retain items, and settings like network throttling.
    
</details>

# Azure Monitoring options. Azure Monitoring Agents & Extensions. Log Analytics Workspace

![image](https://docs.microsoft.com/en-us/training/modules/monitor-performance-using-azure-monitor-for-vms/media/2-azure-monitor-overview.png)

    
<details>
<summary>Azure Monitoring options. Azure Monitoring Agents & Extensions. Log Analytics Workspace</summary>
    
> Log Analytics workspaces are containers where Azure Monitor data is collected, aggregated, and analyzed. To better understand Log Analytics workspaces, the following diagram provides more insight into all the different types of logs that can be ingested.

![image](https://user-images.githubusercontent.com/4239376/190251031-2d11a174-aee7-42ab-87e2-53bdea4175f2.png)

    
### Extensions and Agents
    
![image](https://user-images.githubusercontent.com/4239376/190249214-47815085-91ec-4713-8db6-cf3b229e6ac0.png)

</details> 

# Azure DNS 

<details>
<summary>Azure DNS. A, AAAA, CNAME, DNS Private Zone. Alias Records, Apex Domain.</summary>

Learning Path, Register name in DNS, resolve Name Service (NS Record): https://learn.microsoft.com/en-us/training/modules/host-domain-azure-dns

### Record types

![image](https://user-images.githubusercontent.com/4239376/190914050-a7f3f51f-6f76-4370-9524-e60ea0bfc51e.png)

### Name Server (NS Record)
    
Name server is the server to which your Domain Name Registar delegates resolving. (in our case - Key-value storage on Azure side)
    
![image](https://user-images.githubusercontent.com/4239376/190914367-7254c195-770a-4a01-a337-348d1b9691da.png)

    
### Apex Domain, Root Domain
    
The apex domain is the highest level of your domain. In our case, that's wideworldimports.com. The apex domain is also sometimes referred to as the zone apex or root apex. It's often represented by the @ symbol in your DNS zone records.
    
![image](https://user-images.githubusercontent.com/4239376/190914315-53d04304-48fd-424a-bd76-456948776fd9.png)

### Alias Record
    
![image](https://user-images.githubusercontent.com/4239376/190914440-51d2f516-da61-478f-ace8-a75e79a3ce25.png)

You may use it to automatically update DNS records due to dynamic Ip-addresses or in case when you resource went down
    
![image](https://user-images.githubusercontent.com/4239376/190914497-55b357d5-dc38-4917-8c3d-e60d1126409a.png)


### Private DNS Zone

To provide name resolution for virtual machines (VMs) within a virtual network and between virtual networks, create a private DNS zone.

</details>

<details>
<summary>Azure DNS with Load Balancer (Traffic Manager)</summary>

Using Alias records you may conenct several web services to serve one DNS name. You may direct your traffic to Load balancer instead of VM.
    
</details>

