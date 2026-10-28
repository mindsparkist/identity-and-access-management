# IAM (Identity and Access Management) — Complete Beginner's Guide
**From fundamentals to real-world enterprise IAM | Cloud IAM | AWS | Zero Trust**

IAM is an essential concept in cybersecurity, cloud computing, IT infrastructure, and enterprise IT operations. Since IAM is relevant to cloud and access management, understanding these fundamentals will help you connect identity management concepts with real-world enterprise environments.

Let's build your understanding step by step.

---

# 1. What Is IAM?

**IAM stands for Identity and Access Management.**

IAM is a framework of policies, processes, and technologies used to manage **who can access which resources, under what conditions, and with what level of permission.**

In simple terms, IAM answers three questions:

1. **Who are you?** — Identity
2. **Can you prove it?** — Authentication
3. **What are you allowed to do?** — Authorization

### Real-world IT example

Imagine you work at Deloitte.

You have:
- A corporate user account.
- An email account.
- Access to internal applications.
- Permission to access specific AWS resources.
- Access to an IT ticketing system.
- A corporate laptop requiring authentication.

Your organization needs to ensure that:
- You can sign in using your assigned credentials.
- You can access only the applications required for your job.
- You cannot access confidential systems without authorization.
- Your permissions change when you change roles.
- Your accounts are disabled when you leave the organization.

**IAM manages the identities and access controls that make these requirements possible.**

### What does IAM manage?

| Component | Example |
|---|---|
| Human identities | Employees, contractors, administrators |
| Non-human identities | Applications, services, automated workloads |
| Credentials | Passwords, certificates, access keys |
| Authentication | Passwords, MFA, passkeys |
| Authorization | Roles, permissions, access policies |
| Provisioning | Creating accounts and granting access |
| Deprovisioning | Disabling accounts and revoking access |
| Auditing | Reviewing who accessed which resources |

**Important:** IAM is broader than simply creating user accounts. It covers the identity lifecycle, authentication, authorization, governance, and access reviews.

---

# 2. Authentication vs. Authorization

These are two of the most important IAM concepts.

## A. Authentication — Who are you?

Authentication verifies the identity of a user, application, or service.

It answers:

**"Can you prove that you are who you claim to be?"**

Common authentication methods include:

- Username and password.
- Multi-factor authentication (MFA).
- One-time passwords (OTP).
- Passkeys.
- Biometrics.
- Digital certificates.
- Security tokens.

### Example

You open your company's internal application.

1. Enter your username.
2. Enter your password.
3. Approve an MFA request.
4. The identity system verifies your credentials.

You have now authenticated successfully.

However, successful authentication does not automatically mean you can access every application or resource.

## B. Authorization — What are you allowed to do?

Authorization determines which resources and operations an authenticated identity is permitted to access.

It answers:

**"What are you allowed to do?"**

Examples:
- View an incident ticket.
- Update a ticket.
- Approve a production change.
- Access an AWS S3 bucket.
- Modify IAM policies.
- Restart a production server.

### Example

Suppose three employees authenticate successfully.

| Employee | Authentication | Authorization |
|---|---|---|
| Service Desk Analyst | Successful | View and update assigned tickets |
| Incident Manager | Successful | Manage incidents and coordinate escalations |
| Cloud Administrator | Successful | Administer specifically assigned cloud resources |

All three employees have authenticated, but their permissions differ.

### Easy way to remember

Imagine entering a secure office building.

- **Authentication:** The security guard verifies your identity.
- **Authorization:** Your access card determines whether you can enter the server room.
- **Auditing:** The access-control system records your entry.

### Interview question

**Q: What is the difference between authentication and authorization?**

**Answer:**

Authentication verifies the identity of a user or system, while authorization determines which resources and actions that identity is permitted to access after its identity has been established.

---

# 3. The Core IAM Lifecycle

IAM follows an identity lifecycle that manages access from the time an identity is created until it is removed.

A common enterprise model includes the following stages:



## Step 1: Identity Creation

An identity is created for a new employee, contractor, application, or service.

**Example:** A new employee joins the company.

The HR system records the employee's details, and an identity management process initiates account creation.

Possible tasks:
- Create a corporate identity.
- Assign a username.
- Associate the employee with a department.
- Record the employee's manager.
- Establish the employee's employment status.

## Step 2: Provisioning

Provisioning means creating accounts and assigning the appropriate access.

For example, a new Service Desk Analyst might receive:
- Corporate email.
- ServiceNow access.
- Knowledge-base access.
- Monitoring dashboard access.
- VPN access, if required.

Access should be assigned according to the employee's role and approved requirements.

## Step 3: Authentication

The identity proves its identity when attempting to sign in.

For example:
- Username and password.
- MFA verification.
- Single Sign-On (SSO).

The identity provider verifies the authentication request.

## Step 4: Authorization

The system determines which resources and actions the identity is permitted to use.

For example:
- The employee can view incident tickets.
- The employee can update assigned incidents.
- The employee cannot approve their own privileged production access.

Authorization can depend on roles, policies, resource attributes, and other conditions.

## Step 5: Monitoring and Auditing

The organization monitors access activity and reviews permissions.

Examples:
- Detect repeated failed logins.
- Investigate unusual sign-in locations.
- Review administrator activity.
- Identify inactive accounts.
- Verify that users still require their assigned permissions.

## Step 6: Access Modification

When an employee changes roles, their access must change accordingly.

For example:

A Service Desk Analyst moves into a Cloud Operations role.

The organization may:
1. Remove access that is no longer required.
2. Obtain approval for new access.
3. Grant the appropriate cloud permissions.
4. Update group and role assignments.
5. Record the changes for auditing.

This is an important part of identity lifecycle management.

## Step 7: Deprovisioning

When an employee leaves the organization, access must be removed promptly.

Typical actions include:
- Disable the corporate account.
- Revoke active sessions and refresh tokens where appropriate.
- Remove application access.
- Revoke privileged permissions.
- Disable or rotate credentials associated with the departing identity.
- Preserve audit records according to organizational requirements.

**Why is this important?**

An account belonging to a former employee could become a security risk if it remains active.

### The Joiner–Mover–Leaver (JML) model

You will frequently encounter this term in enterprise IAM.

| Lifecycle stage | Meaning | Example |
|---|---|---|
| Joiner | A person joins the organization | Create an employee account |
| Mover | A person changes roles or responsibilities | Modify permissions |
| Leaver | A person leaves the organization | Revoke access |

**Remember:** JML is a widely used identity lifecycle model. The complete IAM lifecycle can include additional processes such as authentication, authorization, governance, and continuous monitoring.

---

# 4. Why Do Organizations Need IAM?

Without effective IAM, organizations can struggle to control who has access to sensitive information and critical systems.

Here are the major reasons IAM matters.

### 1. Security

IAM helps prevent unauthorized access to corporate applications, databases, servers, and cloud resources.

### 2. Least Privilege

Users should receive only the permissions required to perform their responsibilities.

For example, a support analyst who only needs to restart a particular service should not automatically receive full administrative access to every production server.

### 3. Regulatory Compliance

Organizations may need to demonstrate that access is controlled, approved, monitored, and reviewed.

Depending on the organization and its obligations, IAM controls can support compliance with requirements associated with frameworks and regulations such as ISO 27001, SOC 2, and GDPR.

IAM alone does not guarantee compliance.

### 4. Faster Employee Onboarding

Automated provisioning can provide employees with the correct accounts and permissions more efficiently.

### 5. Reduced Manual Work

Identity automation can reduce repetitive tasks such as:
- Creating accounts.
- Adding users to groups.
- Assigning application access.
- Removing permissions.
- Processing employee departures.

### 6. Reduced Insider and Credential Risks

IAM controls help limit what a compromised or misused account can access.

### 7. Better Auditability

Organizations can maintain records of access approvals, authentication events, permission changes, and administrative actions.

### 8. Cloud Security

Cloud platforms need identity controls to determine which users and workloads can access cloud resources.

For example, an application running on AWS may need permission to retrieve objects from a particular S3 bucket without receiving access to the entire AWS account.

**In one sentence: IAM helps organizations give the right identities the right access to the right resources at the right time.**

---

# 5. IAM Using a Real-Life Example

Let's consider a fictional enterprise called ABC Technologies.

The company has 1,000 employees, several internal applications, AWS workloads, and a Service Desk team.

It wants to manage employee access securely.

## Scenario A: A New Employee Joins

An employee joins as a Service Desk Analyst.

**What happens?**

1. HR records the employee's information.
2. The identity lifecycle process initiates account provisioning.
3. An account is created in the corporate identity system.
4. The employee receives the required application access.
5. MFA is configured.
6. Appropriate Service Desk permissions are assigned.

The employee can now access authorized applications.

## Scenario B: The Employee Signs In

The employee opens a corporate application.

1. The application redirects the employee to the company's identity provider.
2. The employee authenticates.
3. The identity provider verifies the credentials and MFA, when required.
4. The employee receives an authentication token or assertion.
5. The application validates the authentication result.
6. The application evaluates the employee's permissions.

The employee can access the application only to the extent permitted by its access controls.

This is a common pattern in federated identity and SSO environments.

## Scenario C: The Employee Needs AWS Access

The employee needs to investigate an application issue in AWS.

Instead of giving the employee unrestricted access, the organization assigns an appropriate role or permission set.

For example, the employee may be allowed to:
- View selected CloudWatch logs.
- Inspect specific monitoring dashboards.
- Read approved configuration information.

The employee may not be allowed to:
- Delete production databases.
- Modify IAM policies.
- Create unrestricted administrator credentials.

The exact permissions depend on the employee's responsibilities and approved access.

## Scenario D: The Employee Becomes a Cloud Administrator

The employee changes roles.

