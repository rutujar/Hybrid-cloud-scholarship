# Lesson 4

## Hybrid Cloud Security

Security today is more complicated than it’s ever been. There are more workloads than the industry has ever had to deal with before. As a result of virtualization, these workloads are often sitting on a single hardware platform.

With traditional infrastructure, stacks are composed of products from multiple vendors, each with a narrow and limited view of security. Validating and maintaining a security baseline through continuous software upgrades, is time-consuming and often involves error-prone manual processes that take away from innovation and productivity.

Traditional security solutions such as firewalls are often blind to the internal communication between virtual machines and applications. Once cybercriminals infiltrate the network, they can take up residence and move laterally without being detected. The inherent complexity of this infrastructure has led to increased risks.

### Security Standards

Since there’s always that risk of someone getting in, a lot of organizations find themselves in a risky place. More often than not, they deal with large volumes of sensitive data around with a high standard of security must be maintained. In order to ensure there are standards organizations can hold themselves to, a number of widely accepted and enforced definitions have been developed.

There are five major government standards for security that IT needs to take into consideration. They are TAA Compliance, NSA Suite B, 508 Compliance, FIPS Compliance, and Common Criteria.

TAA Compliance
The Trade Agreements Act refers to a law requiring the U.S. government purchase only “U.S.-made or designated country end products.” Companies and contractors are considered TAA-compliant if they follow TAA guidelines.

End products are “articles, materials and supplies to be acquired for public use," according to the text of the law. Designated countries include Free Trade Agreement countries, countries that have signed the World Trade Organization Agreement on Government Procurement, Caribbean basin countries and some "least-developed" countries.

China, Taiwan, India, Thailand and Malaysia are not considered designated countries in the TAA. However, U.S. contractors can use supplies from these countries and other non-designated countries, as long as they substantially transform them into different final products that meet the criteria. Contractors and companies that do not comply with TAA rules may face lawsuits or have trouble obtaining government contracts.

NSA Suite B
NSA Suite B is a set of commercially available encryption algorithms, published by the US’s National Security Agency, for use in commercial applications as well as some types of classified information.

Suite B specifies a mode of operation in which only a specific set of secure cryptographic algorithms should be used. Suite B specifies the encryption algorithm, the key exchange algorithm, the digital signature algorithm, and the hashing algorithms.

508 Compliance
In 1998, the United States Congress amended the Rehabilitation Act to require Federal agencies to make their electronic and information technology accessible to people with disabilities.

Section 508 was enacted to eliminate barriers in information technology, to make available new opportunities for people with disabilities, and to encourage development of technologies that will help achieve these goals. The law applies to all Federal agencies when they develop, procure, maintain, or use electronic and information technology.

508 Compliance, involves ensuring accessibility in technology. While it’s popularly and more commonly known in the context of website accessibility, 508 Compliance is a key part of systems and platform development as well. Although it isn’t technically a security standard, it’s here because – just like security – 508 compliance needs to be built into a product from the ground up.

It needs to be considered in UI design, navigation, menus and interactions, labelling, and so much more.

FIPS Compliance
FIPS 140-2 stands for Federal Information Processing Standard 140-2 and, like the other standards listed here, is US-government specific. The standard itself is used to approve cryptography modules and is required when working in any capacity with the United States government. FIPS 140-2 is derived from the Federal Information Security Management Act of 2002 (FISMA) and the Federal Information Security Modernization Act of 2014.

The Federal Information Security Management Act of 2002 is a United States federal law that recognized the importance of information security to the economic and national security interests of the United States. The act requires each federal agency to develop, document, and implement an agency-wide program to provide information security for the information and information systems that support the agency. This also includes information and system that were provided or managed by another agency, contractor, or other sources.

FISMA was superseded by the Federal Information Security Modernization Act of 2014, which removed some elements from FISMA and amended other aspects for changes in cybersecurity and oversight.

