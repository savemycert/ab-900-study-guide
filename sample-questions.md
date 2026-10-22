# AB-900 Sample Questions with Answers

20 worked practice questions for the **Microsoft 365 Certified: Copilot and Agent Administration Fundamentals (AB-900)** exam. Try each one before you open the answer.

For many more, with the same explanation on every option, use the [AB-900 practice questions](https://www.savemycert.com/practice/copilot-and-agent-administration-fundamentals/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide) on SaveMyCert.

## Question 1

*Identify the core features and objects of Microsoft 365 services*

**An admin created an account for a new employee in the Microsoft 365 admin center last week and configured nothing else. The employee can sign in but has no mailbox and cannot use Teams. What should the admin do?** Choose one.

- **a.** Assign the employee a Microsoft 365 license in the admin center
- **b.** Add the employee to the Members group of the company's SharePoint site
- **c.** Add the employee to a distribution group in the Exchange admin center
- **d.** Assign the employee the Exchange Administrator and Teams Administrator roles

<details>
<summary>Show answer and explanation</summary>

**Answer: a**

- **a** ✅ Services such as an Exchange Online mailbox and Teams are delivered through the service plans in a license. Assigning a license that includes them provisions the mailbox and turns on Teams.
- **b** ❌ Site membership grants access to that site's content. It doesn't give the user a mailbox or Teams.
- **c** ❌ A distribution group only delivers email to its members' existing mailboxes. It can't create a mailbox for an unlicensed account.
- **d** ❌ Admin roles let someone manage the Exchange and Teams services for others. They don't provision a mailbox or Teams access for the person who holds them; that comes from a license.

**The concept.** Access to Microsoft 365 services comes from the licenses assigned to a user. Each license contains service plans such as Exchange Online, SharePoint and Teams.

**Why this is correct.** An account without a license can exist and sign in, but no workload is provisioned for it, so there is no mailbox and no Teams access. Assigning a license that contains the Exchange Online and Teams service plans fixes both. Admin roles, distribution groups and SharePoint groups all control something else (admin rights, mail delivery and site access) and assume the user is already licensed.

**How to reason it out**

1. Notice that the account exists but nothing was assigned to it.
2. Recall that mailboxes and Teams access come from service plans in a license.
3. Reject options that grant admin rights, mail delivery or site access.
4. Choose assigning a license with the needed services.

> **Exam tip:** No license, no services: an account only gets a mailbox, Teams and the apps through the service plans in its license.

</details>

📖 Learn this topic: [AB-900 Core Objects: Microsoft 365 Licenses and the Exchange, SharePoint and Teams Admin Centers](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/microsoft-365-admin-centers-licenses-core-objects/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

---

## Question 2

*Identify the core features and objects of Microsoft 365 services*

**Every member of the Sales security group should receive Microsoft 365 E3 automatically when they join the group and lose it when they leave, with no per-user admin work. What should the admin do?** Choose one.

- **a.** Assign the E3 license to each Sales user from the Active users page of the admin center
- **b.** Assign the E3 license to the Sales group on the Licenses page of the admin center
- **c.** Add the Sales group to the Members group of the Sales team's SharePoint site
- **d.** Assign a Teams meeting policy to the Sales group with a group assignment ranking

<details>
<summary>Show answer and explanation</summary>

**Answer: b**

- **a** ❌ Direct assignment works, but the admin must license and unlicense every person by hand as people join and leave.
- **b** ✅ Group-based licensing assigns the license to the group. Members get it when they are added and lose it when they are removed, with no per-user work.
- **c** ❌ That grants edit access to one site. It doesn't license anyone for Microsoft 365 services.
- **d** ❌ Teams group policy assignment controls Teams behaviour. It doesn't assign Microsoft 365 licenses.

**The concept.** Group-based licensing assigns licenses to a security group, mail-enabled security group or Microsoft 365 group; membership then decides who holds the license.

**Why this is correct.** When the license is assigned to the Sales group, Microsoft Entra ID applies it to each member and removes it when the member leaves the group. That is exactly the automatic join/leave behaviour required. Assigning licenses user by user also works, but it fails the 'no per-user admin work' requirement. Teams policies and SharePoint groups don't license anything.

**How to reason it out**

1. Identify the requirement: licensing that follows group membership automatically.
2. Recall that licenses can be assigned to groups from the Licenses page.
3. Reject direct assignment because it needs per-user work.
4. Reject Teams policy and SharePoint group options because they don't license users.

> **Exam tip:** Assign licenses to a group when membership should decide who is licensed: join the group, get the license; leave it, lose it.

</details>

📖 Learn this topic: [AB-900 Core Objects: Microsoft 365 Licenses and the Exchange, SharePoint and Teams Admin Centers](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/microsoft-365-admin-centers-licenses-core-objects/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

---

## Question 3

*Identify the core features and objects of Microsoft 365 services*

**An admin assigned a Microsoft 365 license to the Employees group. Contractors are added only to a Contractors group, which is itself a member of Employees. Contractors report that they have no license. What should the admin do, with the least ongoing effort?** Choose one.

- **a.** Make Employees a member of the Contractors group so the license flows into Contractors
- **b.** Assign the license to each contractor individually from the Active users page
- **c.** Assign the same license directly to the Contractors group as a second group assignment
- **d.** Convert the Contractors group into a Microsoft 365 group and leave it nested in Employees

<details>
<summary>Show answer and explanation</summary>

**Answer: c**

- **a** ❌ Reversing the nesting doesn't help: Employees holds the license, and nested membership still isn't used by group-based licensing.
- **b** ❌ This licenses the current contractors, but every new contractor must be licensed by hand, which is more ongoing effort than licensing the group.
- **c** ✅ Group-based licensing reaches only direct members of the licensed group. Licensing the Contractors group itself covers its members, and the license still follows membership automatically.
- **d** ❌ The group type isn't the problem. Members of any nested group don't inherit the parent group's license assignment.

**The concept.** Group-based licensing applies the license only to users who are direct members of the licensed group. Members of a nested group are not licensed through the parent group.

**Why this is correct.** The contractors are members of Employees only through the nested Contractors group, so the Employees assignment never reaches them. Two facts decide the answer: nesting isn't followed, and a license can be assigned to more than one group. Licensing the Contractors group directly fixes the gap and keeps licensing automatic as contractors come and go. Licensing each contractor works too, but it creates per-user work for every new contractor. Changing the group type or reversing the nesting leaves the users in a nested group.

**How to reason it out**

1. Spot the nesting: contractors are only indirect members of the licensed group.
2. Recall that group-based licensing reaches direct members only.
3. Look for a fix that keeps licensing tied to membership.
4. Choose a second group assignment on the Contractors group over per-user assignment.

> **Exam tip:** Group-based licensing ignores nested groups: license the group the users are directly in.

</details>

📖 Learn this topic: [AB-900 Core Objects: Microsoft 365 Licenses and the Exchange, SharePoint and Teams Admin Centers](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/microsoft-365-admin-centers-licenses-core-objects/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

---

## Question 4

*Identify the core features and objects of Microsoft 365 services*

**A security architect says every access request should be checked against the user's identity, device health, location and the data requested, even when the request comes from inside the corporate network. Which Zero Trust principle is this?** Choose one.

- **a.** Use least privilege access
- **b.** Assume breach
- **c.** Defense in depth
- **d.** Verify explicitly

<details>
<summary>Show answer and explanation</summary>

**Answer: d**

- **a** ❌ Least privilege limits how much access is granted (just-in-time, just-enough). It does not describe checking each request against identity, device and location signals.
- **b** ❌ Assume breach is about limiting damage once an attacker is inside: segmentation, encryption and detection. The architect is describing how each request is checked.
- **c** ❌ Defense in depth is a general layering strategy, not one of the three Zero Trust principles Microsoft defines.
- **d** ✅ Verify explicitly means authenticating and authorizing every request using all available data points, with no trust granted for being on the internal network.

**The concept.** Zero Trust has three principles: verify explicitly, use least privilege access, and assume breach.

**Why this is correct.** Checking every request against identity, location, device health, the resource and anomalies is the definition of verify explicitly. Least privilege decides how much access to give, and assume breach limits damage after a compromise. Network location earns no trust on its own.

**How to reason it out**

1. Notice the action: each request is evaluated against several signals.
2. Recall which principle covers per-request evaluation.
3. Match it to verify explicitly.

> **Exam tip:** Verify explicitly: check every request on every available signal, inside or outside the network.

</details>

📖 Learn this topic: [AB-900 Microsoft 365 Security Principles: Zero Trust, Authentication, Authorization and Defender XDR](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/ab-900-zero-trust-microsoft-365-security-principles/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

---

## Question 5

*Identify the core features and objects of Microsoft 365 services*

**A 40-person company uses Microsoft 365 Business Basic, which includes only Microsoft Entra ID Free. It wants every user to register for and use multifactor authentication and wants legacy authentication blocked, without buying more licenses. What should the admin turn on?** Choose one.

- **a.** Risk-based policies from Microsoft Entra ID Protection
- **b.** A Conditional Access policy that requires MFA for each user
- **c.** Security defaults for the Microsoft Entra tenant
- **d.** Privileged Identity Management for admins

<details>
<summary>Show answer and explanation</summary>

**Answer: c**

- **a** ❌ Risk-based policies need Microsoft Entra ID P2 and only act on risky users or sign-ins; they do not require MFA for everyone or block legacy authentication.
- **b** ❌ Conditional Access could enforce MFA, but creating policies needs Microsoft Entra ID P1, which the company does not have and does not want to buy.
- **c** ✅ Security defaults are free in every tenant. They require all users to register for MFA, prompt for it when needed, protect admin roles and block legacy authentication.
- **d** ❌ PIM gives just-in-time access to admin roles and needs a P2 or ID Governance license. It does nothing for ordinary users' sign-ins.

**The concept.** Security defaults are a free, one-switch baseline of identity protections in Microsoft Entra ID.

**Why this is correct.** With only Entra ID Free, security defaults are the way to require MFA registration for all users and block legacy authentication. Conditional Access is the flexible alternative but needs P1; ID Protection and PIM need P2 or ID Governance and solve different problems.

**How to reason it out**

1. Note the licence: Entra ID Free, and no budget for more.
2. List what is required: MFA for everyone and no legacy authentication.
3. Rule out features that need P1 or P2.
4. Choose the free baseline that does both: security defaults.

> **Exam tip:** No premium licence? Security defaults give MFA for all and block legacy authentication for free.

</details>

📖 Learn this topic: [AB-900 Microsoft Entra ID Security Features: Conditional Access, SSO, PIM, Secure Score and Logs](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/ab-900-microsoft-entra-id-security-features/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

---

## Question 6

*Identify the core features and objects of Microsoft 365 services*

**All users have Microsoft 365 E3. The legal team must keep everything else in E3 but must not be able to use Microsoft Forms on any device or in the browser. Other departments keep Forms. What should the admin do?** Choose one.

- **a.** Remove the Microsoft 365 E3 license from the legal team
- **b.** Turn off Microsoft Forms in the legal team's E3 license assignment
- **c.** Turn off the Microsoft Forms service on the Org settings page for the tenant
- **d.** Block the Forms app for the legal team with a Teams app permission policy

<details>
<summary>Show answer and explanation</summary>

**Answer: b**

- **a** ❌ This removes Forms but also every other E3 service the legal team must keep, such as the mailbox and Teams.
- **b** ✅ Each license is made of service plans, and individual apps and services can be switched off for a user's or group's assignment. That removes Forms for legal only while all other E3 services stay.
- **c** ❌ Org settings apply to the whole organization. They can't remove Forms for one department while others keep it.
- **d** ❌ A Teams app permission policy only controls apps inside Teams. Legal could still open Forms in the browser.

**The concept.** A license is a bundle of service plans. Admins can turn individual apps and services on or off when they assign the license to a user or a group.

**Why this is correct.** The requirement has three parts: legal loses Forms everywhere, legal keeps everything else in E3, and other departments keep Forms. Turning off Forms in legal's license assignment meets all three. Removing E3 loses the other services. A Teams app permission policy only covers Teams. Org settings change the service for everyone.

**How to reason it out**

1. List the constraints: one service, one department, everywhere.
2. Recall that service plans inside a license can be switched off per assignment.
3. Reject removing the whole license and org-wide settings.
4. Reject the Teams-only control because Forms is also used in the browser.

> **Exam tip:** To remove one app but keep the rest of a license, turn that service off in the license assignment instead of removing the license.

</details>

📖 Learn this topic: [AB-900 Core Objects: Microsoft 365 Licenses and the Exchange, SharePoint and Teams Admin Centers](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/microsoft-365-admin-centers-licenses-core-objects/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

---

## Question 7

*Identify the core features and objects of Microsoft 365 services*

**A company segments access between departments, encrypts traffic end to end and uses analytics to spot unusual activity, planning on the basis that an attacker may already be inside. Which Zero Trust principle drives these measures?** Choose one.

- **a.** Use least privilege access
- **b.** Assume breach
- **c.** Verify explicitly
- **d.** Shared responsibility

<details>
<summary>Show answer and explanation</summary>

**Answer: b**

- **a** ❌ Least privilege limits each identity's rights. Segmentation, encryption and detection designed around an attacker already being inside belong to a different principle.
- **b** ✅ Assume breach means designing as if compromise has happened: minimize blast radius, segment access, encrypt end to end and use analytics to detect threats.
- **c** ❌ Verify explicitly is about evaluating each request's signals at sign-in and access time, not about containing an intruder who is already present.
- **d** ❌ Shared responsibility divides security duties between a cloud provider and its customer. It is not a Zero Trust principle.

**The concept.** Assume breach plans for compromise: limit how far an attacker can move and detect them quickly.

**Why this is correct.** Segmenting access, encrypting end to end and using analytics for detection are exactly the measures Microsoft lists under assume breach. They limit the blast radius of an intruder rather than deciding who gets in or how much access they hold.

**How to reason it out**

1. Identify the planning assumption: an attacker may already be inside.
2. List the measures: segmentation, encryption, detection.
3. These limit damage after compromise, so the principle is assume breach.

> **Exam tip:** Assume breach: minimize blast radius, segment, encrypt, and detect.

</details>

📖 Learn this topic: [AB-900 Microsoft 365 Security Principles: Zero Trust, Authentication, Authorization and Defender XDR](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/ab-900-zero-trust-microsoft-365-security-principles/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

---

## Question 8

*Understand data protection and governance tasks for Microsoft 365 and Copilot*

**A legal team wants contract drafts to stay protected so that only the legal department can open them, even after someone downloads a copy or emails it outside the company. Which Microsoft Purview feature should the admin use?** Choose one.

- **a.** Sensitivity labels that apply encryption to drafts
- **b.** A DLP policy that blocks sharing from the legal sites
- **c.** Retention labels that mark the drafts as legal records
- **d.** An Insider Risk Management policy for the legal team

<details>
<summary>Show answer and explanation</summary>

**Answer: a**

- **a** ✅ Encryption from a sensitivity label is stored with the file, so only the people the label authorizes can open it wherever the copy goes.
- **b** ❌ DLP can block or warn on sharing, but a copy that does get out isn't protected by it. The protection doesn't travel with the file.
- **c** ❌ A record label stops edits and deletion for a retention period. It doesn't control who can open a copy once it leaves the site.
- **d** ❌ Insider Risk Management detects risky activity patterns for investigation. It doesn't restrict who can open a document.

**The concept.** Sensitivity labels classify an item and can apply protection, such as encryption and content markings, that stays with the item.

**Why this is correct.** The requirement is protection that follows the file after it is downloaded or emailed. Encryption applied by a sensitivity label is embedded in the document, so access is checked whenever anyone tries to open it. DLP acts at the moment of sharing, retention labels govern how long items are kept, and Insider Risk Management only detects and scores risky behaviour.

**How to reason it out**

1. Note that protection must persist outside the original location.
2. Recall that label encryption is stored with the item itself.
3. Reject controls that act only at a location or only detect activity.
4. Choose a sensitivity label that applies encryption.

> **Exam tip:** Protection that travels with the file: sensitivity label with encryption.

</details>

📖 Learn this topic: [AB-900 Microsoft Purview and Copilot Data Security: Sensitivity Labels, DLP, Retention and Responsible AI](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/microsoft-purview-sensitivity-labels-copilot-data-security/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

---

## Question 9

*Understand data protection and governance tasks for Microsoft 365 and Copilot*

**When users create a team for a confidential project, they pick a classification and the new team and its SharePoint site become private, with guest access blocked. No admin configures each site by hand. Which feature provides this?** Choose one.

- **a.** Retention labels published to the SharePoint sites
- **b.** DLP policies scoped to Teams chat and channel messages
- **c.** Sensitivity labels configured for groups and sites
- **d.** Retention policies scoped to Microsoft 365 groups

<details>
<summary>Show answer and explanation</summary>

**Answer: c**

- **a** ❌ Retention labels apply retain/delete settings to individual items. They have no effect on team privacy or guests.
- **b** ❌ DLP inspects messages and files for sensitive data. It doesn't set a team's privacy or who can be invited.
- **c** ✅ Labels configured for groups and sites set container settings such as privacy and external user access when the label is chosen.
- **d** ❌ Retention policies decide how long group content is kept or when it is deleted. They don't set privacy or guest access.

**The concept.** Sensitivity labels can be configured for containers (Microsoft 365 groups, Teams and SharePoint sites) as well as for files and emails.

**Why this is correct.** A container label applies settings such as public/private privacy and whether guests can be added the moment the user selects it when creating the team. The label on the container does not label the files inside it. Retention policies and labels govern keeping and deleting content, and DLP inspects content for sensitive data.

**How to reason it out**

1. Spot that the settings apply to the team and site, not to files.
2. Recall that sensitivity labels can be scoped to groups and sites.
3. Rule out retention and DLP, which don't set privacy or guest access.
4. Choose sensitivity labels for groups and sites.

> **Exam tip:** Sensitivity labels also protect containers: privacy and guest access for teams, groups and sites.

</details>

📖 Learn this topic: [AB-900 Microsoft Purview and Copilot Data Security: Sensitivity Labels, DLP, Retention and Responsible AI](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/microsoft-purview-sensitivity-labels-copilot-data-security/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

---

## Question 10

*Understand data protection and governance tasks for Microsoft 365 and Copilot*

**Thousands of existing files in SharePoint contain passport numbers. Nobody plans to open or edit them, but the compliance team wants them labeled Confidential. What should the admin configure?** Choose one.

- **a.** A default sensitivity label in the label policy
- **b.** Mandatory labeling in the label policy for SharePoint site members
- **c.** Auto-labeling settings on the Confidential label for Office apps
- **d.** An auto-labeling policy for SharePoint and OneDrive sites

<details>
<summary>Show answer and explanation</summary>

**Answer: d**

- **a** ❌ A default label is applied to new or unlabeled documents that users create or edit. Untouched files keep no label.
- **b** ❌ Mandatory labeling forces users to pick a label when they save in an Office app. It does nothing for files no one is editing, whichever users the policy is published to.
- **c** ❌ Client-side auto-labeling runs in the Office app while a user edits the file, so files nobody opens are never labeled.
- **d** ✅ A service-side auto-labeling policy scans content at rest and labels matching files without any user opening them.

**The concept.** Sensitivity labels can be applied manually, by default, by required (mandatory) labeling, by client-side auto-labeling in Office apps, or by service-side auto-labeling policies.

**Why this is correct.** The deciding detail is that nobody will open the files. Every client-side option (auto-labeling in the label for Office apps, default labels, mandatory labeling) only acts when a user creates, edits or saves a document. A service-side auto-labeling policy runs in SharePoint and OneDrive (and Exchange for mail in transit), finds content that matches sensitive information types and applies the label without user involvement.

**How to reason it out**

1. Notice the files are at rest and won't be edited.
2. Separate client-side methods (need a user in the app) from service-side policies.
3. Match the requirement to service-side auto-labeling for SharePoint and OneDrive.

> **Exam tip:** Files at rest that nobody opens need a service-side auto-labeling policy.

</details>

📖 Learn this topic: [AB-900 Microsoft Purview and Copilot Data Security: Sensitivity Labels, DLP, Retention and Responsible AI](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/microsoft-purview-sensitivity-labels-copilot-data-security/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

---

## Question 11

*Understand data protection and governance tasks for Microsoft 365 and Copilot*

**A risk officer wants a percentage score that shows progress toward GDPR and ISO 27001 requirements across Microsoft 365, with recommended steps that can be assigned to staff and backed by uploaded evidence. Which tool should the admin open?** Choose one.

- **a.** Microsoft Purview Compliance Manager
- **b.** SharePoint data access governance reports
- **c.** Microsoft Purview DSPM for AI reports
- **d.** Microsoft Defender XDR Secure Score

<details>
<summary>Show answer and explanation</summary>

**Answer: a**

- **a** ✅ Compliance Manager scores progress against regulatory templates and lists improvement actions that can be assigned to owners, tested and supported with evidence files.
- **b** ❌ Data access governance reports show oversharing in SharePoint and OneDrive sites. They don't measure regulatory compliance.
- **c** ❌ DSPM for AI reports on AI use and sensitive data in AI interactions. It doesn't track progress against regulatory controls.
- **d** ❌ Secure Score measures security configuration against Microsoft's recommendations. It isn't organised around regulations such as GDPR, and it has no evidence store for auditors.

**The concept.** Compliance Manager measures how well an organization meets regulations and standards, using assessments, a compliance score and improvement actions.

**Why this is correct.** The requirement combines three things: a score, a mapping to named regulations, and assignable recommended actions with evidence. Compliance Manager provides all three through assessments built from regulatory templates and improvement actions. Secure Score is the tempting near-twin, but it scores security posture rather than regulatory controls.

**How to reason it out**

1. Notice the request is about named regulations, not security settings.
2. Recall which tool builds assessments from regulatory templates.
3. Confirm it supports assigning actions and storing evidence.
4. Choose Compliance Manager.

> **Exam tip:** Regulations, score and improvement actions: Compliance Manager.

</details>

📖 Learn this topic: [AB-900 Data Protection Risks and SharePoint Oversharing: Purview Explorers, Alerts, DSPM for AI and SharePoint Advanced Management](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/ab-900-data-protection-risks-sharepoint-oversharing/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

---

## Question 12

*Understand data protection and governance tasks for Microsoft 365 and Copilot*

**A compliance admin wants Microsoft Purview to find credit card numbers in emails and documents by using a definition Microsoft already provides, without supplying any sample files. What should the admin use?** Choose one.

- **a.** A pretrained trainable classifier
- **b.** An exact data match classifier
- **c.** A document fingerprint from a form
- **d.** A sensitive information type

<details>
<summary>Show answer and explanation</summary>

**Answer: d**

- **a** ❌ Trainable classifiers recognise kinds of documents, such as resumes, rather than a specific number format like a card number.
- **b** ❌ Exact data match needs you to upload your own table of values. The stem asks for something already provided.
- **c** ❌ Fingerprinting matches documents based on a form or template you supply, not individual card numbers.
- **d** ✅ Microsoft provides built-in sensitive information types, such as Credit Card Number, that match patterns, checksums and supporting keywords.

**The concept.** Data classification in Purview identifies sensitive items with sensitive information types (SITs), trainable classifiers and exact data match.

**Why this is correct.** Credit card numbers have a well-defined structure (format and checksum), which is exactly what a sensitive information type describes, and Microsoft ships one ready to use. Trainable classifiers are for categories of documents, exact data match compares against values you upload, and fingerprinting matches a template document.

**How to reason it out**

1. Identify what is being detected: a structured number.
2. Recall that SITs detect patterns with checksums and keywords.
3. Reject methods that need your own data or describe whole document types.

> **Exam tip:** Structured identifiers such as card or passport numbers: use a sensitive information type.

</details>

📖 Learn this topic: [AB-900 Microsoft Purview and Copilot Data Security: Sensitivity Labels, DLP, Retention and Responsible AI](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/microsoft-purview-sensitivity-labels-copilot-data-security/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

---

## Question 13

*Understand data protection and governance tasks for Microsoft 365 and Copilot*

**A compliance admin opens the Improvement actions page in Compliance Manager for the first time. Under the shared responsibility model that Compliance Manager uses, which actions does this page list?** Choose one.

- **a.** Actions that Microsoft completes for its own cloud services
- **b.** Actions that DLP and insider risk alerts have asked admins to take
- **c.** Actions that your organization is responsible for completing
- **d.** Actions that both parties complete, with Microsoft testing them

<details>
<summary>Show answer and explanation</summary>

**Answer: c**

- **a** ❌ Microsoft's share of the controls is handled and tested by Microsoft. Those actions aren't the ones on your Improvement actions page.
- **b** ❌ Alerts are handled in their own queues. Improvement actions are recommended configuration and process steps, not alert follow-ups.
- **c** ✅ The Improvement actions page lists the actions your organization is responsible for; each can be assigned, implemented, tested and backed by evidence.
- **d** ❌ Compliance Manager doesn't split each action this way. Your actions are tested manually by you or automatically through signals from your tenant.

**The concept.** Compliance Manager works on a shared responsibility model: Microsoft completes some actions for its cloud services, and the Improvement actions page lists the ones your organization is responsible for.

**Why this is correct.** Meeting a regulation in Microsoft 365 is shared work. Microsoft implements and tests the controls for its own services, and the customer is responsible for the rest. The Improvement actions page lists the customer's share, with points toward the compliance score, an owner, implementation and test status, and an Evidence tab. Microsoft's own actions aren't listed there, and DLP or insider risk alerts are a different workflow.

**How to reason it out**

1. Recall that Compliance Manager uses a shared responsibility model.
2. Separate Microsoft's share from the customer's share.
3. Recall which share the Improvement actions page tracks.
4. Choose the actions your organization is responsible for.

> **Exam tip:** Improvement actions = your organization's share of the controls, each worth points toward the compliance score.

</details>

📖 Learn this topic: [AB-900 Data Protection Risks and SharePoint Oversharing: Purview Explorers, Alerts, DSPM for AI and SharePoint Advanced Management](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/ab-900-data-protection-risks-sharepoint-oversharing/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

---

## Question 14

*Understand data protection and governance tasks for Microsoft 365 and Copilot*

**A company wants Microsoft Purview to find resumes and source code wherever they're stored. These files don't contain any consistent number pattern or keyword list. Which classification method fits best?** Choose one.

- **a.** Custom sensitive information types with keyword lists
- **b.** Document fingerprinting from a standard form
- **c.** Built-in trainable classifiers for those categories
- **d.** Exact data match with a table of known values

<details>
<summary>Show answer and explanation</summary>

**Answer: c**

- **a** ❌ Keyword-based SITs need consistent terms or patterns, which the stem says these files don't have.
- **b** ❌ Fingerprinting matches documents created from a template form. Resumes and code don't come from one template.
- **c** ✅ Trainable classifiers recognise a kind of document by what it looks like overall, and Microsoft provides ready-made ones such as resumes and source code.
- **d** ❌ Exact data match compares content with values from your own table, such as customer IDs. Resumes don't share such values.

**The concept.** Trainable classifiers use machine learning to recognise categories of content rather than specific patterns.

**Why this is correct.** When the content is identified by what it is, not by a number pattern, a trainable classifier is the right tool. Microsoft ships pre-trained classifiers for categories such as resumes and source code, and you can train your own from samples. SITs need patterns or keywords, exact data match needs a table of values, and fingerprinting needs a template.

**How to reason it out**

1. Note that there is no pattern or keyword to match.
2. Recall that trainable classifiers recognise document categories.
3. Choose the pre-trained classifiers for resumes and source code.

> **Exam tip:** Recognise a kind of document (resume, contract, source code): trainable classifier.

</details>

📖 Learn this topic: [AB-900 Microsoft Purview and Copilot Data Security: Sensitivity Labels, DLP, Retention and Responsible AI](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/microsoft-purview-sensitivity-labels-copilot-data-security/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

---

## Question 15

*Understand data protection and governance tasks for Microsoft 365 and Copilot*

**Before rolling out Microsoft 365 Copilot, an admin needs to see which SharePoint sites, OneDrive accounts and mailboxes hold items already classified as containing credit card numbers, and drill down to each item. Which Microsoft Purview tool fits?** Choose one.

- **a.** Data explorer in Information Protection
- **b.** The DLP alerts page in the Purview portal
- **c.** Activity explorer in Information Protection
- **d.** Improvement actions in Compliance Manager

<details>
<summary>Show answer and explanation</summary>

**Answer: a**

- **a** ✅ Data explorer shows a current snapshot of items with sensitive information types, sensitivity labels, retention labels or trainable classifier matches, by location down to the item.
- **b** ❌ DLP alerts appear only when a policy rule matches an action. Items that nobody has shared or sent don't show up there.
- **c** ❌ Activity explorer lists actions taken on content, such as labels applied or DLP matches. It isn't an inventory of where classified items are stored.
- **d** ❌ Improvement actions are recommended configuration steps. They don't list the files and emails that contain sensitive data.

**The concept.** Data explorer (formerly content explorer) shows where classified content is stored: items that match sensitive information types, sensitivity labels, retention labels or trainable classifiers.

**Why this is correct.** The admin wants an inventory of where already-classified sensitive data sits, with the ability to drill into locations and items. That is Data explorer's job. Activity explorer records what people did with content over time, and DLP alerts only appear when a rule matches an action, so neither gives a full inventory.

**How to reason it out**

1. Spot that the request is about where data is stored, not about actions.
2. Recall which explorer shows a snapshot of classified items.
3. Rule out tools that react to events.
4. Choose Data explorer.

> **Exam tip:** Where is my sensitive data? Data explorer. What did people do with it? Activity explorer.

</details>

📖 Learn this topic: [AB-900 Data Protection Risks and SharePoint Oversharing: Purview Explorers, Alerts, DSPM for AI and SharePoint Advanced Management](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/ab-900-data-protection-risks-sharepoint-oversharing/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

---

## Question 16

*Perform basic administrative tasks for Copilot and agents*

**A company has Microsoft 365 E3 and no Copilot add-on licenses. In Copilot Chat on the web, outside Outlook, a user asks for a summary of what her manager emailed her about the budget this week, and the answer ignores her mailbox. What explains this?** Choose one.

- **a.** The Allow web search in Copilot policy is off, which also stops mailbox lookups
- **b.** Semantic indexing has not finished processing the users’ mailboxes yet
- **c.** Restricted Content Discovery is hiding mailbox content from Copilot responses
- **d.** Without a Microsoft 365 Copilot license, her mailbox isn’t used from there

<details>
<summary>Show answer and explanation</summary>

**Answer: d**

- **a** ❌ That policy controls web grounding only. Turning it on or off has no effect on whether Copilot reads the mailbox.
- **b** ❌ Indexing delay could slow results for a licensed user, but an unlicensed Copilot Chat user has no Graph grounding to wait for.
- **c** ❌ Restricted Content Discovery applies to SharePoint sites, not Exchange mailboxes, and nothing in the scenario says it is configured.
- **d** ✅ Outside Outlook, Copilot Chat included with Microsoft 365 answers from the web and from content the user supplies. It doesn’t reach into her mail, files or meetings through Microsoft Graph on its own.

**The concept.** Copilot Chat (included with eligible Microsoft 365 subscriptions) is grounded in web data; the Microsoft 365 Copilot license adds broad grounding in work data through Microsoft Graph. Copilot Chat inside Outlook is the exception: it can use the user’s own inbox and calendar without the add-on.

**Why this is correct.** Without the add-on license, Copilot Chat uses organizational content only when the user uploads or pastes it, when it runs inside Outlook (which grounds it in her own inbox and calendar), or through a pay-as-you-go agent. She asked on the web, outside Outlook, so her mailbox isn’t searched. The web search policy, indexing and Restricted Content Discovery are all real controls, but none of them explains an unlicensed user getting no mailbox grounding there.

**How to reason it out**

1. Note that the tenant has no Copilot add-on licenses.
2. Note where she asked: Copilot Chat on the web, not inside Outlook.
3. Recall what Copilot Chat is grounded in there without the license.
4. Check whether any distractor actually applies to Exchange mail, then conclude.

> **Exam tip:** No Copilot license: Copilot Chat answers from the web and what you give it, except inside Outlook, where it can see your own mail.

</details>

📖 Learn this topic: [AB-900 Copilot and Agent Features: Licensing vs Pay-As-You-Go, Admin Settings, Researcher and Analyst](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/ab-900-copilot-agent-features-researcher-analyst/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

---

## Question 17

*Perform basic administrative tasks for Copilot and agents*

**Sales managers want Copilot to answer questions that draw automatically on their own emails, meetings and files, without uploading anything, and to work inside Word, Excel and PowerPoint with full access. The tenant currently uses only the Copilot Chat included with Microsoft 365. What should the admin do?** Choose one.

- **a.** Assign Microsoft 365 Copilot licenses to the sales managers
- **b.** Connect a pay-as-you-go billing policy for the sales managers
- **c.** Turn on the Allow web search in Copilot policy for the sales managers
- **d.** Pin Copilot Chat in Teams and Outlook for the sales managers

<details>
<summary>Show answer and explanation</summary>

**Answer: a**

- **a** ✅ The license adds automatic grounding in mail, meetings and files through Microsoft Graph and the full, priority in-app Copilot experience.
- **b** ❌ Pay-as-you-go unlocks metered agents that use shared tenant content. It does not give each manager automatic grounding in their own mailbox and meetings across the apps.
- **c** ❌ That policy adds or removes public web content. It does not give access to the managers’ own work data.
- **d** ❌ Pinning makes Copilot Chat easier to find. It does not change what Copilot Chat is grounded in.

**The concept.** The Microsoft 365 Copilot add-on license turns on broad Microsoft Graph (Work IQ) grounding across mail, meetings, chats and files, plus the full Copilot experience in Word, Excel and PowerPoint. Without it, Copilot Chat has only limited grounding in the user’s own mail and calendar when used inside Outlook.

**Why this is correct.** The requirement is grounding across each manager’s own email, meetings and files plus full in-app Copilot in Word, Excel and PowerPoint. Only the add-on license provides that; unlicensed Copilot Chat users get mail and calendar grounding only inside Outlook, and no Copilot chat inside Word, Excel or PowerPoint. Pay-as-you-go is the tempting distractor because it also involves work data, but it bills for agents grounded in shared tenant content, not for the licensed Copilot experience. Pinning and web search change visibility and web grounding only.

**How to reason it out**

1. Identify the need: automatic grounding in personal work data.
2. Add the second need: the full Copilot experience in Office apps.
3. Recall what pay-as-you-go actually covers (metered agents).
4. Choose the per-user Copilot license.

> **Exam tip:** Personal work data grounding plus full in-app Copilot = Microsoft 365 Copilot license.

</details>

📖 Learn this topic: [AB-900 Copilot and Agent Features: Licensing vs Pay-As-You-Go, Admin Settings, Researcher and Analyst](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/ab-900-copilot-agent-features-researcher-analyst/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

---

## Question 18

*Perform basic administrative tasks for Copilot and agents*

**A company has bought Microsoft 365 Copilot licenses for 40 people in its finance department. Which admin center does the IT admin use to give those people the licenses?** Choose one.

- **a.** Microsoft 365 Apps admin center
- **b.** Microsoft 365 admin center
- **c.** Microsoft Purview portal
- **d.** Power Platform admin center

<details>
<summary>Show answer and explanation</summary>

**Answer: b**

- **a** ❌ This center manages Office app policies and update settings, such as cloud policies. It doesn’t assign licenses.
- **b** ✅ Copilot licenses are managed under Billing > Licenses (or from a user’s Licenses and apps tab) in the Microsoft 365 admin center, for individual users or groups.
- **c** ❌ Purview handles data security and compliance, such as sensitivity labels and audit. License assignment isn’t done there.
- **d** ❌ This center governs environments and Copilot Studio agents. It doesn’t assign Microsoft 365 Copilot user licenses.

**The concept.** Microsoft 365 Copilot is a per-user license that admins assign in the Microsoft 365 admin center, like any other Microsoft 365 license.

**Why this is correct.** In the Microsoft 365 admin center, Billing > Licenses > Microsoft Copilot lets an admin assign, remove and reassign licenses for users or groups, and Users > Active users shows who holds one. The other centers are real Copilot-related tools, but each manages something else: Copilot Studio environments, compliance controls, or app policies.

**How to reason it out**

1. Identify the task: giving users a purchased per-user license.
2. Recall where Microsoft 365 licenses are assigned.
3. Rule out centers that manage agents, compliance or app policies.
4. Choose the Microsoft 365 admin center.

> **Exam tip:** Buying and assigning Copilot licenses happens in the Microsoft 365 admin center.

</details>

📖 Learn this topic: [AB-900 Copilot and Agent Administration: Licenses, Pay-As-You-Go Billing, Usage Reports, Prompts and Agent Governance](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/ab-900-copilot-agent-admin-licenses-billing-monitoring/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

---

## Question 19

*Perform basic administrative tasks for Copilot and agents*

**A marketing team without Microsoft 365 Copilot licenses wants an agent in Copilot Chat that follows written instructions and answers only from the company’s public website. How is this agent’s use paid for?** Choose one.

- **a.** It needs each user to hold a Microsoft 365 Copilot license
- **b.** It is billed per message to a pay-as-you-go billing policy
- **c.** It needs a Copilot Studio capacity pack before anyone can use it
- **d.** It is available at no additional cost in Copilot Chat

<details>
<summary>Show answer and explanation</summary>

**Answer: d**

- **a** ❌ Licensed users get work-data agents included, but web-only agents are already available to unlicensed Copilot Chat users.
- **b** ❌ Metered billing applies to agents that use shared tenant data such as SharePoint content, not to web-only agents.
- **c** ❌ Prepaid capacity is one way to pay for metered agents. A web-only agent is not metered, so no capacity is needed.
- **d** ✅ Declarative agents grounded in instructions and public websites are included with Copilot Chat at no additional cost.

**The concept.** Copilot Chat agents are split into no-cost agents (instructions and public web) and metered agents (shared tenant data such as SharePoint or connector content).

**Why this is correct.** This agent only uses instructions and a public website, so it falls in the no-cost group and is available by default under the existing store settings. Pay-as-you-go billing, Copilot Studio capacity and Copilot licenses only matter once an agent reads organizational content.

**How to reason it out**

1. Identify the agent’s knowledge source: a public website.
2. Recall that web-only declarative agents are included with Copilot Chat.
3. Reject the options that apply only to work-data agents.
4. Conclude there is no additional charge.

> **Exam tip:** Web-only agent in Copilot Chat: free. Agent reading tenant data: metered.

</details>

📖 Learn this topic: [AB-900 Copilot and Agent Features: Licensing vs Pay-As-You-Go, Admin Settings, Researcher and Analyst](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/ab-900-copilot-agent-features-researcher-analyst/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

---

## Question 20

*Perform basic administrative tasks for Copilot and agents*

**Sales staff should get a Microsoft 365 Copilot license as soon as they are added to the Sales security group and lose it when they leave the group, without an admin acting on each change. What should the admin configure?** Choose one.

- **a.** Add the Sales group to Copilot Frontier in Copilot settings
- **b.** Assign the Copilot license to the Sales group itself
- **c.** Assign the Copilot license to each Sales user as they join
- **d.** Scope a pay-as-you-go billing policy to the Sales group

<details>
<summary>Show answer and explanation</summary>

**Answer: b**

- **a** ❌ Frontier controls early access to experimental features. It doesn’t assign or remove a Copilot license.
- **b** ✅ Licensing the group means members receive the license when added and lose it when removed, with no per-user admin step.
- **c** ❌ This works once, but someone must act on every join and leave, which the requirement rules out.
- **d** ❌ A billing policy pays for metered services such as agents for that group. It doesn’t give anyone a Copilot license.

**The concept.** Copilot licenses can be assigned to groups as well as to individual users; group membership then drives who holds a license.

**Why this is correct.** With group-based assignment, the license follows membership: adding someone to Sales licenses them and removing them frees the license. Assigning per user meets the need only with manual work on each change. A pay-as-you-go policy scoped to the group and the Frontier setting both target the same group, which makes them tempting, but neither one grants the per-user license.

**How to reason it out**

1. Note the requirement: the license follows group membership automatically.
2. Recall that licenses can be assigned to groups.
3. Check the group-scoped distractors: billing policy and Frontier don’t grant licenses.
4. Assign the license to the group.

> **Exam tip:** License follows membership: assign Copilot to a group when access should track who is in it.

</details>

📖 Learn this topic: [AB-900 Copilot and Agent Administration: Licenses, Pay-As-You-Go Billing, Usage Reports, Prompts and Agent Governance](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/ab-900-copilot-agent-admin-licenses-billing-monitoring/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

---

[← Back to the AB-900 study guide](README.md)
