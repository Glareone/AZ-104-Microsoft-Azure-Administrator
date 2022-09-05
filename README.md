# AZ-104 Microsoft Azure Administrator Exam. Materials, Tips, Hints.

## Learning Path

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
