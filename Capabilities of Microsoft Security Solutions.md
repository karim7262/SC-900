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

------



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

------




### Describe and explore Azure Secure Score

[Describe and explore Azure Secure score - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-security-management-capabilities-of-azure/4-describe-explore-azure-secure-score)

Security Center continually assesses your resources, subscriptions, and organization for security issues. It then aggregates all the findings into a single score so you can quickly see your current security situation: the higher the score, the lower the identified risk level.

The secure score is shown in the Azure portal pages as a percentage value. The underlying values are also clearly presented:

![Section of the Azure portal showing the Overall Secure Score.](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-security-management-capabilities-of-azure/media/4-overall-secuire-score.png)

To increase your security and raise your score, review Security Center's recommendations page for the outstanding actions necessary. Each recommendation includes instructions to help you remediate the specific issue.



#### How is the security score calculated?

Every control in the recommendations list shows the potential secure score increase if you address the underlying problem. To get every possible security control point, all your resources must follow each security recommendation within the security control. For example, Security Center has multiple recommendations for how to secure your management ports. You must remediate them all to make a difference to your secure score.

For example, the security control called "Apply system updates" has a maximum score of six points. You can see it in the tooltip on the potential increase value of the control:

![Fragment of a screenshot showing a specific recommendation control and the percentage point increase will occur from fixing the issues.](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-security-management-capabilities-of-azure/media/4-specific-recommendations.png)

The maximum score for this control, *Apply system updates*, is always 6. In this example, there are 50 resources. Divide the maximum score by 50, and the result is that every resource contributes 0.12 points.

- **Potential increase** (0.12 x 8 unhealthy resources = 0.96): The remaining points available to you within the control. If you remediate all the recommendations, your score will increase by 2 percent (in this case, 0.96 points rounded up to 1 point).
- **Current score** (0.12 x 42 healthy resources = 5.04): The current score for this control. Each control contributes to the total score. In this example, the control is contributing 5.04 points to the current secure total.
- **Max score**: The maximum number of points you can gain by completing all recommendations within a control. The maximum score for a control indicates its relative significance. *<u>Use the max score values to triage the issues to work on first.</u>*

#### Interactive guide

If you’re the Azure administrator for your organization, you’ll need to be aware of the security of your Azure environment and then improve your security posture. The following interactive click-through demonstrates how you use Azure secure score.  Click on the image below to get started.

