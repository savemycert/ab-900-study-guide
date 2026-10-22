# AB-900 Study Guide: Microsoft 365 Certified: Copilot and Agent Administration Fundamentals

A free, open study guide for the **Microsoft 365 Certified: Copilot and Agent Administration Fundamentals (AB-900)** exam: revision notes for every domain, side-by-side comparisons of commonly confused services, a glossary, 20 worked sample questions, and the official syllabus as a checklist with a full free lesson for every topic.

Maintained by [SaveMyCert](https://www.savemycert.com/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide), where you can read every lesson free, [practice with explained questions](https://www.savemycert.com/practice/copilot-and-agent-administration-fundamentals/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide) and [take timed mock exams](https://www.savemycert.com/mocks/copilot-and-agent-administration-fundamentals/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide).

## Contents

- [Exam at a glance](#exam-at-a-glance)
- [Exam domains](#exam-domains)
- [What is in this repo](#what-is-in-this-repo)
- [Syllabus checklist](#syllabus-checklist)
  - [Domain 1: Identify the core features and objects of Microsoft 365 services](#domain-1-identify-the-core-features-and-objects-of-microsoft-365-services)
  - [Domain 2: Understand data protection and governance tasks for Microsoft 365 and Copilot](#domain-2-understand-data-protection-and-governance-tasks-for-microsoft-365-and-copilot)
  - [Domain 3: Perform basic administrative tasks for Copilot and agents](#domain-3-perform-basic-administrative-tasks-for-copilot-and-agents)
- [How to study for AB-900](#how-to-study-for-ab-900)
- [Sample questions](sample-questions.md)
- [Free resources](#free-resources)

## Exam at a glance

| | |
|---|---|
| Exam code | AB-900 |
| Level | Foundational |
| Questions | 40–60 |
| Time limit | 45 min |
| Passing score | 700 / 1000 |
| Format | Multiple choice & more |
| Exam fee |  (US; varies by country) |
| Valid for | Does not expire |

Exam details change. Always confirm them in the official [Study guide for Exam AB-900: Microsoft 365 Copilot and Agent Administration Fundamentals (Microsoft Learn)](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/ab-900) from Microsoft.

## Exam domains

| # | Domain | Weight | Topics |
|---|---|---|---|
| 1 | [Identify the core features and objects of Microsoft 365 services](#domain-1-identify-the-core-features-and-objects-of-microsoft-365-services) | 33% | 3 |
| 2 | [Understand data protection and governance tasks for Microsoft 365 and Copilot](#domain-2-understand-data-protection-and-governance-tasks-for-microsoft-365-and-copilot) | 38% | 2 |
| 3 | [Perform basic administrative tasks for Copilot and agents](#domain-3-perform-basic-administrative-tasks-for-copilot-and-agents) | 29% | 2 |

That is 3 domains and 7 topics. Spend your time in proportion to the weights: the heaviest domain decides more of your score than the lightest.

Microsoft publishes each weight as a range (for example 30–35%). The figures here fall within those ranges, adjusted to add up to 100%.

## What is in this repo

| File | What it gives you |
|---|---|
| [Domain 1 notes](notes/domain-1-identify-the-core-features-and-objects-of-microsoft-365-services.md) | Identify the core features and objects of Microsoft 365 services: condensed revision notes per topic |
| [Domain 2 notes](notes/domain-2-understand-data-protection-and-governance-tasks-for-microsoft-365-and-copilot.md) | Understand data protection and governance tasks for Microsoft 365 and Copilot: condensed revision notes per topic |
| [Domain 3 notes](notes/domain-3-perform-basic-administrative-tasks-for-copilot-and-agents.md) | Perform basic administrative tasks for Copilot and agents: condensed revision notes per topic |
| [Commonly confused services](comparisons.md) | Side-by-side tables of the services questions set against each other |
| [Glossary](glossary.md) | Every in-scope term and service in one sentence |
| [Sample questions](sample-questions.md) | 20 worked questions with answers and reasoning |
| [Exam-day guide](exam-day-guide.md) | Booking, testing options, scoring, results and retakes |

## Syllabus checklist

Tick each topic off once you can explain it without notes. The "Must know" facts are the ones questions turn on. Each lesson link goes to the complete, free lesson.

### Domain 1: Identify the core features and objects of Microsoft 365 services

**Weight: 33%.** Licensing and the Microsoft 365, Exchange, SharePoint and Teams admin centers, Zero Trust, authentication and authorization, Defender XDR, Microsoft Entra ID, conditional access, SSO, Identity Secure Score, audit logs, PIM and app registrations. Official weight range 30–35%.

📝 Revision notes: [Domain 1: Identify the core features and objects of Microsoft 365 services](notes/domain-1-identify-the-core-features-and-objects-of-microsoft-365-services.md)

- [ ] **Core Objects of Microsoft 365 Services**
  <br>"Identify the core objects of Microsoft 365 services": Explain how license types assigned to users and groups affect access to Microsoft 365 features; Explore the organization configurations by using the Microsoft 365 admin center (domain names and org settings); Identify the appropriate objects to configure by using the Exchange admin center (mailboxes and distribution groups); Identify the appropriate objects to configure by using the SharePoint admin center (sites, libraries, and folders); Identify the appropriate roles and permissions for sites in SharePoint in Microsoft 365; Identify the appropriate objects to configure by using the Teams admin center (teams, channels, and policies).
  - 📖 Lesson: [AB-900 Core Objects: Microsoft 365 Licenses and the Exchange, SharePoint and Teams Admin Centers](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/microsoft-365-admin-centers-licenses-core-objects/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)
  - Must know: An account with no license can sign in but has no mailbox, Teams or other services; licenses grant services, admin roles grant management rights.
  - Must know: Individual services inside a license can be turned off per assignment without removing the license; a usage location is required before direct assignment.
- [ ] **Microsoft 365 Security Principles**
  <br>"Understand the Microsoft 365 security principles": Explain the core Zero Trust principles; Understand authorization; Understand authentication methods; Understand threat protection and intelligence; Understand features and capabilities of Microsoft Defender XDR.
  - 📖 Lesson: [AB-900 Microsoft 365 Security Principles: Zero Trust, Authentication, Authorization and Defender XDR](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/ab-900-zero-trust-microsoft-365-security-principles/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)
  - Must know: Zero Trust: verify explicitly (check every request on every signal), use least privilege access (just-in-time, just-enough), assume breach (limit blast radius, segment, encrypt, detect).
  - Must know: Authentication proves who you are; authorization decides what you may do. Signed in but denied is an authorization result.
- [ ] **Core Security Features of Microsoft 365**
  <br>"Identify the core security features of Microsoft 365 services": Understand features and capabilities of Microsoft Entra ID; Understand conditional access policies; Understand the purpose and benefits of SSO; Identify the appropriate security object to use in an organization (users and groups); Identify the appropriate tools to troubleshoot common sign-in issues (multifactor authentication [MFA], conditional access, and risky sign-ins); Interpret Identity Secure Score in Microsoft Entra ID; Use the appropriate tools to review audit logs for user and admin activity; Identify the role of Privileged Identity Management (PIM) in an organization; Understand App registrations and Enterprise applications.
  - 📖 Lesson: [AB-900 Microsoft Entra ID Security Features: Conditional Access, SSO, PIM, Secure Score and Logs](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/ab-900-microsoft-entra-id-security-features/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)
  - Must know: Security defaults are the free, all-or-nothing baseline (MFA for everyone, legacy authentication blocked); Conditional Access is the flexible alternative and needs Entra ID P1.
  - Must know: Conditional Access: users, target resources and conditions decide whether a policy applies; grant controls block or require something; session controls limit the session afterwards.

### Domain 2: Understand data protection and governance tasks for Microsoft 365 and Copilot

**Weight: 38%.** Microsoft Purview (Information Protection, DLP, Insider Risk Management, Communication Compliance, DSPM for AI, Data Lifecycle Management), sensitivity labels, classification and retention, how Copilot accesses data through Microsoft Graph and permissions, responsible AI, and finding risks and oversharing. Official weight range 35–40%.

📝 Revision notes: [Domain 2: Understand data protection and governance tasks for Microsoft 365 and Copilot](notes/domain-2-understand-data-protection-and-governance-tasks-for-microsoft-365-and-copilot.md)

- [ ] **Microsoft Purview and Copilot Data Security**
  <br>"Understand Microsoft Purview": Understand features and capabilities of Microsoft Purview Information; Identify the use cases for sensitivity labels in Microsoft Purview; Understand data classification in Microsoft Purview; Understand retention. "Understand data security implications of Copilot": Understand how Copilot accesses data; Understand how Microsoft Graph influences Copilot responses; Understand how Copilot uses permissions and other controls in; Understand responsible AI principles.
  - 📖 Lesson: [AB-900 Microsoft Purview and Copilot Data Security: Sensitivity Labels, DLP, Retention and Responsible AI](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/microsoft-purview-sensitivity-labels-copilot-data-security/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)
  - Must know: DLP stops risky sharing in real time; Insider Risk Management correlates user activities (pseudonymized); Communication Compliance reviews message content; DSPM for AI shows AI usage and offers one-click policies; Data Lifecycle Management retains and deletes.
  - Must know: Sensitivity labels classify and protect: encryption travels with the file, markings add headers, footers and watermarks, and container labels set privacy, guest access and external sharing for teams, groups and sites.
- [ ] **Data Protection Risks and SharePoint Oversharing**
  <br>"Identify data protection and governance risks for Microsoft 365 and Copilot": Identify compliance risks and recommendations by using Microsoft; Identify sensitive information by using Microsoft Purview Data; Identify risks by using Insider Risk Management; Identify and respond to alerts generated by Microsoft Purview DLP; Identify policy violations generated by Communication Compliance; Identify user activities reported by Microsoft Purview activity explorer; Discover and manage AI activity by using DSPM for AI; Search for files and emails by using Content search in Microsoft. "Identify and monitor oversharing in SharePoint in Microsoft 365": Identify the tools to troubleshoot oversharing in an organization; Run a data access governance report in SharePoint; Understand features and capabilities of SharePoint Advanced.
  - 📖 Lesson: [AB-900 Data Protection Risks and SharePoint Oversharing: Purview Explorers, Alerts, DSPM for AI and SharePoint Advanced Management](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/ab-900-data-protection-risks-sharepoint-oversharing/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)
  - Must know: Compliance Manager tracks regulations: assessments from templates, improvement actions (your organization's share) with owners and evidence, and a compliance score. Secure Score measures security posture instead.
  - Must know: Data explorer is a snapshot of where classified items are; seeing items needs Data Explorer List viewer (list and locations) or Content viewer (contents).

### Domain 3: Perform basic administrative tasks for Copilot and agents

**Weight: 29%.** Copilot and agent capabilities, Researcher and Analyst, licensing vs pay-as-you-go, enabling features, assigning licenses, billing policies, usage and adoption reporting, prompts, and creating, approving, governing and monitoring agents. Official weight range 25–30%.

📝 Revision notes: [Domain 3: Perform basic administrative tasks for Copilot and agents](notes/domain-3-perform-basic-administrative-tasks-for-copilot-and-agents.md)

- [ ] **Copilot and Agent Features and Capabilities**
  <br>"Understand features and capabilities of Copilot and agents": Compare the built-in capabilities of Copilot and agents; Compare Copilot monthly license model to pay-as-you-go, including; Identify which Copilot features can be enabled or disabled; Identify use cases for Researcher; Identify use cases for Analyst; Identify use cases for custom agents.
  - 📖 Lesson: [AB-900 Copilot and Agent Features: Licensing vs Pay-As-You-Go, Admin Settings, Researcher and Analyst](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/ab-900-copilot-agent-features-researcher-analyst/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)
  - Must know: An agent is Copilot scoped to a job with its own instructions, knowledge and optional actions; it uses the same models and the asking user's permissions, never the creator's.
  - Must know: Copilot Chat included with Microsoft 365 is web-grounded; the Microsoft 365 Copilot license adds automatic Microsoft Graph grounding in the user's mail, meetings and files and full Copilot in the apps.
- [ ] **Copilot and Agent Administration**
  <br>"Perform basic administrative tasks for Copilot": Assign Copilot licenses; Monitor and manage Copilot pay-as-you-go billing policies; Monitor Copilot usage and adoption, including Copilot Analytics and the Microsoft 365 admin center; Manage prompts, including saving, sharing, scheduling, and deleting. "Perform basic administrative tasks for agents": Identify how to configure user access to agents; Create an agent; Understand approval process for agents; Monitor agents, including usage, operational insights, and agent lifecycle, by working with the Microsoft 365 admin center and the.
  - 📖 Lesson: [AB-900 Copilot and Agent Administration: Licenses, Pay-As-You-Go Billing, Usage Reports, Prompts and Agent Governance](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/ab-900-copilot-agent-admin-licenses-billing-monitoring/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)
  - Must know: Copilot licenses are assigned in the Microsoft 365 admin center (Billing > Licenses or a user's Licenses and apps); group-based assignment makes the license follow group membership.
  - Must know: License Administrator is the least-privileged role for assigning licenses; Billing Administrator buys and manages billing.

## How to study for AB-900

1. **Read the lesson for each topic** in the checklist above, starting with the heaviest domain. Every lesson is free on the [AB-900 revision notes](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide).
2. **Practice straight after reading.** Answer [AB-900 practice questions](https://www.savemycert.com/practice/copilot-and-agent-administration-fundamentals/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide) on the topic you just read. Each option comes with an explanation of why it is right or wrong.
3. **Review what you got wrong**, re-read that lesson section, and tick the topic off only when you get its questions right.
4. **Take a full-length [AB-900 mock exam](https://www.savemycert.com/mocks/copilot-and-agent-administration-fundamentals/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)** under the real time limit. Aim to pass mocks comfortably before you book.
5. **On the last day**, skim the [AB-900 cheat sheet](https://www.savemycert.com/cheat-sheet/copilot-and-agent-administration-fundamentals/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide) instead of starting anything new.

## Sample questions

[sample-questions.md](sample-questions.md) has 20 worked AB-900 questions with the answer, why each option is right or wrong, and the reasoning steps.

## Free resources

- [Study guide for Exam AB-900: Microsoft 365 Copilot and Agent Administration Fundamentals (Microsoft Learn)](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/ab-900): the official source (Microsoft)
- [AB-900 certification overview](https://www.savemycert.com/certifications/copilot-and-agent-administration-fundamentals/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)
- [AB-900 revision notes](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide): every lesson, free to read
- [AB-900 practice questions](https://www.savemycert.com/practice/copilot-and-agent-administration-fundamentals/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide): with an explanation on every option
- [AB-900 mock exams](https://www.savemycert.com/mocks/copilot-and-agent-administration-fundamentals/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide): full-length and timed
- [AB-900 cheat sheet](https://www.savemycert.com/cheat-sheet/copilot-and-agent-administration-fundamentals/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide): the key facts on one page
- [All certification study guides](https://github.com/savemycert/certification-study-guides)

## Contributing

Spotted an error or an out-of-date fact? [Open an issue](../../issues) with the topic and a link to the official source. See [CONTRIBUTING.md](CONTRIBUTING.md).

## License and disclaimer

This guide is licensed under [CC BY 4.0](LICENSE). You can reuse and adapt it, including commercially, as long as you credit **SaveMyCert** with a link to https://www.savemycert.com/.

This is an independent study resource. It is not affiliated with or endorsed by Microsoft. Microsoft 365 Certified: Copilot and Agent Administration Fundamentals and AB-900 are trademarks of their respective owner. Exam domains and weights are taken from the official exam guide linked above.
