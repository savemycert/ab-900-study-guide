# AB-900 Commonly Confused Services and Concepts

Side-by-side comparisons of the AB-900 services and ideas that exam questions most often set against each other. Each table ends with the one thing to remember.

- [Domain 1: Identify the core features and objects of Microsoft 365 services](#domain-1-identify-the-core-features-and-objects-of-microsoft-365-services)
- [Domain 2: Understand data protection and governance tasks for Microsoft 365 and Copilot](#domain-2-understand-data-protection-and-governance-tasks-for-microsoft-365-and-copilot)
- [Domain 3: Perform basic administrative tasks for Copilot and agents](#domain-3-perform-basic-administrative-tasks-for-copilot-and-agents)

## Domain 1: Identify the core features and objects of Microsoft 365 services

### Full Access vs Send As vs Send on Behalf

|                  | Full Access                           | Send As                                          | Send on Behalf                     |
| ---------------- | ------------------------------------- | ------------------------------------------------ | ---------------------------------- |
| Lets a person    | Open the mailbox and manage its items | Send mail as the mailbox address                 | Send mail on behalf of the mailbox |
| Recipients see   | Not applicable                        | Only the mailbox address                         | "Person on behalf of mailbox"      |
| Does not include | Sending from the mailbox              | Opening the mailbox                              | Opening the mailbox                |
| Exam cue         | "read and manage the shared inbox"    | "replies must look like they come from support@" | "recipients must see who wrote it" |

**Remember:** the three permissions combine rather than include each other. Working in the inbox is Full Access; sending is Send As or Send on Behalf, chosen by whether the writer's name should show.

### Distribution group vs dynamic distribution group vs mail-enabled security group vs Microsoft 365 group

|                    | Distribution group    | Dynamic distribution group                                  | Mail-enabled security group            | Microsoft 365 group                                   |
| ------------------ | --------------------- | ----------------------------------------------------------- | -------------------------------------- | ----------------------------------------------------- |
| Receives email     | Yes                   | Yes                                                         | Yes                                    | Yes, into a group inbox                               |
| Grants permissions | No                    | No                                                          | Yes                                    | Yes                                                   |
| Membership         | Static                | Calculated from attributes                                  | Static                                 | Static (dynamic is an Entra premium option)           |
| Extras             | None                  | No list to maintain                                         | None                                   | Calendar, SharePoint site, Planner, can become a team |
| Exam cue           | "simple mailing list" | "everyone in the Sydney office, kept current automatically" | "email them and give them site access" | "collaboration space"                                 |

**Remember:** distribution and dynamic distribution groups are mail-only. If the group must also be granted access, it has to be a mail-enabled security group or a Microsoft 365 group.

### Edit vs Contribute vs Read

|                                      | Edit (Members)            | Contribute                      | Read (Visitors) |
| ------------------------------------ | ------------------------- | ------------------------------- | --------------- |
| Add, edit, delete documents          | Yes                       | Yes                             | No              |
| Create or delete libraries and lists | Yes                       | No                              | No              |
| View and download                    | Yes                       | Yes                             | Yes             |
| Exam cue                             | "manage the site's lists" | "change content, not structure" | "view only"     |

**Remember:** Edit and Contribute differ only by Manage Lists. On a group-connected site, read-only people go in the Visitors group, because Microsoft 365 groups have no read-only role.

### Standard vs private vs shared channel

|                 | Standard                    | Private                     | Shared                                                                  |
| --------------- | --------------------------- | --------------------------- | ----------------------------------------------------------------------- |
| Who takes part  | Every team member and guest | A subset of team members    | Chosen people inside or outside the team, including other organizations |
| Outsiders need  | A guest account in the team | A guest account in the team | Only their own organization's account (B2B direct connect)              |
| Files stored in | The team's SharePoint site  | Its own channel site        | Its own channel site                                                    |
| Exam cue        | "the whole team"            | "only some team members"    | "partner joins one channel without becoming a guest"                    |

**Remember:** only a shared channel brings in people from another organization without a guest account.

### Archive vs delete a team

|            | Archive                       | Delete                                       |
| ---------- | ----------------------------- | -------------------------------------------- |
| Content    | Stays readable                | Removed with the team and its group          |
| Posting    | Blocked                       | Not applicable                               |
| Reversible | Unarchive at any time         | The group can be restored for a limited time |
| Exam cue   | "read-only, keep the history" | "remove the team"                            |

**Remember:** archive freezes a team; delete removes it.

### Direct vs group vs Global Teams policy assignment

|          | Direct assignment         | Group assignment                                           | Global (Org-wide default)               |
| -------- | ------------------------- | ---------------------------------------------------------- | --------------------------------------- |
| Priority | Always wins               | Applies if no direct assignment; rank 1 wins across groups | Applies if neither of the others exists |
| Scope    | One user                  | Group members                                              | Everyone else                           |
| Exam cue | "this user always gets X" | "two groups conflict"                                      | "change it for everyone"                |

**Remember:** direct beats group, group ranking only orders groups, and Global is the fallback. Each policy type is resolved separately.

### Verify explicitly vs least privilege vs assume breach

|          | Verify explicitly                          | Use least privilege access              | Assume breach                                 |
| -------- | ------------------------------------------ | --------------------------------------- | --------------------------------------------- |
| Question | Trust this request right now?              | How much access, for how long?          | If they're in, how do we limit damage?        |
| Examples | MFA and device compliance on every sign-in | Just-in-time roles, access that expires | Segmentation, encryption, detection analytics |
| Exam cue | "every request, all signals"               | "only for the hours needed"             | "limit blast radius"                          |

**Remember:** classify a control by its main purpose: checking a request, sizing access, or containing an intruder.

### MFA vs phishing-resistant MFA

|                                                | MFA with codes, SMS or push                | Phishing-resistant MFA                                                         |
| ---------------------------------------------- | ------------------------------------------ | ------------------------------------------------------------------------------ |
| Methods                                        | Authenticator push, OATH codes, SMS, voice | Windows Hello for Business, passkeys (FIDO2), certificate-based authentication |
| Stops password-only attacks                    | Yes                                        | Yes                                                                            |
| Stops relay (adversary-in-the-middle) phishing | No: codes and approvals can be relayed     | Yes: the credential is bound to the real site                                  |
| Exam cue                                       | "add a second factor"                      | "users were phished despite MFA"                                               |

**Remember:** factor categories make MFA; origin binding makes it phishing-resistant.

### Defender for Identity vs Entra ID Protection

|          | Defender for Identity                                            | Entra ID Protection                     |
| -------- | ---------------------------------------------------------------- | --------------------------------------- |
| Watches  | On-premises and hybrid identity: AD, AD FS, AD CS, Entra Connect | Cloud users and sign-ins in Entra ID    |
| Detects  | Credential theft and lateral movement on domain controllers      | Risky users and risky sign-ins          |
| Exam cue | "domain controllers"                                             | "leaked credentials", "atypical travel" |

**Remember:** on-premises identity servers belong to Defender for Identity; cloud sign-in risk belongs to Entra ID Protection.

### Automatic attack disruption vs AIR vs advanced hunting

|          | Automatic attack disruption               | AIR                                                  | Advanced hunting                   |
| -------- | ----------------------------------------- | ---------------------------------------------------- | ---------------------------------- |
| When     | During the attack, automatically          | After an alert                                       | When an analyst runs a query       |
| Does     | Contains compromised accounts and devices | Investigates and remediates; Action center tracks it | KQL over up to 30 days of raw data |
| Exam cue | "stop it spreading now, no analyst"       | "self-healing", "clean up affected assets"           | "proactively search"               |

**Remember:** disruption contains, AIR cleans up, hunting searches.

### Security defaults vs Conditional Access

|             | Security defaults                                     | Conditional Access                           |
| ----------- | ----------------------------------------------------- | -------------------------------------------- |
| License     | Free                                                  | Entra ID P1                                  |
| Flexibility | All-or-nothing, no exclusions or conditions           | Choose users, apps, locations, devices, risk |
| Covers      | MFA registration, MFA when needed, blocks legacy auth | Whatever the policies define                 |
| Together?   | Turned off when Conditional Access takes over         | Replaces security defaults                   |

**Remember:** no budget and no exceptions means security defaults; any condition or exclusion means Conditional Access.

### Report-only mode vs What If tool

|          | Report-only mode                           | What If                                   |
| -------- | ------------------------------------------ | ----------------------------------------- |
| Input    | Real sign-ins as they happen               | One hypothetical sign-in you describe     |
| Enforces | No                                         | No                                        |
| Shows    | Would-have-been result on each sign-in log | Which policies apply and why others don't |
| Exam cue | "measure impact over a week"               | "will this specific sign-in be blocked?"  |

**Remember:** report-only measures real traffic; What If simulates one case. What If ignores policies that are Off.

### App registrations vs Enterprise applications

|           | App registrations                                            | Enterprise applications                |
| --------- | ------------------------------------------------------------ | -------------------------------------- |
| Object    | Application object (global definition)                       | Service principal (local instance)     |
| Exists in | The app's home tenant only                                   | Every tenant that uses the app         |
| Configure | Client ID, secrets, redirect URIs, requested API permissions | Assignment, consent, SSO, provisioning |
| Exam cue  | "developer building an app"                                  | "control who can use a vendor's app"   |

**Remember:** you build an app in App registrations and govern any app, including another company's multitenant app, in Enterprise applications.

### Sign-in risk vs user risk

|                  | Sign-in risk                           | User risk                                           |
| ---------------- | -------------------------------------- | --------------------------------------------------- |
| Question         | Was this sign-in made by someone else? | Is the account compromised?                         |
| Examples         | Anonymous IP, atypical travel          | Leaked credentials                                  |
| Self-remediation | Require MFA                            | Require risk remediation or Require password change |

**Remember:** a risky sign-in is cleared by passing MFA; a risky user needs a secure password change (after MFA). A block policy needs an admin.

### Entra audit logs vs sign-in logs vs Purview Audit

|           | Entra audit logs                   | Entra sign-in logs                   | Purview Audit (Standard)                     |
| --------- | ---------------------------------- | ------------------------------------ | -------------------------------------------- |
| Records   | Directory changes                  | Authentication attempts and outcomes | User and admin activity across Microsoft 365 |
| Retention | 7 days Free, 30 days P1/P2         | 7 days Free, 30 days P1/P2           | 180 days                                     |
| Exam cue  | "who assigned this role last week" | "why did the sign-in fail"           | "several months ago, across workloads"       |

**Remember:** older than 30 days or spanning workloads means Purview Audit.

### PIM eligible vs active assignment

|                   | Eligible                                 | Active                          |
| ----------------- | ---------------------------------------- | ------------------------------- |
| Role held         | Only after activation                    | Immediately                     |
| Approval possible | Yes, plus MFA and justification          | No activation, so no approval   |
| Time-bound        | Can be                                   | Can be                          |
| Exam cue          | "must request and be approved each time" | "has the role until a set date" |

**Remember:** approval only exists on activation, so it needs an eligible assignment.

## Domain 2: Understand data protection and governance tasks for Microsoft 365 and Copilot

### DLP vs Insider Risk Management vs Communication Compliance

|          | DLP                                          | Insider Risk Management                           | Communication Compliance         |
| -------- | -------------------------------------------- | ------------------------------------------------- | -------------------------------- |
| Looks at | One action on one item                       | Sequences of user activity over time              | The content of messages          |
| Timing   | Real time, at the moment of sharing          | Over time, often around an HR signal              | After sending, through review    |
| Output   | Policy tip, block (optional override), alert | Risk scores, alerts, cases; users pseudonymized   | Matches in a queue for reviewers |
| Exam cue | "warn or block when they email card numbers" | "departing employee downloaded and copied to USB" | "harassment in Teams chats"      |

**Remember:** DLP judges an action, Insider Risk judges behaviour, Communication Compliance judges what is said.

### DSPM for AI vs Defender for Cloud Apps

|                  | DSPM for AI                                                  | Defender for Cloud Apps                            |
| ---------------- | ------------------------------------------------------------ | -------------------------------------------------- |
| Answers          | What data goes into AI apps                                  | Which AI and cloud apps are in use                 |
| Acts by          | Reports and one-click Purview policies                       | Tagging apps Sanctioned, Unsanctioned or Monitored |
| Can block an app | No (DLP policies it creates can stop pasting sensitive data) | Yes, Unsanctioned on Defender for Endpoint devices |
| Exam cue         | "sensitive data in prompts"                                  | "shadow AI apps"                                   |

**Remember:** DSPM for AI watches the data; Defender for Cloud Apps finds and blocks the app.

### Sensitivity label vs retention label

|          | Sensitivity label                                | Retention label                          |
| -------- | ------------------------------------------------ | ---------------------------------------- |
| Purpose  | Classify and protect                             | Keep for a period, then delete or review |
| Can do   | Encrypt, mark, set container privacy and sharing | Retain, delete, declare a record         |
| Solution | Information Protection                           | Data Lifecycle Management                |
| Per item | One                                              | One                                      |

**Remember:** an item can carry one of each because they do different jobs, and neither is a legal hold.

### Default vs mandatory vs client-side auto vs service-side auto labeling

|                           | Default label                     | Mandatory labeling          | Client-side auto-labeling                          | Service-side auto-labeling     |
| ------------------------- | --------------------------------- | --------------------------- | -------------------------------------------------- | ------------------------------ |
| Who chooses               | The policy                        | The user, when prompted     | The app, from content (or recommends)              | The service, from content      |
| Needs someone in the file | Yes                               | Yes                         | Yes                                                | No                             |
| Content-based             | No                                | No                          | Yes                                                | Yes                            |
| Exam cue                  | "label everything new as General" | "users must choose a label" | "suggest Confidential when a card number is typed" | "label existing files at rest" |

**Remember:** only a service-side policy labels files nobody opens, and for Exchange it only labels mail sent or received after it is turned on.

### Sensitive information type vs trainable classifier vs exact data match

|            | Sensitive information type      | Trainable classifier            | Exact data match                          |
| ---------- | ------------------------------- | ------------------------------- | ----------------------------------------- |
| Recognises | Patterns, checksums, keywords   | A kind of document              | Values in your own uploaded table         |
| Best for   | Card, passport, account numbers | Resumes, contracts, source code | Only real customers' or employees' values |
| Exam cue   | "detect a number format"        | "no consistent pattern"         | "too many false positives"                |

**Remember:** a stricter pattern still flags well-formed fakes; only EDM checks against your real records.

### Retention policy vs retention label

|            | Retention policy                             | Retention label                                    |
| ---------- | -------------------------------------------- | -------------------------------------------------- |
| Scope      | Whole locations                              | Individual items                                   |
| Applied by | Admin                                        | Users, library defaults, auto-apply                |
| Records    | No                                           | Yes                                                |
| Exam cue   | "keep everything in these sites for N years" | "invoices in the same site kept longer as records" |

**Remember:** location-wide rules are policies; item-level differences and records need labels.

### Preservation Hold library vs recycle bin

|            | Preservation Hold library                        | Recycle bin                  |
| ---------- | ------------------------------------------------ | ---------------------------- |
| Holds      | Copies of retained files users deleted or edited | Items users recently deleted |
| Duration   | Until the retention period ends                  | Short term                   |
| Visible to | Compliance tools, not users                      | Users and site owners        |

**Remember:** retained SharePoint and OneDrive content survives in the Preservation Hold library; mailbox items go to Recoverable Items.

### Copilot connector vs Power Platform connector

|             | Copilot connector                                       | Power Platform connector         |
| ----------- | ------------------------------------------------------- | -------------------------------- |
| Purpose     | Index external content into Microsoft Graph for Copilot | Let apps and flows call services |
| Permissions | Keeps the source's access lists                         | Not about grounding              |
| Exam cue    | "Copilot answers from our third-party wiki"             | "automate a workflow"            |

**Remember:** only a Copilot connector feeds Copilot grounding, and it keeps each item's permissions.

### Copilot DLP policy vs Restricted Content Discovery vs removing EXTRACT

|                   | DLP for the Copilot location              | Restricted Content Discovery                 | Label without EXTRACT         |
| ----------------- | ----------------------------------------- | -------------------------------------------- | ----------------------------- |
| Keys on           | Sensitivity labels (or prompt SITs)       | A whole SharePoint site                      | A label's usage rights        |
| Effect on Copilot | Labeled items not used in responses       | Site content not surfaced                    | No text returned, link only   |
| Effect on users   | None                                      | None; files still open directly              | Users also can't copy content |
| Exam cue          | "keep Highly Confidential out of Copilot" | "hide this unlabeled site while we clean up" | "stop copying as well"        |

**Remember:** DLP needs labels, Restricted Content Discovery works per site regardless of labels, and removing EXTRACT affects people too.

### Fairness vs inclusiveness and transparency vs accountability

|         | Fairness                        | Inclusiveness                         | Transparency                              | Accountability                      |
| ------- | ------------------------------- | ------------------------------------- | ----------------------------------------- | ----------------------------------- |
| About   | Unbiased outcomes               | Designing for everyone                | Understanding how it works and its limits | Who answers for outcomes            |
| Example | Equal promotion recommendations | Accessible interfaces, many languages | Citations, AI-may-be-wrong notices        | A named owner who can switch it off |

**Remember:** biased results break fairness; excluding people breaks inclusiveness; not explaining breaks transparency; nobody responsible breaks accountability.

### Data explorer vs activity explorer

|          | Data explorer                             | Activity explorer                                  |
| -------- | ----------------------------------------- | -------------------------------------------------- |
| Shows    | Where classified items are now            | What people did with labeled and sensitive content |
| Time     | Current snapshot                          | About the last 30 days, from the audit log         |
| Access   | List viewer or Content viewer role groups | Activity filters by user, label, location, date    |
| Exam cue | "inventory before Copilot rollout"        | "who removed labels this month"                    |

**Remember:** explorer of data = state; explorer of activity = history. Older history needs an audit log search.

### Compliance Manager vs Secure Score

|            | Compliance Manager                                                       | Secure Score                      |
| ---------- | ------------------------------------------------------------------------ | --------------------------------- |
| Measures   | Progress against regulations and standards                               | Security posture                  |
| Built from | Assessments from regulatory templates, improvement actions with evidence | Recommended security actions      |
| Exam cue   | "GDPR readiness score"                                                   | "how secure is our configuration" |

**Remember:** a named regulation points to Compliance Manager.

### Content search vs audit log search vs message trace

|          | Content search                         | Audit log search                | Message trace                 |
| -------- | -------------------------------------- | ------------------------------- | ----------------------------- |
| Returns  | The emails, chats and files themselves | Records of what people did      | Mail delivery path and status |
| Scope    | Mailboxes, SharePoint, OneDrive, Teams | Activities across Microsoft 365 | Exchange mail flow only       |
| Exam cue | "find and export the messages"         | "who shared the file"           | "was the email delivered"     |

**Remember:** content search finds content; audit finds actions; message trace follows delivery.

### Escalate vs Escalate for investigation

|          | Escalate                             | Escalate for investigation                              |
| -------- | ------------------------------------ | ------------------------------------------------------- |
| Does     | Routes the match to another reviewer | Creates an eDiscovery (Premium) case, user as custodian |
| Exam cue | "someone else should decide"         | "legal must preserve and investigate"                   |

**Remember:** only the "for investigation" action opens a legal case.

### Snapshot vs activity DAG reports

|          | Snapshot reports                                                     | Activity reports                        |
| -------- | -------------------------------------------------------------------- | --------------------------------------- |
| Describe | Current permissions, however old                                     | New sharing in the last 28 days         |
| Examples | Site permissions across your organization, for users, labels applied | Sharing links, content shared with EEEU |
| Exam cue | "access granted years ago"                                           | "new risky sharing this month"          |

**Remember:** start with snapshots for a baseline; activity reports can't see old grants.

### Default vs custom data risk assessment

|          | Default                           | Custom                       |
| -------- | --------------------------------- | ---------------------------- |
| Scope    | Top 100 SharePoint sites by usage | Sites or users you choose    |
| Runs     | Weekly, automatically             | When you create it           |
| Exam cue | "no setup"                        | "a quiet but sensitive site" |

**Remember:** low-traffic sites can fall outside the default, so scope a custom assessment to them.

### Restricted access control vs Restricted Content Discovery

|          | Restricted access control                               | Restricted Content Discovery                  |
| -------- | ------------------------------------------------------- | --------------------------------------------- |
| Changes  | Who can open the site or OneDrive                       | What Copilot and org-wide search surface      |
| Rule     | Member of up to 10 chosen groups **and** has permission | Permissions unchanged                         |
| OneDrive | Yes                                                     | No, sites only                                |
| Copilot  | Honours the restriction                                 | Stops surfacing the site to anyone            |
| Exam cue | "only Legal may ever open this site"                    | "hide this site from Copilot while we fix it" |

**Remember:** restricted access control locks the door; Restricted Content Discovery takes the sign off the door.

### SharePoint site access review vs Entra ID access review

|             | SharePoint site access review                    | Entra ID access review            |
| ----------- | ------------------------------------------------ | --------------------------------- |
| Starts from | A DAG report finding                             | Identity Governance               |
| Reviewers   | The site's owners                                | Can be users' managers and others |
| Covers      | One SharePoint site's permissions (not OneDrive) | Group membership and app access   |

**Remember:** a site access review always goes to site owners and never changes anything automatically.

## Domain 3: Perform basic administrative tasks for Copilot and agents

### Copilot vs an agent

|              | Copilot                   | An agent                             |
| ------------ | ------------------------- | ------------------------------------ |
| Scope        | Any task                  | One repeated job                     |
| Instructions | The user's prompt         | Saved instructions plus the prompt   |
| Knowledge    | Set by the user's license | Sources the maker chose              |
| Permissions  | The user's                | The asking user's, never the maker's |

**Remember:** an agent is Copilot with saved instructions, scoped knowledge and optional actions. It never widens anyone's access.

### Copilot Chat vs Microsoft 365 Copilot license

|                        | Copilot Chat (included)                                                      | Microsoft 365 Copilot (add-on)                           |
| ---------------------- | ---------------------------------------------------------------------------- | -------------------------------------------------------- |
| Grounding              | Web, plus uploaded or pasted content (own inbox and calendar inside Outlook) | Web plus automatic Microsoft Graph work data             |
| In-app Copilot         | No full in-app experience                                                    | Word, Excel, PowerPoint, Teams meetings, priority access |
| Researcher and Analyst | No                                                                           | Yes                                                      |
| Exam cue               | "no extra cost"                                                              | "summarize my meetings and mail automatically"           |

**Remember:** the deciding factor is what each tier can reach. Automatic work-data grounding needs the license.

### Monthly license vs pay-as-you-go

|           | License                    | Pay-as-you-go                                          |
| --------- | -------------------------- | ------------------------------------------------------ |
| Charge    | Fixed per user per month   | Per use, through Azure meters                          |
| Billed to | Microsoft 365 subscription | Azure subscription via a billing policy                |
| Unlocks   | Full licensed experience   | Metered agents only                                    |
| Fits      | Heavy daily users          | Occasional users, light use at scale, measuring demand |

**Remember:** pay-as-you-go pays for metered agent use, never for Copilot inside Word or Teams.

### Free vs metered agents (unlicensed users)

|            | Instructions or public web only | Shared tenant data (SharePoint, connectors)        |
| ---------- | ------------------------------- | -------------------------------------------------- |
| Cost       | No extra cost                   | Metered                                            |
| Default    | Available                       | Off until pay-as-you-go or Copilot Studio capacity |
| Built with | Any tool                        | Any tool                                           |

**Remember:** the knowledge source decides metering, not the builder.

### Researcher vs Analyst vs standard Copilot

|          | Standard Copilot           | Researcher                               | Analyst                                                  |
| -------- | -------------------------- | ---------------------------------------- | -------------------------------------------------------- |
| Best for | Quick summaries and drafts | Deep, multi-step research                | Raw data across several files                            |
| Output   | Fast answer                | Structured report with citations         | Forecasts, trends, outliers, charts, visible Python code |
| Speed    | Fast                       | Deliberately slower                      | Runs code                                                |
| Exam cue | "two-line reply"           | "cited briefing from news and our plans" | "retention table from a year of exports"                 |

**Remember:** citations and many sources point to Researcher; spreadsheets and code point to Analyst.

### SharePoint agent vs Agent Builder vs Copilot Studio

|                   | SharePoint agent                 | Agent Builder                           | Copilot Studio                                |
| ----------------- | -------------------------------- | --------------------------------------- | --------------------------------------------- |
| For               | Q&A over one site                | Lightweight Q&A for you or a small team | Organization-wide and complex agents          |
| Workflows/actions | No                               | No multi-step workflows                 | Yes, including approvals and external systems |
| Exam cue          | "answer about this project site" | "brand guidelines assistant"            | "check payroll and route leave for approval"  |

**Remember:** anything with actions, approvals or external systems needs Copilot Studio.

### Copilot Frontier vs Targeted release

|         | Copilot Frontier             | Targeted release                        |
| ------- | ---------------------------- | --------------------------------------- |
| Governs | Preview Copilot features     | Microsoft 365 updates in general        |
| Default | No access                    | Set in Org settings release preferences |
| Scope   | All users or specific groups | Release preferences for the tenant      |

**Remember:** preview Copilot features are controlled only by Copilot Frontier.

### Allow vs Allow trials only vs Do not allow (self-service purchases)

|     | Allow | Allow trials only                     | Do not allow |
| --- | ----- | ------------------------------------- | ------------ |
| Try | Yes   | Yes                                   | No           |
| Buy | Yes   | No; the trial doesn't convert to paid | No           |

**Remember:** "let users try but never pay" is Allow trials only.

### Copilot in Teams meetings policy values

|                                             | Default for organizer   | Enforced? |
| ------------------------------------------- | ----------------------- | --------- |
| On                                          | During the meeting only | No        |
| On with saved transcript required (default) | During and after        | Yes       |
| On with transcript saved by default         | During and after        | No        |
| Off                                         | Off                     | No        |

**Remember:** only "saved transcript required" is enforced. Off can be overridden by the organizer.

### License Administrator vs Billing Administrator

|          | License Administrator              | Billing Administrator                                          |
| -------- | ---------------------------------- | -------------------------------------------------------------- |
| Does     | Assigns, removes, updates licenses | Buys, manages subscriptions and billing, sets up pay-as-you-go |
| Exam cue | "assign Copilot to the sales team" | "purchase more seats", "create a billing policy"               |

**Remember:** assign = License Administrator; buy = Billing Administrator.

### Microsoft 365 role vs Azure role for a billing policy

|            | Microsoft 365 role                                              | Azure role                                                  |
| ---------- | --------------------------------------------------------------- | ----------------------------------------------------------- |
| Which      | Billing Administrator, AI Administrator or Global Administrator | Owner or Contributor on the subscription and resource group |
| Granted in | Microsoft Entra ID                                              | Azure RBAC                                                  |

**Remember:** a billing policy needs both layers; neither implies the other.

### Budget alert vs spending cap

|              | Billing policy budget                   | Actually limiting spend                      |
| ------------ | --------------------------------------- | -------------------------------------------- |
| Effect       | Emails recipients at chosen percentages | Scope the policy to a group or disconnect it |
| Usage stops? | No                                      | Yes, for those outside scope or the service  |

**Remember:** budgets notify; they never stop usage.

### Usage report vs readiness report vs Copilot Dashboard

|          | Copilot usage report            | Copilot readiness report     | Copilot Dashboard (Viva Insights)          |
| -------- | ------------------------------- | ---------------------------- | ------------------------------------------ |
| Audience | IT admins                       | IT admins                    | Leaders and managers                       |
| Shows    | Enabled vs active users, by app | Who should get licenses next | Readiness, adoption, impact, sentiment     |
| Access   | Admin center (Reports Reader)   | Admin center                 | Automatic for senior leaders, or delegated |

**Remember:** leaders without admin access use the Copilot Dashboard.

### Enabled vs active user

|                          | Enabled                 | Active                                       |
| ------------------------ | ----------------------- | -------------------------------------------- |
| Means                    | Holds a Copilot license | Took an intentional action, such as a prompt |
| Opening the pane counts? | Not relevant            | No                                           |

**Remember:** a license makes a user enabled; only a deliberate action makes them active.

### Saved vs shared vs scheduled vs organizational prompts

|                | Saved        | Shared to a team   | Scheduled                                          | Organizational                    |
| -------------- | ------------ | ------------------ | -------------------------------------------------- | --------------------------------- |
| Who sees it    | The owner    | One team's members | The owner                                          | Everyone                          |
| Runs by itself | No           | No                 | Yes                                                | No                                |
| Managed by     | The user     | The user           | The user; admins disable org-wide via Cloud Policy | AI Administrator or Search Editor |
| Delete         | User deletes | User removes share | User deletes in Copilot settings                   | Permanent, no restore             |

**Remember:** only organizational prompts reach everyone, and deleting one is permanent.

### User access vs Agent and plugin access vs Sharing

|          | User access                   | Agent and plugin access       | Sharing                                    |
| -------- | ----------------------------- | ----------------------------- | ------------------------------------------ |
| Limits   | Which people                  | Which publisher types         | Org-wide sharing of Agent Builder agents   |
| Exam cue | "pilot agents with one group" | "no third-party agents, ever" | "stop users sharing their agents org-wide" |

**Remember:** people, publishers, sharing: three separate settings.

### Audience vs preinstall (Publish to store)

|          | Audience            | Preinstall                         |
| -------- | ------------------- | ---------------------------------- |
| Means    | Who **can** install | Who **gets it installed** for them |
| Required | Yes                 | Optional                           |

**Remember:** preinstall is the step that puts an agent into people's apps.

### Block vs delete vs uninstall an agent

|          | Block                              | Delete                                   | Uninstall                      |
| -------- | ---------------------------------- | ---------------------------------------- | ------------------------------ |
| Effect   | Nobody can use it; config kept\*   | Soft delete, restorable for 30 days      | Removes admin-installed copies |
| Duration | Until unblocked                    | Permanent after 30 days (or immediately) | Store availability unchanged   |
| Exam cue | "pause it during an investigation" | "retire it"                              | "remove it from people's apps" |

\*For Agent Builder and Copilot Studio agents. Blocking a SharePoint or Microsoft Foundry agent affects only its availability in Copilot Chat.

**Remember:** block pauses, delete retires, uninstall removes copies.

### Assign new owner vs Add owner

|                | Assign new owner                       | Add owner                                 |
| -------------- | -------------------------------------- | ----------------------------------------- |
| Previous owner | Loses all access                       | Keeps ownership                           |
| Use            | Ownerless agent after the maker leaves | Share ownership of an Agent Builder agent |

**Remember:** assign replaces; add shares.

### Microsoft 365 admin center vs Power Platform admin center (agents)

|             | Microsoft 365 admin center                      | Power Platform admin center                           |
| ----------- | ----------------------------------------------- | ----------------------------------------------------- |
| Agents seen | All, including Agent Builder and Copilot Studio | Copilot Studio only                                   |
| Shows       | Inventory, usage, lifecycle actions             | Active agents (28 days), session success, consumption |

**Remember:** missing Agent Builder agents in Power Platform is expected; use the Agent Registry.

[← Back to the study guide](README.md)
