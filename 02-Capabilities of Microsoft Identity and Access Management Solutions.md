[TOC]

# Describe the capabilities of Microsoft Identity and Access Management Solutions (25-30%) 



## Identity Principles and Concepts

### Identity as the primary security perimeter

[Define Identity as the primary security perimeter - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-identity-principles-concepts/3-define-identity-primary-security-perimeter)

- The traditional perimeter based security model is no longer enough. Identity has become the new security perimeter that enables organisations to secure their assets.
- Enterprise security needs to adapt new reality, security perimeter can no longer be viewed as on-premises network, it now extends to,
  - SaaS app for business critical work may be hosted outside the corporate network.
  - BYOD devices that employees are using to access corporate network while working from home.
  - Unmanaged device that a customer or partner is using to access corporate data or collaborating with employees.
  - IoT devices installed throughout your corporate network and inside customer locations.

![Identity is the new security perimeter](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-identity-principles-concepts/media/3-identity-new-security-perimeter.png)

### Four Pillars of Identity

Addressing following four pillars is key to a comprehensive and robust identity and access control situation.

1. Administration
2. Authentication
3. Authorisation
4. Auditing



### Common Identity Attacks

[Describe common identity attacks - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-identity-principles-concepts/2-describe-common-identity-attacks)

- Some of the most common types of security threats that organisation face today.

- Design to steal credentials to authenticate that someone or something is who they are claiming to be, resulting in Identity Theft.

- To protect against such Identity attacks, robust security and monitoring is needed. ***Risk detections in Azure AD Identity Protection include identified suspicious actions related to user accounts.***

- There are **two types of Risk,**

  - **User Risk**
    - Represent the probability that a given identity or account is compromised.
  - **Sign-in Risk**
    - Represent the probability that a given authentication request is not authorised by the identity owner.

  #### Password-based Attacks

  ![Password spray attack](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-identity-principles-concepts/media/2-password-spray-attack.png)

  - This includes Password spray attacks and Brute force attacks.
    - ***Password Spray Attack***, this attack attempts to match a username against a list of weak passwords
    - ***Brute Force Attack***, this attack try many passwords against one or more accounts, sometimes using dictionaries of commonly used passwords. 

  #### Phishing Attack

  - A phishing attack is when a hacker sends an email that appears to come from a reputable source. 

  #### Spear Phishing Attack

  - A spear phishing scam is a variant on Phishing. Hackers build databases of information about users, which can be used to create highly credible emails. The email may appear to have come from someone in your organisation who is requesting information. 

### Authentication (AuthN)

Identity authentication determines if the person is who they say they are. Authentication relies on additional data that is difficult to produce, except by that specific person.

