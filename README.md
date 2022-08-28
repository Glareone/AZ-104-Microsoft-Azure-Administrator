# AZ-104 Microsoft Azure Administrator Exam. Materials, Tips, Hints.

## Learning Path

## Azure Active Directory, Azure Active Directory Domain Services (AD DS)

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