Common Criteria
The Common Criteria for Information Technology Security Evaluation, also called Common Criteria, is an international standard for computer security. It allows the users of a system to specify their functional and functional assurance requirements for a specific product. Technology vendors can then, based on these requirements, evaluate their products against these requirements to confirm compliance.

Common Criteria provides assurance that the process of specification, implementation and evaluation of a computer security product has been conducted in a rigorous, and standard manner at a level that corresponds with its target use environment. Once this process is completed successfully, a vendor achieves Common Criteria certification.

There are two major components to Common Criteria. The first, is a Protection Profile, which is a document that specifies the requirements for a class of security devices, such as firewalls. This document is what vendors evaluate their products against to determine Common Criteria Compliance.

The second component is the Evaluation Assurance Level, which – as the name suggests – refers to the evaluation itself. More specifically, it is a numerical rating that described the rigor and depth of an evaluation.

### How Secure Are Your Clouds?
Leveraging the public cloud doesn’t mean you give up all control over security. There are still measures that you can implement, but they only go so far. In practice, you’ll find that you can control and secure about 80% of a public cloud’s capabilities. While that is a considerable amount of control, it does still mean that roughly 20% is left to the cloud provider and their security measures. Most public cloud providers do an excellent job of securing that 20%, but that doesn’t mean breaches are an impossibility.

On the other hand, with the private cloud, you have full control over your security. That means you can potentially be more secure than the public cloud but, simply having an on-prem setup doesn’t bolster security by itself. That is one of the reasons that these security standards are so important. They represent a benchmark against which you can measure your own security profile, determine what areas of your environment are well set up and which ones are in need of some tightening. Your on-prem cloud is only as secure as the products you use to build your technology stack. This is why security needs to be built into those products from the ground up.

### Securing Clouds from the Ground Up

Toggle Sidebar
Securing Clouds from the Ground Up
Securing Clouds from the Ground Up

Why are the standards we just talked about are so important?

Each of these standards represents a set of considerations for the way a product is conceptualized, designed, programmed, and tested - and ultimately determines who it can be sold to. These considerations aren’t things that can be bolted on at the last minute.

For a system – any system – to be as protected as it can be, security needs to be built in from the ground up. This is why compliance is something you consider even before you start development. When you’re gathering requirements, determining functionality, and figuring out the sort of product that you’re going to build, you need to consider how security will affect decisions you make during development.

Because of this, it’s important to understand the security development life cycle.

### Security Development Life Cycle
This is a high-level overview of the Security Development Life Cycle. It is a process with different phases that contain security activities that sits inside of the classic people-process-technology triangle. The SecDL forms the process portion.

It includes both the central security team that governs the process and updates it, as well as the product or development teams that perform security activities. The technology portion consists of tools that assist in finding vulnerabilities in source code or discovering vulnerabilities in a running instance of the product or application.

The SecDL is methodology-neutral. Security activities fit within any product development methodology, whether waterfall, or DevOps. Methodology differences show up in the cadence of security activities.

The SecDL was developed during the time of waterfall, so it is usually portrayed as a linear process that begins with requirements and ends with the release. When the SDL is extended to agile, some security activities get integrated into the normal sprint schedule, while others are pursued out-of-band. With DevOps, activities are embedded into the build pipeline using automation, while additional activities happen outside the pipeline.

### SecDL: Analyze
The first phase is essentially requirements gathering. In this phase, the goal is to defined the security best practices that will be integrated into a product. These practices may come from industry standards or be based on responses to problems that have occurred in the past. Requirements exist to define the functional security requirements implemented in the product, and include all the activities of the SDL. They are used as an enforcement point to ensure that all pieces are properly considered.

Requirements may take the classic form, stating that the product or application must, can, or should, do something. An example might be that the product must enforce a minimum password length of eight characters. In the agile world, requirements are expressed as user stories. These stories contain the same information as do the requirements, but security functionality is written from the user's perspective.