The organization:
1. Reviews the employee's new responsibilities.
2. Approves the required access.
3. Removes permissions no longer needed.
4. Assigns the appropriate cloud role.
5. Records the change.
6. Reviews the resulting access.

## Scenario E: The Employee Leaves

HR records the departure.

The identity lifecycle process initiates deprovisioning, disabling the employee's account and revoking associated access according to company policy.

This helps prevent continued access after employment ends.

### What did IAM accomplish?

It helped ABC Technologies control identity creation, authentication, permissions, access changes, monitoring, and account removal.

That is IAM in practice.

---

# 6. Important IAM-Related Terms

These terms frequently appear in enterprise identity and cloud security environments.

## 6.1 Identity Provider (IdP)

An **Identity Provider** authenticates identities and provides information about their authentication to applications or services.

Examples include:
- Microsoft Entra ID.
- Okta.
- Amazon Cognito.

An IdP can support SSO and federated authentication.

**Example:** An employee signs in to a corporate identity service and then accesses multiple authorized applications without separately entering credentials into each application.

The IdP authenticates the user, while the applications and their authorization systems determine the access the user receives.

## 6.2 Single Sign-On (SSO)

SSO allows a user to authenticate once and access multiple integrated applications without repeatedly performing a full login.

For example, after signing in to a corporate identity portal, an employee may access approved email, ticketing, and collaboration applications.

SSO does not automatically grant access to every connected application.

## 6.3 Multi-Factor Authentication (MFA)

MFA requires two or more different types of authentication factors.

The main categories are:
- Something you know: a password or PIN.
- Something you have: a security key or authenticator device.
- Something you are: a biometric characteristic.

For example, a password plus a security key can provide MFA.

Two passwords alone are not two different authentication factors.

## 6.4 Role-Based Access Control (RBAC)

RBAC assigns permissions through roles.

Example:

| Role | Typical permissions |
|---|---|
| Service Desk Analyst | View and update permitted tickets |
| Incident Manager | Coordinate incident management |
| Cloud Operations | Access approved cloud operations |
| Cloud Administrator | Perform authorized administrative tasks |

The organization assigns a role to the user, and the role determines the associated permissions.

## 6.5 Attribute-Based Access Control (ABAC)

ABAC evaluates attributes and policies to determine whether access should be allowed.

Attributes can relate to:
- The user.
- The resource.
- The requested action.
- The environment or context.

**Example:** Permit access to a confidential resource only when the user belongs to the approved department, the resource has the required classification, and the request meets the organization's security conditions.

RBAC and ABAC can be used together.

## 6.6 Least Privilege

Least privilege means granting only the minimum permissions required for an identity to perform its approved responsibilities.

For example, an application that only needs to read objects from one S3 bucket should not receive unrestricted access to all AWS services.

## 6.7 Identity Governance and Administration (IGA)

IGA focuses on governing identities and access throughout their lifecycle.

It commonly includes:
- Access requests and approvals.
- Access certification and reviews.
- Role management.
- Segregation of duties.
- Identity lifecycle workflows.
- Compliance evidence.

**Example:** A manager periodically reviews their team's access to ensure employees still need the permissions they hold.

## 6.8 Privileged Access Management (PAM)

PAM manages and protects accounts and permissions with elevated privileges.

Examples include:
- Domain Administrator accounts.
- Root or privileged cloud access.
- Database administrator accounts.
- Production server administrator accounts.

PAM is discussed in more detail below.

## 6.9 Identity Federation

Federation establishes trust between separate identity systems so that an identity authenticated by one system can access resources managed by another.

**Example:** An employee uses a corporate identity provider to access an AWS environment without needing a separate long-lived IAM user credential.

Federation commonly uses standards such as SAML 2.0 and OpenID Connect.

## 6.10 Just-in-Time (JIT) Access

JIT access provides permissions only when needed, often for a limited duration.

For example, an engineer requests elevated production access for a scheduled maintenance activity. The access is approved, granted temporarily, and revoked when the authorized period ends.

JIT access can reduce the risks associated with permanently assigned administrative permissions.

---

# 7. PAM — Privileged Access Management

**PAM stands for Privileged Access Management.**

PAM is a specialized area of identity and access security focused on controlling, monitoring, and protecting privileged accounts and activities.

Why does PAM matter?

A compromised standard account might expose limited resources. A compromised administrator account could allow an attacker to make widespread changes to critical systems.

### Examples of privileged identities

- Windows Domain Administrator.
- Linux root user.
- AWS account administrator.
- Production database administrator.
- Network infrastructure administrator.
- Emergency or break-glass account.

### Common PAM capabilities

| Capability | Purpose |
|---|---|
| Credential vaulting | Securely store privileged credentials |
| Credential rotation | Change credentials periodically or after relevant events |
| Session monitoring | Record or monitor privileged sessions |
| Access approval | Require authorization before privileged access |
| JIT access | Provide temporary elevated permissions |
| Privileged activity auditing | Record administrative actions |
| Least privilege | Limit administrative permissions |

### Real-world PAM example

A production server has a privileged administrator account.

Instead of allowing every engineer to know its permanent password:

1. The engineer requests access through the approved PAM workflow.
2. The request is approved if required.
3. The PAM system provides controlled access to the privileged account or session.
4. Administrative activity is recorded or monitored.
5. Access expires or is revoked according to policy.
6. Credentials may be rotated as required.

This helps the organization control sensitive administrative access.

### IAM vs. PAM

| IAM | PAM |
|---|---|
| Manages identities and access broadly | Focuses on privileged access |
| Covers ordinary employees and non-human identities | Focuses on highly privileged identities and activities |
| Handles authentication, authorization, provisioning, and access governance | Adds controls such as privileged credential vaulting and session monitoring |
| Example: Employee application access | Example: Controlled Domain Administrator access |

**Interview point:** PAM is not a replacement for IAM. It is a specialized capability that complements the broader IAM program.

---

# 8. CIAM — Customer Identity and Access Management

**CIAM stands for Customer Identity and Access Management.**

CIAM manages identities and access for customers, consumers, partners, and other external users who interact with an organization's digital services.

Traditional workforce IAM focuses on identities inside an organization.

CIAM focuses on identities outside the organization, especially customer-facing applications.

### Real-world example

Imagine an online shopping platform.

Customers need to:
- Register accounts.
- Sign in.
- Reset passwords.
- Enable MFA.
- Manage their profiles.
- View their orders.
- Access only their own personal information.

CIAM helps provide these identity and access capabilities.

For example, one customer must not be able to view another customer's order history simply by changing an order ID in a URL. The application must enforce authorization checks that restrict access to the correct customer's data.

### Common CIAM capabilities

- Customer registration.
- Login and account recovery.
- Social login, where supported.
- SSO across customer-facing applications.
- MFA and adaptive authentication.
- Consent and privacy management.
- Customer profile management.
- Fraud and suspicious-login detection.
- API and application access controls.

### IAM vs. CIAM

| Workforce IAM | CIAM |
|---|---|
| Manages employee and workforce identities | Manages customer and external-user identities |
| Often integrates with HR systems and corporate directories | Often integrates with customer databases and digital applications |
| Emphasizes enterprise access governance and productivity | Emphasizes customer experience, scalability, privacy, and account security |
| Example: Employee accessing ServiceNow | Example: Customer accessing an online shopping account |

### Where does Amazon Cognito fit?

Amazon Cognito provides identity capabilities for web and mobile applications, including user sign-in, authentication, and federation.

It is commonly used in CIAM scenarios.

For example, a company building an online shopping application can use Cognito to manage customer sign-up and sign-in while implementing application-specific authorization to protect customer data.

**Important:** Authentication through Cognito does not automatically guarantee that every API request is authorized to access the correct customer's resources. The application must enforce the appropriate permissions and ownership checks.

---

# 9. Zero Trust

**Zero Trust is a security approach based on the principle that access should not be trusted solely because a user or device is inside a corporate network.**

A traditional network-security assumption might be:

"If the employee is connected to the office network, they can be trusted."

Zero Trust challenges that assumption.

It requires access decisions to be based on identity, resource, context, policy, and other relevant signals.

### Core Zero Trust principles

1. **Verify explicitly:** Evaluate available identity and contextual signals before granting access.
2. **Use least privilege:** Give identities only the access they require.
3. **Assume breach:** Design systems with the expectation that an account, device, or network component could be compromised.

### Real-world example

An employee is working remotely and wants to access a production management application.

A Zero Trust-oriented system may evaluate:
- Whether the employee has authenticated successfully.
- Whether MFA requirements are satisfied.
- Whether the device meets security requirements.
- Whether the employee is authorized for the application.
- Whether the requested action complies with policy.
- Whether risk signals require additional verification or denial.

If the request does not meet the applicable policy, access may be denied or restricted.

Zero Trust does not mean repeatedly asking every employee for a password. It means making access decisions using appropriate evidence and policies rather than relying on implicit trust.

### How IAM supports Zero Trust

IAM provides important capabilities for Zero Trust, including:
- Identity verification.
- MFA.
- Centralized authentication.
- Role and permission management.
- Least-privilege access.
- Access policies.
- Identity and access auditing.

However, Zero Trust is broader than IAM. It can also involve endpoint security, network controls, application security, workload protection, and continuous risk assessment.

---

# 10. IdP vs. IAM vs. PAM vs. CIAM vs. Zero Trust

These terms are related, but they do not mean the same thing.

