# Domain 2: Understand data protection and governance tasks for Microsoft 365 and Copilot (38%)

The heaviest domain (official range 35–40%). It covers what each Microsoft Purview solution does, sensitivity labels, classification and retention, how Copilot reaches data through Microsoft Graph and which controls it honours, responsible AI, and the tools that find data risk and SharePoint oversharing. Most questions describe a requirement and a constraint (is a user involved, is the content new or already stored, what must stay unchanged) and ask for the solution, setting or report that fits.

## 2.1 Microsoft Purview and Copilot Data Security

- **Six Purview solutions named in the outline, each with one job:**

| Solution                   | Job                                                                                         | When it acts                                                            |
| -------------------------- | ------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| Information Protection     | Discover, classify and protect with sensitivity labels                                      | When content is created, edited or labeled, then wherever the file goes |
| Data Loss Prevention (DLP) | Stop sensitive data leaving through risky actions: policy tips, warnings, blocks            | In real time, at sharing, sending, copying or prompting                 |
| Insider Risk Management    | Correlate risky user activities into risk scores and alerts; users pseudonymized by default | Over time, across sequences of activity                                 |
| Communication Compliance   | Flag inappropriate or sensitive message content for designated reviewers                    | After messages are sent, through a review workflow                      |
| DSPM for AI                | Show AI app usage and sensitive data in AI interactions; one-click policies                 | Continuously, as a reporting hub                                        |
| Data Lifecycle Management  | Retain content for a period, delete it when no longer needed                                | For the retention period, then at expiry                                |

- Distractors: **eDiscovery** searches and holds content for legal cases (a hold has no automatic deletion); **Compliance Manager** tracks regulatory controls. Neither replaces the six.
- **DLP vs Insider Risk vs Communication Compliance:**
  - DLP evaluates one action on one item as it happens (output: policy tip, block with optional override, alert).
  - Insider Risk looks at what users **do** over time: downloads, USB copies, printing, cloud uploads, external sharing, risky AI use, often triggered by an HR signal such as a resignation date.
  - Communication Compliance looks at what users **say**: Teams, Exchange email, Viva Engage and Copilot interactions, for harassment, threats, profanity or sensitive info types.
- **DSPM for AI:** covers Microsoft 365 Copilot and Copilot Chat, Copilot Studio agents and third-party AI apps, including consumer chatbot sites.
  - Reports: AI interactions, users and apps, sensitive info types in prompts and responses.
  - Recommendations: one-click DLP, Insider Risk, Communication Compliance and collection policies.
  - Third-party AI sites are seen from devices onboarded to Purview with the Purview browser extension, or through a SASE/SSE network integration. Without these it can't see what users type into a consumer site.
  - Now labelled _DSPM for AI (classic)_ beside the newer unified DSPM; the exam guide still says DSPM for AI.
  - DSPM for AI = **what data** goes into AI apps. Defender for Cloud Apps = **which** AI apps are used, and can block them.
- **Sensitivity labels (Information Protection):**
  - Files and emails: **encryption** (who can open, with usage rights such as VIEW, EDIT, PRINT, EXTRACT) that travels with the file, including downloaded or forwarded copies; **content marking** (headers, footers, watermarks); or classification only, which DLP, Copilot and reports can still use.
  - Groups and sites (container labels): chosen when creating a team, group or site; set privacy (public/private), guest access, external sharing level, unmanaged device access. A container label does **not** label the files inside.
  - An item can carry one sensitivity label and one retention label. Neither places a legal hold; that is eDiscovery.
- **How labels get applied:**

| Method                     | Set in                                                  | Behaviour                                                                         | User needed?         |
| -------------------------- | ------------------------------------------------------- | --------------------------------------------------------------------------------- | -------------------- |
| Manual                     | Label policy                                            | User picks a label in Office or Outlook                                           | Yes                  |
| Default label              | Label policy                                            | Unlabeled items get it regardless of content, in the apps, when created or opened | Only inside the apps |
| Mandatory labeling         | Label policy                                            | User must pick a label to save or send an unlabeled item                          | Yes, user picks      |
| Client-side auto-labeling  | The label's own settings                                | While editing matching content, the app **recommends** (dismissible) or applies   | Yes                  |
| Service-side auto-labeling | Auto-labeling policy for SharePoint, OneDrive, Exchange | The service labels matching content                                               | No                   |

- Thousands of existing files at rest in SharePoint/OneDrive that nobody will open → service-side policy. Service-side policies can't recommend.
- Exchange service-side labeling covers mail **sent or received after** the policy is on, not mail already stored. SharePoint and OneDrive can be labeled at rest.
- **Classification methods:**