[![Interactive guide](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-security-management-capabilities-of-azure/media/4-interactive-guide-place-holder.png)](https://edxinteractivepage.blob.core.windows.net/edxpages/Security fundamentals/LP03M02 - Use Azure secure score to improve your security posture/index.html)



------



### Describe the benefit and use cases of Azure Defender

Previously this was known as, **Cloud Workload Protection Platform (CWPP)**

[Describe the benefit and use cases of Azure Defender - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-security-management-capabilities-of-azure/5-describe-benefit-use-cases-defender)

- Azure Defender is a built-in tool that provides threat protection for workloads running in Azure, on-premises, and other clouds. Azure Defender is the leading Microsoft extended detection and response (XDR) solution for threat protection. 
- Integrated with Azure Security Center, Azure Defender protects your hybrid data, cloud-native services and servers, and integrates with your existing security workflows.
- You'll find the Azure Defender dashboard in Azure Security Center. It provides visibility and control of your organization's cloud workload protection (CWP) features across the network.



##### Scope of Azure Defender

Azure Defender comes with several different plans that can be enabled separately and will run simultaneously to provide a comprehensive defense for compute, data, and service layers in your environment. The Azure Defender plans you can select from are:

- **Azure Defender for servers** adds threat detection and advanced defenses for your Windows and Linux machines.
- **Azure Defender for App Service** uses the cloud scale to identify attacks targeting applications running over App Service.
- **Azure Defender for Storage** detects potentially harmful activity on your Azure Storage accounts. Data can be protected, whether stored as blob containers, file shares, or data lakes.
- **Azure Defender for SQL** extends Azure Security Center's data security package to secure your databases and their data wherever they're located.
- **Azure Defender for Kubernetes** provides the best cloud-native Kubernetes security environment hardening, workload protection, and run-time protection.
- **Azure Defender for container registries** protects all the Azure Resource Manager based registries in your subscription. Azure Defender scans all images pushed to the registry, or imported into the registry, or any images pulled within the last 30 days.
- **Azure Defender for Key Vault** is Azure-native, advanced threat protection for Azure Key Vault, providing an extra layer of security intelligence.



##### Hybrid cloud protection

You can defend your Azure environment, and add Azure Defender capabilities to the hybrid cloud environment:

- Protect your non-Azure servers.
- Protect your virtual machines in other clouds (such as AWS and GCP).



##### Azure Defender alerts

When Azure Defender detects a threat in any area of your environment, it generates an alert. These alerts describe details of the affected resources, suggested remediation steps, and in some cases, an option to trigger a logic app in response. The alerts can also be exported into Azure Sentinel.



##### Advanced protection

Azure Defender uses advanced analytics for tailored recommendations as they relate to your resources. These analytics might include securing the management ports of your VMs with just-in-time access and adaptive application controls to create allow lists for what apps should and shouldn't run on your machines.



##### Vulnerability assessment

Azure Defender includes vulnerability scanning for your virtual machines and container registries. Review the findings from these vulnerability scanners and respond to them all from within Security Center.

------



### Describe security baseline for Azure

Microsoft's cybersecurity group and the Center for Internet Security (CIS), have developed best practices to help establish security baselines for the Azure platform. A baseline is the implementation of the benchmark on the individual Azure service.

CIS benchmarks have been used with Azure security services and tools to make security and compliance easier for customer applications running on Azure services. 

Every service comes with a baseline that's already designed to help provide security for most common-use cases. These baselines also provide a consistent experience when securing your environment.



#### The Azure Security Benchmark

A benchmark contains security recommendations for a specific technology, such as Azure. The recommendations are categorized by the control to which they belong. The Azure Security Benchmark (ASB) provides prescriptive best practices and recommendations to help improve the security of workloads, data, and services on Azure.

The ASB focuses on cloud-centric control areas. These controls are consistent with well-known security benchmarks, such as those described by the CIS. The areas covered include network security, identity management, posture and vulnerability management, and endpoint security.

Each recommendation includes the following information:

- **Azure ID**: The Azure Security Benchmark ID that corresponds to the recommendation.
- **Recommendation**: The recommendation provides a high-level description of the control.
- **Guidance**: The rationale for the recommendation and links to guidance on how to implement it.
- **Responsibility**: Who is responsible for implementing the control? Possible scenarios are customer responsibility, Microsoft responsibility, or shared responsibility.
- **Azure Security Center monitoring**: Does Azure Security Center monitor the control?

All recommendations, including the ones that don't apply to this specific service, appear in the baseline to provide a complete picture of how the Azure Security Benchmark relates to each service.

Security baselines are included for many Azure services, including Azure security baseline for Security Center.

------

### Describe the different pricing tiers

Cloud security posture management is essential for every organization. Microsoft Azure lets you decide how much you need to meet your regulatory, compliance, and corporate security needs.

Security Center is offered in two modes:

#### Azure Defender off

Security Center without Azure Defender is enabled free of charge on all your Azure subscriptions when you visit the Azure Security Center dashboard in the Azure portal for the first time, or if enabled programmatically via API.

#### Azure Defender on

Enabling Azure Defender extends the free mode capabilities to workloads running in private and other public clouds, providing unified security management and threat protection across your hybrid cloud workloads.

For more information visit [Azure Defender pricing](https://azure.microsoft.com/pricing/details/azure-defender/).





## Security capabilities of Azure Sentinel



### Define the concepts of SIEM, SOAR, XDR

[Define the concepts of SIEM, SOAR, XDR - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-security-capabilities-of-azure-sentinel/2-define-concepts-of-siem-soar-xdr)

Cybercriminals will often escalate their activity in times of national or global crisis, looking to exploit the situation and find ways into your organization. Having a resilient and robust, industry-standard set of tools can help mitigate and prevent these exploits. Security incident and event management (SIEM), security orchestration automated response (SOAR), and extended detection and response (XDR) provide excellent security insights and security automation that can enhance an organization's network security perimeter.

#### What is security incident and event management (SIEM)?

A SIEM system is a tool that an organization uses to collect data from across the whole estate, including infrastructure, software, and resources. It does analysis, looks for correlations or anomalies, and generates alerts and incidents.

#### What is security orchestration automated response (SOAR)?

A SOAR system takes alerts from many sources, such as a SIEM system. The SOAR system then triggers action-driven automated workflows and processes to run security tasks that mitigate the issue.

#### What is extended detection and response (XDR)?

An XDR system is designed to deliver intelligent, automated, and integrated security across an organization’s domain. It helps prevent, detect, and respond to threats across identities, endpoints, applications, email, IoT, infrastructure, and cloud platforms.

To provide a comprehensive security perimeter, an organization needs to use a solution that embraces or combines all of the above systems.

------

### Describe how Sentinel provides integrated threat protection

[Describe how Sentinel provides integrated threat protection - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-security-capabilities-of-azure-sentinel/3-describe-sentinel-provide-integrated-threat-protection)

Microsoft Azure Sentinel is a scalable, cloud-native SIEM/SOAR solution that delivers intelligent security analytics and threat intelligence across the enterprise. It provides a single solution for alert detection, threat visibility, proactive hunting, and threat response.

![Diagram showing the four aspects of Azure Sentinel: collect, detect, investigate, and respond.](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-security-capabilities-of-azure-sentinel/media/3-four-aspects-azure-sentinel.png)

This diagram shows the end-to-end functionality of Azure Sentinel.

- **Collect** data at cloud scale across all users, devices, applications, and infrastructure, both on-premises and in multiple clouds.
- **Detect** previously uncovered threats and minimize false positives using analytics and unparalleled threat intelligence.
- **Investigate** threats with AI and hunt suspicious activities at scale, tapping into decades of cybersecurity work at Microsoft.
- **Respond** to incidents rapidly with built-in orchestration and automation of common security tasks.

Azure Sentinel helps enable end-to-end security operations. It starts with log ingestion and continues through to automated response to security alerts.



#### Connect Sentinel to your data

Azure Sentinel comes with many connectors for Microsoft solutions, available out of the box and providing real-time integration. Included are Microsoft 365 Defender (formerly Microsoft Threat Protection) solutions, and Microsoft 365 sources, including Office 365, Azure AD, Microsoft Defender for Identity (formerly Azure ATP), Microsoft Cloud App Security, and more.

First, you must have your data ingested into Azure Sentinel, for which you need data connectors. There are data connectors that cover a wide range of scenarios and sources, including but not limited to:

- syslog
- Windows Event Logs
- Common Event Format (CEF)
- Trusted Automated eXchange of Indicator Information (TAXII), for threat intelligence
- Azure
- AWS services



#### Workbooks

After you connect data sources to Azure Sentinel, you can monitor the data using the Azure Sentinel integration with Azure Monitor Workbooks. You'll see a canvas for data analysis and the creation of rich visual reports within the Azure portal. Through this integration, Azure Sentinel allows you to create custom workbooks across your data. It also comes with built-in workbook templates that allow quick insights across your data as soon as you connect a data source.

#### Analytics

The power of Azure Sentinel comes into play here. Using built-in analytics alerts within the Azure Sentinel workspace, you’ll get notified when anything suspicious occurs. There are various types of alerts, some of which you can edit to your own needs. Other alerts are built on machine learning models that are proprietary to Microsoft.

#### Manage incidents in Azure Sentinel

An incident is created when an alert that you've enabled is triggered. You can do standard incident management tasks like changing status or assigning incidents to individuals for investigation in Azure Sentinel. It also has investigation functionality, so you can visually investigate incidents by mapping entities across log data along a timeline.

#### Security automation and orchestration

You can use Azure Sentinel to automate some of your security operations and make your security operations center (SOC) more productive. Azure Sentinel integrates with Azure Logic Apps, so you can create automated workflows, or playbooks, in response to events. This functionality could be used for incident management, enrichment, investigation, or remediation.

#### Playbooks

A security playbook is a collection of procedures that can help automate and orchestrate your response. It can be run manually or set to run automatically when specific alerts are triggered. Security playbooks in Azure Sentinel are based on Azure Logic Apps. You get all the power, customizability, and built-in templates of Logic Apps. Each playbook is created for the specific subscription you choose.

#### Investigation

Currently in preview, Azure Sentinel's deep investigation tools help you to understand the scope of a potential security threat and find the root cause. You choose an entity on the interactive graph to ask specific questions, then drill down into that entity and its connections to get to the root cause of the threat.

#### Hunting

Use Azure Sentinel's powerful hunting search-and-query tools, based on the MITRE framework, to hunt proactively for security threats across your organization’s data sources, before an alert is triggered. After you discover which hunting query provides high-value insights into possible attacks, you can also create custom detection rules based on your query, and surface those insights as alerts to your security incident responders.

While hunting, you can bookmark interesting events, enabling you to return to them later, share them with others, and group them with other correlating events to create a compelling incident for investigation.

#### Integrated threat protection

Threat protection is a continuously evolving battle front. Cybercriminals look for any vulnerability they can exploit to steal, damage, or extort company data, assets, and resources. Microsoft provides a suite of tools that give extended detection and response (XDR) through Microsoft 365 Defender and Azure Defender.

![Diagram showing Microsoft 365 Defender and Azure Defender.](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-security-capabilities-of-azure-sentinel/media/3-defender-azure-defender.png)

Both tools integrate smoothly with Azure Sentinel to provide a complete and thorough threat protection capability for your organization.

![Diagram showing the three elements that make up the complete threat protection: Microsoft 365 and Azure Defender, and Azure Sentinel.](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-security-capabilities-of-azure-sentinel/media/3-elements-threat-protection.png)

#### Azure Sentinel video presentation

In this nine-minute video, you’ll explore many of the key features available in Azure Sentinel, including incidents, workbooks, hunting, notebooks, analytics, and playbooks.

<iframe src="https://www.microsoft.com/en-au/videoplayer/embed/RE4LHLR?postJsllMsg=true&amp;autoCaptions=en-au" frameborder="0" allowfullscreen="true" data-linktype="external" style="box-sizing: inherit; margin: 0px; padding: 0px; border: 0px; outline-color: inherit; width: 640px; position: absolute; inset: 0px; height: 360px;"></iframe>



















#### Understand Sentinel costs

Azure Sentinel provides intelligent security analytics across your enterprise. The data for this analysis is stored in an Azure Monitor Log Analytics workspace. Billing is based on the volume of data ingested for analysis in Azure Sentinel and stored in the Azure Monitor Log Analytics workspace. There are two ways to pay for the Azure Sentinel service: Capacity Reservations and Pay-As-You-Go.

- **Capacity Reservations**: With Capacity Reservations, you're billed a fixed fee based on the selected tier, enabling a predictable total cost for Azure Sentinel.
- **Pay-As-You-Go**: With Pay-As-You-Go pricing, you're billed per gigabyte (GB) for the volume of data ingested for analysis in Azure Sentinel and stored in the Azure Monitor Log Analytics workspace.

For more information on pricing and a free trial of Azure Sentinel on an Azure Monitor Log Analytics workspace, visit [Azure Sentinel pricing](https://azure.microsoft.com/pricing/details/azure-sentinel/).





## Protection with Microsoft 365 Defender (Formerly Microsoft Threat Protection)



### Describe Microsoft 365 Defender services

[Describe Microsoft 365 Defender services - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-threat-protection-with-microsoft-365-defender/2-describe-services)

Microsoft 365 Defender is an enterprise defense suite that protects against sophisticated cyberattacks. With Microsoft 365 Defender, you can natively coordinate the detection, prevention, investigation, and response to threats across email, identity, and applications.

This short three-minute video provides an essential overview of Microsoft 365 Defender.

<iframe src="https://www.microsoft.com/en-au/videoplayer/embed/RE4IPYr?postJsllMsg=true&amp;autoCaptions=en-au" frameborder="0" allowfullscreen="true" data-linktype="external" style="box-sizing: inherit; margin: 0px; padding: 0px; border: 0px; outline-color: inherit; width: 640px; position: absolute; inset: 0px; height: 360px;"></iframe>



















Microsoft 365 Defender allows admins to assess threat signals from applications, email, and identity to determine an attack's scope and impact. It gives greater insight into how the threat occurred, and what systems have been affected. Microsoft 365 Defender can then take automated action to prevent or stop the attack.

![Diagram that shows the four aspects that make up the Microsoft 365 Defender suite: identity, endpoints, apps, and email.](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-threat-protection-with-microsoft-365-defender/media/2-four-aspects-microsoft-365-defender.png)

Microsoft 365 Defender suite protects:

- **Endpoints with Microsoft Defender for Endpoint** - Microsoft Defender for Endpoint is a unified endpoint platform for preventative protection, post-breach detection, automated investigation, and response.
- **Email and collaboration with Microsoft Defender for Office 365** - Defender for Office 365 safeguards your organization against malicious threats posed by email messages, links (URLs), and collaboration tools.
- **Identities with Microsoft Defender for Identity and Azure AD Identity Protection** - Microsoft Defender for Identity uses Active Directory signals to identify, detect, and investigate advanced threats, compromised identities, and malicious insider actions directed at your organization.
- **Applications with Microsoft Cloud App Security** - Microsoft Cloud App Security is a comprehensive cross-SaaS solution that brings deep visibility, strong data controls, and enhanced threat protection to your cloud apps.

Use Microsoft Defender to protect your organization against sophisticated cyberattacks. It coordinates your detection, prevention, investigation, and response to threats across identities, email, and applications.



### Describe Microsoft Defender for Identity

Microsoft Defender for Identity, formerly Azure Advanced Threat Protection (Azure ATP), is a cloud-based security solution. 

It uses your on-premises Active Directory data (called signals) to identify, detect, and investigate advanced threats, compromised identities, and malicious insider actions directed at your organization. 

Microsoft Defender for Identity covers these key areas:

- Monitor and profile user behavior and activities.
- Protect user identities and reduce the attack surface.
- Identify suspicious activities and advanced attacks across the cyberattack kill-chain.

#### Monitor and profile user behavior and activities

Defender for Identity monitors and analyzes user activities and information across your network, including permissions and group membership, creating a behavioral baseline for each user. Defender for Identity then identifies anomalies with adaptive built-in intelligence. It gives insights into suspicious activities and events, revealing the advanced threats, compromised users, and insider threats facing your organization.

#### Protect user identities and reduce the attack surface

Defender for Identity gives invaluable insights on identity configurations and suggested security best practices. Through security reports and user profile analytics, Defender for Identity helps reduce your organizational attack surface, making it harder to compromise user credentials and advance an attack.

Defender for Identity security reports, help identify users and devices that authenticate using clear-text passwords. It also provides extra insights into how to improve security posture and policies.

#### Identify suspicious activities and advanced attacks across the cyberattack kill-chain

Typically, attacks are launched against any accessible entity, such as a low-privileged user. Attacks then quickly move laterally until the attacker accesses valuable assets. These assets might include sensitive accounts, domain administrators, and highly sensitive data. Defender for Identity identifies these advanced threats at the source throughout the entire cyberattack kill chain:

- Reconnaissance
- Compromised credentials
- Lateral movements
- Domain dominance

#### Investigate alerts and user activities

Defender for Identity is designed to reduce general alert noise, providing only relevant, important security alerts in a simple, real-time organizational attack timeline.

Use the Defender for Identity attack timeline view and the intelligence of smart analytics to stay focused on what matters. Also, you can use Defender for Identity to quickly investigate threats, and gain insights across the organization for users, devices, and network resources.

Microsoft Defender for Identity protects your organization from compromised identities, advanced threats, and malicious insider actions.



### Describe Microsoft Defender for Office 365

[Describe Microsoft Defender for Office 365 - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-threat-protection-with-microsoft-365-defender/4-describe-defender-office)

Microsoft Defender for Office 365, formerly Office 365 Advanced Threat Protection, safeguards your organization against malicious threats posed by email messages, links (URLs), and collaboration tools, including Microsoft Teams, SharePoint Online, OneDrive for Business, and other Office clients.

Microsoft Defender for Office 365 covers these key areas:

- **Threat protection policies**: Define threat protection policies to set the appropriate level of protection for your organization.
- **Reports**: View real-time reports to monitor Microsoft Defender for Office 365 performance in your organization.
- **Threat investigation and response capabilities**: Use leading-edge tools to investigate, understand, simulate, and prevent threats.
- **Automated investigation and response capabilities**: Save time and effort investigating and mitigating threats.

Microsoft Defender for Office 365 is available in two plans. The plan you choose influences the tools you’ll see and use. It's important to make sure you select the best plan to meet your organization's needs.

#### Microsoft Defender for Office 365 Plan 1

This plan offers configuration, protection, and detection tools for your Office 365 suite:

- **Safe Attachments**: Checks email attachments for malicious content.
- **Safe Links**: Links are scanned for each click. A safe link remains accessible, but malicious links are blocked.
- **Protection for SharePoint, OneDrive, and Microsoft Teams**: Protects your organization when users collaborate and share files by identifying and blocking malicious files in team sites and document libraries.
- **Anti-phishing protection**: Detects attempts to impersonate your users and internal or custom domains.
- **Real-time detections**: A real-time report that allows you to identify and analyze recent threats.

#### Microsoft Defender for Office 365 Plan 2

This plan includes all the core features of Plan 1, and provides automation, investigation, remediation, and simulation tools to help protect your Office 365 suite:

- **Threat Trackers**: Provide the latest intelligence on prevailing cybersecurity issues, and allow an organization to take countermeasures before there's an actual threat.
- **Threat Explorer**: A real-time report that allows you to identify and analyze recent threats.
- **Automated investigation and response (AIR)**: Includes a set of security playbooks that can be launched automatically, such as when an alert is triggered, or manually. A security playbook can start an automated investigation, provide detailed results, and recommend actions that the security team can approve or reject.
- **Attack Simulator**: Allows you to run realistic attack scenarios in your organization to identify vulnerabilities.

#### Microsoft Defender for Office 365 availability

Microsoft Defender for Office 365 is included in certain subscriptions, such as Microsoft 365 E5, Office 365 E5, Office 365 A5, and Microsoft 365 Business Premium.

If your subscription doesn’t include Defender for Office 365, you can purchase it as an add-on.

Use Microsoft 365 Defender for Office 365 to protect your organization's collaboration tools and messages.



### Describe Microsoft Defender for Endpoint

[Describe Microsoft Defender for Endpoint - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-threat-protection-with-microsoft-365-defender/5-describe-defender-endpoint)

Microsoft Defender for Endpoint, formerly Microsoft Defender Advanced Threat Protection, is a platform designed to help enterprise networks protect endpoints. It does so by preventing, detecting, investigating, and responding to advanced threats. Microsoft Defender for Endpoint embeds technology built into Windows 10 and MSFT cloud services.

This technology includes endpoint behavioral sensors that collect and process signals from the operating system, cloud security analytics that turn signals into insights, detections and recommendations, and threat intelligence to identify attacker tools, techniques, generate alerts.

![Diagram showing the seven aspects of Microsoft Defender Endpoint: Threat and Vulnerability Management, Attack surface reduction, Next-generation protection, Endpoint detection and response, automated investigation and remediation, Microsoft Threat Experts, and Centralized configuration and administration.](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-threat-protection-with-microsoft-365-defender/media/5-seven-aspects-microsoft-defender.png)

Microsoft Defender for Endpoint includes:

- **Threat and vulnerability management**: A risk-based approach to the discovery, prioritization, and remediation of endpoint vulnerabilities and misconfigurations. It uses sensors on devices to avoid the need for agents or scans, and prioritizes vulnerabilities.
- **Attack surface reduction**: Reduces the places where your organization is vulnerable to cyberthreats and attacks by ensuring only *allowed* apps can run, and preventing apps from accessing dangerous locations.
- **Next generation protection**: Brings together machine learning, big data analysis, in-depth threat resistance research, and the Microsoft cloud infrastructure to protect devices in your enterprise organization.
- **Endpoint detection and response**: Provides advanced attack detections that are near real time and actionable. Security analysts can prioritize alerts, see the full scope of a breach, and take response actions to remediate threats.
- **Automated investigation and remediation**: The automated investigation feature uses inspection algorithms and processes used by analysts (such as playbooks) to examine alerts and take quick remediation action to resolve breaches. This process significantly reduces the volume of alerts that must be investigated individually.
- **Microsoft Threat Experts**: A managed threat hunting service that provides Security Operation Centers (SOCs) with monitoring and analysis tools to ensure critical threats don’t get missed.
- **Management and APIs**: Provides APIs to integrate with other solutions.

Microsoft Defender for Endpoint includes Microsoft Secure Score for Devices to help you dynamically assess the security state of your enterprise network, identify unprotected systems, and take recommended actions to improve overall security. Microsoft Defender for Endpoint integrates with various components in the Microsoft Defender suite, and with other Microsoft solutions including Intune and Azure Security Center.

Use Microsoft Defender for Endpoint to protect your organization's endpoints and respond to advanced threats.



### Describe Microsoft Cloud App Security

[Describe Microsoft Cloud App Security - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-threat-protection-with-microsoft-365-defender/6-describe-microsoft-cloud-app-security)

Microsoft Cloud App Security (MCAS) is a Cloud Access Security Broker (CASB). It's a comprehensive cross-SaaS solution that operates as an intermediary between a cloud user and the cloud provider. 

Microsoft Cloud App Security provides rich visibility to your cloud services, control over data travel, and sophisticated analytics to identify and combat cyberthreats across all your Microsoft and third-party cloud services. Use this service to gain visibility into Shadow IT by discovering the cloud apps being used. You can control and protect data in the apps after you sanction them to the service.

#### What is a Cloud Access Security Broker?

A CASB acts as a gatekeeper to broker real-time access between your enterprise users and the cloud resources they use, wherever they're located, and whatever device they're using.

CASBs address security gaps in an organization’s use of cloud services. Protection is provided by many capabilities across these areas: **visibility** to detect all cloud services, **data security**, **threat protection**, and **compliance**. These capability areas represent the basis of the Cloud App Security framework described below.



#### The Cloud App Security framework

MCAS is built on a framework that provides the following capabilities:

- **Discover and control the use of Shadow IT**: Identify the cloud apps, and IaaS and PaaS services used by your organization. Investigate usage patterns, assess the risk levels and business readiness of more than 16,000 SaaS apps against more than 80 risks.
- **Protect your sensitive information** **anywhere in the cloud**: Understand, classify, and protect the exposure of sensitive information at rest. Use out-of-the-box policies and automated processes to apply controls in real time across all your cloud apps.
- **Protect against cyberthreats and anomalies**: Detect unusual behavior across cloud apps to identify ransomware, compromised users, or rogue applications, analyze high-risk usage, and remediate automatically to limit risks.
- **Assess your cloud apps' compliance**: Assess if your cloud apps meet relevant compliance requirements, including regulatory compliance and industry standards. Prevent data leaks to non-compliant apps and limit access to regulated data.



#### Microsoft Cloud App Security architecture

Cloud App Security isn’t only about how you strengthen or harden your servers to detect and prevent cyberattacks. It requires consideration on the architecture of your entire estate. How each server connects to its neighbor, and the routes that network traffic takes can make a significant difference your security model. 

Cloud App Security integrates visibility with your cloud by:

- Using Cloud Discovery to map and identify your cloud environment and the cloud apps your organization uses. Cloud Discovery uses your traffic logs to dynamically discover and analyze the cloud apps being used.
- Sanctioning and unsanctioning apps in your cloud. You can use Cloud App Security to sanction or unsanction apps in your organization by using the Cloud app catalog. It includes more than 16,000 cloud apps that are ranked and scored based on industry standards.
- Using straightforward app connectors that use provider APIs for visibility and governance of apps you connect to. App connectors use APIs from cloud app providers to integrate their cloud apps with MCAS, extending control and protection. These connectors also give you access to information directly from cloud apps, for Cloud App Security analysis.
- Using Conditional Access App Control protection to get real-time visibility and control over access and activities within your cloud apps.
- Helping you have continuous control by setting and then continually fine-tuning policies. You can use policies to define users' behavior in the cloud. Use policies to detect risky behavior, violations, or suspicious data points and activities in your cloud environment.

![Diagram showing how Cloud App Security acts as an intermediary, checking and verifying cloud apps usage.](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-threat-protection-with-microsoft-365-defender/media/6-cloud-app-security-intermediary.png)

#### Office 365 Cloud App Security

Office 365 Cloud App Security is a subset of Microsoft Cloud App Security that provides enhanced visibility and control for Office 365. Office 365 Cloud App Security includes threat detection based on user activity logs, discovery of Shadow IT for apps with similar functionality to Office 365 offerings, control app permissions to Office 365, and apply access and session controls.

It offers a subset of the core MCAS features.

#### Enhanced Cloud App Discovery in Azure Active Directory

Azure Active Directory Premium P1 includes Azure Active Directory Cloud App Discovery at no extra cost. This feature is based on the Microsoft Cloud App Security Cloud Discovery capabilities that provide deeper visibility into cloud app usage in your organization.

It provides a reduced subset of the MCAS discovery capabilities.

Use Microsoft Cloud App Security to intelligently and proactively identify and respond to threats across your organization's Microsoft and non-Microsoft cloud services.

#### Interactive guide

In this interactive guide, you’ll get an introduction to the many services and capabilities available through the Cloud App Security portal, including Discover, Investigate, Control, and Alerts.

To work through this guide, follow the prompts on the screen.

[![Interactive guide](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-threat-protection-with-microsoft-365-defender/media/6-interactive-guide-place-holder.png)](https://edxinteractivepage.blob.core.windows.net/edxpages/Security fundamentals/LP03M04 - Describe threat protection with Microsoft 365/index.html)





## Security management capabilities of Microsoft 365

### Describe and explore the Microsoft 365 Security Centre

[Describe and explore the Microsoft 365 security center - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-security-management-capabilities-of-microsoft-365/2-describe-explore-security-center)

The Microsoft 365 security center is the new home for monitoring and managing security across your Microsoft identities, data, devices, apps, and infrastructure. Here you can view the security health of your organization, act to configure devices, users, and apps, and get alerts for suspicious activity. The Microsoft 365 security center helps security admins and security operations teams manage and protect their organization.

The Microsoft 365 security center home page shows many of the common cards that security teams need. The composition of cards and data depends on the user role. Because the Microsoft 365 security center uses role-based access control, different roles will see cards that are more meaningful to their day-to-day jobs.

The Microsoft 365 security center allows admins to tailor the navigation pane to meet daily operational needs. Admins can customize the navigation pane to show or hide functions and services based on their specific preferences. Customization is specific to the individual admin, so other admins won’t see these changes.

 The Microsoft 365 security center navigation pane has these options:

- **Home**: Get an at-a-glance view of the overall security health of your organization.
- **Incidents**: See the broader story of an attack by connecting the dots seen on individual alerts on entities. You'll know exactly where an attack started, what devices are impacted, who was affected, and where the threat has gone.
- **Alerts**: Have greater visibility into all the alerts across your Microsoft 365 environment. Includes alerts from Microsoft Cloud App Security, Microsoft Defender for Office 365, Azure Active Directory, Microsoft Defender for Identity, and Microsoft Defender for Endpoint. Available to E3 and E5 customers.
- **Action center**: Reduce the volume of alerts your security team must address manually, allowing them to focus on more sophisticated threats and other high-value initiatives.
- **Reports**: Get the detail and information you need to better protect your users, devices, apps, and more.
- **Secure Score**: Improve your overall security posture with Microsoft Secure Score. This page provides an all up summary of the different security features and capabilities you've enabled, and includes recommendations for areas to improve.
- **Advanced hunting**: Proactively search for malware, suspicious files, and activities in your Microsoft 365 organization.
- **Classification**: Help protect data loss by adding labels to classify documents, email messages, sites, and more. When a label is applied (automatically or by the user), the content or site is protected based on the settings you choose. For example, you can create labels that encrypt files, add content marking, and control user access to specific sites.
- **Policies**: Set up policies to manage devices, protect against threats, and receive alerts about various activities in your organization.
- **Permissions**: Manage who, in your organization, has access to view content and perform tasks in the Microsoft 365 security center. You can also assign Microsoft 365 permissions in the Azure AD portal.

```
You must be assigned an appropriate role, such as Global Administrator, Security Administrator, Security Operator, or Security Reader in Azure Active Directory to access the Microsoft 365 security center.
```

The new Microsoft 365 security center is a specialized workspace designed to meet the needs of security and compliance teams. The Microsoft 365 security center provides actionable insights to help reduce risks and safeguard your digital estate.



### Describe how to use Microsoft Secure Score

[Describe how to use Microsoft Secure Score - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-security-management-capabilities-of-microsoft-365/3-describe-how-to-use-microsoft-secure-score)

Microsoft Secure Score, one of the tools in the Microsoft security center, is a representation of a company's security posture. The higher the score, the better your protection.

Secure Score helps organizations:

- Report on the current state of their security posture.
- Improve their security posture by providing discoverability, visibility, guidance, and control.
- Compare benchmarks and establish key performance indicators (KPIs).

Points are given for the following actions:

- Configuring recommended security features.
- Doing security-related tasks.
- Addressing the improvement action with a third-party application or software, or an alternate mitigation.

Some improvement actions only give points when fully completed. Others give partial points if they're completed for some devices or users. If you can't, or don't want to, enact one of the improvement actions, you can choose to accept the risk or remaining risk.

If you have a license for one of the supported Microsoft products, you'll see related recommendations. Secure Score will show all possible improvements for the product, whatever the license edition, subscription, or plan. You'll then see all the security best practices and improvements that can be made to your score.

Your absolute security posture, represented by Secure Score, stays the same whatever licenses your organization owns for a specific product. Keep in mind that security should be balanced with usability, and not every recommendation can work for your environment.

Currently Microsoft Secure Score supports recommendations for Microsoft 365 (including Exchange Online), Azure Active Directory, Microsoft Defender for Endpoint, Microsoft Defender for Identity, and Cloud App Security. New recommendations are being added to Secure Score all the time.

In this diagram, you can see the Secure Score is 32.86%. It illustrates a breakdown of the score by points, and then shows the improvement areas that will boost your score. Finally, it provides an indication of how well your score compares to other similar organizations.

[![Screenshot showing a Microsoft Secure Score page, with several panels highlighted: Secure Score, Breakdown of score, implementation actions, and a comparison of the score against other organizations.](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-security-management-capabilities-of-microsoft-365/media/3-secure-score-overview-inline.png)](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-security-management-capabilities-of-microsoft-365/media/3-secure-score-overview-expanded.png#lightbox)

#### Differences between the Azure and Microsoft Secure Score

There's a Secure Score for both Microsoft 365 Defender and Azure Defender, but they're subtly different. Secure Score in the Azure Security Center is a measure of the security posture of your Azure subscriptions. Secure Score in the Microsoft 365 security center is a measure of the security posture of the organization across your apps, devices, and identities.

Both the Azure and Microsoft Secure Score provide a list of steps you can take to improve your score. In Microsoft 365 Secure Score, these steps are called improvement actions. In the Azure Secure Score, scores are assessed for each subscription. The steps you can take to improve your score are called security recommendations and they're grouped into security controls.

Use Microsoft Secure Score to understand and rapidly improve your organization’s security posture.

#### Interactive guide

As the Microsoft 365 admin, you need to monitor and work on the security of your organization's Microsoft 365 identities, apps, data, and devices. The following interactive click-through demonstrates how Microsoft Secure Score can help.

[![Interactive guide](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-security-management-capabilities-of-microsoft-365/media/3-interactive-guide-place-holder.png)](https://edxinteractivepage.blob.core.windows.net/edxpages/Security fundamentals/LP03M05 - Explore Microsoft Secure Score/index.html)



### Explore security reports and dashboards

[Explore security reports and dashboards - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-security-management-capabilities-of-microsoft-365/4-explore-security-reports-dashboards)

The Microsoft security center includes a **Reports** section that shows various cards covering different areas. Security analysts and administrators can track the cards as part of their day-to-day operations. On drill-down, cards provide detailed reports and, in some cases, management options.

By default, cards are grouped by the following categories:

- **Identities** - user accounts and credentials.
- **Data** - email and document contents.
- **Devices** - computers, mobile phones, and other devices.
- **Apps** - programs and attached online services.

In the example below, the cards are grouped by category. 

- The first category is **Identities** where you find two cards, **Users at risk** and **Global admins**. 
- The second category is **Data** where you find two cards, **Users with the most shared files** and **Third-party DLP policy matches**.

[![Screenshot showing the Microsoft 365 security reports page.](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-security-management-capabilities-of-microsoft-365/media/4-microsoft-security-reports-inline.png)](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-security-management-capabilities-of-microsoft-365/media/4-microsoft-security-reports-expanded.png#lightbox)

You can group cards by topic, which will rearrange the cards and group them into the following areas:

- **Risk** - cards that highlight entities, such as accounts and devices, that might be at risk. These cards also highlight possible sources of risk, such as new threat campaigns and privileged cloud apps.
- **Detection trends** - cards that highlight new threat detections, anomalies, and policy violations.
- **Configuration and health** - cards that cover the configuration and deployment of security controls, including device onboarding states to management services.
- **Other** - all cards not categorized under other topics.

In the example below, the cards are grouped by topic. The first category is **Risk**. The second category is **Detection trends**.

[![Screen shot showing the Reports page within Microsoft 365 Security.](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-security-management-capabilities-of-microsoft-365/media/4-microsoft-security-reports-details-inline.png)](https://docs.microsoft.com/en-au/learn/wwl-sci/describe-security-management-capabilities-of-microsoft-365/media/4-microsoft-security-reports-details-expanded.png#lightbox)

Use the **Reports** section to view security trends across your organization, and track the protection of your organization’s devices, apps, identities, and data.





### Describe incident capabilities

[Describe incidents capabilities - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-security-management-capabilities-of-microsoft-365/5-describe-incidents-capabilities)

Incidents are a collection of correlated alerts created when a suspicious event is found. Alerts are generated from different device, user, and mailbox entities, and can come from many different domains. These alerts are automatically aggregated by Microsoft 365 Defender. It's the grouping of these related alerts that form an incident. The incident provides a comprehensive view and context of an attack.

Security personnel can use an incident to determine where an attack started, what methods were used, and to what extent the attack has progressed within the network. They can also determine the scope of the attack, and how many users, devices, and mailboxes were affected. The severity of the attack can also be determined.

#### Incident management

Managing incidents is critical in ensuring that threats are contained and addressed. In Microsoft 365 Defender, you can manage incidents on devices, users accounts, and mailboxes.

You can manage incidents by selecting one from the Incidents queue.

Incidents are automatically assigned a name based on an alert. You can edit the name of an incident, resolve it, then set its classification and determination. You can also assign the incident to yourself, and add incident tags and comments.

When you investigate cases where you want to move alerts from one incident to another, you can also do so from the Alerts tab. You'll create a larger or smaller incident that includes all relevant alerts.

Watch this four-minute video, which describes incidents and incident management.

<iframe src="https://www.microsoft.com/en-au/videoplayer/embed/RE4J3mt?postJsllMsg=true&amp;autoCaptions=en-au" frameborder="0" allowfullscreen="true" data-linktype="external" style="box-sizing: inherit; margin: 0px; padding: 0px; border: 0px; outline-color: inherit; width: 640px; position: absolute; inset: 0px; height: 360px;"></iframe>



















Use incidents to effectively and appropriately respond to alerts across your organization’s environment.





## Endpoint security with Microsoft Intune

[Describe endpoint security with Microsoft Intune - Learn | Microsoft Docs](https://docs.microsoft.com/en-au/learn/modules/describe-endpoint-security-with-microsoft-intune/)

Microsoft Intune is a cloud-based service that focuses on mobile device management (MDM) and mobile application management (MAM). You control how your organization’s devices, including mobile phones, tablets, and laptops, are used. You can also configure specific policies to control applications. For example, you can prevent emails from being sent to people outside your organization.

Intune also allows people in your organization to use their personal devices for school or work. On personal devices, Intune helps make sure your organization data stays protected, and can isolate it from personal data.

With Intune, admins can:

- Support a diverse mobile environment and manage iOS/iPadOS, Android, Windows, and macOS devices securely.
- Set rules and configure settings on personal and organization-owned devices to access data and networks.
- Deploy and authenticate apps for both on-premises and mobile devices.
- Protect your company information by controlling the way users access and share information.
- Be sure devices and apps are compliant with your security requirements.

### Mobile device management (MDM)

For devices that are owned by the business, organizations can maintain full control. This includes settings, features, and security. When these devices are enrolled with Intune, they'll receive rules and settings defined by Intune policies. For example, you can define password requirements.

When devices are enrolled and managed in Intune, administrators can:

- See the devices enrolled, and get an inventory of the ones accessing organization resources.
- Configure devices so they meet your security and health standards. For example, you probably want to block jailbroken devices.
- Push certificates to devices so users can easily access your Wi-Fi network, or use a VPN to connect to it.
- See reports on users and devices to determine if they're compliant.
- Remove organization data if a device is lost, stolen, or not used anymore.

To learn more, go to: [Manage devices](https://docs.microsoft.com/en-us/mem/intune/fundamentals/what-is-intune#manage-devices).

### Mobile application management (MAM)

Users with personal devices might not want their phone to be under full corporate control. Mobile application management (MAM) gives admins the ability to protect corporate data at the application level. Where users just want to access apps like email or Microsoft Teams, admins can use application protection policies, without requiring the device to be enrolled in Intune, supporting bring-your-own device (BYOD) scenarios.

MAM can be used with custom applications and store apps.

When apps are managed in Intune, administrators can:

- Add and assign mobile apps to user groups and devices, including users and devices in specific groups, and more.
- Configure apps to start or run with specific settings enabled and update existing apps already on the device.
- See reports on which apps are used and track their usage.
- Do a selective wipe by removing only organization data from apps.

To learn more, go to: [Manage apps](https://docs.microsoft.com/en-us/mem/intune/fundamentals/what-is-intune#manage-apps).



# Describe endpoint security with Intune

When admins want to configure and manage security tasks for at-risk devices, they can go to the Endpoint security node in Intune.

#### Manage devices

The Endpoint security node includes the *All devices* view, where you'll see a list of all devices from your Azure AD that are available in Microsoft Endpoint Manager.

From this view, you can select devices to drill in for more information, such as which policies a device isn't compliant with. You can also use access from this view to remediate issues for a device, including restarting, start a scan for malware, or rotate BitLocker keys on a Windows 10 device.

For more information, go to: [Manage devices with endpoint security in Microsoft Intune](https://docs.microsoft.com/en-us/mem/intune/protect/endpoint-security-manage-devices).

#### Manage security baselines

Intune includes [security baselines](https://docs.microsoft.com/en-us/mem/intune/protect/endpoint-security#manage-security-baselines) for Windows devices and a growing list of applications, including Microsoft Edge, Microsoft Defender for Endpoint (previously Microsoft Defender Advanced Threat Protection), and more. Security baselines are preconfigured groups of Windows settings that help admins apply recommended security.

As an example, the MDM Security Baseline automatically enables BitLocker for removable drives, automatically requires a password to unlock a device, and automatically disables basic authentication. Admins can also customize the baselines to enforce only those settings and values that are required.

#### Use policies to manage device security

Each [Endpoint security policy](https://docs.microsoft.com/en-us/mem/intune/protect/endpoint-security#use-policies-to-manage-device-security) focuses on aspects of device security like antivirus, disk encryption, firewalls, and areas such as endpoint detection and response and attack surface reduction, made available through integration with Microsoft Defender for Endpoint.

Endpoint security policies are one of several methods in Intune to configure settings on devices. When managing settings, it's important to understand what other methods being used in your environment can configure your devices, to [avoid policy conflicts](https://docs.microsoft.com/en-us/mem/intune/protect/endpoint-security#avoid-policy-conflicts).

#### Use device compliance policy

Use device compliance policy to establish the conditions by which devices and users are allowed to access the corporate network and company resources. With compliance policies, admins can set the rules that devices and users must meet to be considered compliant. Rules can include OS versions, password requirements, device threat levels, and more. To learn more, go to: [Use compliance policies to set rules for devices you manage with Intune](https://docs.microsoft.com/en-us/mem/intune/protect/device-compliance-get-started).

Device compliance policies are one of several methods in Intune to configure settings on devices. When managing settings, it's important to understand what other methods being used in your environment can configure your devices to [avoid policy conflicts](https://docs.microsoft.com/en-us/mem/intune/protect/endpoint-security#avoid-policy-conflicts).

#### Configure conditional access

Intune can be integrated with Azure AD conditional access policies to enforce compliance policies. Intune passes the results of your device compliance policies to Azure AD, which then uses conditional access policies to enforce which devices and apps can access your corporate resources.

The following are two common methods of using conditional access with Intune:

- Device-based conditional access, to ensure only managed and compliant devices can access network resources.
- App-based conditional access, which uses app protection policies to manage access to network resources by users on devices that aren't managed with Intune.

To learn more about using conditional access with Intune, go to: [Learn about Conditional Access and Intune.](https://docs.microsoft.com/en-us/mem/intune/protect/conditional-access)

#### Integration with Microsoft Defender for Endpoint

Intune can integrate with Microsoft Defender for Endpoint (formerly Microsoft Defender ATP) for a Mobile Threat Defense solution. Integration can help prevent security breaches and limit the impact of breaches within an organization.

Microsoft Defender for Endpoint works with devices that run:

- Android
- iOS/iPadOS
- Windows 10 or later

By integrating Intune with Microsoft Defender for Endpoint, organizations can take advantage of Microsoft Defender for Endpoint’s Threat and Vulnerability Management (TVM), using Intune to remediate endpoint weakness identified by TVM.

To learn more, go to: [Enforce compliance for Microsoft Defender for Endpoint with Conditional Access in Intune](https://docs.microsoft.com/en-us/mem/intune/protect/advanced-threat-protection).

#### Role-based access control with Microsoft Intune

Role-based access control (RBAC) helps manage who has access to the organization's resources and what they do with them. By assigning roles to Intune users, admins limit what they'll see and change. Each role has a set of permissions that determine what users with that role can access and change within your organization.

To manage tasks in the Endpoint security node of the Microsoft Endpoint Manager admin center, an account must have RBAC permissions equal to the permissions provided by the built-in Intune role of **Endpoint Security Manager**. The Endpoint Security Manager role grants access to the Microsoft Endpoint Manager admin center. This role can be used by individuals who manage security and compliance features, including security baselines, device compliance, conditional access, and Microsoft Defender for Endpoint.

To learn more, go to: [Role-based access control (RBAC) with Microsoft Intune](https://docs.microsoft.com/en-us/mem/intune/fundamentals/role-based-access-control).

#### Video demonstration of Microsoft Endpoint Manager capabilities

In this eight-minute video, you’ll explore Endpoint Manager, and some of its capabilities.

<iframe src="https://www.microsoft.com/en-au/videoplayer/embed/RE4LTIu?postJsllMsg=true&amp;autoCaptions=en-au" frameborder="0" allowfullscreen="true" data-linktype="external" style="box-sizing: inherit; margin: 0px; padding: 0px; border: 0px; outline-color: inherit; width: 640px; position: absolute; inset: 0px; height: 360px;"></iframe>

\