### SecDL: Design
The design phase of the SDL consists of activities that ideally occur before code is written. Secure design is about quantifying an architecture, for a single feature or the entire product, and then searching for problems.

The key to identifying problems is threat modeling. Threat modeling is the process of thinking through how a feature or system will be attacked, and then mitigating those future attacks in the design before writing the code. If you’ve seen the 2002 film Minority Report, that’s kind of the function that threat modeling serves – it’s about preventing crimes before they happen.

A solid threat model understands a feature's, or product's, attack surface. It then defines the most likely attacks that will occur across those interfaces. A threat model is only as good as the mitigations it contains to fix the problems. It is crucial to identifying security issues early in the process.

### SecDL: Implement
The next phase is implementation, which involves actually writing secure code. The SecDL contains a few things programmers must do to ensure that their code has the best chance of being secure. The process involves a mixture of standards and automated tools.

On the standards front, a solid SecDL defines a secure coding guide, that defines what is expected and provides guidance for when developers hit a specific issue and need insight. Implementation tools include Static Application Security Testing, or SAST, and Dynamic Application Security Testing, or DAST, software.

SAST is like a spell-checker for code, identifying potential vulnerabilities in the source code. SAST runs against a nightly build or may be integrated into your IDE. It may find and open new bugs in the bug management system nightly or prompt the developer to pause while coding to fix a problem in real time.

DAST checks the application's runtime instantiation. It spiders through an application to find all possible interfaces and then attempts to exploit common vulnerabilities in the application. These tools are primarily used on web interfaces.

### SecDL: Test
Formal test activities include security functional test plans, vulnerability scanning, and penetration testing. Vulnerability scanning uses industry-standard tools to determine if any system-level vulnerabilities exist with the application or product.

Penetration testing involves testers attempting to work around the security protections in a given application and exploit them. Penetration testing also stretches the product and exposes it to testing scenarios that automated tools cannot replicate. Because penetration testing is resource-intensive, it is usually not performed for every release.

### SecDL: Update
The findings from tests are updated as necessary and the product itself is then prepared for release.

Release occurs when all the security activities are confirmed against the final build and the software is sent to customers or made available for download. After the software is released, an interface is typically provided for external customers and security researchers to report security problems in products.

Part of this response interface should ideally include a product security-incident response team that focuses on triaging and communicating product vulnerabilities, both individual bugs and those that will require industry-wide collaboration such as Heartbleed, Bashbug, etc.

Finally, there are other security activities are also important to the success of a SecDL, including security champions, bug bounties, and education and training.

### SecDL and Nutanix
Our security development life cycle integrates security into every step of product development, rather than applying it as an afterthought. It is a foundational part of product design. The pervasive culture and processes built around security harden the Hybrid Cloud OS and eliminate zero-day vulnerabilities.

For example, research and development teams work together to fully understand all the code in the product, whether it is produced in-house or inherited from dependencies. We schedule product updates to handle known common vulnerabilities and exposures, or CVEs, for minor release cycles, and backport all dependencies to their latest release versions in major release cycles. This approach significantly reduces zero-day risks without slowing down product evolution.

Efficient one-click operations and self-healing security models enable automation to maintain security in an always-on hyperconverged solution. Finally, Nutanix also delivers validated joint solutions with security-focused vendors.

### Security in the Hybrid Cloud
As a result of the Nutanix approach to SecDL, and with the way we built security into our products from the ground up, you’ll find that the Hybrid Cloud has a number of security features available out of the box.

While there’s more to Nutanix security than the five points you’re seeing here, these are the major topics we’re going to talk about in this lesson. Broadly, we’re going to cover two-factor authentication, cluster lockdown, key management and administration, STIG implementation, data-at-rest encryption, and role-based access control.

### Two-Factor Authentication
Several different types of authentication exist, including one way, two way, and two-factor.

