# ☁️ Introduction to Cloud Computing

A beginner-friendly guide to cloud computing, on-premises infrastructure, cloud deployment models, and cloud service models, with practical examples and AWS services.

---

## 📚 Table of Contents

- [Introduction to Cloud Computing](#-introduction-to-cloud-computing)
- [Cloud Computing vs On-Premises](#-cloud-computing-vs-on-premises)
  - [What Is On-Premises Infrastructure?](#1-what-is-on-premises-infrastructure)
  - [What Is Cloud Computing?](#2-what-is-cloud-computing)
  - [Advantages of On-Premises Infrastructure](#3-advantages-of-on-premises-infrastructure)
  - [Disadvantages of On-Premises Infrastructure](#4-disadvantages-of-on-premises-infrastructure)
  - [Advantages of Cloud Computing](#5-advantages-of-cloud-computing)
  - [Disadvantages of Cloud Computing](#6-disadvantages-of-cloud-computing)
  - [Cloud vs On-Premises Comparison](#7-cloud-vs-on-premises-comparison)
  - [Real-World Example](#8-real-world-example)
- [AWS Cloud Computing Models](#-aws-cloud-computing-models)
  - [Deployment Models](#-deployment-models)
  - [Public Cloud](#-public-cloud)
  - [Private Cloud](#-private-cloud)
  - [Hybrid Cloud](#-hybrid-cloud)
  - [Multicloud](#-multicloud)
  - [Service Models](#-service-models)
  - [IaaS](#-iaas--infrastructure-as-a-service)
  - [PaaS](#-paas--platform-as-a-service)
  - [SaaS](#-saas--software-as-a-service)
- [Quick Revision](#-quick-revision)
- [References](#-references)

---

## 🌥️ Introduction to Cloud Computing

Cloud computing is the delivery of computing services such as servers, storage, databases, networking, and software over the internet.

Instead of purchasing physical servers and maintaining them in our own data center, we can rent computing resources from cloud providers such as Amazon Web Services (AWS), Microsoft Azure, and Google Cloud.

**Example:** Imagine you want to start an online shopping website. Instead of purchasing a physical server, you can use AWS to rent a virtual computer, store your website files, and make your website available to customers over the internet.

## 🏢 Cloud Computing vs On-Premises

### 1. What Is On-Premises Infrastructure?

On-premises infrastructure means a company purchases and maintains its own IT infrastructure, such as physical servers, storage devices, networking equipment, and security systems, at its own location or data center.

The company is responsible for managing the hardware, software, maintenance, security, and upgrades.

**Example:** A bank purchases physical servers, installs them in its own data center, and uses them to run banking applications and store customer data.

### 2. What Is Cloud Computing?

Cloud computing means using computing resources over the internet instead of purchasing and maintaining all the physical hardware yourself.

Cloud providers manage the underlying physical infrastructure, while customers manage their resources and applications according to the services they use.

**Example:** A company uses AWS to rent virtual computers, store data, and host its website instead of purchasing physical servers.

### 3. Advantages of On-Premises Infrastructure

- **Full control:** The company has direct control over its physical servers and infrastructure.
- **Data control:** The company can directly manage where its data is stored.
- **Customization:** Hardware and software can be configured according to business requirements.
- **Security control:** The company can implement its own security policies and access controls.
- **No cloud provider dependency:** The company does not depend on a cloud provider for its infrastructure.
- **Predictable costs:** Owning hardware may be cost-effective for stable workloads over the long term.
- **Legacy application support:** Older applications that require specific hardware or software can continue running on-premises.

### 4. Disadvantages of On-Premises Infrastructure

- **High initial investment:** Companies need to spend money purchasing physical servers, storage, and networking equipment.
- **Maintenance:** The company is responsible for maintaining servers and replacing damaged hardware.
- **Electricity costs:** Servers run continuously and consume electricity.
- **Cooling costs:** Data centers need cooling systems to prevent servers from overheating.
- **Difficult to scale:** Business growth may require purchasing additional servers and storage.
- **Disaster recovery:** The company needs backup systems and recovery plans.
- **IT staff required:** Skilled employees are needed to manage and maintain the infrastructure.

### 5. Advantages of Cloud Computing

- **Low initial investment:** No need to purchase physical servers or build your own data center.
- **Easy scalability:** Resources can be increased or decreased when needed.
- **Pay-as-you-go:** Many cloud services offer usage-based pricing.
- **High availability options:** Cloud providers offer features to help applications remain available.
- **Global access:** Applications can be accessed from different locations through the internet or private connections.
- **Less hardware maintenance:** The provider manages the physical servers, power, and cooling.
- **Backup and recovery:** Cloud services offer options for backups and disaster recovery.

### 6. Disadvantages of Cloud Computing

- **Internet dependency:** Access to cloud services generally requires a reliable network connection.
- **Ongoing costs:** Usage-based charges can become expensive if resources are not managed properly.
- **Security risks:** Incorrect configurations can expose sensitive data.
- **Less hardware control:** Customers generally cannot directly control the provider's physical servers.
- **Vendor dependency:** Moving applications and data between providers can be difficult.
- **Technical knowledge:** Managing cloud services requires knowledge of cloud platforms.
- **Service outages:** Cloud services can sometimes experience downtime.

### 7. Cloud vs On-Premises Comparison

| Comparison | On-Premises | Cloud Computing |
|---|---|---|
| Infrastructure | Company owns hardware | Provider supplies hardware |
| Location | Company's data center | Cloud provider's data center |
| Initial cost | Usually high | Usually lower |
| Maintenance | Company manages hardware | Provider manages physical hardware |
| Scalability | Requires purchasing hardware | Easier to scale |
| Storage | Company purchases storage devices | Storage available as a cloud service |
| Security | Company manages its infrastructure security | Shared responsibility |
| Accessibility | Depends on network configuration | Internet or private network access |
| Payment | Hardware and maintenance costs | Usage-based or subscription pricing |
| Physical control | More direct control | Less direct control |

### 8. Real-World Example

Imagine a company wants to launch an e-commerce website.

**🏢 On-Premises Approach**

The company purchases physical servers, storage devices, and networking equipment. It installs everything in its own data center and hires IT engineers to maintain the infrastructure.

If the number of customers increases, the company may need to purchase additional servers.

**☁️ Cloud Approach**

Instead of purchasing physical servers, the company uses AWS to host its website. Resources can be increased or decreased as demand changes.

**AWS Walkthrough: Starting a Small Online Shop**

1. **Amazon EC2:** Rent a virtual computer to run the website.
2. **Amazon EBS:** Provide block storage for the EC2 instance, such as its operating system and application files.
3. **Customer access:** Customers visit the website and purchase products.
4. **Auto Scaling:** Add EC2 instances as demand increases when Auto Scaling is configured.
5. **Scale in:** Reduce the number of EC2 instances when demand decreases to help control costs.

In this way, AWS allows companies to adjust computing resources when required without purchasing physical servers.

---

## ☁️ AWS Cloud Computing Models

Cloud computing can be classified in two different ways:

- **Deployment models:** Explain how the cloud environment is organized and used.
- **Service models:** Explain what the cloud provider manages and what the customer manages.

## 🔍 Deployment Models

### ☁️ Public Cloud

Cloud services are delivered by a provider over the internet. The provider's infrastructure serves multiple customers, while their resources and data are logically separated.

**AWS examples:** Amazon EC2 and Amazon S3.

**Scenario:** A business hosts its website on AWS instead of buying and maintaining physical servers.

### 🔒 Private Cloud

A private cloud environment is dedicated to one organization. It can run in the organization's own data center or on dedicated infrastructure.

**AWS note:** An Amazon VPC is a logically isolated network within AWS. A VPC is useful for building a private network, but a VPC by itself is not a complete private cloud.

**Scenario:** A company places application servers and a database in private subnets so they are not directly reachable from the public internet.

### 🔗 Hybrid Cloud

A hybrid cloud connects a private environment, often an on-premises data center, with a public cloud such as AWS.

**AWS examples:** AWS Direct Connect and AWS Site-to-Site VPN can connect a company network to an AWS VPC.

**Scenario:** A company keeps a database in its own data center while running its website in AWS.

### 🌐 Multicloud

Multicloud means using services from two or more cloud providers.

**Example:** A company runs one workload on AWS and another on Microsoft Azure or Google Cloud.

**Remember:** Using multiple AWS services is still using one cloud provider. That alone is not multicloud.

### 📊 Deployment Models at a Glance

| Model | Simple Explanation | Example |
|---|---|---|
| Public cloud | Provider's cloud infrastructure serves multiple customers | Website hosted on AWS |
| Private cloud | Cloud environment dedicated to one organization | Organization's dedicated private environment |
| Hybrid cloud | Private environment connected to a public cloud | On-premises database connected to AWS |
| Multicloud | Services from multiple cloud providers | One company uses AWS and Azure |

---

## 🧰 Service Models

Service models describe how management responsibilities are divided between the cloud provider and the customer.

**Key idea:** IaaS gives you more control and responsibility, while SaaS provides a ready-to-use application.

### 🖥️ IaaS — Infrastructure as a Service

The provider supplies basic computing resources such as virtual servers, storage, and networking. You manage more of the software, including the operating system and your application.

**AWS example:** Amazon EC2.

**Scenario:**

1. Launch an EC2 instance.
2. Choose an operating system.
3. Install a web server.
4. Deploy your website.

You have more control over the server, but you are also responsible for managing its operating system and software.

### ⚙️ PaaS — Platform as a Service

The provider manages more of the infrastructure and application platform. You focus mainly on deploying and maintaining your application.

**AWS example:** AWS Elastic Beanstalk.

**Scenario:** Deploy your web application to Elastic Beanstalk, which helps provision and manage the environment needed to run it.

### 📱 SaaS — Software as a Service

The provider runs a complete application. You access and configure the software without managing its servers or operating system.

**Example:** Salesforce is a SaaS application. Web-based email is another familiar example.

**Scenario:** Sign in to an online application through a browser. The provider operates and maintains the application.

### 📊 Service Models at a Glance

| Model | Provider Manages | Customer Mainly Manages | Example |
|---|---|---|---|
| IaaS | Physical infrastructure and virtualization | Operating system, applications, and data | Amazon EC2 |
| PaaS | Infrastructure and much of the application platform | Application and its data | AWS Elastic Beanstalk |
| SaaS | Complete application and underlying infrastructure | How the application is used and configured | Salesforce |

---

## 🛒 Putting the Models Together

Imagine an online shop:

1. **Public cloud deployment:** The shop runs on AWS.
2. **IaaS:** Amazon EC2 runs an application server, and the team manages its operating system.
3. **Managed database:** Amazon RDS handles much of the database infrastructure.
4. **SaaS:** The company uses a SaaS tool to manage customer support.

One application can use multiple cloud services, each with a different level of management responsibility.

---

## 📝 Quick Revision

| Term | Remember This |
|---|---|
| On-premises | The company owns and manages its own infrastructure |
| Cloud computing | Computing resources are provided over a network |
| Public cloud | Provider's cloud infrastructure serves multiple customers |
| Private cloud | Cloud environment dedicated to one organization |
| Hybrid cloud | Private environment connected to a public cloud |
| Multicloud | Services from multiple cloud providers |
| IaaS | Rent infrastructure and manage more of the software stack |
| PaaS | Deploy your application on a managed platform |
| SaaS | Use a ready-to-use application managed by its provider |

### 🎯 Key Takeaway

**On-premises vs cloud** explains where infrastructure is owned and operated.

**Deployment models** explain how cloud environments are organized.

**Service models** explain how responsibilities are shared between the provider and the customer.

Companies choose their approach based on their budget, security requirements, business needs, and workloads. Some organizations use a **hybrid approach**, combining on-premises infrastructure with cloud services.

---

## 🔗 References

- [AWS — Types of Cloud Computing](https://aws.amazon.com/types-of-cloud-computing/)
- [AWS — Overview of Amazon Web Services](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/)
