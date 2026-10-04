# Unit 1: Introduction to Cloud Computing (Deep Exam Notes)

> **Target:** 7-Mark Questions (Long Answer) & MCQs
> **Focus:** Definitions, Layers, Types, Features, Challenges.

---

## Q1: Define Cloud Computing. Explain its Roots and Evolution. (7 Marks)

### 1. Definition (NIST)
**Cloud Computing** is a model for enabling convenient, on-demand network access to a shared pool of configurable computing resources (e.g., networks, servers, storage, applications, and services) that can be rapidly provisioned and released with minimal management effort or service provider interaction.

**Key Keywords for Answer:**
*   On-demand network access
*   Shared pool (Multi-tenancy)
*   Rapid provisioning (Elasticity)
*   Pay-per-use

### 2. Roots of Cloud Computing (Evolution)
Cloud computing didn't appear overnight. It is the result of the evolution of several technologies:

1.  **Mainframe Computing (1950s):**
    *   Large, powerful computers used by large organizations.
    *   **Concept:** Multiple users accessed a central computer via "dumb terminals".
    *   *Precursor to:* Shared resources.

2.  **Cluster Computing:**
    *   Connecting multiple independent computers (nodes) to work together as a single system.
    *   *Precursor to:* High availability and parallel processing.

3.  **Grid Computing (1990s):**
    *   Distributed computing where resources from different locations/organizations create a "virtual supercomputer" to solve complex problems.
    *   *Difference from Cloud:* Grid is often for specific tasks/projects; Cloud is general-purpose.

4.  **Virtualization (The Key Enabler):**
    *   Software (Hypervisor) allows running multiple OS on one physical machine.
    *   *Impact:* Maximized hardware utilization, formed the backbone of Cloud.

5.  **Utility Computing:**
    *   The business model of offering computing resources as a metered service (like water or electricity).

6.  **SaaS/Cloud (Modern Era):**
    *   Delivery of applications and infrastructure over the internet (Salesforce, AWS).

---

## Q2: Explain the Layers and Types of Cloud (Deployment Models). (7 Marks)

### A. Layers of Cloud
(Briefly mentions the stack, detailed in Unit 2, but relevant here)
1.  **Infrastructure Layer (IaaS):** Hardware, Network, Storage.
2.  **Platform Layer (PaaS):** Runtime, Middleware, OS.
3.  **Application Layer (SaaS):** End-user software.

### B. Types of Cloud (Deployment Models)
This answers "Where is the cloud located?" and "Who owns it?".

#### 1. Public Cloud
*   **Definition:** Services offered over the public internet and available to anyone who wants to purchase them.
*   **Owner:** Cloud Service Provider (AWS, Azure, Google).
*   **Pros:** No maintenance, pay-as-you-go, high scalability.
*   **Cons:** Less security (shared hardware), less control.
*   **Example:** Gmail, Dropbox, Amazon EC2.

#### 2. Private Cloud
*   **Definition:** Infrastructure operated solely for a single organization. Can be on-premise or hosted by a third party.
*   **Owner:** The Organization.
*   **Pros:** Maximum security, full control, compliance.
*   **Cons:** High cost, maintenance responsibility.
*   **Example:** A bank's internal data center.

#### 3. Hybrid Cloud
*   **Definition:** A composition of two or more clouds (Public + Private) that remain unique entities but are bound together.
*   **Use Case:** Keep sensitive financial data on Private Cloud, run web server on Public Cloud (Cloud Bursting).
*   **Pros:** Flexibility, balance of security and cost.
*   **Cons:** Complex network configuration.

#### 4. Community Cloud
*   **Definition:** Shared by several organizations (a specific community) with common concerns (e.g., security, compliance).
*   **Example:** Several hospitals sharing a cloud for patient records (HIPAA compliance).

---

## Q3: What are the Desired Features (Characteristics) of a Cloud? (7 Marks)

According to NIST, there are **5 Essential Characteristics**:

1.  **On-Demand Self-Service:**
    *   A consumer can provision resources (server time, storage) automatically without human interaction with the provider.

2.  **Broad Network Access:**
    *   Services are available over the network and accessed through standard mechanisms (mobile phones, tablets, laptops, workstations).

3.  **Resource Pooling (Multi-tenancy):**
    *   The provider’s computing resources are pooled to serve multiple consumers using a *multi-tenant model*.
    *   *Location Independence:* The customer generally has no control or knowledge over the exact location of the hardware.

4.  **Rapid Elasticity:**
    *   Capabilities can be elastically provisioned and released to scale rapidly outward and inward commensurate with demand.
    *   *User view:* Resources appear infinite.

5.  **Measured Service (Pay-per-use):**
    *   Cloud systems automatically control and optimize resource use by leveraging a metering capability (e.g., storage, processing, bandwidth, and active user accounts). Billing is transparent.

---

## Q4: Discuss the Benefits and Disadvantages/Risks of Cloud Computing. (7 Marks)

### Benefits (Pros)
1.  **Cost Savings:** No CapEx (Capital Expenditure) on hardware. Move to OpEx (Operational Expenditure).
2.  **Scalability:** Ability to scale up (Vertical) or scale out (Horizontal) instantly.
3.  **Reliability:** Cloud providers have massive redundancy. If one server fails, another takes over.
4.  **Accessibility:** Access data from anywhere, anytime.
5.  **Speed to Market:** Developers can deploy apps in minutes rather than weeks.

### Disadvantages & Risks (Cons)
1.  **Security & Privacy:** Data is stored on a third-party server. Risk of data breaches or unauthorized access.
2.  **Downtime:** If the internet goes down or the provider has an outage, you have no access.
3.  **Vendor Lock-in:** It is difficult to move from one provider (e.g., AWS) to another (e.g., Azure) due to proprietary formats/APIs.
4.  **Limited Control:** Users have limited control over the underlying infrastructure (especially in SaaS/PaaS).
5.  **Compliance Issues:** Certain data (healthcare, government) cannot legally be stored in public clouds.

---

## Q5: Cloud Infrastructure Management & Providers. (MCQ/Short Focus)

### Cloud Infrastructure Management (CIM)
CIM refers to the software and technologies designed to operate and monitor the applications, data, and services residing in the cloud.
*   **Goal:** To ensure the cloud infrastructure is efficiently utilized and available.

### Infrastructure as a Service (IaaS) Providers
*   **Amazon Web Services (AWS):** EC2 (Elastic Compute Cloud).
*   **Microsoft Azure:** Virtual Machines.
*   **Google Cloud Platform (GCP):** Compute Engine.
*   **Rackspace:** OpenStack based.

### Platform as a Service (PaaS) Providers
*   **Google App Engine:** For running web apps.
*   **Heroku:** Popular for developers (Salesforce owned).
*   **Microsoft Azure App Service.**
*   **Red Hat OpenShift.**
