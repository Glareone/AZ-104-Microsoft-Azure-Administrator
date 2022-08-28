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