| Term | Full form | Primary purpose | Example |
|---|---|---|---|
| IAM | Identity and Access Management | Manage identities and access across systems | Employee access to corporate applications |
| IdP | Identity Provider | Authenticate identities and provide authentication information | Corporate SSO login |
| PAM | Privileged Access Management | Protect privileged accounts and administrative access | Controlled production server access |
| CIAM | Customer Identity and Access Management | Manage customer-facing identities and access | Customer login to an e-commerce application |
| Zero Trust | Zero Trust security model | Make access decisions without relying on implicit trust | Verify identity, device, and policy before granting access |
| IGA | Identity Governance and Administration | Govern access through approvals, reviews, and policies | Quarterly employee access review |
| SSO | Single Sign-On | Enable access to multiple integrated applications through a common sign-in experience | Corporate login portal |
| MFA | Multi-Factor Authentication | Verify identity using multiple authentication-factor types | Password plus security key |
| RBAC | Role-Based Access Control | Assign permissions based on roles | Service Desk role |
| ABAC | Attribute-Based Access Control | Evaluate attributes and policies for access | Permit access based on department and resource classification |
| JIT | Just-in-Time Access | Provide temporary access when needed | Temporary administrator permissions |

### Remember the distinctions

- **IAM** is the broad identity and access discipline.
- **IdP** is a system or service that performs identity-provider functions.
- **PAM** specializes in privileged access.
- **CIAM** specializes in customer identities.
- **Zero Trust** is a broader security model that uses identity and other signals to make access decisions.

---

# 11. How IAM Works in Cloud Computing

Let's connect these fundamentals to AWS.

Suppose a company hosts an application in AWS.

The environment contains:
- EC2 instances.
- S3 buckets.
- CloudWatch logs.
- Databases.
- Developers.
- Cloud administrators.
- Applications that interact with other AWS services.

The organization needs to control both human and machine access.

### Human access

A cloud engineer signs in through the organization's identity provider.

The organization can federate the identity into AWS and assign an appropriate role or permission set.

The engineer then accesses only the AWS resources permitted by the resulting authorization controls.

### Workload access

An application running on EC2 needs to read objects from an S3 bucket.

Instead of storing a developer's personal AWS access key in the application, the workload can use an IAM role through an EC2 instance profile.

The role's permissions define which AWS actions and resources the workload can access.

For example, it may allow reading objects from a specific bucket without granting permission to delete objects or administer other AWS services.

### Relevant AWS IAM concepts

| AWS concept | Purpose |
|---|---|
| IAM user | An identity for a person or workload, where that identity model is appropriate |
| IAM group | Organizes IAM users for permission assignment |
| IAM role | Provides an identity with permissions that can be assumed by trusted principals |
| IAM policy | Defines permissions or access conditions |
| IAM Identity Center | Supports workforce access to AWS accounts and applications |
| Permission boundary | Limits the maximum permissions that identity-based policies can grant to an IAM user or role |
| Service control policy (SCP) | Sets permission guardrails for accounts in AWS Organizations |
| Instance profile | Delivers an IAM role to an EC2 instance |
| AWS STS | Provides temporary security credentials through supported operations |

AWS IAM is an AWS-specific implementation of identity and access management concepts.

For further study, explore the official [AWS IAM documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html?utm_source=chatgpt.com) and the [AWS IAM Identity Center documentation](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html?utm_source=chatgpt.com).

---

# 12. A Practical IAM Troubleshooting Scenario

This is a useful scenario for cloud support and IAM interviews.

### Incident

A user reports:

> "I can sign in to the AWS console, but I cannot access an S3 bucket."

What does this tell you?

The successful sign-in suggests that authentication succeeded. However, it does not establish that the user is authorized to access the bucket.

### Troubleshooting workflow

**Step 1: Confirm the identity**

- Which user or federated identity is being used?
- Is the user signing in to the correct AWS account?
- Is the expected role or permission set active?

**Step 2: Identify the denied action**

Determine the exact operation that failed.

For example:
- `s3:ListBucket`
- `s3:GetObject`
- `s3:PutObject`

These are different permissions. A user may be permitted to list a bucket but not retrieve its objects, or vice versa.

**Step 3: Check the applicable policies**

Depending on the access path, examine:
- Identity-based policies.
- Resource-based bucket policies.
- Permissions boundaries.
- AWS Organizations service control policies.
- Session policies.
- Any relevant explicit-deny statements.

Also verify that the resource ARN and requested action match the intended permissions.

**Step 4: Check access conditions**

Review relevant conditions, such as:
- Required network or endpoint conditions.
- Encryption requirements.
- Principal or resource restrictions.
- Session or organization restrictions.

**Step 5: Review logs and error messages**

Use the available AWS error details and relevant CloudTrail events to investigate the denied request.

**Step 6: Apply the least-privilege fix**

If access is legitimately required, request approval and grant only the necessary permissions.

Do not solve the incident by granting unrestricted administrator access.

### Key lesson

**Successful authentication does not guarantee successful authorization.**

This distinction is essential when troubleshooting IAM incidents.

---

# 13. IAM Interview Questions and Answers

### Q1. What is IAM?

IAM is a framework of technologies, policies, and processes used to manage identities and control access to resources throughout the identity lifecycle.

### Q2. What is the difference between authentication and authorization?

Authentication verifies identity. Authorization determines the resources and actions that identity is permitted to access.

### Q3. What is the principle of least privilege?

It means providing an identity with only the permissions necessary to perform its approved tasks.

### Q4. What is an IdP?

An Identity Provider authenticates identities and supplies authentication information to integrated applications or services.

### Q5. What is SSO?

Single Sign-On allows users to authenticate through a common identity system and access multiple integrated applications without repeatedly performing a full login.

### Q6. What is MFA?

Multi-Factor Authentication requires two or more different types of authentication factors to verify an identity.

### Q7. What is PAM?

Privileged Access Management protects elevated accounts and administrative activities using controls such as credential vaulting, session monitoring, and temporary privileged access.

### Q8. What is CIAM?

Customer Identity and Access Management manages customer identities and their access to digital applications and services.

### Q9. What is Zero Trust?

Zero Trust is a security model that avoids granting implicit trust based solely on network location and evaluates access using identity, context, policy, and other relevant signals.

### Q10. What is identity provisioning?

Provisioning is the process of creating an identity or account and assigning the appropriate access to systems and resources.

### Q11. What is deprovisioning?

Deprovisioning removes or disables identities, accounts, credentials, and permissions when they are no longer required.

### Q12. What is RBAC?

Role-Based Access Control assigns permissions through roles that represent specific job functions or responsibilities.

### Q13. What is the difference between RBAC and ABAC?

RBAC evaluates permissions associated with assigned roles. ABAC evaluates attributes and policy conditions. Organizations can use both approaches together.

### Q14. What is identity federation?

Identity federation allows trusted identity systems to work together so that identities authenticated by one system can access resources managed by another.

### Q15. Why is IAM important in AWS?

AWS IAM controls which identities can perform which actions on AWS resources. It helps enforce least privilege, protect cloud resources, and support access auditing.

---

# 14. Your IAM Learning Roadmap

If you want to move deeper into Cloud IAM, I recommend learning these topics in sequence.

| Stage | Topics to learn | Practical exercise |
|---|---|---|
| 1. Fundamentals | IAM, authentication, authorization, MFA, SSO | Explain the difference using real-world examples |
| 2. Access Control | RBAC, ABAC, least privilege, access policies | Design access for Service Desk, Cloud Ops, and Administrators |
| 3. Identity Lifecycle | JML, provisioning, deprovisioning, access reviews | Create a sample employee onboarding and offboarding workflow |
| 4. Identity Protocols | SAML 2.0, OAuth 2.0, OpenID Connect | Understand the browser-based login and token flow |
| 5. AWS IAM | Users, groups, roles, policies, STS, IAM Identity Center | Create a least-privilege policy in a sandbox AWS account |
| 6. Application IAM | Amazon Cognito, application authentication, API authorization | Build a small application with authenticated endpoints |
| 7. Enterprise IAM | IdP integration, federation, IGA, PAM | Diagram an enterprise identity architecture |
| 8. Security | Zero Trust, conditional access, credential risks, auditing | Investigate a simulated access-denied incident |
| 9. Automation | Identity workflows, APIs, scripting | Automate a safe, simulated account lifecycle workflow |

### Suggested practical projects

**Project 1: AWS IAM least-privilege lab**
- Create a test S3 bucket.
- Create a dedicated IAM role or user, as appropriate for the lab.
- Grant only the required read permissions.
- Test permitted and denied operations.
- Review relevant audit events.
- Remove unnecessary resources and permissions afterward.

**Project 2: Employee Joiner–Mover–Leaver workflow**
- Create sample employee records.
- Define role-based access requirements.
- Simulate onboarding.
- Change an employee's role.
- Simulate offboarding.
- Document approvals and access changes.

**Project 3: Customer authentication with Amazon Cognito**
- Create a small web application.
- Configure customer registration and login.
- Test authentication and token handling.
- Protect an API endpoint.
- Verify that users cannot access another user's data.

**Project 4: IAM incident investigation**
- Simulate a user who can sign in but cannot access an AWS resource.
- Identify the denied operation.
- Review the relevant policies and audit evidence.
- Apply a least-privilege correction.
- Document the root cause and resolution.

For learning purposes, use a dedicated sandbox environment and avoid modifying production identities or permissions without authorization.

---

## Final Revision: Remember These Five Things

1. **IAM:** Manages identities and access across systems.
2. **Authentication:** Verifies who you are.
3. **Authorization:** Determines what you can do.
4. **PAM:** Protects privileged accounts and administrative access.
5. **CIAM and Zero Trust:** CIAM manages customer identities, while Zero Trust is a broader security approach that evaluates access rather than assuming trust.

**A useful way to think about IAM is this:** An identity must be established, its access must be authorized, its permissions must be monitored and reviewed, and its access must be removed when it is no longer needed.

# PAM vs. CIAM vs. Enterprise IAM: Vendors and Product Comparison

The most important thing to understand is that **CyberArk, BeyondTrust, HashiCorp Vault, SailPoint, Microsoft Entra ID, Microsoft Entra External ID, Amazon Cognito, Ping Identity, and Keycloak do not all solve the same problem.**