| Method                     | Recognises                                                          | Best for                                               |
| -------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------ |
| Sensitive information type | Patterns (regex), checksums, keywords, proximity, confidence levels | Credit card, passport, bank account numbers            |
| Trainable classifier       | A kind of document, by machine learning                             | Resumes, source code, contracts, harassment            |
| Exact data match (EDM)     | Detected values against your uploaded table (stored hashed)         | Cutting false positives to real customers or employees |

- A stricter regex is still a pattern; only EDM checks your own records. **Document fingerprinting** recognises documents built from a standard template. Classification feeds DLP, auto-labeling, auto-apply retention, Data explorer and DSPM for AI.
- **Retention (Data Lifecycle Management):** retain only, delete only, or retain then delete.

|            | Retention policy                                                               | Retention label                                           |
| ---------- | ------------------------------------------------------------------------------ | --------------------------------------------------------- |
| Scope      | Whole locations: mailboxes, sites, OneDrive, Teams chats, Copilot interactions | Individual items                                          |
| Applied by | Admin, no user action                                                          | Users, library/folder defaults, auto-apply policies       |
| Records    | No                                                                             | Can declare a record (restricts editing, blocks deletion) |
| Per item   | Several can apply                                                              | One at a time                                             |

- **Principles of retention** when settings conflict:
  1. Retention wins over deletion.
  2. The longest retention period wins.
  3. Explicit wins over implicit for deletion (a label beats a location policy).
  4. The shortest deletion period wins when only deletion settings remain.
- **Where retained content lives:** deleted or edited retained SharePoint/OneDrive files → **Preservation Hold library** (hidden from users, visible to compliance tools). Mailbox items → **Recoverable Items**. Teams and Copilot messages → hidden mailbox folders (SubstrateHolds once deleted). Recycle bins are short-term, not where retained copies live.
- **How Copilot reaches data:**
  1. User prompts in Word, Outlook, Teams or Copilot Chat.
  2. **Grounding:** Copilot searches Microsoft Graph, using the semantic index, for mail, files, chats, meetings and calendar items **the user can access**, plus the open document or meeting. Web grounding, if allowed, adds public web results.
  3. The LLM writes a response from the grounded prompt.
  4. Responsible AI checks run; the answer returns with **citations**.
- **Permission trimming:** Copilot only uses content the user can at least view. The Copilot license, admin roles or having opened a file before don't change that. Two users can get different answers to the same question.
- **Oversharing** is the flip side: content shared too widely today becomes far easier to find through Copilot.
- **Copilot connectors** (formerly Microsoft Graph connectors), set up in the Microsoft 365 admin center, index external content into Graph **with its access lists**, so trimming still applies. Copying an export into SharePoint or an agent's knowledge flattens those permissions. Power Platform connectors let apps and flows call services; they don't feed Copilot grounding.
- **Data commitments:**
  - Prompts, responses and Graph data are **not used to train foundation models**; there's no per-tenant model.
  - Prompts and responses are stored in a **hidden folder in the user's Exchange Online mailbox**, so Content search, eDiscovery and retention can act on them. The audit log records that an interaction happened; eDiscovery shows what was typed.
  - Web search sends a generated query (not the whole prompt or files) to Bing, outside the Microsoft 365 service boundary.
  - Microsoft 365 Copilot is opted out of human abuse-monitoring review.
  - Retention location for Copilot is **Microsoft Copilot experiences**, now separate from Teams chats. The Exchange mailboxes location doesn't cover the hidden Copilot folder.
- **Controls Copilot honours:**
  - Microsoft 365 permissions decide what each user, and therefore Copilot, can reach.
  - Encrypted content: Copilot needs the user to have **VIEW and EXTRACT** to return text. VIEW without EXTRACT → no summary, but it can still return a link.
  - **Label inheritance:** new content made from labeled sources gets the **highest-priority** source label, replacing a lower-priority label already on the document.
  - **DLP for the Microsoft 365 Copilot and Copilot Chat location:** "content contains sensitivity labels" keeps those items out of Copilot's responses (they can still appear as citations; user access unchanged); "prompt contains sensitive information types" can stop the prompt being used for web search (blocking the response entirely is in preview). The two conditions can't share a rule. The policy doesn't relabel, block opening or delete.
  - **Defender for Cloud Apps** discovers cloud and generative AI apps (Cloud Discovery, risk scores). Tagging **Unsanctioned** blocks the app on Defender for Endpoint devices when enforcement is on; **Monitored** watches only. Conditional Access can't block a consumer AI site with its own sign-in.
