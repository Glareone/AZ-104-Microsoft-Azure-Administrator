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
