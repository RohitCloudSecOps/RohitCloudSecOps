# 👋 Rohit Yallaling

### IAM Engineer | Cloud IAM | Identity Security | Cloud Security | DevSecOps

**Hyderabad, India**

Technology professional with **10+ years of experience** spanning application and security validation, software engineering, cloud platforms, **Enterprise IAM**, identity security, and **DevSecOps**. Focused on **Identity & Access Management, Identity Governance, PAM, Identity Lifecycle Management, Cloud IAM, SSO/Federation, cloud security, Infrastructure as Code, automation, and AI-assisted engineering**.

Building expertise across the intersection of **IAM → Identity Security → Cloud Security → DevSecOps → Automation**, with a security-first engineering approach centered on least privilege, governance, automation, and continuous security.

---

## 🧭 Career Journey

```text
Application & Security Validation Engineer
2015 – 2019
        │
        ▼
Software Engineer
2019 – 2020
        │
        ▼
IAM Engineer
2020 – Present
```

**Application & Security Validation → Security → Cloud / DevSecOps → IAM & Identity Security**

---

# 🔐 Core IAM Expertise

### Identity & Access Management

`Microsoft Entra ID` `AWS IAM` `SailPoint` `Okta` `Ping Identity` `CyberArk`

`IAM` `IGA` `PAM` `JML` `Identity Lifecycle Management`

`Access Governance` `RBAC` `ABAC` `Least Privilege` `Zero Trust`

### Authentication & Federation

`SSO` `MFA` `SAML 2.0` `OAuth 2.0` `OIDC`

`SCIM` `Federation` `Authentication` `Authorization`

### ☁️ Cloud Security

`AWS` `Azure` `Cloud IAM`

`AWS IAM Roles & Policies` `STS` `Cross-Account Access`

`Azure RBAC` `KMS` `Secrets Management`

`Cloud Logging` `Security Groups` `NSGs` `Network Segmentation`

### ⚙️ DevSecOps & Infrastructure

`Terraform` `Ansible` `Git` `GitHub`

`GitHub Actions` `Jenkins` `CI/CD`

`Docker` `Kubernetes` `Helm`

`Infrastructure as Code` `Policy as Code`

### 🛡️ Security Engineering

`Checkov` `Trivy` `Snyk` `Semgrep`

`SonarQube` `OWASP ZAP` `Falco` `OPA`

`IaC Security` `Container Security` `Security Scanning`

### 🐍 Programming & Automation

`Python` `Bash` `PowerShell`

`REST APIs` `JSON` `YAML`

`Automation` `Scripting`

### 🤖 AI-Assisted Engineering

`Claude` `Cursor`

`AI-Assisted Automation`

`AI-Assisted Debugging`

`Log / Error Analysis`

---

# 🏗️ IAM & Identity Security Capabilities

### Identity Security

* Identity Lifecycle Management
* Joiner-Mover-Leaver (**JML**) workflows
* Identity Governance and Administration (**IGA**)
* Access Governance
* Role-Based Access Control (**RBAC**)
* Attribute-Based Access Control (**ABAC**)
* Least Privilege
* Zero Trust
* SSO / MFA
* Identity Federation
* Application Onboarding
* Privileged Access Management (**PAM**)

### Cloud IAM Security

* AWS IAM
* Azure RBAC
* Cloud IAM
* Cross-Account Access
* IAM Policies
* Trust Relationships
* AWS STS
* KMS
* Cloud Logging
* Network Segmentation
* Security Groups / NSGs
* Identity-centric cloud security

### DevSecOps

* Terraform
* Infrastructure as Code
* CI/CD Security
* Policy as Code
* IaC Security
* Container Security
* Security Scanning
* GitHub Actions
* Kubernetes Security
* Continuous Security Automation

---

# 🏛️ Architecture Knowledge