- **Responsible AI principles:**

| Principle              | Means                                                     | Example                                                           |
| ---------------------- | --------------------------------------------------------- | ----------------------------------------------------------------- |
| Fairness               | Equitable treatment, no biased allocation                 | Promotions recommended less often for one group violates it       |
| Reliability and safety | Consistent, safe behaviour, even in unexpected conditions | Testing and content filters                                       |
| Privacy and security   | Protect data, respect permissions                         | Copilot using only accessible content; no training on tenant data |
| Inclusiveness          | Empower everyone, including people with disabilities      | Accessible interfaces, many languages                             |
| Transparency           | People understand how it works and its limits             | Citations; notices that AI content may be wrong                   |
| Accountability         | People stay responsible for outcomes                      | Naming who answers for an agent and can switch it off             |

- **Traps:**
  - "Warn or block while they share" → DLP. "Signals correlated around a resignation" → Insider Risk. "Tone of Teams messages, reviewed by people" → Communication Compliance.
  - Container labels don't label files in the site.
  - "Copilot shows a user a confidential file" means the user already had access; fix permissions, not Copilot.
  - Fairness = biased outcomes; inclusiveness = designing for everyone. Transparency = understanding; accountability = who answers.

📖 Full lesson: [AB-900 Microsoft Purview and Copilot Data Security: Sensitivity Labels, DLP, Retention and Responsible AI](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/microsoft-purview-sensitivity-labels-copilot-data-security/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

## 2.2 Data Protection Risks and SharePoint Oversharing

- **Pick the tool by the question:**

| Question                                          | Tool                                                              |
| ------------------------------------------------- | ----------------------------------------------------------------- |
| How far are we toward a regulation, what's next?  | Compliance Manager                                                |
| Where does classified sensitive data sit now?     | Data explorer                                                     |
| What did people do with labeled content recently? | Activity explorer                                                 |
| Whose behaviour suggests data risk?               | Insider Risk Management                                           |
| What did a DLP policy catch?                      | DLP alerts (Defender XDR or Purview portal)                       |
| Which messages broke a conduct policy?            | Communication Compliance                                          |
| What are people doing with Copilot and AI apps?   | DSPM for AI                                                       |
| Find these emails and files and export them       | Content search (Purview eDiscovery)                               |
| Which sites are shared too widely?                | Data access governance reports, DSPM for AI data risk assessments |

- **Compliance Manager:** for a score plus a named regulation (GDPR, ISO/IEC 27001, ISO/IEC 27701, NIST...) plus assignable steps with evidence.
  - Assessments are created from **regulatory templates**; a data protection baseline assessment exists by default.
  - Improvement actions carry points, an owner, implementation status, test status and an Evidence area; some are tested automatically.
  - Compliance score rises as actions are implemented and tested.
  - **Shared responsibility:** Microsoft's controls for its own services count automatically; the Improvement actions page lists **your** share.
  - Secure Score measures security posture, not regulatory progress.
- **Data explorer** (formerly content explorer): a **snapshot** of items with sensitive info types, sensitivity labels, retention labels or classifier matches, counted per location and drillable to items.
  - **Data Explorer List viewer:** list of items and locations, not contents (showing item names can also need Content viewer).
  - **Data Explorer Content viewer:** item contents.
  - Separate role groups, not cumulative. An admin role that opens the page can show counts but no items.
- **Activity explorer:** a **history** of actions on labeled and sensitive content (label applied, changed or removed, file read, DLP match), filterable by activity, user, label, location, date. Built from the unified audit log, so not real time, and only **about the last 30 days**. Older events → Purview Audit search (Standard keeps 180 days).
- **Insider Risk alert triage:** **confirm** and create (or add to) a case when the risk is real; **dismiss** when explained (an authorized migration). Usernames are **pseudonymized by default**. Cases can later be escalated to eDiscovery (Premium); that isn't an alert-triage option.
- **DLP alerts:** Microsoft recommends managing them in the **Defender portal (Defender XDR)**, where they correlate into incidents; Purview also lists them and is where policies are edited.
  - Event details: policy and rule, sensitive info types and counts, user, location, action, and any **override with business justification**. That tip decision lives only in the alert.
  - **Single-event** alerts fire on every match (high severity, low volume). **Aggregated (threshold)** alerts fire past a count or volume in a window (needs E5/A5/G5 or an add-on). Only the alert type changes alert volume.
- **Communication Compliance remediation** (Pending tab → Resolved):

| Action                     | Effect                                                    |
| -------------------------- | --------------------------------------------------------- |
| Resolve                    | Closes the match                                          |
| Tag as                     | Compliant, Noncompliant or Questionable                   |
| Notify                     | Emails the user a notice template                         |
| Escalate                   | Routes to another reviewer                                |
| Escalate for investigation | Creates an eDiscovery (Premium) case, user as custodian   |
| Remove message in Teams    | Hides the message from participants, replaced by a notice |

- **DSPM for AI in use:** reports and its own AI activity explorer, one-click policies, data risk assessments.
  - Needs **Purview Audit on**: reports are built from audit records.
  - Third-party AI sites need devices **onboarded to Purview** and, in Chrome, the **Purview browser extension** (Edge integrates via policy).
  - **Default data risk assessment:** runs automatically **weekly on the top 100 SharePoint sites by usage**. A quiet but sensitive site may be missed → create a **custom assessment** scoped to chosen sites or users. Results offer fixes: restrict access, Restricted Content Discovery, auto-label, start a site access review.
- **Content search:** keyword and condition searches across Exchange mailboxes (where Teams chats are stored), SharePoint, OneDrive and Teams, with preview and export. Classic page retired in 2025; it runs in the new **Purview eDiscovery** experience.
  - Not audit search (records of actions), not Data explorer (already-classified items), not message trace (mail flow, no bodies).
  - **eDiscovery Manager** role group = least privilege for search, preview and export.
- **Oversharing** = content shared wider than it should be; Copilot makes it easy to find, so fix it before rollout.
- **Data access governance (DAG) reports:** SharePoint admin center > Reports > Data access governance.

| Report                                              | Type              | Answers                                                                                                         |
| --------------------------------------------------- | ----------------- | --------------------------------------------------------------------------------------------------------------- |
| Site permissions across your organization           | Snapshot          | Sites granting access to many people or broad groups such as Everyone except external users (EEEU), however old |
| Site permissions for users                          | Snapshot          | Every site and OneDrive one named user can access, and how                                                      |
| Sensitivity labels applied to files                 | Snapshot          | Which sites hold files with a chosen label                                                                      |
| Sharing links (Anyone, org-wide, specific external) | Activity, 28 days | Sites with the most new links of each kind                                                                      |
| Content shared with EEEU                            | Activity, 28 days | Sites with content newly shared with EEEU                                                                       |

- Microsoft recommends starting with snapshot reports. Access granted months ago is invisible to 28-day activity reports.
- **SharePoint Advanced Management (SAM):** included with at least one Microsoft 365 Copilot license, or bought separately. E5 admins without SAM get only limited DAG activity reporting (no snapshots, no remediation).
  - **Site access review:** started from a DAG report; emails each site's **owners**, who fix permissions and mark it complete. Admin tracks on _My review requests_ without seeing file-level changes. Nothing removed automatically. Up to **100 sites** at once in the web view (PowerShell for more). **SharePoint sites only, not OneDrive.** Different from Entra ID access reviews (group membership and app access, can go to managers).
  - **Restricted access control:** only members of up to **10** Microsoft 365 or Entra security groups who **also** have site permission can open the site or OneDrive. Earlier sharing stops working for everyone else.
  - **Restricted Content Discovery:** hides a site's content from Copilot and org-wide search for everyone; permissions unchanged, content stays indexed for eDiscovery, Copilot still works on a document a user has open. Sites only, not OneDrive. Works regardless of labels, so it's the stopgap while labeling catches up.
  - **Block download policy:** per site, browser-only, no download, print or sync (`Set-SPOSite -BlockDownloadPolicy`), optional exemptions.
  - **Authentication context:** publish a context in Entra, target it with a Conditional Access policy, apply it to one site (via `Set-SPOSite` or a sensitivity label). Other sites keep current rules.
  - **Inactive site policy:** emails owners of inactive sites; unconfirmed sites become read-only or are archived with Microsoft 365 Archive.
  - **Site ownership policy:** finds sites with too few owners; checks counts, not activity.
  - **Change history report:** site property and setting changes over up to 180 days.
- **Traps:**
  - Current state = Data explorer; history = activity explorer; older than 30 days = audit log.
  - Escalate ≠ Escalate for investigation. Only Remove message in Teams changes what others see.
  - Restricted access control changes **who can open**; Restricted Content Discovery changes only **what is surfaced**.
  - Site access reviews go to site owners, never auto-remediate, and skip OneDrive.

📖 Full lesson: [AB-900 Data Protection Risks and SharePoint Oversharing: Purview Explorers, Alerts, DSPM for AI and SharePoint Advanced Management](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/ab-900-data-protection-risks-sharepoint-oversharing/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

[← Back to the study guide](../README.md)