[What is Authentication - YouTube](https://www.youtube.com/watch?v=927KdwZZoU0)

[Identity Authentication – Are They Who They Say They Are? (trulioo.com)](https://www.trulioo.com/blog/identity-authentication)

### Authorisation (AuthZ)

Authorization is the process of giving someone the ability to access a resource.

[What is Authorization? - Examples and definition - Auth0](https://auth0.com/intro-to-iam/what-is-authorization/)



### Modern Authentication

[Describe modern authentication and the role of the identity provider - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-identity-principles-concepts/4-describe-modern-authentication-role-identity-provider)

- Morden authentication is an umbrella term for AuthN and AuthZ methods between a client, such as your laptop or phone, and a server, like a website or application.

  

### Identity Providers (IdP) 

[Describe modern authentication and the role of the identity provider - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-identity-principles-concepts/4-describe-modern-authentication-role-identity-provider)

- Identity Provider (IdP) is the role at the centre of modern authentication.

- All services including all AuthN services are supplied by a central Identity Provider. Information that is used to authenticate the user with the server is stored and managed centrally by the Identity Provider (IdP).

- With a central identity provider, organizations can establish authentication and authorization policies, monitor user behaviour, identify suspicious activities, and reduce malicious attacks.

- Microsoft Azure Active Directory is an example of a cloud-based identity provider. Other examples include Twitter, Google, Amazon, LinkedIn, and GitHub.

- Another fundamental capability of an identity provider (IdP) and “modern authentication” is the support for single sign-on (SSO). With SSO, the user logs in once and that credential is used to access multiple applications or resources. When you set up SSO between multiple identity providers, it's called federation.

  

### Federated Services

[Describe the concept of Federated Services - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-identity-principles-concepts/5-describe-concept-federated-services)

- Federation enables the access of services across organizational or domain boundaries by establishing trust relationships between the respective domain’s identity provider. With federation, there's no need for a user to maintain a different username and password when accessing resources in other domains.

![Simplifed view of how federation works](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-identity-principles-concepts/media/5-federated-identification.png)

- The simplified way to think about this federation scenario is as follows:
  - The website uses the authentication services of IdP-A.
  - The user authenticates with IdP-B.
  - IdP-A has a trust relationship configured with IdP-B.
  - When the user’s credentials are passed to the website, the website trusts the user and allows access.
- **With federation, trust isn't always bidirectional. Although IdP-A may trust IdP-B and allow the user in domain B to access the website in domain A, the opposite isn't true, unless that trust relationship is configured.**
- A common example of federation in practice is when a user logs in to a third-party site with their social media account, such as Twitter. In this scenario, Twitter is an identity provider, and the third-party site might be using a different identity provider, such as Azure AD. There's a trust relationship between Azure AD and Twitter.



## Basic Identity services and Identity types of Azure AD

### Concept of Directory Services and Active Directory

[Describe the concept of directory services and active directory - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-identity-principles-concepts/6-describe-concept-of-directory-services-active-directory)

- **Directory Service**
  - In the context of a computer network, a directory is a hierarchical structure that stores information about objects on the network. A directory service stores directory data and makes it available to network users, administrators, services, and applications.
- **Active Directory (AD)**
  - Active Directory (AD) is a set of directory services developed by Microsoft as part of Windows 2000 for on-premises domain-based networks. The best-known service of this kind is Active Directory Domain Services (AD DS). It stores information about members of the domain, including devices and users, verifies their credentials, and defines their access rights. A server running AD DS is a domain controller (DC).
  - AD DS is a central component in organizations with on-premises IT infrastructure. AD DS gives organizations the ability to manage multiple on-premises infrastructure components and systems using a single identity per user. AD DS doesn't, however, natively support mobile devices, SaaS applications, or line of business apps that require *modern authentication* methods.

- **Azure Active Directory (Azure AD)**
  - Azure Active Directory is the next evolution of identity and access management solutions. It provides organizations with an Identity as a Service (IDaaS) solution for all their apps across cloud and on-premises.

#### What is Azure Active Directory?

[Describe what is Azure Active Directory - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/explore-basic-services-identity-types/2-describe-what-azure-active-directory)

- Azure Active Directory (Azure AD) is Microsoft’s cloud-based identity and access management service. Organizations use Azure AD to enable their employees, guests, and others to sign in and access the resources they need, including:
  - ***Internal resources***, such as apps on your corporate network and intranet, and cloud apps developed by your own organization.
  - ***External services***, such as Microsoft Office 365, the Azure portal, and any SaaS applications used by your organization.
- Azure AD simplifies the way organizations manage authorization and access by providing a single identity system for their cloud and on-premises applications. Azure AD can be synchronized with your existing on-premises Active Directory, synchronized with other directory services, or used as a standalone service.
- Azure AD also allows organizations to securely enable the use of personal devices, such as mobiles and tablets, and enable collaboration with business partners and customers.

![Azure Active Directory works with cloud apps such as M365, devices, and on-premises applications](https://docs.microsoft.com/en-au/learn/wwl-sci/explore-basic-services-identity-types/media/azure-active-directory-diagram-expanded.png)

##### Azure AD Editions

[Describe the available Azure AD editions - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/explore-basic-services-identity-types/3-describe-available-editions)

- **Azure Active Directory Free**
  - The free version allows you to administer users and create groups, synchronize with on-premises Active Directory, create basic reports, configure self-service password change for cloud users, and enable single sign-on across Azure, Microsoft 365, and many popular SaaS apps. 
  - ***T******he free version also has an upper limit of 500000 objects that can be held in Azure AD***. The free edition is included with subscriptions to Office 365, Azure, Dynamics 365, Intune, and Power Platform.
- **Office 365 Apps**
  - The Office 365 Apps edition allows you to do everything included in the free version, plus self-service password reset for cloud users, and device write-back, which offers two-way synchronization between on-premises directories and Azure AD. 
  - The Office 365 Apps edition of Azure Active Directory is included in subscriptions to Office 365 E1, E3, E5, F1, and F3.
- **Azure Active Directory Premium P1**
  - The Premium P1 edition includes all the features in the free and Office 365 apps editions. 
  - It also supports advanced administration, such as,
    - dynamic groups, 
    - self-service group management, 
    - Microsoft Identity Manager (an on-premises identity and access management suite) and 
    - cloud write-back capabilities, which allow self-service password reset for your on-premises users.
- **Azure Active Directory Premium P2**
  - P2 offers all the Premium P1 features, and [Azure Active Directory Identity Protection](https://docs.microsoft.com/en-us/azure/active-directory/identity-protection/overview-identity-protection) to help provide risk-based Conditional Access to your apps and critical company data. 
  - P2 also gives you [Privileged Identity Management](https://docs.microsoft.com/en-us/azure/active-directory/privileged-identity-management/pim-getting-started) to help discover, restrict, and monitor administrators and their access to resources, and to provide just-in-time access when needed.
- **Other**
  - There's also an option for "**Pay as you go**" **feature licenses**. You can get other feature licenses separately, such as Azure Active Directory Business-to-Customer (B2C). B2C can help you provide identity and access management solutions for your customer-facing apps.



### Azure AD Identities

- Azure AD manages different types of identities,

  - **Users**

    - Employees and guests are represented as users in Azure AD. 
    - [Interactive Guide to create a user in Active Directory](https://edxinteractivepage.blob.core.windows.net/edxpages/Security%20fundamentals/LP02M02%20-%20Create%20a%20New%20User%20in%20Azure%20Active%20Directory/index.html)

  - **Service Principals (Applications)**

    - A service principal is a security identity used by applications or services to access specific Azure resources. You can think of it as an identity for an application.

  - **Managed Identities**

    - A managed identity is automatically managed in Azure AD. Managed identities are typically used to manage the credentials for authenticating a cloud application with an Azure service.

    - There are two types of managed identities: 

      - <u>**system-assigned**</u>

        -  Some Azure services allow you to enable a managed identity directly on a service instance. When you enable a system-assigned managed identity, an identity is created in Azure AD that's tied to the lifecycle of that service instance. When the resource is deleted, Azure automatically deletes the identity for you. 
        - By design, only that Azure resource can use this identity to request tokens from Azure AD.

      - **<u>user-assigned</u>**

        - A user-assigned managed identity is assigned to one or more instances of an Azure service. 
        - You can create a user-assigned managed identity and assign it to one or more instances of an Azure service. With user-assigned managed identities, the identity is managed separately from the resources that use it.

        

        *Difference between System-assigned and User-assigned Managed Identities*,

        | Property                       | System-assigned managed identity                             | User-assigned managed identity                               |
        | :----------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
        | Creation                       | Created as part of an Azure resource, such as an Azure virtual machine or Azure App Service. | Created as a standalone Azure resource.                      |
        | Lifecycle                      | Shared lifecycle with the Azure resource. When the parent resource is deleted, the managed identity is also deleted. | Independent life cycle. Must be explicitly deleted.          |
        | Sharing across Azure resources | Cannot be shared. Associated with a single Azure resource.   | Can be shared. A user-assigned managed identity can be associated with more than one Azure resource. |
        | Common use cases               | Workloads that are contained within a single Azure resource. Workloads for which you need independent identities, such as an application that runs on a single virtual machine. | Workloads that run on multiple resources and which can share a single identity. Workloads that need preauthorization to a secure resource as part of a provisioning flow. Workloads where resources are recycled frequently, but permissions should stay consistent. For example, a workload where multiple virtual machines need to access the same resource. |

  - **Devices**

    - A device is a piece of hardware, such as mobile devices, laptops, servers, or printer. 
    - Device identities can be set up in different ways in Azure AD, to determine properties such as who owns the device. 
    - Managing devices in Azure AD allows an organization to protect its assets by using tools such as Microsoft Intune to ensure standards for security and compliance. Azure AD also enables single sign-on to devices, apps, and services from anywhere through these devices.
    - Options for devices in Azure AD,
      - **Azure AD Registered Devices**
        - This can be Windows 10, iOS, Android, or macOS devices. Devices that are Azure AD registered are typically owned personally, rather than by the organization. 
        - They're signed in with a personal Microsoft account or another local account.
      - **Azure AD Joined Devices**
        - These devices exist only in the cloud. Azure AD joined devices are owned by an organization and signed in with their account. 
        - Users sign in to their devices with their Azure AD or synced Active Directory work or school accounts. You can configure Azure AD joined devices for all Windows 10 devices (except Windows 10 Home).
      - **Hybrid Azure AD Joined**
        - These devices can be Windows 7, 8.1, or 10, or Windows Server 2008, or newer. 
        - Devices that are hybrid Azure AD joined are owned by an organization and signed in with an Active Directory Domain Services account belonging to that organization. They exist in the cloud and on-premises.

### External Identity Types

Azure AD External Identities is a set of capabilities that enable organizations to allow access to external users, such as customers or partners. Your customers, partners, and other guest users can "bring their own identities" to sign in.

This ability for external users is enabled through Azure AD support of external identity providers like other Azure AD tenants, Facebook, Google, or enterprise identity providers.

Admins can set up federation with identity providers so your external users can sign in with their existing social or enterprise accounts instead of creating a new account just for your application.

*<u>Azure AD External Identities is a feature of Premium P1 and P2 Azure AD editions, and pricing is based on Monthly Active Users.</u>* 

[Azure AD pricing](https://azure.microsoft.com/pricing/details/active-directory/external-identities/).

**There are two different Azure AD External Identities:** 

- **<u>Business 2 Business (B2B)</u>** 
  - B2B collaboration allows you to share your apps and resources with external users.
  - B2B collaboration uses an invitation and redemption process, allowing external users to access your resources with their credentials.
  - With B2B collaboration, external users are managed in the same directory as employees but are typically annotated as guest users. Guest users can be managed in the same way as employees, added to the same groups, and so on. With B2B, SSO to all Azure AD-connected apps is supported.
- **<u>Business 2 Customers (B2C)</u>**
  - B2C is an identity management solution for consumer and customer facing apps.
  - Azure AD B2C is a **Customer Identity Access Management (CIAM)** solution. 
  - Azure AD B2C allows external users to sign in with their preferred social, enterprise, or local account identities to get single sign-on to your applications. 
  - Azure AD B2C supports millions of users and billions of authentications per day. It takes care of the scaling and safety of the authentication platform, monitoring, and automatically handling threats like denial-of-service, password spray, or brute force attacks.
  - With Azure AD B2C, external users are managed in the Azure AD B2C directory, separately from the organization's employee and partner directory. SSO to customer owned apps within the Azure AD B2C tenant is also supported.
  - Azure AD B2C is an authentication solution that you can customize with your brand so that it blends with your web and mobile applications.

![Azure AD B2C customized sign-in screen](https://docs.microsoft.com/en-au/learn/wwl-sci/explore-basic-services-identity-types/media/customized-screen.png)



### Hybrid Identities

[Describe the concept of hybrid identities - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/explore-basic-services-identity-types/6-describe-concept-of-hybrid-identities)

Organizations may use the hybrid identity model, or the cloud-only identity model. In the hybrid model, identities are created in Windows Active Directory or another identity provider, and then synchronized to Azure AD. In the cloud-only model, identities are created and wholly managed in Azure AD. Whether identities are created on-premises or in the cloud, users can access both cloud and on-premises resources.

With the hybrid model, users accessing both on-premises and cloud apps are hybrid users managed in the on-premises Active Directory. When you make an update in your on-premises AD DS, all updates to user accounts, groups, and contacts are synchronized to your Azure AD. The synchronization is managed with ***Azure AD Connect***.

![Azure AD connect manages the synchronization to Azure Active Directory](https://docs.microsoft.com/en-au/learn/wwl-sci/explore-basic-services-identity-types/media/azure-active-directory-connect-expanded.png)

**When using the hybrid model, authentication can either be done by Azure AD, which is known as *managed authentication*,** 

or

 **Azure AD redirects the client requesting authentication to another identity provider, which is known as *federated authentication*.**



One of three authentication methods can be used:

- **Password hash synchronization**. The simplest way to enable authentication for on-premises directory objects in Azure AD. Users have the same username and password that they use on-premises without any other infrastructure required.
- **Pass-through authentication (PTA)**. Provides a simple password validation for Azure AD authentication services by using a software agent that runs on one or more on-premises servers. The servers validate the users directly with an on-premises Active Directory, which ensures that the password validation doesn't happen in the cloud.
- **Federated authentication**. Azure AD hands off the authentication process to a separate trusted authentication system, such as on-premises Active Directory Federation Services (AD FS), to validate the user’s password.



## Authentication Capabilities of Azure AD

### Different authentication methods of Azure AD

Legacy applications have relied on a single form of authentication, most often a password. *Multifactor authentication* requires more than one form of verification, such as a trusted device or a fingerprint scan, to prove that an identity is legitimate. It means that, even when an identity’s password has been compromised, a hacker can't access a resource.

Multifactor authentication dramatically improves the security of an identity, while still being simple for users. The extra authentication factor must be something that's difficult for an attacker to obtain or duplicate.

The following video explains the problem with passwords, and why multifactor authentication is so important.

Azure Active Directory multifactor authentication works by requiring,

- **Something you know** – typically a password or PIN **and**
- **Something you have** – such as a trusted device that's not easily duplicated, like a phone or hardware key **or**
- **Something you are** – biometrics like a fingerprint or face scan.



The following extra forms of verification can be used with Azure Active Directory multifactor authentication:

- **Microsoft Authenticator app**
- **SMS**
- **Voice call**
- **OATH Hardware token**

![Microsoft authenticator app](https://docs.microsoft.com/en-au/learn/wwl-sci/explore-authentication-capabilities/media/2-microsoft-authenticator-app.png)



### Security defaults and multifactor authentication

Security defaults are a set of basic identity security mechanisms recommended by Microsoft. When enabled, these recommendations will be automatically enforced in your organization. The goal is to ensure that all organizations have a basic level of security enabled at no extra cost. These defaults enable some of the most common security features and controls, including:

- Enforcing Azure Active Directory multifactor authentication registration for all users.
- Forcing administrators to use multifactor authentication.
- Requiring all users to complete multifactor authentication when needed.

Security defaults are a great option for organizations that want to increase their security posture but don’t know where to start, or for organizations using the free tier of Azure AD licensing. 

***Security defaults may not be appropriate for organizations with Azure AD premium licenses or more complex security requirements.*** 



### Multi-factor authentication (MFA) in Azure AD

[Describe Multi-factor authentication (MFA) in Azure AD - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/explore-authentication-capabilities/3-describe-multi-factor-authentication)

![Passwords should be supplemented or replaced](https://docs.microsoft.com/en-au/learn/wwl-sci/explore-authentication-capabilities/media/3-passwords-supplemented-replaced.png)

- Passwords
- Password and additional verification
- Phone
- MS Authenticator App
- OAUTH Software
- OAUTH Hardware



#### Passwordless Authentication

- Biometrics using Windows Hello
- MS Authenticator App (Fingerprint or facial scan)
- FIDO2 (Fast Identity Online)


[How Azure AD MFA works?](https://docs.microsoft.com/en-us/azure/active-directory/authentication/concept-mfa-howitworks)

[Configure Azure AD Multi-Factor Authentication](https://docs.microsoft.com/en-us/azure/active-directory/authentication/howto-mfa-mfasettings)



### Windows Hello for Business

[Describe Windows Hello for Business - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/explore-authentication-capabilities/4-describe-windows-hello-for-business)

- Windows Hello, an authentication feature built into Windows 10, replaces passwords with strong two-factor authentication on PCs and mobile devices. This authentication consists of a new type of user credential that's tied to a device and uses a biometric or PIN.
- Windows Hello lets users authenticate to:
  - A Microsoft account.
  - An Active Directory account.
  - An Azure Active Directory (Azure AD) account.
  - Identity Provider Services or Relying Party Services that support Fast ID Online (FIDO) v2.0 authentication (in preview)
- Windows stores PIN and biometric data securely on the local device; it is never sent to external device or servers.
- There are **<u>two</u>** types of Windows Hello configuration,
  - **Windows Hello**
    - Configured by a user on their personal device and is referred to as **Windows Hello Convenience PIN**. This PIN is not backed by asymmetric (public or private key) or certificate-based authentication.
  - **Windows Hello for Business**
    - Configured by Group Policy or Mobile Device Management (MDM) policy such as Microsoft Intune, and always uses key based or certificate based authentication. It is much more secure than Windows Hello Convenience PIN.
    - By default, Windows Hello Convenience PIN is **disabled** on all domain joined computers.
- Why is **Windows Hello** safer than a Password?
  - Although PIN is like a password, in this instance it is more secure, as when Windows Hello PIN is setup is tied to the device it was setup on. Without the Hardware, PIN is useless.
  - A password is transmitted to a server where it can be intercepted or stolen. A PIN is local to the device and it is not transmitted anywhere and it is not stored on a server.
  - Windows Hello PIN is backed by a **Trusted Platform Module (TPM)** chip, which is a crypto processor that is designed to carry out cryptographic operations. The chip includes multiple physical security mechanisms to make it temper resistant and malicious software can not temper with the security function of TPM. Many mobile phones and modern laptop have TPM.



### Self-Service Password Reset (SSPR) in Azure AD

[Describe self-service password reset (SSPR) in Azure AD - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/explore-authentication-capabilities/5-describe-self-service-password-reset)

Self-service password reset (SSPR) is a feature of Azure AD that allows users to change or reset their password, without administrator or help desk involvement.

If a user's account is locked or they forget the password, they can follow a prompt to reset it and get back to work. Self-service password reset has several benefits:

- It increases security, as help desks add an extra security layer.
- It saves the organization money by reducing the number of calls and requests to help desk staff.
- It increases productivity, allowing the user to return to work faster.

Self-service password reset works in the following scenarios:

- **Password change**: when a user knows their password but wants to change it to something new.
- **Password reset**: when a user can't sign in, such as when they forget the password, and want to reset it.
- **Account unlock**: when a user can't sign in because their account is locked out.

To use self-service password reset, users must be:

- Assigned an Azure AD license. See **Licensing requirements for Azure Active Directory self-service password reset** in the Learn More section below.
- Enabled for SSPR by an administrator.
- Registered, with the authentication methods they want to use. Two or more authentication methods are recommended in case one is unavailable.

The following authentication methods are available for SSPR:

- Mobile app notification
- Mobile app code
- Email
- Mobile phone
- Office phone
- Security questions

When a user resets their password using self-service password reset, it can also be written back to an on-premises Active Directory. Password write-back allows users to use their updated credentials with on-premises devices and applications without a delay.

To keep users informed about account activity, admins can configure email notifications to be sent when an SSPR event happens. These notifications can cover both regular user accounts and admin accounts. For admin accounts, this notification provides an extra layer of awareness when a privileged administrator account password is reset using SSPR. All global admins would be notified when SSPR is used on an admin account.

#### Interactive guide

In this interactive guide, you'll enable self-service password reset for users in Azure Active Directory.

[![Interactive guide](https://docs.microsoft.com/en-au/learn/wwl-sci/explore-authentication-capabilities/media/5-azure-active-directory-interactive-guide-expanded.png)](https://edxinteractivepage.blob.core.windows.net/edxpages/Security fundamentals/LP02M03 - Enable SSPR in Azure Active Directory/index.html)



### Password Protection and Management Capabilities 

Password Protection is a feature of Azure AD that reduces the risk of users setting weak passwords. Azure AD Password Protection detects and blocks known weak passwords and their variants, and can also block other weak terms that are specific to your organization.

With Azure AD Password Protection, default global banned password lists are automatically applied to all users in an Azure AD tenant. To support your own business and security needs, you can define entries in a custom banned password list. When users change or reset their passwords, these lists are checked to enforce the use of strong passwords.

You should use extra features like Azure Active Directory multifactor authentication, not just rely on strong passwords enforced by Azure AD Password Protection.

#### Global banned password list

A global banned password list with known weak passwords is automatically updated and enforced by Microsoft. This list is maintained by the Azure AD Identity Protection team, who analyse security telemetry data to find weak or compromised passwords. Examples of passwords that might be blocked are P@$$w0rd or Passw0rd1 and all variations.

Variations are created using an algorithm that transposes text case and letters to numbers such as "1" to an "l". Variations on Password1 might include Passw0rd1, Pass0rd1, and others. These passwords are then checked and added to the global banned password list and made available to all Azure AD users. The global banned password list is automatically applied and can't be disabled.

If an Azure AD user tries to set their password to one of these weak passwords, they receive a notification to choose a more secure one. The global banned list is sourced from real-world, actual password spray attacks. This approach improves the overall security and effectiveness, and the password validation algorithm also uses smart fuzzy-matching techniques. Azure AD Password Protection efficiently detects and blocks millions of the most common weak passwords from being used in your enterprise.

#### Custom banned password lists

Admins can also create custom banned password lists to support specific business security needs. The custom banned password list prohibits passwords such as the organization name or location. Passwords added to the custom banned password list should be focused on organizational-specific terms such as:

- Brand names
- Product names
- Locations, such as company headquarters
- Company-specific internal terms
- Abbreviations that have specific company meaning

The custom banned password list is combined with the global banned password list to block variations of all the passwords.

- ***Banned password lists are a feature of Azure AD Premium 1 or 2.***



#### Protecting against password spray

Azure AD Password Protection helps you defend against password spray attacks. Most password spray attacks submit a few of the known weakest passwords against each of the accounts in an enterprise. This technique allows the attacker to quickly search for an easily compromised account and avoid potential detection thresholds.

Azure AD Password Protection efficiently blocks all known weak passwords likely to be used in password spray attacks. This protection is based on real-world security telemetry data from Azure AD, which is used to build the global banned password list.



#### Hybrid security

For hybrid security, admins can integrate Azure AD Password Protection within an on-premises Active Directory environment. **A component installed in the on-premises environment receives the global banned password list and custom password protection policies from Azure AD**. Domain controllers then use them to process password change events. This hybrid approach makes sure that, wherever a user changes their password, Azure AD Password Protection is applied.

Although password protection improves the strength of passwords, you should still use best practice features like Azure Active Directory multifactor authentication. Passwords alone, even strong ones, are not as secure as multiple layers of security.



## Access Management capabilities of Azure AD



### Conditional Access and its benefits

Conditional Access is a feature of Azure AD that provides an extra layer of security before allowing authenticated users to access data or other assets. Conditional Access is implemented through policies that are created and managed in Azure AD. **A Conditional Access policy analyses signals including user, location, device, application, and risk to automate decisions for authorizing access to resources (apps and data).**

![Conditional Access policies use signals to decide whether to allow or block access](https://docs.microsoft.com/en-au/learn/wwl-sci/explore-access-management-capabilities/media/2-conditional-access-policies.png)

A Conditional Access policy might state that *if* a user belongs to a certain group, then they're required to provide multifactor authentication to sign in to an application.

Watch the video to see how Conditional Access policies work.

<iframe src="https://www.microsoft.com/en-au/videoplayer/embed/RE4INyI?postJsllMsg=true&amp;autoCaptions=en-au" frameborder="0" allowfullscreen="true" data-linktype="external" style="box-sizing: inherit; margin: 0px; padding: 0px; border: 0px; outline-color: inherit; width: 640px; position: absolute; inset: 0px; height: 360px;"></iframe>



















#### Conditional Access signals

Conditional Access can use the following signals to control the who, what, and where of the policy:

- **User or group membership**. Policies can be targeted to specific users and groups (including admin roles), giving administrators fine-grained control over access.
- **Named location information**. Named location information can be created using IP address ranges, and used when making policy decisions. Also, administrators can opt to block or allow traffic from an entire country's IP range.
- **Device**. Users with devices of specific platforms or marked with a specific state can be used.
- **Application**. Users attempting to access specific applications can trigger different Conditional Access policies.
- **Real-time sign-in risk detection**. Signals integration with Azure AD Identity Protection allows Conditional Access policies to identify risky sign-in behaviour. Policies can then force users to perform password changes or multifactor authentication to reduce their risk level or be blocked from access until an administrator takes manual action.
- **Cloud apps or actions**. Cloud apps or actions can include or exclude cloud applications or user actions that will be subject to the policy.
- **User risk**. For customers with access to Identity Protection, user risk can be evaluated as part of a Conditional Access policy. User risk represents the probability that a given identity or account is compromised. User risk can be configured for high, medium, or low probability.

## Access controls

When the Conditional Access policy has been applied, an informed decision is reached on whether to grant access, block access, or require extra verification. Common decisions are:

- Block access
- Grant access
- Require one or more conditions to be met before granting access:
  - Require multifactor authentication.
  - Require device to be marked as compliant.
  - Require hybrid Azure AD joined device.
  - Require approved client app.
  - Require app protection policy.
  - Require password change.
- Control user access based on session controls to enable limited experiences within specific cloud applications. As an example, Conditional Access App Control uses signals from Microsoft Cloud App Security (MCAS) to block, download, cut, copy and print sensitive documents, or to require labeling of sensitive files. Other session controls include sign-in frequency and application enforced restrictions that, for selected applications, use the device information to provide users with a limited or full experience, depending on the device state.

Conditional Access policies can be targeted to members of specific groups or guests. For example, you can create a policy to exclude all guest accounts from accessing sensitive resources. Conditional Access is a feature of paid Azure AD editions.

#### Interactive guide

In this interactive guide, you'll create a Conditional Access policy for a group of users.

[![Interactive guide](https://docs.microsoft.com/en-au/learn/wwl-sci/explore-access-management-capabilities/media/2-interactive.png)](https://edxinteractivepage.blob.core.windows.net/edxpages/Security fundamentals/LP02M04 - Create a Conditional Access Policy/index.html)



### Azure AD Role Based Access Control (RBAC)

Azure AD roles control permissions to manage Azure AD resources. For example, allowing user accounts to be created, or billing information to be viewed. Azure AD supports built-in and custom roles.

#### Built-in roles

A few of the most common built-in roles are:

- *Global administrator*: users with this role have access to all administrative features in Azure Active Directory. The person who signs up for the Azure Active Directory tenant automatically becomes a global administrator.
- *User administrator*: users with this role can create and manage all aspects of users and groups. This role also includes the ability to manage support tickets and monitor service health.
- *Billing administrator*: users with this role make purchases, manage subscriptions and support tickets, and monitor service health.

There are many built-in roles for different areas of responsibility. All built-in roles are preconfigured bundles of permissions designed for specific tasks.

#### Custom roles

Although there are many built-in admin roles in Azure AD, custom roles give flexibility when granting access.

Granting permission using custom Azure AD roles is a two-step process that involves creating a custom role definition, consisting of a collection of permissions that you add from a pre-set list. These permissions are the same ones used in the built-in roles. When you’ve created your role definition, you can assign it to a user by creating a role assignment.

A role assignment grants the user the permissions in a role definition, at a specified scope. A custom role can be assigned at organization-wide scope, meaning the role member has the role permissions over all resources. A custom role can also be assigned at an object scope. An example of an object scope would be a single application.

Unlike built-in roles, which are assigned at a tenant level and are preconfigured bundles of permissions designed for specific tasks, custom roles can be assigned at the resource level (such as a single application) and allow permissions to be added to a custom role definition.

<u>***Custom roles require an Azure AD Premium P1 or P2 license.***</u>

#### Azure AD role-based access control

Managing access using roles is known as role-based access control (RBAC). Azure AD built-in and custom roles are a form of RBAC in that Azure AD roles control access to Azure AD resources.

#### Only grant the access users need

It's best practice, and more secure, to grant users the least privilege to get their work done. It means that if someone mostly manages users, you should assign the user administrator role, and not global administrator. This mitigates the risk of a user account being compromised, and a hacker locking you out of your account. By assigning least privileges, you limit the damage that could be done with a compromised account.



## Identity Protection and Governance capabilities of Azure AD



### Identity Governance in Azure AD

[Describe identity governance in Azure AD - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-identity-protection-governance-capabilities/2-describe-identity-governance)

Azure AD identity governance gives organizations the ability to do the following tasks:

- Govern the identity lifecycle.
- Govern access lifecycle.
- Secure privileged access for administration.

These actions can be completed for employees, business partners and vendors, and across services and applications, both on-premises and in the cloud.



#### Identity lifecycle

Managing users’ identity lifecycle is at the heart of identity governance.

When planning identity lifecycle management for employees, for example, many organizations model the "join, move, and leave" process. Or, when an individual first joins an organization, a new digital identity is created if one isn't already available. When an individual moves between organizational boundaries, more access authorizations may need to be added or removed to their digital identity. When an individual leaves, access may need to be removed, and the identity might no longer be required, other than for audit purposes.

The diagram below shows a simplified version of the identity lifecycle.

![Identity lifecycle management is the foundation for identity governance](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-identity-protection-governance-capabilities/media/2-identify-lifecycle-management.png)

For many organizations, this identity lifecycle for employees is tied to the representation of that user in a human resources (HR) system such as Workday or SuccessFactors. The HR system is authoritative for providing the current list of employees, and some of their properties, such as name or department.

Azure AD Premium offers integration with cloud-based HR systems. When a new employee is added to an HR system, Azure AD can create a corresponding user account. Similarly, when their properties, such as department or employment status, change in the HR system, synchronization of those updates to Azure AD ensures consistency.

**Azure AD Premium also includes Microsoft Identity Manager**, which can import records from on-premises HR systems such as SAP HCM, Oracle eBusiness, and Oracle PeopleSoft. 

**In general, managing the lifecycle of an identity is about updating the access that users need, whether through integration with an HR system, or through the user provisioning applications.**



#### Access lifecycle

Access lifecycle is the process of managing access throughout the user’s organizational life. Users require different levels of access from the point at which they join an organization to when they leave it. At various stages in between, they'll need access rights to different resources depending on their role and responsibilities.

Organizations can automate the access lifecycle process through technologies such as **dynamic groups**. Dynamic groups enable admins to create attribute-based rules to determine membership of groups. When any attributes of a user or device change, the system evaluates all dynamic group rules in a directory to see if the change would trigger any users to be added or removed from a group. If a user or device satisfies a rule for a group, they're added as a member of that group. If they no longer satisfy the rule, they're removed.

#### Privileged access lifecycle

Monitoring privileged access is a key part of identity governance. When employees, vendors, and contractors are assigned administrative rights, there should be a governance process because of the potential for misuse.

Azure AD Privileged Identity Management (PIM), provides extra controls tailored to securing access rights. PIM helps you minimize the number of people who have access to resources across Azure AD, Azure, and other Microsoft online services. PIM provides a comprehensive set of governance controls to help secure your company's resources. **PIM is a feature of Azure AD Premium P2.**



### Entitlement management and access reviews

**Entitlement management is an identity governance feature that enables organizations to manage identity and access lifecycle at scale.** Entitlement management automates access request workflows, access assignments, reviews, and expiration.

The following video introduces entitlement management, and looks at how access packages are used for resources.

<iframe src="https://www.microsoft.com/en-au/videoplayer/embed/RE4JXQr?postJsllMsg=true&amp;autoCaptions=en-au" frameborder="0" allowfullscreen="true" data-linktype="external" style="box-sizing: inherit; margin: 0px; padding: 0px; border: 0px; outline-color: inherit; width: 640px; position: absolute; inset: 0px; height: 360px;"></iframe>



















***Entitlement management includes the following capabilities*** to address these challenges:

- **Delegate the creation of access packages to non-administrators**. These access packages contain resources that users can request. The delegated access package managers then define policies that include rules such as which users can request access, who must approve their access, and when access expires.
- **Managing external users**. When a user who isn't yet in your directory requests access, and is approved, they're automatically invited into your directory and assigned access. When their access expires, if they have no other access package assignments, their B2B account in your directory can be automatically removed.

Entitlement management is a feature of Azure AD Premium P2. Entitlement management uses access packages to manage access to resources.

#### Azure AD access reviews

Azure Active Directory (AD) access reviews enable organizations to efficiently manage group memberships, access to enterprise applications, and role assignment. Regular access reviews ensure that only the right people have access to resources. Excessive access rights are a known security risk. However, when people move between teams, or take on or relinquish responsibilities, access rights can be difficult to control.

Access reviews are helpful when:

- You have too many users in privileged roles, such as global administrator.
- When automation isn't possible, such as when HR data isn't in Azure AD.
- You want to control business critical data access.
- Your governance policies require periodic reviews of access permissions.

Access reviews can be created through Azure AD access reviews, or Azure AD Privileged Identity Management (PIM). ***Access reviews can be used to review and manage access for both users and guests.*** **When an access review is created, it can be set up so that each user reviews their own access, or to have one or more users review everyone's access.** **Similarly, all guests can be asked to review their own access, or have it looked at by one or more users.**

![Access reviews invite users to review access rights](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-identity-protection-governance-capabilities/media/3-access-reviews-invite-users-to-review-access-rights.png)

Admins who create access reviews can track progress as the reviewers complete their process. No access rights are changed until the review is finished. You can, however, stop a review before it reaches its scheduled end.

When the review is complete, it can be set to manually or auto-apply changes to remove access from a group membership or application assignment, except for a dynamic group or a group that originates on-premises. In those cases, the changes must be applied directly to the group.

**Access reviews are a feature of Azure AD Premium P2.**

#### Azure AD terms of use

Azure AD terms of use allow information to be presented to users, before they access data or an application. Terms of use ensure users read relevant disclaimers for legal or compliance requirements.

Employees or guests can be required to accept terms of use in the following situations:

- Before they access sensitive data or an application.
- On a recurring schedule, so they're reminded of regulations.
- When terms of use are required in different languages.
- Based on user attributes, such as terms applicable to certain roles.
- Presenting terms for all users in your organization.

Terms of use are presented in a PDF format, using content that you create, such as an existing contract document. Terms of use can also be presented to users on mobile devices.

***<u>Conditional Access policies</u>* are used to require a terms of use statement being displayed, and ensuring the user has agreed to those terms before accessing an application.** 

Admins can then view who has agreed to terms of use, and who has declined.



### Capabilities of Privileged Identity Management (PIM)



**Privileged Identity Management (PIM)** is a service in Azure Active Directory (Azure AD) that enables you to manage, control, and monitor access to important resources in your organization.

PIM reduces the chance of a malicious actor getting access by minimizing the number of people who have access to secure information or resources. By time-limiting authorized users, it reduces the risk of an authorized user inadvertently affecting sensitive resources. PIM also provides oversight for what users are doing with their administrator privileges.

**PIM can manage/control/monitor resources in Azure AD, Azure, and other Microsoft online services such as Microsoft 365 or Microsoft Intune**. 

PIM mitigates the risks of excessive, unnecessary, or misused access permissions. It requires justification to understand why users want permissions, and enforces multifactor authentication to activate any role.

PIM is:

- **Just in time, providing privileged access only when needed, and not before.**
- **Time-bound, by assigning start and end dates that indicate when a user can access resources.**
- **Approval-based, requiring specific approval to activate privileges.**
- **Visible, sending notifications when privileged roles are activated.**
- **Auditable, allowing a full access history to be downloaded.**

Privileged Identity Management is a feature of **Azure AD Premium P2.**

<iframe src="https://www.microsoft.com/en-au/videoplayer/embed/RE4ILbu?postJsllMsg=true&amp;autoCaptions=en-au" frameborder="0" allowfullscreen="true" data-linktype="external" style="box-sizing: inherit; margin: 0px; padding: 0px; border: 0px; outline-color: inherit; width: 640px; position: absolute; inset: 0px; height: 360px;"></iframe>





















### Azure Identity Protection

Identity Protection is a tool that allows organizations to accomplish three key tasks:

- **Automate** the detection and remediation of identity-based risks.
- **Investigate** risks using data in the portal.
- **Export risk detection** data to third-party utilities for further analysis.

Microsoft analyses 6.5 trillion signals per day to identify potential threats. These signals come from learnings Microsoft has acquired from their position in organizations with Azure AD, the consumer space with Microsoft Accounts, and in gaming with Xbox.

**The signals generated by these services are fed to Identity Protection. These signals can then be used by tools such as Conditional Access, which uses them to make access decisions. Signals are also fed to security information and event management (SIEM) tools, such as Sentinel, for further investigation.**

Identity Protection categorizes risk into three tiers: **low, medium, and high**. It can also calculate the **sign-in risk, and user identity risk.**

**Sign-in risk** is the probability that it wasn’t performed by the user, and uses the following signals to calculate the risk:

- Atypical travel. Sign-in from an atypical location based on the user's recent activity.
- Anonymous IP address. Sign-in from an anonymous IP address; for example, Tor browser, anonymized VPNs).

**User risk** is about the probability that their identity has been compromised, and uses the following signals to calculate the risk:

- Unfamiliar sign-in properties. Sign-in with properties you've not seen recently for a given user.
- Sign-in from a malware-linked IP address.
- Leaked credentials. Indicates that the user's valid credentials have been leaked.
- Password spray. Indicates that multiple usernames are being attacked using common passwords in a unified, brute-force manner.
- Azure AD threat intelligence. Microsoft's internal and external threat intelligence sources have identified a known attack pattern.

**These risk signals can trigger actions such as requiring users to provide multifactor authentication, reset their password, or block access until an administrator takes action.**

Identity Protection provides organizations with three reports that they can use to investigate identity risks in their environment. These reports are the **risky users**, **risky sign-ins**, and **risk detections**. Investigation of events is key to understanding and identifying any weak points in your security strategy.

After completing an investigation, admins will want to take action to remediate the risk or unblock users. Organizations can also enable automated remediation using their risk policies. Microsoft recommends closing events quickly because time matters when working with risk.

**Identity Protection is a feature of Azure AD Premium P2.**