Some specialize in protecting administrator accounts. Others manage employee identities, customer logins, application secrets, or identity governance.

Let's separate them by purpose, understand the major vendors, and then compare their products using practical examples.

# 1. PAM — Privileged Access Management

## What is PAM?

**Privileged Access Management (PAM)** is a security discipline that protects accounts, credentials, and sessions with elevated permissions.

Examples of privileged accounts include:

- Windows Domain Administrator.
- Linux `root` user.
- AWS administrator.
- Database administrator.
- Network administrator.
- VMware administrator.
- Production server administrator.
- Service accounts with elevated permissions.

These accounts are particularly sensitive because they can control critical systems, modify configurations, access confidential data, or create additional privileged accounts.

### A real-world example

Imagine you are a Cloud Operations engineer supporting production infrastructure.

You need to restart a production server, but the organization does not allow engineers to know or share the permanent administrator password.

A PAM solution can implement the following workflow:

1. You request privileged access.
2. The request is approved if required by policy.
3. PAM provides controlled access to the server or administrator account.
4. Your administrative session is monitored or recorded, depending on the configuration.
5. Access expires or is revoked according to policy.
6. The system records the relevant activity for auditing.

The exact workflow depends on the PAM product and how the organization configures it.

## Core PAM capabilities

| Capability | What it does | Example |
|---|---|---|
| Credential vaulting | Securely stores privileged credentials | Store a Domain Administrator password |
| Password rotation | Changes privileged passwords automatically | Rotate a service account password |
| Session management | Controls privileged connections | Allow approved RDP or SSH access |
| Session recording | Records administrative activity | Review a production server session |
| Just-in-Time (JIT) access | Provides temporary privileges | Grant administrator access for 30 minutes |
| Least privilege | Limits unnecessary administrative permissions | Allow restarting a service without granting full server administration |
| Discovery | Finds privileged accounts and credentials | Identify unmanaged local administrator accounts |
| Auditing | Records relevant access and administrative events | Investigate who accessed a production server |