### IAM Architecture


                         ┌───────────────────────────────┐
                         │        ENTERPRISE USERS       │
                         │ Employees • Contractors       │
                         │ Partners • Service Identities │
                         └───────────────┬───────────────┘
                                         │
                                         ▼
              ┌──────────────────────────────────────────────┐
              │              IDENTITY SOURCES                │
              │ HR System • Active Directory • Directories  │
              └─────────────────────┬────────────────────────┘
                                    │
                           JML / Identity Lifecycle
                                    │
                                    ▼
              ┌──────────────────────────────────────────────┐
              │          IDENTITY GOVERNANCE / IGA           │
              │                                              │
              │              SAILPOINT                       │
              │                                              │
              │ • Joiner-Mover-Leaver                        │
              │ • Access Requests                            │
              │ • Access Certifications                      │
              │ • RBAC / Entitlements                        │
              │ • SoD / Governance                           │
              │ • Provisioning / Deprovisioning              │
              └─────────────────────┬────────────────────────┘
                                    │
                         Provisioning / SCIM / API
                                    │
                    ┌───────────────┴────────────────┐
                    │                                │
                    ▼                                ▼
       ┌───────────────────────┐        ┌───────────────────────┐
       │   IDENTITY PROVIDER   │        │   PRIVILEGED ACCESS   │
       │                       │        │                       │
       │ Microsoft Entra ID    │        │       CyberArk        │
       │ Okta                  │        │                       │
       │ Ping Identity         │        │ • PAM                 │
       │                       │        │ • Vaulting             │
       │ Authentication        │        │ • JIT Privilege        │
       │ SSO / Federation      │        │ • Privileged Sessions  │
       │ MFA                   │        │ • Credential Security  │
       └───────────┬───────────┘        └───────────┬───────────┘
                   │                                │
                   │                                │
                   ▼                                ▼
       ┌─────────────────────────────────────────────────────┐
       │                 ZERO TRUST LAYER                    │
       │                                                     │
       │  Verify Explicitly • Least Privilege • Assume       │
       │  Breach • Device • User • Location • Risk •        │
       │  Application • Session Context                      │
       └────────────────────────┬────────────────────────────┘
                                │
                                ▼
       ┌─────────────────────────────────────────────────────┐
       │              AUTHENTICATION LAYER                   │
       │                                                     │
       │  SSO • MFA • Conditional Access • Federation        │
       │                                                     │
       │  SAML 2.0 • OAuth 2.0 • OIDC • SCIM                │
       └────────────────────────┬────────────────────────────┘
                                │
                                ▼
       ┌─────────────────────────────────────────────────────┐
       │             AUTHORIZATION / ACCESS                  │
       │                                                     │
       │  RBAC • ABAC • Policies • Entitlements              │
       │  Least Privilege • Privileged Access                │
       └────────────────────────┬────────────────────────────┘
                                │
                 ┌──────────────┼──────────────┐
                 │              │              │
                 ▼              ▼              ▼
        ┌──────────────┐ ┌──────────────┐ ┌──────────────┐
        │ Enterprise   │ │ Cloud        │ │ Privileged   │
        │ Applications │ │ Platforms    │ │ Resources    │
        │              │ │              │ │              │
        │ SaaS / Apps  │ │ AWS         │ │ Servers      │
        │ APIs         │ │ Azure       │ │ Databases    │
        │ Internal Apps│ │ Kubernetes  │ │ Network      │
        └──────┬───────┘ └──────┬───────┘ └──────┬───────┘
               │                │                │
               └────────────────┼────────────────┘
                                │
                                ▼
       ┌─────────────────────────────────────────────────────┐
       │             SECURITY / MONITORING                   │
       │                                                     │
       │ Audit Logs • Identity Logs • Access Logs            │
       │ SIEM • Threat Detection • Alerts • Reporting        │
       │ Compliance • Access Reviews • Forensics             │
       └─────────────────────────────────────────────────────┘


### Cloud IAM Security Architecture

