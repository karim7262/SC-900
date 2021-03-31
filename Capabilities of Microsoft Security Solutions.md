[TOC]

# Describe the capabilities of Microsoft Security Solutions (30-35%) 



## Basic security capabilities in Azure



### Azure Network Security Groups (NSG)

[Describe Azure Network Security groups - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-basic-security-capabilities-azure/2-describe-azure-network-security-groups)

Network security groups (NSGs) let you allow or deny network traffic to and from Azure resources that exist in your Azure virtual network; for example, a virtual machine. When you create an NSG, it can be associated with multiple subnets or network interfaces in your VNet. An NSG consists of rules that define how the traffic is filtered.

**NSG security rules are evaluated by priority using five information points: source, source port, destination, destination port, and protocol to either allow or deny the traffic.** 

As a guideline, you shouldn't create two security rules with the same priority and direction.

![Diagram showing a simplified virtual network with two subnets each with a dedicated virtual machine resource, the first subnet has a network security group and the second subnet doesn't.](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-basic-security-capabilities-azure/media/2-virtual-network.png)

#### Inbound / Outbound Security Rule

By default, Azure creates a series of rules, three inbound and three outbound rules, to provide a baseline level of security. You can't remove the default rules, but you can override them by creating new rules with higher priorities.

Each rule specifies one or more of the following properties:

- **Name**: Every NSG rule needs to have a unique name that describes its purpose. For example, AdminAccessOnlyFilter.
- **Priority**: A number between 100 and 4096. Rules are processed in priority order, with lower numbers processed before higher numbers. When traffic matches a rule, processing stops. This means that any other rules with a lower priority (higher numbers) won't be processed.
- **Source or destination**: Specify either individual IP address or an IP address range, service tag (a group of IP address prefixes from a given Azure service), or application security group. Specifying a range, a service tag, or application security group, enables you to create fewer security rules.
- **Protocol**: What network protocol will the rule check? The protocol can be any of: TCP, UDP, ICMP or Any.
- **Direction**: Whether the rule should be applied to inbound or outbound traffic.
- **Port range**: You can specify an individual or range of ports. For example, you could specify 80 or 10000-10005. Specifying ranges enables you to create fewer security rules. You can't specify multiple ports or port ranges in the same security rule in NSGs created through the classic deployment model.
- **Action**: Finally, you need to decide what will happen when this rule is triggered.

### Azure DDoS protection

[Describe Azure DDoS protection - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-basic-security-capabilities-azure/3-describe-azure-ddos-protection)

Any company, large or small, can be the target of a serious network attack. The nature of these attacks might be to make a statement, or simply happen because the attacker wanted a challenge.

#### Distributed Denial of Service attacks

The aim of a Distributed Denial of Service (DDoS) attack is to overwhelm the resources on your applications and servers, making them unresponsive or slow for genuine users. A DDoS attack will usually target any public-facing endpoint that can be accessed through the internet.

The three most frequent types of DDoS attack are:

- **Volumetric attacks**: These are volume-based attacks that flood the network with seemingly legitimate traffic, overwhelming the available bandwidth. Legitimate traffic can't get through. These types of attacks are measured in bits per second.
- **Protocol attacks**: Protocol attacks render a target inaccessible by exhausting server resources with false protocol requests that exploit weaknesses in layer 3 (network) and layer 4 (transport) protocols. These types of attacks are typically measured in packets per second.
- **Resource (application) layer attacks**: These attacks target web application packets, to disrupt the transmission of data between hosts.

#### What is Azure DDoS Protection?

The Azure DDoS Protection service is designed to help protect your applications and servers by analysing network traffic and discarding anything that looks like a DDoS attack.

![Diagram showing network flow into Azure from both customers and attackers, and how  Azure DDoS Protection filters out DDoS attacks.](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-basic-security-capabilities-azure/media/2-network-flow.png)

In the diagram above, Azure DDoS Protection identifies an attacker's attempt to overwhelm the network. It blocks traffic from the attacker, ensuring that it doesn't reach Azure resources. Legitimate traffic from customers still flows into Azure without any interruption of service.

Azure DDoS Protection uses the scale and elasticity of Microsoft's global network to bring DDoS mitigation capacity to every Azure region. 

During a DDoS attack, Azure can scale your computing needs to meet demand. DDoS Protection manages cloud consumption by ensuring that your network load only reflects actual customer usage.

Azure DDoS Protection comes in two tiers:

- **Basic**: The Basic service tier is automatically enabled for every property in Azure, at no extra cost, as part of the Azure platform. Always-on traffic monitoring and real-time mitigation of common network-level attacks provide the same defences that Microsoft’s online services use. Azure’s global network is used to distribute and mitigate attack traffic across regions.
- **Standard**: The Standard service tier provides extra mitigation capabilities that are tuned specifically to Microsoft Azure Virtual Network resources. DDoS Protection Standard is simple to enable and requires no application changes. Protection policies are tuned through dedicated traffic monitoring and machine learning algorithms. ***Policies are applied to public IP addresses, which are associated with resources deployed in virtual networks, such as Azure Load Balancer and Application Gateway.***

#### Azure DDoS pricing

The DDoS Standard Protection service has a fixed monthly charge that includes protection for 100 resources. Protection for additional resources are charged on a monthly per-resource basis.

For more information on pricing, visit the [Azure DDoS Protection pricing page](https://azure.microsoft.com/pricing/details/ddos-protection/).

Use Azure DDoS to protect your devices and applications by analysing traffic across your network, and taking appropriate action on suspicious traffic.



### Azure Firewall

[Describe what is Azure Firewall - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-basic-security-capabilities-azure/4-describe-what-azure-firewall)

Azure Firewall is a managed, cloud-based network security service that protects your Azure virtual network (VNet) resources from attackers. You can deploy Azure Firewall on any virtual network but the best approach is to use it on a centralized virtual network. All your other virtual and on-premises networks will then route through it. The advantage of this model is the ability to centrally exert control of network traffic for all your VNets across different subscriptions.

![Diagram showing how Azure Firewall is running on a centralized VNet can protect both cloud-based VNets and your on-premises network.](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-basic-security-capabilities-azure/media/2-azure-firewall.png)

With Azure Firewall, you can scale up the usage to accommodate changing network traffic flows, so you don't need to budget for peak traffic. Network traffic is subjected to the configured firewall rules when you route it to the firewall as the subnet default gateway.

#### Key features of Azure Firewall

Azure Firewall comes with many features, including but not limited to:

- **Built-in high availability and availability zones**: High availability is built in so there's nothing to configure. Also, Azure Firewall can be configured to span multiple availability zones for increased availability.
- **Network and application level filtering**: Use IP address, port, and protocol to support fully qualified domain name filtering for outbound HTTP(s) traffic and network filtering controls.
- **Outbound SNAT and inbound DNAT to communicate with internet resources**: Translates the private IP address of network resources to an Azure public IP address (source network address translation) to identify and allow traffic originating from the virtual network to internet destinations. Similarly, inbound internet traffic to the firewall public IP address is translated (Destination Network Address Translation) and filtered to the private IP addresses of resources on the virtual network.
- **Multiple public IP addresses**: These addresses can be associated with Azure Firewall.
- **Threat intelligence**: Threat intelligence-based filtering can be enabled for your firewall to alert and deny traffic from/to known malicious IP addresses and domains.
- **Integration with Azure Monitor**: Integrated with Azure Monitor to enable collecting, analysing, and acting on telemetry from Azure Firewall logs.

Use Azure Firewall to help protect the Azure resources you've connected to Azure Virtual Networks.



### Azure Bastion

[Describe what is Azure Bastion - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-basic-security-capabilities-azure/5-describe-what-azure-bastion)

![Diagram showing how a user can make a remote desktop connection to an Azure VM using Azure Bastion.](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-basic-security-capabilities-azure/media/2-azure-bastion.png)

**Azure Bastion provides secure and seamless RDP/SSH connectivity to your virtual machines directly from the Azure portal using Transport Layer Security (TLS).** When you connect via Azure Bastion, your virtual machines don't need a public IP address, agent, or special client software.

Bastion provides secure RDP and SSH connectivity to all VMs in the virtual network in which it's provisioned. Using Azure Bastion protects your virtual machines from exposing RDP/SSH ports to the outside world, while still providing secure access using RDP/SSH.

**Azure Bastion deployment is per virtual network, not per subscription/account or virtual machine.** When you provision an Azure Bastion service in your virtual network, the RDP/SSH experience is available to all your VMs in the same virtual network.

#### Key features of Azure Bastion

- **RDP and SSH directly in Azure portal**: You get to the RDP and SSH session directly in the Azure portal, using a single-click experience.
- **Remote session over TLS and firewall traversal for RDP/SSH**: Use an HTML5-based web client that's automatically streamed to your local device. You'll get your Remote Desktop Protocol (RDP) and Secure Shell (SSH) to traverse the corporate firewalls securely.
- **No Public IP required on the Azure VM**: Azure Bastion opens the RDP/SSH connection to your Azure virtual machine using private IP on your VM. You don't need a public IP.
- **No hassle of managing NSGs**: A fully managed platform PaaS service from Azure that's hardened internally to provide secure RDP/SSH connectivity. You don't need to apply any NSGs on an Azure Bastion subnet.
- **Protection against port scanning**: Because you don't need to expose your virtual machines to the internet, your VMs are protected against port scanning by rogue and malicious users located outside your virtual network.
- **Protect against zero-day exploits**: A fully platform-managed PaaS service. Because it sits at the perimeter of your virtual network, you don’t need to worry about hardening each virtual machine in the virtual network. The Azure platform protects against zero-day exploits by keeping the Azure Bastion hardened and always up to date for you.



### Web Application Firewall

[Describe what is Web Application Firewall - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-basic-security-capabilities-azure/6-describe-what-web-application-firewall)

Web Application Firewall (WAF) provides centralized protection of your web applications from common exploits and vulnerabilities. A centralized WAF helps make security management simpler, improves the response time to a security threat, and allows patching a known vulnerability in one place, instead of securing each web application. A WAF also gives application administrators better assurance of protection against threats and intrusions.

![Diagram showing how the Web Application Firewall provides protection against common exploits.](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-basic-security-capabilities-azure/media/2-web-app-firewall.png)

#### Supported services

***WAF can be deployed with Azure Application Gateway, Azure Front Door, and Azure Content Delivery Network (CDN) services from Microsoft.*** WAF has features that are customized for each specific service.

Use Azure WAF to achieve centralized protection for your web applications from common exploits and vulnerabilities.



### Describe ways Azure encrypts data

[Describe ways Azure encrypts data - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-basic-security-capabilities-azure/7-describe-ways-azure-encrypts-data)

Microsoft Azure provides many different ways to secure your data, each depending on the service or usage required.

- **Azure Storage Service Encryption** helps to protect data at rest by automatically encrypting before persisting it to Azure-managed disks, Azure Blob Storage, Azure Files, or Azure Queue Storage, and decrypts the data before retrieval.
- **Azure Disk Encryption** helps you encrypt Windows and Linux IaaS virtual machine disks. Azure Disk Encryption uses the industry-standard BitLocker feature of Windows and the dm-crypt feature of Linux to provide volume encryption for the OS and data disks.
- **Transparent data encryption (TDE)** helps protect Azure SQL Database and Azure Data Warehouse against the threat of malicious activity. It performs real-time encryption and decryption of the database, associated backups, and transaction log files at rest without requiring changes to the application.

#### What is Azure Key Vault?

Azure Key Vault is a centralized cloud service for storing your application secrets. Key Vault helps you control your applications' secrets by keeping them in a single, central location and by providing secure access, permissions control, and access logging capabilities. It's useful for different kinds of scenarios:

- **Secrets management**. You can use Key Vault to store securely and tightly control access to tokens, passwords, certificates, Application Programming Interface (API) keys, and other secrets.
- **Key management**. You can use Key Vault as a key management solution. Key Vault makes it easier to create and control the encryption keys used to encrypt your data.
- **Certificate management**. Key Vault lets you provision, manage, and deploy your public and private Secure Sockets Layer/ Transport Layer Security (SSL/ TLS) certificates for Azure, and internally connected, resources more easily.
- **Store secrets backed by hardware security modules (HSMs)**. The secrets and keys can be protected either by software or by FIPS 140-2 Level 2 validated HSMs.

------

## Security management capabilities of Azure



### Describe Cloud Security Posture Management (CSPM)

[Describe Cloud security posture management - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-security-management-capabilities-of-azure/2-describe-cloud-security-posture-management)

**Cloud security posture management (CSPM) is a relatively new class of tools designed to improve your cloud security management.** It assesses your systems and automatically alerts security staff in your IT department when a vulnerability is found. CSPM uses tools and services in your cloud environment to monitor and prioritize security enhancements and features.

CSPM uses a combination of tools and services:

- **Zero Trust-based access control**: Considers the active threat level during access control decisions.
- **Real-time risk scoring**: To provide visibility into top risks.
- **Threat and vulnerability management (TVM)**: Establishes a holistic view of the organization's attack surface and risk and integrates it into operations and engineering decision-making.
- **Discover sharing risks**: To understand the data exposure of enterprise intellectual property, on sanctioned and unsanctioned cloud services.
- **Technical policy**: Apply guardrails to audit and enforce the organization's standards and policies to technical systems.
- **Threat modeling systems and architectures**: Used alongside other specific applications.

The main goal for a cloud security team working on posture management is to continuously report on and improve the organization's security posture by focusing on disrupting a potential attacker's return on investment (ROI).

The function of CSPM in your organization might be spread across multiple teams, or there may be a dedicated team. CSPM can be useful to many teams in your organization:

- Threat intelligence team
- Information technology
- Compliance and risk management teams
- Business leaders and SMEs
- Security architecture and operations
- Audit team

Use CSPM to improve your cloud security management by assessing the environment, and automatically alerting security staff for vulnerabilities.



### Describe and explore Azure Security Centre

[Describe and explore the Azure Security center - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-security-management-capabilities-of-azure/3-describe-explore-azure-security-center)

Using Azure Security Centre gives you infrastructure level security management to protect your data. It also provides advanced threat protection for on-premises, cloud, and hybrid workloads in the cloud, whether they're in Azure or not, as well as on-premises.

Azure Security Centre provides the tools you need to harden your network, secure services, and ensure you're on top of your security posture.

Azure Security Centre addresses the three most urgent security challenges:

- **Rapidly changing workloads**: As organizations empower users to do more, the challenge is to ensure that the ever-changing services people use and create meet your security standards and follow best practices.
- **Increasingly sophisticated attacks**: Wherever your work is situated, the attacks keep getting more sophisticated. Securing your public internet-facing services is essential; otherwise, you'll be even more vulnerable.
- **Security skills are in short supply**: The number of security alerts and alerting systems far outnumbers the total of administrators who have the necessary background and experience to ensure your environments are protected.

To help protect against these challenges, Azure Security Centre provides tools to:

#### Strengthen your security posture

You can improve your security posture using Azure Security Centre to identify and perform hardening tasks across your machines, data services, and applications. With Azure Security Centre, you can manage and enforce security policies to ensure compliance across your virtual machines, non-Azure servers, and Azure PaaS services.

##### Continuous Assessment

Security Centre brings continuous assessment of your entire estate, discovering and reporting whether new and existing resources and assets are configured according to security compliance requirements. You’ll get an ordered list of recommendations of what needs to be fixed to maintain maximum protection. 

Security Centre groups the recommendations into security controls and adds a secure score value to each control. This process is crucial in enabling you to prioritize security work.

![Screenshot showing part of Azure Security Center with recommendations as to what needs to be fixed to maintain maximum protection.](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-security-management-capabilities-of-azure/media/3-security-center-recommendations.png)

##### Network Map

One of the most powerful Security Centre tools for continuously monitoring the security status of your network is the network map. Use the map to look at the topology of your workloads, so you can see if each node is properly configured. You'll see how your nodes are connected, which helps you block unwanted connections that could potentially make it easier for an attacker to creep along your network.

![Diagram showing the Security Center network map.](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-security-management-capabilities-of-azure/media/3-network-map.png)

#### Protect against threats

With Azure Security Centre's threat protection, you can detect and prevent threats on infrastructure as a service (IaaS), non-Azure servers, and platform as a service (PaaS). It comes with these features:

- **Integration with Microsoft Defender**: Security Centre natively integrates with Microsoft Defender for Endpoint.
- **Protect PaaS**: Security Centre helps you detect threats across Azure PaaS services. You can detect threats targeting Azure services, including Azure App Service, Azure SQL, Azure Storage Account, and more data services.
- **Block brute force attacks**: By reducing access to virtual machine ports, using the just-in-time VM access, you can harden your network by preventing unnecessary access.
- **Protect data services**: Get assessments for potential vulnerabilities across Azure SQL and Storage services and recommendations for mitigating them.

Security Centre's threat protection automatically correlates alerts in your environment based on cyber kill-chain analysis. It helps you to better understand the full story of an attack campaign, where it started and the impact it had on your resources.

#### Get secure faster

With Security Centre, organizations can get secure faster through integration with other Microsoft security solutions. Also, integration with Azure and its resources means you'll pull together a complete security story involving Azure Policy and built-in Security Centre policies across all your Azure resources. You then ensure that the whole thing is automatically applied to newly discovered resources as you create them in Azure.



### Describe and explore Azure Secure Score





### Describe the benefit and use cases of Azure Defender

Previously this was known as, **Cloud Workload Protection Platform (CWPP)**





### Describe security baseline for Azure





### Describe the different pricing tiers



















































































































## Security capabilities of Azure Sentinel



## Protection with Microsoft 365 Defender (Formerly Microsoft Threat Protection)



## Security management capabilities of Microsoft 365



## Endpoint security with Microsoft Intune