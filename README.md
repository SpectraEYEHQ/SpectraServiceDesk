# 🛡️ SpectraServiceDesk - ITSM & Project Management

> **SpectraServiceDesk** is a multi-tenant platform that unifies **Service Desk**, **Customer Support Portal**, **Client Organization Management**, and **Project Management** into a single operational ecosystem.

It enables each tenant organization to manage internal operations, external customer support, project delivery, knowledge sharing, and service execution through a single platform.

---

## 📚 Table of Contents

1. [About the Project](#about-the-project)
2. [Core Business Model](#core-business-model)
3. [Core Modules](#core-modules)
4. [Key Features](#key-features)

   * [Service Desk & Ticketing](#service-desk--ticketing)
   * [Customer Portal](#customer-portal)
   * [Client Organizations](#client-organizations)
   * [Workspace (Project Management)](#workspace-project-management)
   * [Knowledge Base](#knowledge-base)
   * [Service Catalog](#service-catalog)
5. [Roles & Permissions](#roles--permissions)
6. [Multi-Tenant Data Isolation](#multi-tenant-data-isolation)
7. [Technology Stack](#technology-stack)
8. [System Architecture](#system-architecture)

   * [Platform Context](#platform-context)
   * [Technical Blueprint](#technical-blueprint)
   * [Business Domain Map](#business-domain-map)
   * [Tenant and Client Access Model](#tenant-and-client-access-model)
   * [Authentication & Tenant Resolution Flow](#authentication--tenant-resolution-flow)
   * [Internal vs External Ticket Sources](#internal-vs-external-ticket-sources)
   * [Ticketing Automation Flow](#ticketing-automation-flow)
   * [External Support Lifecycle](#external-support-lifecycle)
   * [SLA Escalation Flow](#sla-escalation-flow)
   * [Project Delivery Flow](#project-delivery-flow)
   * [Knowledge Deflection Flow](#knowledge-deflection-flow)
   * [Notification Flow](#notification-flow)
   * [Visibility Boundary Model](#visibility-boundary-model)
9. [Project Structure](#project-structure)
10. [License](#license)

---

## 🚀 About the Project

**SpectraServiceDesk** is designed for organizations that need both operational support and delivery management in the same platform.

The platform connects:

* support agents,
* project managers,
* internal employees,
* tenant administrators,
* and external customers

through a unified multi-tenant architecture.

A tenant organization can use SpectraServiceDesk for:

* **Internal Service Desk / ITSM** for requests, incidents, workflows, ownership, and SLA execution.
* **Customer Support Operations** through an external portal where customer users can open and track tickets.
* **Project Management** for tasks, milestones, phases, risks, allocations, and delivery reporting.
* **Knowledge Sharing** for public and internal documentation.
* **Client Management** for customer organizations, memberships, service relationships, and support visibility.

---

## 🧩 Core Business Model

SpectraServiceDesk follows a **tenant-based model**.

### Example Scenario

* **Google** creates a tenant account in SpectraServiceDesk.
* Google uses the platform internally for:

  * internal tickets,
  * project planning,
  * task execution,
  * internal knowledge sharing.
* Google can also manage support relationships for external customer organizations.
* Customer organizations can request or receive access to the **Customer Portal**.
* Users from those customer organizations can open support requests related to services such as Gmail, YouTube, Google Workspace, or other managed products.

This allows each tenant to operate in two directions at the same time:

1. **internally**, for its own teams and operations;
2. **externally**, for its customers, partners, or supported organizations.

---

## 🧱 Core Modules

SpectraServiceDesk is structured around six core modules:

1. **Service Desk**

   * ticket lifecycle management
   * SLA monitoring
   * assignment and routing
   * comments, notes, history, attachments

2. **Customer Portal**

   * self-service request creation
   * portal visibility for customer users
   * customer replies and tracking

3. **Client Organizations**

   * external company records
   * memberships and portal access
   * grouping by organization, services, and contracts

4. **Workspace**

   * project planning and execution
   * tasks, milestones, risks, allocations

5. **Knowledge Base**

   * internal and public articles
   * support deflection and operational guidance

6. **Tenant Administration**

   * users, permissions, workflows, services, settings, governance

---

## ✨ Key Features

### 🎫 Service Desk & Ticketing

* Ticket lifecycle management:

  * Open
  * In Progress
  * Pending
  * Resolved
  * Closed
* SLA engine for:

  * First Response Time
  * Resolution Time
  * warning thresholds
  * breach escalation
* Assignment and routing rules
* Priority, severity, impact, and category classification
* Merge / split ticket support
* Internal notes vs public replies
* Attachments and activity history
* Canned responses
* Customer satisfaction flow after resolution
* Auto-close policies

### 🌐 Customer Portal

* Self-service ticket submission
* Ticket status tracking and history
* Customer replies and updates
* Access to relevant knowledge base content
* Invitation-based and organization-based access
* Multi-user access under one customer organization
* Secure separation between internal and external users

### 🏢 Client Organizations

* Manage external customer companies linked to a tenant
* Create customer organizations and contacts
* Invite customer users to portal access
* Group tickets by customer organization
* Associate customers with products, services, or support scope
* Support B2B customer management scenarios

### 📈 Workspace (Project Management)

* Project and phase management
* Task boards and structured work tracking
* Milestones and delivery checkpoints
* Team allocation and ownership
* Gantt visualization
* Risk register and mitigation workflows
* Lessons learned repository
* Delivery progress reporting

### 📖 Knowledge Base

* Category and sub-category hierarchy
* Rich text content
* Attachment support
* Public vs internal article visibility
* Searchable help content
* Reusable guidance for ticket deflection and faster resolution

### 🛎️ Service Catalog

* Define supported services or products per tenant
* Route requests based on selected service
* Attach SLA, teams, categories, or workflows to each service
* Support examples such as:

  * Gmail Support
  * YouTube Support
  * Google Workspace Admin Support
  * Billing Support
  * Infrastructure Support

---

## 👥 Roles & Permissions

SpectraServiceDesk uses **RBAC** to enforce operational control and scoped visibility.

### Platform Role

* **Super Admin**

  * manages tenants
  * manages licenses
  * monitors global activity
  * controls platform-wide governance

### Tenant Roles

* **Tenant Admin**

  * manages organization settings
  * manages users, teams, SLAs, workflows, services, and portal setup
* **Project Manager**

  * manages projects, milestones, risks, and allocations
* **Agent / Employee**

  * handles tickets, tasks, updates, and execution
* **Viewer / Stakeholder**

  * read-only or limited observational access where applicable

### Customer-Side Roles

* **Customer Organization Admin**

  * manages users from the customer company
  * can create and track support requests
  * can view company-level ticket history if allowed
* **Customer User**

  * opens tickets
  * replies to tickets
  * tracks own requests or organization-scoped requests based on permissions
  * accesses allowed portal knowledge base articles

---

## 🔐 Multi-Tenant Data Isolation

Each request in SpectraServiceDesk is resolved within a **tenant boundary**.
Customer portal users are additionally restricted to their linked **customer organization scope** and granted permissions.

Isolation layers include:

* tenant resolution
* role-based access control
* customer organization scoping
* ticket visibility rules
* knowledge base visibility rules
* audit logging
* scheduled job locking and scoped automation

This model helps ensure that:

* one tenant cannot access another tenant's data;
* customer users only see data explicitly allowed to their organization or identity;
* internal employees have broader operational visibility only within their own tenant.

---

## 🛠️ Technology Stack

### Frontend

* **React 18**
* **Vite**
* **TypeScript**
* **TanStack Query**
* **TailwindCSS**
* **Shadcn/UI**
* **DND Kit**
* **Recharts**
* **Frappe Gantt**

### Backend

* **Node.js**
* **Express**
* **MySQL 8.x**
* **WebSocket (ws)** for realtime notifications
* **SendGrid API** for email communication

### Architecture Characteristics

* Multi-tenant request resolution
* UTC-based persistence strategy
* Role-based access control
* Realtime notifications
* Background jobs for SLA, automation, cleanup, and governance

---

## 🏗️ System Architecture

### Platform Context

```mermaid
flowchart LR
  TENANT["Tenant Organization"] --> SSD["SpectraServiceDesk Platform"];
  EMP["Internal Employees"] --> SSD;
  PM["Project Managers"] --> SSD;
  AGENT["Support Agents"] --> SSD;
  CLIENTORG["Client Organizations"] --> SSD;
  CLIENTUSR["Customer Users"] --> SSD;
```

### Technical Blueprint

```mermaid
flowchart LR
  subgraph FE["Frontend - React / Vite"]
    UI["UI + Routing"];
    STATE["Query Cache + State"];
    PORTAL["Portal Experience"];
  end

  subgraph BE["Backend - Node / Express"]
    API["REST API"];
    AUTH["Auth + Tenant Resolution"];
    RULES["Rules Engine"];
    NOTIFY["Notification Services"];
    WS["WebSocket Server"];
    JOBS["Jobs: SLA, CSAT, Auto-Close, License, Cleanup"];
  end

  subgraph DB["MySQL"]
    TENANTDATA["Tenant Data"];
    CLIENTDATA["Client Org Data"];
    LOCKS["Scheduler Locks"];
    AUDIT["Audit Logs"];
  end

  UI --> STATE;
  STATE --> API;
  PORTAL --> API;
  API --> AUTH;
  AUTH --> RULES;
  RULES --> TENANTDATA;
  RULES --> CLIENTDATA;
  API --> AUDIT;
  JOBS --> TENANTDATA;
  JOBS --> LOCKS;
  NOTIFY --> WS;
  WS --> UI;
  WS --> PORTAL;
```

### Business Domain Map

```mermaid
flowchart TB
  subgraph ROLES["Roles"]
    SA["Super Admin"];
    TA["Tenant Admin"];
    PM["Project Manager"];
    AG["Agent / Employee"];
    COA["Customer Org Admin"];
    CU["Customer User"];
  end

  subgraph DOMAINS["Business Domains"]
    PL["Platform Management"];
    ORG["Tenant Administration"];
    SD["Service Desk"];
    CP["Customer Portal"];
    CM["Client Organizations"];
    WS["Workspace / Projects"];
    KB["Knowledge Base"];
  end

  SA --> PL;
  TA --> ORG;
  TA --> SD;
  TA --> CM;
  TA --> KB;
  PM --> WS;
  AG --> SD;
  AG --> WS;
  COA --> CP;
  CU --> CP;
  CP --> SD;
  CP --> KB;
  CM --> SD;
```

### Tenant and Client Access Model

```mermaid
flowchart TB
  PLATFORM["SpectraServiceDesk"];

  subgraph TENANT["Tenant: Example - Google"]
    TADMIN["Tenant Admins"];
    TAGENTS["Agents / Employees"];
    TPM["Project Managers"];
    INTERNALSD["Internal Service Desk"];
    INTERNALPM["Internal Project Workspace"];
    TENANTKB["Tenant Knowledge Base"];
    CLIENTMGMT["Client Organizations Module"];
  end

  subgraph CLIENTS["External Client Side"]
    C1["Client Organization A"];
    C2["Client Organization B"];
    C1U["Customer Users"];
    C2U["Customer Users"];
    PORTAL["Customer Portal"];
  end

  PLATFORM --> TENANT;
  TADMIN --> CLIENTMGMT;
  TAGENTS --> INTERNALSD;
  TPM --> INTERNALPM;
  INTERNALSD --> TENANTKB;
  CLIENTMGMT --> C1;
  CLIENTMGMT --> C2;
  C1 --> C1U;
  C2 --> C2U;
  C1U --> PORTAL;
  C2U --> PORTAL;
  PORTAL --> INTERNALSD;
  PORTAL --> TENANTKB;
```

### Authentication & Tenant Resolution Flow

```mermaid
flowchart LR
  A["User Request"] --> B["Resolve Tenant by Domain / Context"];
  B --> C["Authenticate User"];
  C --> D["Load Roles and Permissions"];
  D --> E["Apply Visibility Scope"];
  E --> F["Grant Access to Module"];
```

### Internal vs External Ticket Sources

```mermaid
flowchart TB
  A["Internal Employee"] --> B["Internal Ticket"];
  C["Customer User"] --> D["Portal Ticket"];
  B --> E["Shared Service Desk Engine"];
  D --> E;
  E --> F["Assignment, SLA, Workflow, Reporting"];
```

### Ticketing Automation Flow

```mermaid
flowchart LR
  A["Ticket Created"] --> B["Rule Engine: Classify, Assign, Notify"];
  B --> C["Agent Work In Progress"];
  C --> D{"SLA Check"};
  D -->|Warning| N["Notify Assignee / Team / Manager"];
  D -->|Within SLA| C;
  C --> E["Resolved"];
  E --> F["Send CSAT Request after 24h"];
  E --> G{"Customer Reopens?"};
  G -->|Yes| C;
  G -->|No| H["Auto-Close after 7 days"];
```

### External Support Lifecycle

```mermaid
flowchart LR
  A["Customer User"] --> B["Customer Portal"];
  B --> C["Create Ticket"];
  C --> D["Tenant Service Desk"];
  D --> E["Routing Rules"];
  E --> F["Assigned Agent"];
  F --> G["Public Reply / Update"];
  G --> H["Customer Reviews Progress"];
  H --> I{"Resolved?"};
  I -->|No| F;
  I -->|Yes| J["Resolution Confirmed"];
  J --> K["CSAT"];
  K --> L["Closed"];
```

### SLA Escalation Flow

```mermaid
flowchart LR
  A["Ticket Active"] --> B["Track First Response SLA"];
  B --> C{"Threshold Reached?"};
  C -->|No| D["Continue Monitoring"];
  C -->|Yes| E["Warning Notification"];
  E --> F{"Breach?"};
  F -->|No| D;
  F -->|Yes| G["Escalate to Team Lead / Admin"];
```

### Project Delivery Flow

```mermaid
flowchart LR
  A["Project Created"] --> B["Define Phases"];
  B --> C["Create Tasks and Milestones"];
  C --> D["Assign Members"];
  D --> E["Track Progress"];
  E --> F{"Risk Detected?"};
  F -->|Yes| G["Log Risk and Mitigation Plan"];
  F -->|No| H["Continue Execution"];
  G --> H;
  H --> I["Milestone Review"];
  I --> J["Project Closure"];
  J --> K["Lessons Learned"];
```

### Knowledge Deflection Flow

```mermaid
flowchart LR
  A["Customer Starts New Request"] --> B["Search Knowledge Base"];
  B --> C{"Article Helpful?"};
  C -->|Yes| D["Ticket Avoided"];
  C -->|No| E["Continue Ticket Submission"];
```

### Notification Flow

```mermaid
flowchart LR
  A["Business Event"] --> B["Notification Engine"];
  B --> C["In-App Notification"];
  B --> D["Email Notification"];
  B --> E["Realtime WebSocket Push"];
```

### Visibility Boundary Model

```mermaid
flowchart TB
  SA["Super Admin"] --> P["Platform Scope"];
  TA["Tenant Admin"] --> T["Tenant Scope"];
  AG["Agent / Employee"] --> I["Internal Operational Scope"];
  COA["Customer Org Admin"] --> C["Customer Organization Scope"];
  CU["Customer User"] --> U["Own Tickets / Allowed Company Data"];
```

---

## 📂 Project Structure

```bash
SpectraServiceDesk/
├── src/                         # Frontend React application
├── public/                      # Static assets
├── backend/                     # Backend API and services
│   ├── routes/                  # API domains
│   │   ├── admin/
│   │   ├── auth/
│   │   ├── customers/
│   │   ├── knowledge-base/
│   │   ├── projects/
│   │   ├── service-catalog/
│   │   ├── tickets/
│   │   └── tenant/
│   ├── services/                # Business logic
│   │   ├── audit/
│   │   ├── email/
│   │   ├── notifications/
│   │   ├── rules/
│   │   ├── sla/
│   │   └── tenant/
│   ├── middleware/              # Auth, RBAC, tenant resolution
│   ├── migrations/              # SQL migrations
│   ├── jobs/                    # Scheduled jobs
│   ├── uploads/                 # Local file storage
│   └── websocket/               # Realtime gateway
```

---

## ⚙️ Installation & Setup

### Requirements

* Node.js 18+
* MySQL 8.x

---

## 📄 License

Distributed under the Proprietary License. See `LICENSE` for more information.

---

<p align="center">
  **Built with ❤️ by the SpectraEYE Team**
</p>