```mermaid
flowchart TB

    U["👤 Users / Workloads<br/>Employees • Developers • Service Identities"]

    ID["🪪 Enterprise Identity Layer<br/>Microsoft Entra ID • Okta • Ping Identity"]

    SSO["🔑 SSO / Federation<br/>SAML • OAuth 2.0 • OIDC"]

    MFA["🛡️ Authentication & Risk<br/>MFA • Conditional Access<br/>Device • Location • Risk • Session"]

    GOV["🏛️ Identity Governance<br/>SailPoint • JML • Access Reviews<br/>RBAC • ABAC • Entitlements"]

    AWS["☁️ AWS Identity Layer<br/>IAM • IAM Roles • Policies<br/>STS • Cross-Account Access"]

    AZ["☁️ Azure Identity Layer<br/>Azure RBAC • Managed Identity<br/>Service Principals • PIM"]

    PAM["🔐 Privileged Access<br/>CyberArk • PAM • Vaulting<br/>JIT / JEA • Privileged Sessions"]

    POL["⚖️ Authorization & Policy<br/>Least Privilege • Resource Policies<br/>Policy as Code • Separation of Duties"]

    RES["🏗️ Cloud Resources<br/>EC2 • S3 • RDS • Lambda<br/>Azure VMs • Storage • Key Vault<br/>Kubernetes • Databases • APIs"]

    SEC["🔒 Cloud Security Controls<br/>KMS • Key Vault • Secrets<br/>Security Groups • NSGs<br/>Network Segmentation"]

    LOG["📊 Logging & Monitoring<br/>CloudTrail • Azure Activity Logs<br/>IAM Logs • SIEM • Alerts"]

    COMP["📋 Governance & Compliance<br/>Access Reviews • Audit<br/>Continuous Monitoring • Reporting"]

    U --> ID
    ID --> SSO
    SSO --> MFA
    MFA --> GOV

    GOV --> AWS
    GOV --> AZ

    AWS --> POL
    AZ --> POL

    U --> PAM
    PAM --> POL

    POL --> RES
    RES --> SEC
    RES --> LOG

    AWS --> LOG
    AZ --> LOG
    PAM --> LOG

    LOG --> COMP
```

----------------------------------------------------------------------

# ⚙️ Engineering Approach

| Principle                      | Focus                                                                        |
| ------------------------------ | ---------------------------------------------------------------------------- |
| 🔐 **Least Privilege**         | Minimize unnecessary access and permissions                                  |
| 🛡️ **Zero Trust**             | Verify identity, context, and authorization continuously                     |
| 🔒 **Security by Design**      | Integrate security into architecture and engineering workflows               |
| 🔄 **Identity Lifecycle**      | Govern identity access from Joiner to Mover to Leaver                        |
| 🏗️ **Infrastructure as Code** | Manage infrastructure consistently through code                              |
| 📜 **Policy as Code**          | Automate security and compliance controls                                    |
| 🤖 **Automation**              | Reduce manual identity and security operations                               |
| 🔁 **Continuous Security**     | Integrate security throughout CI/CD and cloud operations                     |
| 🔎 **Root Cause Analysis**     | Investigate failures through logs, evidence, and systematic analysis         |
| 🧠 **AI-Assisted Engineering** | Apply AI tools to automation, debugging, analysis, and engineering workflows |

------------------------------------------------------
              ZERO TRUST
     ┌─────────────────────────────┐
     │ Verify Explicitly            │
     │ Least Privilege              │
     │ Assume Breach                │
     │ Continuous Verification      │
     │ Risk-Based Access            │
     └──────────────┬──────────────┘
                    │
        ┌───────────┴───────────┐
        ↓                       ↓
     AWS IAM                Azure RBAC
        ↓                       ↓
        Cloud Resources        Cloud Resources
--------------------------------------------------------
____
# 💼 Professional Experience Summary

### 🔐 IAM Engineering

Experience across **Enterprise IAM, Identity & Access Management, Cloud IAM, Identity Governance, and Identity Security**, including:

