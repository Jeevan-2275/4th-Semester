# Unit 2: Cloud Architecture, Services & Applications (Deep Exam Notes)

> **Target:** 7-Mark Questions (Comparisons & Architecture)
> **Key Concepts:** The SPI Model (SaaS, PaaS, IaaS), Deployment Models, Service Management.

---

## Q1: Explain the Cloud Computing Stack (Layered Architecture). (7 Marks)

The Cloud Computing Stack is often referred to as the **SPI Model** (SaaS, PaaS, IaaS). It represents the different layers of abstraction provided to the user.

### 1. The Stack Layers
*   **Bottom Layer: Infrastructure as a Service (IaaS):**
    *   The foundation. Provides raw computing power (virtual machines, storage, networks).
    *   *Analogy:* Renting a plot of land and building your own house.
*   **Middle Layer: Platform as a Service (PaaS):**
    *   Provides a development environment (OS, databases, web servers) for developers to build apps.
    *   *Analogy:* Renting a furnished house where you can cook your own food.
*   **Top Layer: Software as a Service (SaaS):**
    *   Provides finished applications to end-users over the web.
    *   *Analogy:* Staying in a hotel where everything is provided (room service, cleaning).

---

## Q2: Differentiate between IaaS, PaaS, and SaaS. (7 Marks - *Most Common Question*)

| Feature | IaaS (Infrastructure as a Service) | PaaS (Platform as a Service) | SaaS (Software as a Service) |
| :--- | :--- | :--- | :--- |
| **Definition** | Provides virtualized computing resources over the internet. | Provides a platform allowing customers to develop, run, and manage applications. | Provides software that is accessed online via a subscription. |
| **Target User** | System Admins, Network Architects | Developers | End Users (Business/Consumer) |
| **You Manage** | Application, Data, Runtime, Middleware, OS | Application, Data | Nothing (just usage settings) |
| **Vendor Manages** | Virtualization, Servers, Storage, Networking | Runtime, Middleware, OS, Virtualization, Servers, Storage, Network | Everything (App to Network) |
| **Technical Knowledge** | High (must know OS, Networking) | Medium (Coding skills needed) | Low (None) |
| **Examples** | AWS EC2, Google Compute Engine (GCE), DigitalOcean | Google App Engine, Heroku, AWS Elastic Beanstalk | Gmail, Salesforce, Dropbox, Zoom |

---

## Q3: Deep Dive into Service Models. (7 Marks per model)

### A. Infrastructure as a Service (IaaS)
*   **Core Capability:** Provisioning processing, storage, networks.
*   **Key Features:**
    *   **Virtualization:** The enabler of IaaS.
    *   **Scalability:** Scale up/down VMs instantly.
    *   **Control:** User has root/admin access to the VM.
*   **Case Study: Amazon EC2 (Elastic Compute Cloud):**
    *   Allows users to rent virtual computers involved in "instances".
    *   Users can choose CPU, RAM, and Storage capacity.

### B. Platform as a Service (PaaS)
*   **Core Capability:** Deploy onto the cloud infrastructure consumer-created or acquired applications.
*   **Key Features:**
    *   **No OS Management:** Developer doesn't worry about Windows updates or Linux patches.
    *   **Built-in Tools:** Database, Web Servers pre-installed.
    *   **Focus:** "Code and Deploy".
*   **Case Study: Google App Engine:**
    *   Allows building and hosting web apps in Google-managed data centers.
    *   SDKs available for Java, Python, Go.

### C. Software as a Service (SaaS)
*   **Core Capability:** Use the provider’s applications running on a cloud infrastructure.
*   **Key Features:**
    *   **Accessibility:** Web browser based.
    *   **Centralized Updates:** Provider updates the software for everyone instantly.
    *   **Multi-tenancy:** One instance serves multiple customers.
*   **Case Study: Salesforce.com:**
    *   CRM (Customer Relationship Management) heavily used by enterprises.

---

## Q4: Identity as a Service (IDaaS). (Short Note)

**IDaaS** is a cloud-based service for Identity and Access Management (IAM).
*   **Problem:** With so many SaaS apps (Gmail, Slack, Jira), users have too many passwords.
*   **Solution: Single Sign-On (SSO):** Log in once (e.g., with Google) and access all other apps.
*   **Features:**
    *   Authentication (Who are you?)
    *   Authorization (What can you do?)
    *   Password Management.
*   **Examples:** Okta, Auth0, OneLogin.

---

## Q5: Compliance as a Service (Short Note)

Helps organizations manage compliance with laws and regulations (like HIPAA for health, GDPR for privacy) using cloud tools.
*   Ensures data is stored and processed according to legal standards.
*   Automated auditing and reporting.