These are common capabilities across the PAM market, although the feature set differs by product. [Microsoft Learn](https://learn.microsoft.com/en-us/defender-for-identity/integrate-microsoft-and-pam-services?utm_source=chatgpt.com)

## Common PAM vendors

The following are established names to know when learning enterprise PAM.

| Vendor | Main product or platform | General focus |
|---|---|---|
| [CyberArk](https://www.cyberark.com/?utm_source=chatgpt.com) | CyberArk Privileged Access Management | Enterprise privileged account and access security |
| [BeyondTrust](https://www.beyondtrust.com/?utm_source=chatgpt.com) | BeyondTrust PAM solutions | Privileged credential security, remote access, and privilege management |
| [Delinea](https://delinea.com/?utm_source=chatgpt.com) | Secret Server and Delinea Platform | Privileged credential vaulting and access management |
| [One Identity](https://www.oneidentity.com/?utm_source=chatgpt.com) | Safeguard | Privileged account and session security |
| [ManageEngine](https://www.manageengine.com/?utm_source=chatgpt.com) | PAM360 | Privileged account management |
| [WALLIX](https://www.wallix.com/?utm_source=chatgpt.com) | WALLIX Bastion | Privileged session and access security |
| [Keeper Security](https://www.keepersecurity.com/?utm_source=chatgpt.com) | KeeperPAM | Privileged access and credential security |
| [ARCON](https://arconnet.com/?utm_source=chatgpt.com) | ARCON PAM | Enterprise privileged access management |

These are examples, not a ranking. Product scope, deployment options, and licensing vary. [Gartner](https://www.gartner.com/en/documents/8528809?utm_source=chatgpt.com)

### Which PAM vendors should you learn first?

For a strong foundation, start with:

1. **CyberArk:** Learn credential vaults, password rotation, privileged sessions, and access workflows.
2. **BeyondTrust:** Learn privileged remote access, endpoint privilege management, and controlled administrator access.
3. **Delinea:** Learn privileged credential management and vault-based access workflows.
4. **HashiCorp Vault:** Learn application secrets, dynamic credentials, and DevOps identity.

The fourth is an important distinction: HashiCorp Vault is particularly relevant to application and infrastructure secrets. It is not simply interchangeable with a traditional enterprise PAM platform.

---

# 2. CIAM — Customer Identity and Access Management

## What is CIAM?

CIAM manages the identities and authentication experiences of **customers and other external users** accessing an organization's applications and digital services.

Examples include customers of:

- Online shopping platforms.
- Banking applications.
- Food delivery services.
- Streaming services.
- Travel websites.
- Mobile applications.
- SaaS products.

### Real-world example: An online shopping application

Suppose you build an e-commerce application.

Customers need to:

1. Register using an email address or another supported method.
2. Verify their email address.
3. Sign in securely.
4. Reset forgotten passwords.
5. Enable MFA when supported.
6. Access their profiles and orders.
7. Sign out and recover their accounts when necessary.

A CIAM platform can provide many of these identity capabilities.

Your application must still implement appropriate authorization checks. For example, authenticating a customer does not entitle them to view another customer's order history.

## What does CIAM typically manage?

| Capability | Purpose |
|---|---|
| Customer registration | Create customer accounts |
| Authentication | Verify customer identities |
| Account recovery | Restore access when credentials are lost |
| Social login | Support sign-in through configured external identity providers |
| MFA | Strengthen account security |
| SSO | Enable a common sign-in experience across integrated applications |
| Token issuance | Support authenticated application and API access |
| Customer profiles | Manage customer identity information |
| Consent and privacy | Support applicable customer preferences and privacy requirements |
| Fraud prevention | Help identify suspicious registration or login activity |

Not every CIAM product provides all these capabilities natively; some require integrations or application-level implementation.

## Common CIAM vendors

| Vendor | Product | General focus |
|---|---|---|
| [Amazon Web Services](https://aws.amazon.com/?utm_source=chatgpt.com) | Amazon Cognito | Authentication and identity for web and mobile applications |
| [Microsoft](https://www.microsoft.com/?utm_source=chatgpt.com) | Microsoft Entra External ID | External identities, including customer-facing scenarios |
| [Okta](https://www.okta.com/?utm_source=chatgpt.com) | Okta Customer Identity Cloud, associated with Auth0 | Application-focused customer authentication |
| [Ping Identity](https://www.pingidentity.com/?utm_source=chatgpt.com) | Ping Identity Platform | Enterprise identity, federation, and customer identity |
| [Keycloak](https://www.keycloak.org/?utm_source=chatgpt.com) | Keycloak | Open-source identity and access management for applications |
| [SAP](https://www.sap.com/?utm_source=chatgpt.com) | SAP Customer Data Cloud | Customer identity and customer data capabilities |

These products have different strengths. The best fit depends on the application architecture, customer population, integration requirements, and operational model. [CIOPages](https://www.ciopages.com/buyer-guides/customer-identity-access-management?utm_source=chatgpt.com)

---

# 3. The Most Important Product Comparison

You mentioned these products:

- Amazon Cognito
- Microsoft Entra External ID
- Microsoft Entra ID
- CyberArk
- BeyondTrust
- HashiCorp Vault
- SailPoint
- Ping Identity
- Keycloak

The easiest way to understand them is to classify them by their primary purpose.

## Product classification

| Product | Primary category | Main purpose |
|---|---|---|
| Amazon Cognito | CIAM | Customer authentication for web and mobile applications |
| Microsoft Entra External ID | External identity / CIAM | Customer sign-in and external identity scenarios |
| Microsoft Entra ID | Workforce IAM / IdP | Employee identities, SSO, MFA, and enterprise application access |
| CyberArk | PAM / Identity Security | Protect privileged accounts, credentials, and access |
| BeyondTrust | PAM / Identity Security | Control privileged access, credentials, remote sessions, and endpoint privileges |
| HashiCorp Vault | Secrets Management | Secure application secrets, credentials, certificates, and encryption keys |
| SailPoint | IGA / Identity Security | Govern identities, permissions, access requests, and access reviews |
| Ping Identity | IAM / CIAM / Access Management | Enterprise authentication, federation, and customer identity |
| Keycloak | IAM / Identity and Access Management | Open-source authentication, SSO, and application identity |

**Important:** These categories overlap. For example, Ping Identity offers several identity capabilities, while CyberArk and BeyondTrust have expanded beyond traditional password vaulting. The table describes the primary use cases you should associate with each product, not every capability it offers.

Let's examine each product.

---

# 4. Amazon Cognito vs. Microsoft Entra External ID

These are two products worth comparing if you're interested in Cloud IAM and application development.

## A. Amazon Cognito



**What it does:** Provides identity and authentication capabilities for web and mobile applications.

Imagine you're developing an e-commerce application hosted on AWS.

You need customers to register, log in, reset passwords, and access authorized application features.

Cognito provides managed identity components for these requirements.

### Two important Cognito components

**1. User Pools**

Used for customer directories, sign-up, sign-in, and issuing tokens to applications and APIs.

For example:
- Customer registration.
- Email verification.
- Password-based login.
- MFA.
- Social identity federation.
- JWT issuance.

**2. Identity Pools**

Used when an application needs temporary AWS credentials for authenticated or, when configured, unauthenticated users.

For example, an application can exchange a trusted identity token for temporary credentials that permit access to specific AWS resources.

You don't necessarily need both components. A typical application that only needs customer sign-in may use a user pool without an identity pool. [AWS Documentation](https://docs.aws.amazon.com/cognito/latest/developerguide/what-is-amazon-cognito.html?utm_source=chatgpt.com)

Official documentation: [Amazon Cognito Developer Guide](https://docs.aws.amazon.com/cognito/latest/developerguide/what-is-amazon-cognito.html?utm_source=chatgpt.com)

## B. Microsoft Entra External ID

**What it does:** Provides external identity capabilities, including customer identity and access management for applications.

Imagine a company builds a customer-facing application using .NET, React, or another supported technology.

It needs:
- Customer registration and sign-in.
- Customizable login experiences.
- External identity provider integration.
- MFA and applicable access policies.
- Identity management for external application users.

Microsoft Entra External ID can provide these capabilities.

It is designed for customer-facing applications and external identity scenarios. It is not simply another name for workforce Microsoft Entra ID. [Microsoft Learn](https://learn.microsoft.com/en-us/entra/external-id/customers/?utm_source=chatgpt.com)

Official documentation: [Microsoft Entra External ID](https://learn.microsoft.com/en-us/entra/external-id/?utm_source=chatgpt.com)

## Cognito vs. Entra External ID

| Feature | Amazon Cognito | Microsoft Entra External ID |
|---|---|---|
| Primary use | Application identity, particularly CIAM | External identity, including CIAM |
| Cloud ecosystem | AWS | Microsoft identity ecosystem |
| Customer registration and sign-in | Yes | Yes |
| MFA | Supported | Supported, subject to configuration and tenant capabilities |
| Social identity federation | Supported | Supported for configured providers |
| Application tokens | Supports JWTs | Supports standards-based application authentication |
| AWS resource access | Identity pools can issue temporary AWS credentials | Not its primary purpose |
| Microsoft application ecosystem | Can integrate through supported federation protocols | Integrates with supported Microsoft identity capabilities |
| Application integration | AWS SDKs and application integrations | Microsoft identity libraries and supported protocols |
| Typical scenario | Customer login for an AWS-hosted application | Customer login for an application using Microsoft's external identity platform |

### Which should you choose?

**Choose Amazon Cognito when:**
- Your application is built around AWS services.
- You need managed customer authentication.
- Your application needs to integrate with AWS identity and resource access.
- You want to learn application authentication within the AWS ecosystem.

**Consider Microsoft Entra External ID when:**
- You need customer identity capabilities within the Microsoft identity ecosystem.
- Your application uses supported Microsoft identity libraries and integrations.
- You want to manage external identities using Microsoft's CIAM platform.

Neither is universally better. Your application architecture and required identity flows determine the appropriate choice.

---

# 5. Microsoft Entra ID vs. Microsoft Entra External ID

This is a particularly important distinction.

## Microsoft Entra ID

Formerly known as Azure Active Directory, Microsoft Entra ID is Microsoft's cloud identity platform for workforce identity and access management.

It manages access to resources such as:
- Microsoft 365.
- Azure resources.
- Enterprise SaaS applications.
- Internal business applications.
- Applications integrated through SSO.
- Resources protected by Conditional Access policies.

Typical capabilities include:
- Employee identity management.
- SSO.
- MFA.
- Conditional Access.
- Application provisioning.
- Managed identities for supported Azure workloads.
- Enterprise application integration.

For example, an employee signs in to Microsoft 365 using their company account and accesses the applications they are authorized to use.

That is a typical workforce IAM scenario. [Microsoft Learn](https://learn.microsoft.com/en-us/entra/identity/?utm_source=chatgpt.com)

Official documentation: [Microsoft Entra ID documentation](https://learn.microsoft.com/en-us/entra/identity/?utm_source=chatgpt.com)

## Microsoft Entra External ID

External ID addresses identities outside the core workforce.

Examples include:
- Customers registering for an application.
- Business customers using a company's SaaS platform.
- External partners accessing permitted resources.

One important nuance: Microsoft Entra External ID also supports **B2B collaboration scenarios**, where external guests access organizational resources. The configuration and tenant model differ from customer-facing CIAM scenarios.

Microsoft distinguishes workforce tenants used for collaboration from external tenants used for customer-facing applications. [Microsoft Learn](https://learn.microsoft.com/en-us/entra/external-id/external-identities-overview?utm_source=chatgpt.com)

## Comparison

| Question | Microsoft Entra ID | Microsoft Entra External ID |
|---|---|---|
| Who primarily uses it? | Employees and organizational identities | Customers, partners, and other external identities |
| Typical login | Employee signs in to corporate resources | Customer signs in to a company's application |
| Microsoft 365 access | Core workforce scenario | Customer-facing external tenants do not provide SSO to Microsoft 365 |
| Customer registration | Not its primary purpose | Supported in CIAM scenarios |
| Enterprise SSO | Core capability | Supports external identity scenarios; exact capabilities depend on tenant type |
| Conditional Access | Supported | Supported capabilities depend on tenant type and configuration |
| Example | Employee signs in to Teams | Customer signs in to a shopping application |

### Easy example

Consider an organization operating two systems.

**System 1: Internal corporate portal**

Only employees should sign in.

Use workforce identity capabilities provided by Microsoft Entra ID.

**System 2: Customer shopping application**

Thousands of customers register and sign in.

Consider Microsoft Entra External ID or Amazon Cognito.

**The distinction is the identity use case, not simply whether the application is hosted in the cloud.**

---

# 6. CyberArk vs. BeyondTrust

These are two important vendors to understand in PAM.

## CyberArk

CyberArk focuses on privileged access and identity security.

Common use cases include:
- Protecting administrator credentials.
- Vaulting privileged passwords.
- Rotating credentials.
- Controlling privileged sessions.
- Managing privileged access across infrastructure.
- Protecting application and machine identities through applicable products.

### Example

A Windows server has a privileged administrator account.

CyberArk can be configured to store its password securely, control who can retrieve or use it, rotate it according to policy, and support auditing of privileged access.

## BeyondTrust

BeyondTrust also focuses on privileged access security.

Its product capabilities include:
- Privileged credential management.
- Privileged Remote Access.
- Endpoint privilege management.
- Controlled administrative access.
- Privileged session monitoring.
- Just-in-time access through applicable offerings.

### Example

A third-party vendor needs to troubleshoot a production server remotely.

BeyondTrust can provide a controlled remote-access workflow, limiting which systems the vendor can access and supporting session monitoring and auditing.

CyberArk and BeyondTrust both cover privileged access, but their products, integrations, deployment options, and licensing differ. [Microsoft Learn](https://learn.microsoft.com/en-us/defender-for-identity/integrate-microsoft-and-pam-services?utm_source=chatgpt.com)

## Comparison

| Feature | CyberArk | BeyondTrust |
|---|---|---|
| Main category | PAM / Identity Security | PAM / Identity Security |
| Privileged password vaulting | Available through relevant offerings | Available through relevant offerings |
| Credential rotation | Supported by applicable products | Supported by applicable products |
| Privileged session controls | Supported | Supported |
| Remote privileged access | Supported capabilities | A key use case |
| Endpoint privilege management | Available through applicable products | A key use case |
| Enterprise infrastructure security | Yes | Yes |
| Typical example | Secure administrator credentials and sessions | Control remote vendor access and endpoint privileges |

### Which is better?

There is no universal winner.

For learning purposes, associate **CyberArk with enterprise privileged access and credential security**, and **BeyondTrust with privileged access, remote sessions, and endpoint privilege management**.

Both have broader portfolios than these examples suggest.

---

# 7. HashiCorp Vault vs. CyberArk vs. BeyondTrust

This distinction is especially useful if you are learning AWS, Docker, Kubernetes, Terraform, or CI/CD.

## HashiCorp Vault



HashiCorp Vault is primarily a **secrets management and data protection platform**.

A secret is sensitive information that must be protected, such as:
- Database passwords.
- API keys.
- Application credentials.
- TLS certificates.
- Encryption keys.
- Cloud credentials.

Vault can securely manage these secrets, issue dynamic credentials through supported secrets engines, and audit interactions.

For example, an application running in Kubernetes needs database access. Instead of embedding a permanent database password in the container image, the application can authenticate to Vault and obtain credentials through an appropriately configured secrets workflow.

Depending on the secrets engine, credentials can be generated dynamically and revoked or allowed to expire. [HashiCorp Developer](https://developer.hashicorp.com/vault/docs/about-vault/what-is-vault?utm_source=chatgpt.com)

Official documentation: [HashiCorp Vault documentation](https://developer.hashicorp.com/vault/docs?utm_source=chatgpt.com)

## How are the three different?

| Scenario | Best product category to investigate |
|---|---|
| Secure a Domain Administrator password | Traditional PAM, such as CyberArk or BeyondTrust |
| Control and record a privileged RDP session | PAM |
| Give a developer temporary access to a production server | PAM or a suitable JIT privileged-access solution |
| Secure database passwords used by applications | Secrets management, such as HashiCorp Vault |
| Provide dynamic database credentials to a workload | HashiCorp Vault |
| Store and rotate API credentials used in a CI/CD pipeline | HashiCorp Vault or another appropriate secrets manager |
| Control which employees can access business applications | Workforce IAM |
| Review employee permissions and access approvals | IGA |

**Important:** There is overlap. CyberArk and BeyondTrust also offer capabilities for application identities and secrets, while HashiCorp Vault can support privileged access workflows. However, they should not be treated as interchangeable products.

---

# 8. SailPoint — Identity Governance and Administration

SailPoint is primarily associated with **Identity Security and Identity Governance and Administration (IGA)**.

Its focus is not simply authenticating users at login.

Instead, it helps organizations determine:
- Which identities exist.
- Which applications users can access.
- Whether access is appropriate.
- Who approved the access.
- Whether users still need their permissions.
- Whether conflicting permissions create a risk.

### Example: Employee access review

Suppose an employee has access to:
- ServiceNow.
- AWS.
- A financial reporting system.
- An internal administration application.

The employee changes roles and no longer requires access to the financial system.

An identity governance workflow can help identify the existing entitlement, obtain a review or approval, and coordinate the removal of unnecessary access.

### Common IGA capabilities

- Identity lifecycle governance.
- Access request and approval workflows.
- Access certifications.
- Role management.
- Segregation-of-duties controls.
- Application entitlement visibility.
- Provisioning and deprovisioning integrations.

SailPoint is therefore especially relevant to access governance and compliance-focused identity programs.

Official website: [SailPoint](https://www.sailpoint.com/?utm_source=chatgpt.com)

**Remember:** SailPoint complements authentication platforms. An organization may use Microsoft Entra ID for employee sign-in and SailPoint for access governance.

---

# 9. Ping Identity — Enterprise IAM and CIAM

Ping Identity provides identity and access capabilities for enterprises and customer-facing applications.

Its platform includes capabilities for:
- Authentication.
- SSO.
- MFA.
- Identity federation.
- Access management.
- Directory services.
- Identity lifecycle management through applicable products.

### Example

A bank has:
- Employees using corporate applications.
- Customers using a mobile banking application.
- External partners connecting to selected services.

The bank may use identity technologies to establish authentication, federation, and access policies across these systems.

Ping Identity offers products relevant to enterprise IAM and CIAM, so it is broader than a customer-login-only service. [Ping Identity Docs](https://docs.pingidentity.com/platform/?utm_source=chatgpt.com)

Official website: [Ping Identity](https://www.pingidentity.com/?utm_source=chatgpt.com)

---

# 10. Keycloak — Open-Source IAM

Keycloak is an open-source identity and access management solution used to add authentication and SSO to applications.

It supports standards-based identity integrations, including OpenID Connect and SAML.

### Example

You build a Java Spring Boot application with a React frontend.

Rather than implementing every login flow from scratch, you can integrate Keycloak to manage user authentication and provide tokens to the application.

Your backend must still validate the authentication result and enforce authorization rules for its endpoints and data.

### Common Keycloak use cases

- Application login.
- SSO.
- User and role management.
- Identity federation.
- OpenID Connect.
- SAML-based integrations.
- Development and testing of IAM architectures.

### Keycloak vs. Amazon Cognito

| Feature | Keycloak | Amazon Cognito |
|---|---|---|
| Model | Open-source software | AWS-managed identity service |
| Hosting | Self-managed or supported managed deployments | AWS-managed |
| Customer authentication | Yes | Yes |
| SSO | Supported | Supported for appropriate integrations |
| Standards | OpenID Connect and SAML | OpenID Connect, SAML integrations, and OAuth-based flows |
| Infrastructure responsibility | Depends on deployment; self-hosting requires operational management | AWS manages the underlying service |
| AWS integration | Possible through integrations | Native AWS integration |
| Customization | Flexible, depending on implementation | Customization within Cognito's supported model |
| Typical user | Teams wanting control over an identity deployment | Teams wanting managed application identity on AWS |

Official project: [Keycloak documentation](https://www.keycloak.org/documentation?utm_source=chatgpt.com)

---

# 11. Where Each Product Fits in a Real Enterprise

Imagine an organization running an e-commerce platform in AWS.

It has 500 employees, 100 administrators and engineers, and 200,000 customers.

A possible architecture could look like this:

| Requirement | Example product | Why |
|---|---|---|
| Employee login | Microsoft Entra ID | Workforce authentication and SSO |
| Customer login | Amazon Cognito | Customer registration and authentication |
| Privileged administrator access | CyberArk or BeyondTrust | Control sensitive administrator credentials and sessions |
| Application secrets | HashiCorp Vault | Manage application credentials and secrets |
| Employee access reviews | SailPoint | Govern entitlements and access approvals |
| Alternative application IAM | Keycloak | Self-managed application authentication |
| Enterprise and customer identity requirements | Ping Identity | Evaluate the relevant enterprise IAM or CIAM products |

This is an illustrative architecture, not a requirement to deploy every product.

An organization may choose a smaller number of platforms based on its existing infrastructure, security requirements, budget, integrations, and operational capabilities.

Some products overlap, and some can replace particular components of another vendor's architecture.

---

# 12. Final Comparison: The Quick Revision Table

Use this table when preparing for interviews.

| Product | Remember it as | Question it helps answer |
|---|---|---|
| **Amazon Cognito** | AWS application identity / CIAM | How do customers sign in to my application? |
| **Microsoft Entra External ID** | External identity / CIAM | How do external customers or partners authenticate to supported applications? |
| **Microsoft Entra ID** | Workforce IAM / IdP | How do employees authenticate and access corporate applications? |
| **CyberArk** | PAM / Identity Security | How do we protect privileged credentials and access? |
| **BeyondTrust** | PAM / Identity Security | How do we control privileged access, remote sessions, and endpoint privileges? |
| **HashiCorp Vault** | Secrets management | How do applications securely obtain and manage secrets? |
| **SailPoint** | IGA / Identity Governance | Who should have access, who approved it, and should they still have it? |
| **Ping Identity** | Enterprise IAM / CIAM | How do we provide authentication, SSO, and identity federation? |
| **Keycloak** | Open-source IAM | How do we implement authentication and SSO for our applications? |

## My recommended learning order

For a practical foundation in cloud identity and access management, follow this sequence:

1. **IAM fundamentals:** Authentication, authorization, MFA, SSO, RBAC, and ABAC.
2. **Microsoft Entra ID:** Workforce identity, enterprise applications, Conditional Access, and identity federation.
3. **AWS IAM:** Policies, roles, trust relationships, STS, and least privilege.
4. **Amazon Cognito:** User pools, identity pools, JWTs, and application authentication.
5. **PAM fundamentals:** Vaulting, credential rotation, privileged sessions, and JIT access.
6. **HashiCorp Vault:** Secrets engines, policies, dynamic credentials, and workload authentication.
7. **IGA and CIAM:** Learn SailPoint's governance use cases and compare customer identity architectures.

**The key takeaway:** Learn the security problem first, then the vendor's implementation. Once you understand what a product protects and how it fits into an identity architecture, learning the product itself becomes much easier.

# OAuth 2.0 vs. OpenID Connect (OIDC) vs. SAML vs. LDAP

These four technologies are fundamental to **IAM, authentication, authorization, Single Sign-On (SSO), and enterprise identity management**.

The most important distinction is that they do not all perform the same job:

- **OAuth 2.0:** Allows an application to obtain limited access to a resource.
- **OIDC (OpenID Connect):** Adds an identity and authentication layer on top of OAuth 2.0.
- **SAML:** Exchanges authentication and authorization-related information between identity systems and applications, commonly for enterprise SSO.
- **LDAP:** A protocol for accessing and managing information in a directory service, such as user accounts and groups.

Let's understand each one with real-world examples and compare how they work.

---

# 1. Start With a Real-Life Example

Imagine you work for a company that uses Microsoft Entra ID for employee identities.

You want to access an internal application, such as a ServiceNow portal.

The application needs to establish who you are and determine what you're allowed to do.

Different technologies can play different roles in this process.

| Technology | What it does | Real-world analogy |
|---|---|---|
| OAuth 2.0 | Grants delegated access to resources | Giving an application a limited-access permission slip |
| OIDC | Enables an application to authenticate a user through an identity provider | Receiving a verified identity card |
| SAML | Exchanges signed authentication assertions for SSO | Receiving a signed statement from a trusted authority |
| LDAP | Lets systems query or update directory information | Looking up a person in a company's employee directory |

**Important:** OAuth 2.0 and OIDC are closely related, but OAuth 2.0 alone is not an authentication protocol. SAML is commonly used for browser-based enterprise SSO, while LDAP is commonly used for directory access.

# 2. OAuth 2.0 — Authorization

OAuth 2.0 is an authorization framework that allows an application to obtain limited access to a protected resource without needing the user's password.

### Real-world example: Photo printing application

Suppose you use a photo-printing application that needs access to selected photos in your cloud account.

You don't want to give the photo-printing application your cloud account password.

Instead, you authorize the application to access the permitted photos.

The process works conceptually like this:

1. You open the photo-printing application.
2. It redirects you to the relevant authorization service.
3. You authenticate with that service if necessary.
4. You grant the requested permissions.
5. The authorization server issues an access token.
6. The application uses that token to make permitted API requests.
7. The API validates the token and enforces the applicable permissions.

The application receives delegated access rather than your account password.

### Important OAuth 2.0 terms

| Term | Meaning |
|---|---|
| Resource owner | The person or entity that controls access to the resource |
| Client | The application requesting access |
| Authorization server | The service that issues tokens |
| Resource server | The API or service protecting the resource |
| Access token | A credential used to access a protected resource |
| Scope | A description of the requested access permissions |
| Refresh token | A credential that can be used to obtain new access tokens when permitted |

**Example scopes:**

- `files.read`
- `files.write`
- `calendar.read`

These are illustrative scope names; actual scopes depend on the API.

If an application receives a token permitting read access, it should not be able to perform write operations merely because it possesses that token.

### OAuth 2.0 does not automatically authenticate the user to your application

This is a common interview trap.

An access token tells a resource server that the request has an associated authorization grant. Its exact meaning depends on the token format and the issuing system.

OAuth 2.0 does not, by itself, standardize how a client verifies the end user's identity for login.

For user authentication, OpenID Connect adds the necessary identity layer. [Microsoft Learn](https://learn.microsoft.com/en-us/entra/identity-platform/authentication-vs-authorization?utm_source=chatgpt.com)

---

# 3. OIDC — OpenID Connect

OIDC stands for **OpenID Connect**.

It is an identity and authentication protocol built on top of OAuth 2.0.

While OAuth 2.0 focuses on delegated authorization, OIDC adds a standardized way for an application to verify a user's authentication and obtain identity claims.

### Real-world example: Sign in with Google

Imagine you build a web application and offer a **Sign in with Google** button.

The typical process is:

1. The user clicks the sign-in button.
2. Your application redirects the user to Google's identity service.
3. The user authenticates and grants any required consent.
4. The identity provider returns the relevant tokens through the configured OIDC flow.
5. Your application validates the ID token.
6. The application establishes the user's authenticated session.

The ID token contains claims about the authentication and the user's identity.

### The three tokens to understand

| Token | Purpose |
|---|---|
| ID token | Communicates authentication and identity claims to the client |
| Access token | Used to access a protected API or resource |
| Refresh token | Can be used to obtain new tokens when the authorization server permits it |

Not every flow returns all three tokens.

### What is a JWT?

A JSON Web Token (JWT) is a compact token format that can carry claims.

OIDC commonly uses a JWT for the ID token.

For example, an ID token might contain claims conceptually similar to these:

```json
{
  "iss": "https://identity.example.com",
  "sub": "user-12345",
  "aud": "my-application",
  "name": "Alex",
  "exp": 1900000000
}
```

This is an illustrative example, not a real token.

- `iss`: Issuer of the token.
- `sub`: Subject identifier.
- `aud`: Intended audience.
- `name`: A sample identity claim.
- `exp`: Expiration time expressed as a Unix timestamp.

An application must validate the token's signature and relevant claims, including issuer, audience, and expiration, according to the protocol and its security requirements.

**Never assume a JWT is trustworthy simply because it can be decoded.**

### When should you use OIDC?

OIDC is commonly used for:
- Web application login.
- Mobile application login.
- Single-page applications.
- SaaS authentication.
- Customer identity platforms.
- Modern enterprise SSO.
- Authentication integrations with Microsoft Entra ID, Amazon Cognito, and Keycloak.

For new application development, OIDC is generally a strong default for authentication when supported by the identity provider and application architecture. [Microsoft Learn](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/saml-vs-oidc-decision-guide?utm_source=chatgpt.com)

Official specification: [OpenID Connect specifications](https://openid.net/developers/specs/?utm_source=chatgpt.com)

---

# 4. SAML — Security Assertion Markup Language

SAML 2.0 is a standards-based protocol commonly used for enterprise federated authentication and Single Sign-On.

It allows an identity provider to communicate authentication information to an application using a SAML assertion, typically encoded as XML.

### Real-world example: Corporate ServiceNow login

Suppose your company uses Microsoft Entra ID as its identity provider and ServiceNow as an enterprise application.

You open ServiceNow and choose corporate sign-in.

The process typically works like this:

1. You access ServiceNow.
2. ServiceNow redirects you to Microsoft Entra ID.
3. Microsoft Entra ID authenticates you and applies relevant access policies.
4. Microsoft Entra ID generates a SAML response containing a signed assertion.
5. Your browser carries the response to ServiceNow's assertion consumer service.
6. ServiceNow validates the response and assertion.
7. ServiceNow establishes a session for the authenticated user.

The exact process depends on the application's SAML configuration.

### Important SAML components

| Component | Purpose |
|---|---|
| Identity Provider (IdP) | Authenticates the user and issues assertions |
| Service Provider (SP) | The application the user wants to access |
| SAML assertion | Contains statements about identity and authentication |
| SAML response | Carries the assertion and related protocol information |
| Metadata | Describes endpoints, identifiers, and signing certificates |
| ACS URL | Assertion Consumer Service endpoint that receives the SAML response |

### What does a SAML assertion contain?

Depending on the configuration, it may include:
- Subject identity.
- Authentication information.
- User attributes.
- Group or role-related attributes.
- Validity conditions.
- Audience restrictions.

SAML assertions commonly use digital signatures to protect their integrity and establish trust.

The receiving application must validate the assertion correctly, including its signature and applicable conditions.

### Why do enterprises use SAML?

SAML is widely used for:
- Enterprise application SSO.
- Integrating corporate identity providers with SaaS applications.
- Federated identity across organizations.
- Applications that require SAML-based integration.

For example, a company might integrate its identity provider with Salesforce, ServiceNow, or another enterprise SaaS platform using SAML.

SAML remains valuable in established enterprise environments, while OIDC is often preferred for newer application architectures. [Microsoft Learn](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/saml-vs-oidc-decision-guide?utm_source=chatgpt.com)

Official specification: [OASIS SAML specifications](https://www.oasis-open.org/standard/saml/?utm_source=chatgpt.com)

---

# 5. LDAP — Lightweight Directory Access Protocol

LDAP differs from OAuth 2.0, OIDC, and SAML because its primary purpose is accessing and managing directory information.

A directory is a structured store of information about identities and other objects.

Examples include:
- User accounts.
- Groups.
- Organizational units.
- Contact details.
- Directory attributes.
- Certain authentication-related information.

A common implementation is Microsoft Active Directory Domain Services, which supports LDAP.

### Real-world example: Employee lookup

Suppose a Service Desk analyst needs to check an employee's account information.

A directory-enabled tool may use LDAP to query Active Directory for:
- The user's directory account.
- Group membership.
- Department.
- Email address.
- Account status, where available.

An application may also use an LDAP bind operation to authenticate to an LDAP server, depending on its configuration.

### Common LDAP operations

| Operation | Purpose |
|---|---|
| Bind | Establish a session and, when applicable, authenticate to the directory |
| Search | Find directory entries matching specified criteria |
| Add | Create a directory entry, subject to permissions |
| Modify | Update directory attributes |
| Delete | Remove a directory entry, subject to permissions |
| Compare | Check whether an entry has a specified attribute value |

### LDAP example

An application might search for a user using a distinguished name (DN) or another directory search filter.

An illustrative DN:

```text
CN=Alex Smith,OU=Employees,DC=example,DC=com
```

Meaning:

- `CN=Alex Smith`: Common Name.
- `OU=Employees`: Organizational Unit.
- `DC=example,DC=com`: Domain components.

This is an example of directory naming syntax, not a guaranteed representation of every organization's Active Directory structure.

An application might search for users using an LDAP filter such as:

```text
(&(objectCategory=person)(objectClass=user)(sAMAccountName=alex.smith))
```

This filter is intended to find an Active Directory user matching the specified account name.

### Is LDAP secure?

LDAP itself does not automatically guarantee that communications are encrypted.

Common approaches include:
- LDAPS, typically LDAP over TLS on port 636.
- LDAP with StartTLS, where supported and configured.

Applications should use appropriate transport security and authentication methods, and avoid sending passwords over unencrypted LDAP connections.

Official overview: [Microsoft's LDAP documentation](https://learn.microsoft.com/en-us/windows/win32/adsi/ldap-adsi-provider?utm_source=chatgpt.com)

---

# 6. OAuth 2.0 vs. OIDC vs. SAML vs. LDAP

Here is the comparison you should remember for interviews.

| Feature | OAuth 2.0 | OIDC | SAML 2.0 | LDAP |
|---|---|---|---|---|
| Full name | Open Authorization 2.0 | OpenID Connect | Security Assertion Markup Language | Lightweight Directory Access Protocol |
| Primary purpose | Delegated authorization | Authentication and identity claims | Federated authentication and enterprise SSO | Accessing directory information |
| Is it an authentication protocol? | Not by itself | Yes | Yes, commonly used for federated authentication | Can support authentication through bind operations |
| Common data format | Token format depends on implementation | JSON-based claims, commonly JWTs | XML assertions | LDAP protocol messages |
| Common credentials or artifacts | Access token, optionally refresh token | ID token, access token, optionally refresh token | SAML assertion | Directory entries and LDAP bind credentials |
| Common use case | Allow an application to access an API | Sign in to an application | Enterprise application SSO | Query Active Directory |
| Typical application | API integration | Web or mobile application | Corporate SaaS application | Employee directory |
| Common environment | APIs, web services, cloud applications | Modern web, mobile, and enterprise applications | Enterprise federation and SSO | Enterprise directories |
| Example | Grant an application permission to read calendar data | Sign in with Microsoft | Sign in to ServiceNow using corporate SSO | Look up a user's AD group membership |

The fundamental differences are supported by the official Microsoft identity documentation. [Microsoft Learn](https://learn.microsoft.com/en-us/entra/identity-platform/authentication-vs-authorization?utm_source=chatgpt.com)

## 7. Understand How They Work Together

These technologies are not mutually exclusive. An organization can use several of them within the same identity architecture.

Consider an enterprise application.



A possible workflow is:

1. **LDAP:** An identity system queries an enterprise directory to retrieve identity information.
2. **OIDC:** An employee authenticates to a modern application through the organization's identity provider.
3. **SAML:** A different enterprise application uses a SAML assertion for SSO.
4. **OAuth 2.0:** The application obtains an access token to call a protected API.

For example, Microsoft Entra ID can support applications that use either SAML or OIDC for SSO, while OAuth 2.0 supports access to protected APIs. [Microsoft Learn](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/understand-microsoft-sso-model?utm_source=chatgpt.com)

The exact architecture depends on the organization's directory, identity provider, applications, and security requirements.

---

# 8. Common Interview Questions

### Q1. What is the difference between OAuth 2.0 and OIDC?

OAuth 2.0 is an authorization framework that allows applications to access protected resources. OIDC builds on OAuth 2.0 to provide authentication and standardized identity claims.

### Q2. What is the difference between OIDC and SAML?

Both can support federated authentication and SSO.

- OIDC uses OAuth 2.0 and commonly uses JSON Web Tokens.
- SAML 2.0 uses XML-based assertions and is widely used for enterprise SSO.

OIDC is generally a good default for new web and mobile application development, while SAML remains important for established enterprise integrations.

### Q3. What is the difference between LDAP and SAML?

LDAP provides a protocol for accessing and managing directory information. SAML enables identity providers to communicate authentication assertions to applications.

LDAP is commonly used with enterprise directories, while SAML is commonly used to integrate identity providers with enterprise applications.

### Q4. Can LDAP replace OAuth 2.0?

Not directly. LDAP and OAuth 2.0 serve different purposes.

LDAP provides directory access, while OAuth 2.0 provides delegated authorization for protected resources.

### Q5. Can OIDC and OAuth 2.0 be used together?

Yes. OIDC builds on OAuth 2.0. An application can authenticate a user through OIDC and obtain an access token for an API.

### Q6. What is the difference between SAML SSO and OAuth 2.0?

SAML SSO allows an identity provider to communicate authentication information to an application through a SAML assertion.

OAuth 2.0 enables delegated access to protected resources. It is not, by itself, a user-login protocol.

### Q7. What is the relationship between Active Directory and LDAP?

Active Directory Domain Services is a directory service. LDAP is one of the protocols clients can use to access its directory information.

Active Directory also supports other protocols, including Kerberos for network authentication.

---

# 9. The Memory Trick

Remember these four lines:

| Technology | Remember it as |
|---|---|
| **OAuth 2.0** | Authorization: What access can an application obtain? |
| **OIDC** | Authentication: Who signed in? |
| **SAML** | Enterprise federation: How does an application receive a trusted authentication assertion? |
| **LDAP** | Directory access: How do I find or manage identity information? |

### My recommendation for your IAM learning path

Study them in this order:

1. **LDAP and Active Directory:** Understand users, groups, directory queries, and enterprise identities.
2. **SAML:** Learn IdP, SP, metadata, assertions, certificates, and enterprise SSO.
3. **OAuth 2.0:** Understand authorization flows, scopes, access tokens, and refresh tokens.
4. **OIDC:** Learn ID tokens, claims, discovery, and authentication flows.
5. **Hands-on integration:** Configure an application with Keycloak, Microsoft Entra ID, or Amazon Cognito.

For practical work, focus particularly on the **OIDC Authorization Code Flow with PKCE**, the OAuth 2.0 client credentials flow for machine-to-machine access, and SAML-based enterprise SSO.

These concepts will give you a strong foundation for understanding Cloud IAM, CIAM, application authentication, and enterprise identity troubleshooting.

# The AAA Framework in Cybersecurity & IAM
**Authentication • Authorization • Accounting**

The **AAA Framework** is a security model used to control access to systems and resources and track user activity.

AAA stands for:

- **A — Authentication:** Who are you?
- **A — Authorization:** What are you allowed to do?
- **A — Accounting:** What did you do?

AAA is commonly used in network security, enterprise IT, remote access, VPNs, and infrastructure administration.

---

## 1. The Three Components of AAA

### 1. Authentication — Who are you?

Authentication verifies the identity of a user, device, or service.

**Example:** You sign in to your company's VPN using your username, password, and MFA.

The authentication system verifies your credentials before allowing the login to proceed.

Common methods:
- Username and password.
- Multi-Factor Authentication (MFA).
- Digital certificates.
- Biometrics.
- Security keys.

**Related IAM technologies:** LDAP, Kerberos, OIDC, SAML, and RADIUS can participate in authentication architectures, although they serve different purposes.

### 2. Authorization — What are you allowed to do?

Authorization determines which resources and actions an authenticated identity can access.

**Example:** After connecting to the corporate VPN, a Service Desk analyst can access ServiceNow but cannot administer production servers.

Common authorization mechanisms:
- Role-Based Access Control (RBAC).
- Attribute-Based Access Control (ABAC).
- Access Control Lists (ACLs).
- IAM policies.
- Group and permission assignments.

**Important:** Successfully authenticating does not automatically grant unrestricted access.

### 3. Accounting — What did you do?

Accounting records resource usage and user activity for auditing, troubleshooting, security monitoring, and reporting.

**Example:** An administrator connects to a server, executes administrative commands, and disconnects.

Depending on the system, accounting records may capture:
- Login and logout times.
- Session duration.
- Source IP address.
- Commands executed.
- Resources accessed.
- Data transferred.
- Administrative actions.

Accounting does not necessarily record every command or action. The available information depends on the system and its logging configuration.

**Important:** In AAA, *accounting* means activity tracking and audit records, not financial accounting.

---

## 2. Real-World Example: Employee Accessing a Corporate Network

Imagine you are an IT support engineer working for an enterprise.

You need to connect to the corporate network remotely.

Here's how AAA works:



| Step | AAA component | What happens |
|---|---|---|
| 1 | Authentication | You enter your credentials and complete the required MFA challenge. |
| 2 | Authorization | The network access system determines which network resources you can access. |
| 3 | Accounting | The system records session details, such as connection time and duration. |

Suppose the employee's role permits access to the support network but not the production database network.

The user may authenticate successfully and connect to the VPN, yet still be denied access to the production database.

This demonstrates the difference between authentication and authorization.

---

## 3. AAA and IAM: What's the Difference?

AAA and IAM are closely related, but they are not interchangeable.

| Feature | AAA Framework | IAM |
|---|---|---|
| Full form | Authentication, Authorization, Accounting | Identity and Access Management |
| Primary purpose | Control access and track activity | Manage identities and their access throughout their lifecycle |
| Authentication | Core component | Core capability |
| Authorization | Core component | Core capability |
| Activity tracking | Core component | Supported through logging, auditing, and integrations |
| Identity lifecycle | Not its primary focus | Includes provisioning, role changes, and deprovisioning |
| Access governance | May integrate with governance systems | Can include approvals, reviews, and compliance controls |
| Example | Controlling and logging VPN access | Managing employee identities across corporate applications |

**Remember:** AAA describes three important access-control functions. IAM is the broader discipline that manages identities and access across systems.

---

## 4. RADIUS and TACACS+: How AAA Is Implemented

In enterprise networking, AAA is often implemented using protocols such as RADIUS and TACACS+.

### RADIUS

**RADIUS** stands for Remote Authentication Dial-In User Service.

It is commonly used for:
- VPN access.
- Wi-Fi authentication.
- Network Access Control (NAC).
- Network access through supported switches and access points.

A typical architecture is:

`User → VPN Gateway → RADIUS Server → Identity Source`

The RADIUS server evaluates the authentication request and can return access-related attributes or decisions, depending on the deployment.

RADIUS can support authentication, authorization-related decisions, and accounting.

### TACACS+

**TACACS+** is commonly used to control administrative access to network infrastructure.

Examples include:
- Cisco routers.
- Network switches.
- Firewalls.
- Network administration consoles.

It supports centralized authentication, authorization, and accounting for administrative access.

A notable distinction is that TACACS+ separates authentication and authorization processes more explicitly and provides command-level authorization capabilities in supported implementations.

### RADIUS vs. TACACS+

| Feature | RADIUS | TACACS+ |
|---|---|---|
| Common use | Network access, VPNs, Wi-Fi | Network device administration |
| Authentication | Yes | Yes |
| Authorization | Supported within its access-control model | Supports granular authorization, including command authorization |
| Accounting | Yes | Yes |
| Transport | Commonly UDP; newer secure transport options exist | Commonly TCP |
| Typical example | Authenticate an employee connecting to a VPN | Control which commands an administrator can execute on a network switch |

Both protocols can implement AAA functions, but they are suited to different deployment patterns.

---

## 5. AAA in a Real Enterprise Environment

Consider an organization using Microsoft Active Directory, a VPN, and network switches.

A possible architecture is:

1. **Identity source:** Active Directory stores employee identities and group information.
2. **Authentication:** A supported authentication service verifies the user's identity.
3. **Authorization:** Network policies determine which resources or administrative actions are permitted.
4. **Accounting:** The VPN or network infrastructure records connection and activity information.
5. **Auditing:** Security teams review the logs to investigate suspicious activity.

Depending on the architecture, RADIUS or TACACS+ may provide AAA services, while Active Directory or another identity source supplies identity information.

A centralized AAA service does not replace the identity directory; the systems work together.

---

## 6. Interview Questions and Answers

**Q1. What is the AAA Framework?**

AAA stands for Authentication, Authorization, and Accounting. It is a security framework used to verify identities, control access to resources, and record user activity.

**Q2. What is the difference between authentication and authorization?**

Authentication verifies who the user is. Authorization determines what that user is permitted to access or do.

**Q3. What is accounting in AAA?**

Accounting records access sessions and activity for auditing, monitoring, troubleshooting, and security investigations.

**Q4. Which protocols are commonly used for AAA?**

RADIUS and TACACS+ are common AAA protocols in networking environments.

**Q5. What is the difference between RADIUS and TACACS+?**

RADIUS is commonly used for network access, such as VPN and Wi-Fi authentication. TACACS+ is commonly used for administrative access to network devices and supports granular command authorization.

**Q6. Is AAA the same as IAM?**

No. AAA focuses on authentication, authorization, and accounting. IAM covers the broader identity lifecycle, access management, and often identity governance.

**Q7. Can a user authenticate successfully but still be denied access?**

Yes. Authentication verifies identity, but authorization determines whether the requested resource or action is permitted.

---

## 7. Quick Revision Cheat Sheet

| Concept | Key question | Example |
|---|---|---|
| Authentication | Who are you? | Verify username, password, and MFA |
| Authorization | What can you do? | Permit access to approved servers |
| Accounting | What did you do? | Record VPN session duration |
| RADIUS | How can network access be controlled centrally? | Authenticate VPN users |
| TACACS+ | How can network administrators' actions be controlled? | Restrict commands on a switch |
| IAM | How are identities and access managed across their lifecycle? | Provision and remove employee access |

### The one-line answer to remember

**AAA verifies identity, controls permissions, and records activity.**

For your Cloud IAM learning path, the next useful step is to understand how AAA relates to **Zero Trust, RBAC, LDAP, RADIUS, and PAM**—particularly how they work together in an enterprise access-control architecture.