* Microsoft Entra ID
* AWS IAM
* SailPoint
* Okta
* Ping Identity
* CyberArk
* JML and Identity Lifecycle Management
* RBAC / ABAC
* SSO / MFA
* SAML / OAuth 2.0 / OIDC / SCIM
* Access Governance
* Least Privilege
* Cloud IAM and authorization

### ☁️ Software Engineering / DevSecOps

Technical exposure across:

* AWS / Azure
* Terraform
* Ansible
* Git / GitHub
* Jenkins
* GitHub Actions
* CI/CD
* Docker
* Kubernetes
* Security Scanning
* Infrastructure as Code Security
* Policy as Code

### 🧪 Application & Security Validation

Background spanning:

* Functional Validation
* Integration Testing
* Regression Testing
* Security Validation
* Troubleshooting
* Log Analysis
* Root Cause Analysis
* Defect Analysis
* Release Qualification

---

# 🧰 Technology Stack

### 🔐 IAM

![Microsoft Entra ID](https://img.shields.io/badge/Microsoft%20Entra%20ID-0078D4?style=flat-square\&logo=microsoft\&logoColor=white)
![AWS IAM](https://img.shields.io/badge/AWS%20IAM-232F3E?style=flat-square\&logo=amazonaws\&logoColor=white)
![SailPoint](https://img.shields.io/badge/SailPoint-00A4A6?style=flat-square)
![Okta](https://img.shields.io/badge/Okta-007DC1?style=flat-square\&logo=okta\&logoColor=white)
![Ping Identity](https://img.shields.io/badge/Ping%20Identity-0073CF?style=flat-square)
![CyberArk](https://img.shields.io/badge/CyberArk-1A1A1A?style=flat-square)

**Microsoft Entra ID · AWS IAM · SailPoint · Okta · Ping Identity · CyberArk · IAM · IGA · PAM**

### 🪪 Identity

`RBAC` `ABAC` `JML` `IGA` `PAM` `SSO` `MFA`

`SAML 2.0` `OAuth 2.0` `OIDC` `SCIM` `Federation`

`Identity Lifecycle Management` `Access Governance` `Least Privilege`

### ☁️ Cloud

![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square\&logo=amazonaws\&logoColor=white)
![Azure](https://img.shields.io/badge/Azure-0078D4?style=flat-square\&logo=microsoftazure\&logoColor=white)

`AWS` `Azure` `Cloud IAM` `KMS` `STS`

`IAM Roles & Policies` `Azure RBAC` `Cross-Account Access`

### ⚙️ DevSecOps

![Terraform](https://img.shields.io/badge/Terraform-844FBA?style=flat-square\&logo=terraform\&logoColor=white)
![Ansible](https://img.shields.io/badge/Ansible-EE0000?style=flat-square\&logo=ansible\&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square\&logo=githubactions\&logoColor=white)
![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=flat-square\&logo=jenkins\&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square\&logo=docker\&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square\&logo=kubernetes\&logoColor=white)

`Terraform` `Ansible` `Git` `GitHub` `GitHub Actions` `Jenkins`

`CI/CD` `Docker` `Kubernetes` `Helm`

`Infrastructure as Code` `Policy as Code`

### 🛡️ Security

`Checkov` `Trivy` `Snyk` `Semgrep`

`SonarQube` `OWASP ZAP` `Falco` `OPA`

`IaC Security` `Container Security` `Security Scanning`

### 🐍 Programming & Automation

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square\&logo=python\&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-121011?style=flat-square\&logo=gnubash\&logoColor=white)
![PowerShell](https://img.shields.io/badge/PowerShell-5391FE?style=flat-square\&logo=powershell\&logoColor=white)

`Python` `Bash` `PowerShell` `REST APIs` `JSON` `YAML`

`Automation` `Scripting`

### 🤖 AI-Assisted Engineering

`Claude` `Cursor`

`AI-Assisted Automation` · `AI-Assisted Debugging` · `Log / Error Analysis`

---

---

# 🔗 Connect With Me

**GitHub:** [RohitCloudSecOps](https://github.com/RohitCloudSecOps)

**Portfolio:** [rohitcloudsecops.in](https://rohitcloudsecops.in)

---

<p align="center">

**IAM • Identity Security • Cloud IAM • Cloud Security • DevSecOps • Automation**

</p>


<br/>

<!-- ─────────────  CLICKABLE ACTION BAR  ───────────── -->
<div align="center">

<a href="https://rohitcloudsecops.in"><img src="https://img.shields.io/badge/%F0%9F%8C%90%20Portfolio-0B1220?style=for-the-badge&labelColor=0B1220&color=1E3A5F" alt="Portfolio" /></a>
&nbsp;
<a href="assets/Rohit_Yallaling_Resume.pdf"><img src="https://img.shields.io/badge/%F0%9F%93%84%20Resume-0B1220?style=for-the-badge&labelColor=0B1220&color=3B0764" alt="Resume" /></a>
&nbsp;
<a href="#"><img src="https://img.shields.io/badge/LinkedIn-0B1220?style=for-the-badge&logo=linkedin&logoColor=60A5FA&labelColor=0B1220&color=1E3A5F" alt="LinkedIn" /></a>
&nbsp;
<a href="https://github.com/RohitCloudSecOps"><img src="https://img.shields.io/badge/GitHub-0B1220?style=for-the-badge&logo=github&logoColor=FFFFFF&labelColor=0B1220&color=0B1220" alt="GitHub" /></a>
&nbsp;
<a href="mailto:rohit.cloudsecops@gmail.com"><img src="https://img.shields.io/badge/%E2%9C%89%20Email-0B1220?style=for-the-badge&labelColor=0B1220&color=3B0764" alt="Email" /></a>

</div>

<br/>

---

<!-- ─────────────  LIVE GITHUB ANALYTICS  ───────────── -->
<div align="center">

<img src="https://github-profile-summary-cards.vercel.app/api/cards/stats?username=RohitCloudSecOps&theme=github_dark" height="180" alt="GitHub Stats" />
&nbsp;
<img src="https://github-profile-summary-cards.vercel.app/api/cards/repos-per-language?username=RohitCloudSecOps&theme=github_dark" height="180" alt="Top Languages" />

<br/><br/>

<img src="https://streak-stats.demolab.com?user=RohitCloudSecOps&hide_border=true&background=0B1220&stroke=1E40AF&ring=6D28D9&fire=A78BFA&currStreakLabel=60A5FA&sideLabels=C9D1D9&dates=8B949E&currStreakNum=FFFFFF&sideNums=FFFFFF" alt="GitHub Streak" />

<br/><br/>

<img src="https://github-readme-activity-graph.vercel.app/graph?username=RohitCloudSecOps&bg_color=0B1220&color=60A5FA&line=6D28D9&point=A78BFA&area=true&area_color=1E40AF&hide_border=true" width="96%" alt="Contribution Graph" />

<br/><br/>

<!-- Contribution Snake · generated by snake.yml workflow -->
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/RohitCloudSecOps/RohitCloudSecOps/output/github-contribution-grid-snake-dark.svg" />
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/RohitCloudSecOps/RohitCloudSecOps/output/github-contribution-grid-snake.svg" />
  <img alt="Contribution Snake" src="https://raw.githubusercontent.com/RohitCloudSecOps/RohitCloudSecOps/output/github-contribution-grid-snake-dark.svg" width="96%" />
</picture>

<br/><br/>

<img src="https://komarev.com/ghpvc/?username=RohitCloudSecOps&style=for-the-badge&label=PROFILE%20VIEWS&labelColor=0B1220&color=1E40AF" alt="Profile Views" />
&nbsp;
<a href="https://github.com/RohitCloudSecOps?tab=followers"><img src="https://img.shields.io/github/followers/RohitCloudSecOps?style=for-the-badge&label=FOLLOWERS&labelColor=0B1220&color=6D28D9" alt="Followers" /></a>

</div>

<br/>

<div align="center">
  <i>"Building secure, scalable and intelligent identity &amp; cloud security solutions for the future."</i>
</div>