One way authentication involves simply authenticating to the server. Two-way involves the server also authenticating the client.

Two-factor authentication is a subset of multi-factor authentication, which involves presenting two or more pieces of evidence to an authentication mechanism. These pieces of evidence are typically combinations of three things: something the user knows, something the user has, and something the user is.

A good example of this is typically bank transactions. Very often, when performing an online transaction, you’ll also be asked to confirm the transaction by entering a time-limited password sent to your mobile phone via text message, or to your email account. In this case, entering your card or account details represent knowledge as the first factor, and the password comes from something you have or own – in this example, your phone or email account.

Two-factor authentication simply involves two pieces of information. In the case of Nutanix’s implementation, it involves a username and password combination, and a client certificate. For two-factor authentication, Nutanix administrators can use either local accounts, or Active Directory.

### Cluster Lockdown
Cluster lockdown is the ability to disable password-based CVM access and/or only allow key based access.

However, you can add your public SSH-key via Prism and still login via SSH by using your ssh key. This adds a layer of non-repudiation to the connection, since the key used to access the emergency account on the shell is logged. This adds a layer of cryptographic exchange to the connection instead of just a source IP.

All CVMs have a set of ssh-keys that are generated at installation, so all CVMs in a cluster can still communicate with each other using keys,and you can ssh between them using keys once you gain access.

### Key Management and Administration
Nutanix nodes are authenticated by a key management server, or KMS. SEDs generate new encryption keys, which are uploaded to the KMS. In the event of power failure or a reboot, keys are retrieved from the KMS and used to unlock the SEDs. These security keys can also be instantly reprogrammed. And finally, Crypto Erase can be used to instantly erase all data on an SED while generating a new key.

### Security Technical Implementation Guides
Security Technical Implementation Guides, or STIGs, are the configuration standards for DoD Information Assurance, or IA, and IA-enabled devices/systems. STIGs specify how a computing device must be configured to maximize security.

A STIG describes how to minimize network-based attacks and prevent system access when the attacker is interfacing with the system, either physically at the machine or over a network. STIGs also describe maintenance processes such as software updates and vulnerability patching. Advanced STIGs cover the design of a corporate network, covering the configurations of routers, firewalls, domain name servers, and switches.

Once deployed, STIGs lock down IT environments and reduce security vulnerabilities in infrastructure. Traditionally, using STIGs to secure an environment is a manual process that is highly time-consuming and error prone. Because of this, only the most security-conscious IT shops follow the required process. Nutanix has created custom STIGs that are based on the guidelines outlined by The Defense Information Systems Agency, or DISA, to keep the Hybrid Cloud Platform within compliance and reduce attack surfaces.

### Data-at-Rest Encryption
Data-at-Rest Encryption secures data while at rest using self-encrypting drives and key-based access management. For customers who require enhanced data security, Nutanix provides a software-only encryption option for data-at-rest security which does not require self-encrypting drives.

With Nutanix’s Data-at-Rest Encryption implementation data is encrypted on all drives at all times, data is inaccessible in the event of drive or node theft, data on a drive can be securely destroyed, protection can be enabled or disabled at any time, and no performance penalty is incurred despite encrypting all data.

### Role-Based Access Control
The last security capacity that we’re going to discuss in this lesson is role-based access control. Prism supports role-based access control that you can configure to provide customized access permissions to users based on their assigned roles. The roles dashboard allows you to view information about all defined roles and the users and groups assigned to those roles.

Prism includes a set of predefined roles. You can also define additional custom roles. Configuring authentication confers default user permissions that vary depending on the type of authentication like full permissions from a directory service, or no permissions from an identity provider. You can configure role maps to customize these user permissions. Finally, you can refine access permissions even further by assigning roles to individual users or groups that apply to a specified set of entities.

### Lesson Recap
* Introduced you to security
* Went over security standards
* Discussed the Security Development Life Cycle
* Discussed how to secure the Hybrid Cloud
