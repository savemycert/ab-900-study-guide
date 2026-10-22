# Domain 1: Identify the core features and objects of Microsoft 365 services (33%)

This domain covers the objects an admin configures in each Microsoft 365 admin center, the security principles behind Microsoft 365, and the Microsoft Entra ID features that control and check access. Microsoft publishes the weight as a 30–35% range. Questions are short admin scenarios: a requirement plus a constraint (no extra license, read-only, least privilege, no manual work), and you pick the object, role, setting or tool that fits.

## 1.1 Core Objects of Microsoft 365 Services

- **Licenses turn identities into working accounts.** Creating a user gives an Entra ID identity that can sign in, but no services. Assigning a license (E3, Business Premium, and so on) provisions what it contains: a mailbox, Teams, OneDrive and SharePoint access, the Microsoft 365 apps.
- **A license is a bundle of service plans** (Exchange Online, Teams, Forms, Planner...). Three levers:
  - Assign or remove the whole license. When removed, Exchange data is kept for a 30-day grace period, then deleted.
  - Turn individual services off inside one assignment (for example, Planner off for contractors). Other users with the same license are unaffected.
  - Add an add-on license on top of a base plan (Microsoft 365 Copilot, extra storage, Teams Phone).
- **License vs role:** a license grants services; an admin role (Exchange Administrator, Teams Administrator) grants management rights. Signs in but has no mailbox → licensing. Has services but can't manage a workload → roles.

| Family           | Aimed at                                   | Examples                                                                                                    |
| ---------------- | ------------------------------------------ | ----------------------------------------------------------------------------------------------------------- |
| Business plans   | Small and medium orgs, capped at 300 users | Business Basic (web/mobile apps), Standard (adds desktop apps), Premium (adds Intune and advanced security) |
| Enterprise plans | Any size, no seat cap                      | E3 (desktop apps, device and compliance features), E5 (adds advanced security, compliance, analytics)       |
| Frontline plans  | Shift workers on shared or mobile devices  | F1 (Teams and SharePoint, no mailbox), F3 (adds a small mailbox and web/mobile apps)                        |
| Add-ons          | Extra capability on a base plan            | Microsoft 365 Copilot, extra storage, Teams Phone                                                           |

- **Usage location** must be set before a license can be assigned directly, because service availability differs by country. It is not the office location field. Group-licensed members with no usage location inherit the tenant's.
- **Direct vs group-based licensing:**
  - Direct: Active users > user > Licenses and apps. Someone must act on every joiner and leaver. Good for exceptions.
  - Group-based: Billing > Licenses > product > Groups (or Entra ID). Membership drives the license automatically. Good for departments and roles.
  - Works with security groups, mail-enabled security groups and security-enabled Microsoft 365 groups. **Not** distribution groups.
  - **Nested groups are not followed.** Only direct members of the licensed group get it. Fix: license the nested group too, or add users directly.
  - Same product from two sources = one license consumed; enabled services combine.
- **Domains (Settings > Domains):** every tenant starts with `contoso.onmicrosoft.com`, which can never be removed.
  1. Verify ownership: add the tenant-specific TXT record (`MS=ms...`) at the DNS host.
  2. Connect services: MX and SPF for mail flow, autodiscover CNAME for Outlook, optional DKIM CNAMEs.
  - Workload settings that refer to a domain (such as Exchange accepted domains) only work after it is added and verified here. Then it can be the default for new users.
- **Org settings (Settings > Org settings)** apply to the whole organization:
  - Services tab: calendar sharing, Forms, Bookings, Microsoft 365 Groups guest settings, modern authentication.
  - Security & privacy tab: password expiration policy, privacy profile, sharing (users adding guests).
  - Organization profile tab: org information, release preferences (standard or targeted release), custom themes, help desk contact.
  - Wrong tool for changing one department: use license assignments or scoped service policies.
- **Exchange admin center: mailbox types**

| Mailbox   | For                                                      | License                                                          |
| --------- | -------------------------------------------------------- | ---------------------------------------------------------------- |
| User      | One person's mail, calendar, contacts                    | Created by a license that includes Exchange Online               |
| Shared    | A common inbox such as support@                          | None within 50 GB; needed for more storage, an archive or a hold |
| Room      | A bookable place; can auto-accept                        | None                                                             |
| Equipment | A bookable item that isn't a place (projector, pool car) | None                                                             |

- Room and equipment are both **resource mailboxes**. A shared mailbox has an Entra account whose sign-in is blocked by default and should stay blocked.
- **Shared mailbox permissions combine; none includes another:**
  - Full Access: open, read, manage and delete items. Does not allow sending.
  - Send As: the message appears to come from the mailbox alone.
  - Send on Behalf: shows "Person on behalf of mailbox".
  - Access granted through a group does not automap in Outlook; only individual Full Access does.
- **Exchange group types:**

| Group                       | Receives email    | Can grant permissions | Membership                                                                                         |
| --------------------------- | ----------------- | --------------------- | -------------------------------------------------------------------------------------------------- |
| Distribution group          | Yes               | No                    | Static                                                                                             |
| Dynamic distribution group  | Yes               | No                    | Calculated from attributes (Department, Office), recalculated at least every 24 hours              |
| Mail-enabled security group | Yes               | Yes                   | Static                                                                                             |
| Microsoft 365 group         | Yes (group inbox) | Yes                   | Static (Entra dynamic membership is premium); adds calendar, team site, Planner, can become a team |

- **SharePoint hierarchy:** site → document libraries (and lists) → folders → files. The SharePoint admin center manages sites; libraries and folders are managed on the site by its owners and members.

| Site type                          | Purpose                                                         | Permissions                                                                 |
| ---------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------------------- |
| Team site with Microsoft 365 group | Group collaboration on shared files                             | Group owners/members become site owners/members; Visitors group also exists |
| Team site without a group          | Collaboration without mailbox, calendar or team                 | SharePoint Owners, Members, Visitors                                        |
| Communication site                 | Publishing: news, policies, intranet; few authors, many readers | Owners, Members, Visitors (readers in Visitors)                             |
| Channel site                       | Auto-created for a private or shared Teams channel              | Follows the channel's membership                                            |

- **Active sites** page: create sites; manage site admins, sharing level, storage limit, hub association, group connection.
- **Deleted sites** are kept for **93 days** and restored with all content. Deleting a group-connected site's Microsoft 365 group deletes the site; restoring the group restores it.
- **Site recycle bins** restore items deleted inside a site that still exists, not the site itself.
- **SharePoint permission levels:**

| Group / level        | Can do                                                                                 |
| -------------------- | -------------------------------------------------------------------------------------- |
| Owners: Full Control | Everything, including settings, permissions and membership                             |
| Members: Edit        | Add, edit, delete items **and** create, change or delete lists and libraries           |
| Visitors: Read       | View and download, change nothing                                                      |
| Contribute           | Add, edit, delete items in existing lists and libraries, but not create or delete them |
| Design               | Edit plus approve items and customize pages and themes                                 |

- Edit vs Contribute differs only by the Manage Lists permission. Site admins (site collection administrators) have full control regardless of groups.
- **Group-connected sites:** Microsoft 365 groups have owners, members and guests, with **no read-only role**. For read-only access without the group mailbox and calendar, add people (or a security group) to the site's **Visitors** SharePoint group.
- **Permission inheritance:** libraries, folders and files inherit from the site by default. For a Contracts library only legal can open, stop inheriting on that library and grant access there. Use sparingly. Hiding a library from navigation is not a security control.
- **Teams admin center: teams.** Every team sits on a Microsoft 365 group (mailbox, SharePoint site, owners/members/guests). Teams > Manage teams: create, membership, privacy (public/private), channels, archive, delete.

| Channel  | Who takes part                                                                                     | Files in                   |
| -------- | -------------------------------------------------------------------------------------------------- | -------------------------- |
| Standard | Every team member (and team guests)                                                                | The team's SharePoint site |
| Private  | A subset of team members chosen by the channel owner                                               | Its own channel site       |
| Shared   | Specific people inside or outside the team, including other organizations, with their own accounts | Its own channel site       |

- Shared channels use Microsoft Entra B2B direct connect, which both organizations must allow. Standard and private channels need outsiders to be guests.
- **Archive vs delete:** archive makes the team read-only (readable, no posting, can be unarchived; optionally the site is read-only too). Delete removes the team and its group for everyone; the group can be restored for a limited time.
- **Teams policy types:** messaging (delete/edit sent messages, read receipts, Giphy), meeting (recording, transcription, lobby bypass, screen sharing), app setup (pinned apps), app permission (which apps can be installed), Teams policy (private/shared channel creation, discovery), calling (forwarding, voicemail, simultaneous ring; call park has its own policy).
- **Precedence, resolved per policy type:**
  1. A direct assignment to the user always wins.
  2. Otherwise group assignments, highest ranking (rank 1) wins.
  3. Otherwise the Global (Org-wide default).
  - Ranking only orders groups against each other; it never beats a direct assignment. The user's Policies tab shows each effective policy and its source.
- **Traps:**
  - "Sign in works, no mailbox" is licensing, not a role or a password problem.
  - "Audience defined by an attribute, no maintenance" → dynamic distribution group. "Email the group and grant it site access" → mail-enabled security group or Microsoft 365 group.
  - "Change content but not site structure" → Contribute, not Edit.
  - "External partners in one channel without guest accounts" → shared channel.
  - "Read-only, keep the history" → archive, not delete.

📖 Full lesson: [AB-900 Core Objects: Microsoft 365 Licenses and the Exchange, SharePoint and Teams Admin Centers](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/microsoft-365-admin-centers-licenses-core-objects/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

## 1.2 Microsoft 365 Security Principles

- **Zero Trust:** never trust a request because of where it comes from. A sign-in from the office is evaluated like one from a café.

| Principle                  | Question it answers                               | Practices                                                                                                           |
| -------------------------- | ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| Verify explicitly          | Should this request be trusted right now?         | Authenticate and authorize every request on all signals: identity, location, device health, the resource, anomalies |
| Use least privilege access | How much access, and for how long?                | Just-in-time and just-enough access (JIT/JEA), risk-based adaptive policies, protect the data                       |
| Assume breach              | If an attacker is inside, how do we limit damage? | Minimize blast radius, segment, encrypt end to end, detect with analytics                                           |

- Classify a control by its **main purpose**: checking one request (MFA plus compliant device) = verify explicitly; sizing access in scope and time (role active only for a few hours, access that expires with a contract) = least privilege; containing an intruder (segmentation, encryption, detection) = assume breach.
- Zero Trust is a strategy, not a product. In Microsoft 365: Entra ID (identity), Intune (device compliance), Purview (data), Defender XDR (detection and response). Defense in depth and shared responsibility are separate models.
- **Authentication vs authorization:**
  - Authentication (AuthN) proves who the caller is, first, at sign-in, using credentials.
  - Authorization (AuthZ) decides what they may do, on each request, using roles, group membership, permissions and licenses.
  - "Signed in but access denied" = passed authentication, failed authorization.
- **Admin authorization is RBAC:** assign the narrowest built-in role that covers the task. Keep Global Administrator to a few people.

| Role                                    | Allows                                                                                  |
| --------------------------------------- | --------------------------------------------------------------------------------------- |
| Global Administrator                    | Every setting in the tenant                                                             |
| Global Reader                           | See everything a Global Admin sees, change nothing                                      |
| Security Reader                         | Read security information and reports                                                   |
| Reports Reader                          | Read usage and activity reports                                                         |
| Password Administrator                  | Reset passwords for non-admins and a few low-privilege roles only                       |
| Helpdesk Administrator                  | Password resets for non-admins and some limited admins, plus other support tasks        |
| User Administrator                      | Create and manage users and groups                                                      |
| Privileged Authentication Administrator | Set or reset authentication methods and passwords for any user, including Global Admins |

- **MFA = factors from at least two different categories:** something you know (password, PIN), something you have (Authenticator phone, FIDO2 key, smart card), something you are (biometrics). Two "know" factors (password plus passphrase) are still single-factor. A longer password strengthens one factor; it doesn't add one.
- **Phishing-resistant methods:** Windows Hello for Business, passkeys (FIDO2) on security keys or in Authenticator, and certificate-based authentication. The credential is bound to the real sign-in site and never leaves the device.

| Method                               | MFA-capable | Phishing-resistant                           |
| ------------------------------------ | ----------- | -------------------------------------------- |
| Windows Hello, passkeys, CBA         | Yes         | Yes                                          |
| Authenticator push approval          | Yes         | No: a user can approve an attacker's sign-in |
| Authenticator or OATH one-time codes | Yes         | No: codes can be relayed                     |
| SMS and voice                        | Yes         | No, and the weakest MFA option               |

- **Adversary-in-the-middle (relay) phishing** passes the password and code to the real site and steals the session cookie. Codes, SMS and push don't stop it; origin-bound passkeys do. Microsoft recommends phishing-resistant methods for admins first.
- **Temporary Access Pass (TAP):** a time-limited passcode an admin issues so a user with no usable credential can sign in, typically to onboard or recover and register a passwordless method. Admin sets the lifetime and one-time or multi-use. Must be enabled in the Authentication methods policy. Not an everyday method.
- **Threat protection vs threat intelligence:** protection = controls that prevent, detect and respond; intelligence = knowledge about attackers (campaigns, tools, URLs, files) that makes those controls smarter.
  - Built in: a phishing URL seen at another customer is blocked by Defender for Office 365 at a company that never saw it. The key is that the knowledge came from someone else's attack.
  - As reports: **Threat analytics** in the Defender portal publishes Microsoft research on active campaigns and maps it to your exposure (affected devices and mailboxes, incidents, mitigations in place). Former Defender Threat Intelligence capabilities are now in the Defender portal.

| Product                           | Protects                                                              |
| --------------------------------- | --------------------------------------------------------------------- |
| Defender for Office 365           | Email and collaboration: Exchange Online, Teams, SharePoint, OneDrive |
| Defender for Endpoint             | Devices: EDR, isolation, file quarantine                              |
| Defender for Identity             | On-premises and hybrid identity: AD, AD FS, AD CS, Entra Connect      |
| Microsoft Entra ID Protection     | Cloud identities: risky users and sign-ins                            |
| Defender for Cloud Apps           | SaaS apps: shadow IT discovery, app and session governance            |
| Defender Vulnerability Management | Device weaknesses and misconfigurations                               |

- **Safe Links** checks a URL **at time of click**. **Safe Attachments** detonates attachments in a sandbox **before delivery**. Zero-hour auto purge acts on mail already delivered. Anti-spam filters bulk and junk at delivery.
- **Defender XDR** correlates signals across endpoints, identities, email and cloud apps in the Defender portal:
  - **Incidents** group related alerts from several products into one attack story. An alert is one detection from one product.
  - **Cross-product response:** a detection in one product triggers action in another (Endpoint finds a file, Office 365 removes copies from mailboxes).
  - **AIR (automated investigation and response):** investigates after an alert and remediates mailboxes, devices and identities; actions tracked in the Action center.
  - **Automatic attack disruption:** contains an attack in progress (disable a compromised account, contain a device) without waiting for an analyst.
  - **Advanced hunting:** KQL queries over up to 30 days of raw data.
- Defender XDR does not label documents or retain mail (Purview) and does not decide sign-in access (Entra ID, Conditional Access).
- **Traps:**
  - Password plus security question is not MFA.
  - "MFA is enabled but users were still phished through a proxy page" → the answer is a phishing-resistant method, not more MFA prompts.
  - Defender for Identity is on-premises AD; Entra ID Protection is cloud sign-ins.
  - Auditor who sees everything and changes nothing → Global Reader. Resets staff passwords only → Password Administrator.

📖 Full lesson: [AB-900 Microsoft 365 Security Principles: Zero Trust, Authentication, Authorization and Defender XDR](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/ab-900-zero-trust-microsoft-365-security-principles/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

## 1.3 Core Security Features of Microsoft 365

- **Microsoft Entra ID** holds users, groups and app identities, authenticates every sign-in and decides whether it gets access. Exchange, SharePoint, Teams, Copilot and connected SaaS apps trust its tokens. Managed in the **Microsoft Entra admin center**.

| License             | Adds (relevant here)                                                                                |
| ------------------- | --------------------------------------------------------------------------------------------------- |
| Entra ID Free       | Users, groups, basic SSO, security defaults, audit and sign-in logs (7 days), Identity Secure Score |
| Entra ID P1         | Conditional Access, dynamic membership groups, group-based licensing at scale, 30-day logs          |
| Entra ID P2         | P1 plus ID Protection risk-based policies and full reports, and PIM                                 |
| Entra ID Governance | Advanced governance: PIM, access reviews, entitlement management                                    |

- E3 and Business Premium include P1; E5 includes P2.
- **Security defaults:** free, one switch. Every user registers for MFA, MFA prompted when needed (always for admins), privileged activity protected, **legacy authentication blocked**. All-or-nothing: no exclusions, no conditions. Turned off when Conditional Access takes over; the two don't run together.
- **Security objects:**
  - Member user (cloud-only or synced from on-premises AD by Entra Connect) for employees.
  - Guest user (B2B collaboration) for external people, who sign in with their own organization's account. The partner manages their password.
  - Mail contact: an external address in the address book; cannot sign in or get access.
  - Security group grants access, licenses and Conditional Access targeting (no mailbox). Microsoft 365 group adds collaboration. Mail-enabled security group = access plus email. Distribution list = email only.
  - Membership is **assigned** or **dynamic** (rule such as `user.department -eq "Engineering"`; needs P1).
  - Access a user requests with approval and an expiry → access package (entitlement management). Delegated admins for one department → administrative unit.
- **Conditional Access (P1)** is an if–then evaluated at every sign-in:

| Part             | Side | Examples                                                                                                                                              |
| ---------------- | ---- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| Users            | If   | Users, groups, directory roles, guests, workload identities, exclusions                                                                               |
| Target resources | If   | Cloud apps, user actions, authentication contexts                                                                                                     |
| Conditions       | If   | Network location, device platform, client app (incl. legacy), user and sign-in risk (P2), device filters                                              |
| Grant controls   | Then | Block, or require MFA, an authentication strength, a compliant or hybrid-joined device, an app protection policy, password change or risk remediation |
| Session controls | Then | Sign-in frequency, persistent browser session, app enforced restrictions, Conditional Access App Control                                              |

- Conditions can only test what the sign-in carries. Common patterns: MFA for all or admins, block legacy auth, compliant device for sensitive apps, block unexpected countries.
- **Policy states:** On, Off, Report-only.
  - **Report-only** evaluates real sign-ins and records what would have happened, without enforcing. Results show on each sign-in's Report-only tab and in the insights workbook. Use it to measure impact over days.
  - **What If** simulates one hypothetical sign-in you describe and lists which policies would apply and why others wouldn't. It evaluates On and Report-only policies, never Off ones.
  - A policy switched On enforces for everyone it targets, even a pilot group.
- **SSO:** sign in once with one Entra identity to reach Microsoft 365, gallery SaaS apps (SAML, OpenID Connect), your own apps and on-premises apps via application proxy.
  - Users: one password, fewer prompts and resets.
  - Admins: one control point, so the same MFA and Conditional Access cover every app, and sign-ins land in one set of logs.
  - Offboarding: block one account and revoke sessions to cut off every connected app.
  - SSO doesn't remove MFA and doesn't license SaaS apps. Removing a Microsoft 365 license doesn't stop sign-in to other Entra-trusting apps.
- **App registrations vs Enterprise applications:**
  - App registrations = the **application object**, the global definition, only in the app's home tenant: client ID, secrets and certificates, redirect URIs, requested API permissions, single or multitenant. Developers start here.
  - Enterprise applications = the **service principal**, the app's instance in every tenant that uses it: user/group assignment, consent and granted permissions, SSO, provisioning, sign-in activity.
  - Consenting to another company's multitenant app creates a service principal in your tenant. You manage it under Enterprise applications; you have no App registrations entry for it.
- **Troubleshooting sign-ins:** start with the **Entra sign-in logs** (result, error code, failure reason, app, client app, location, device, MFA details, and a Conditional Access tab listing each policy evaluated).

| Symptom                                           | Where / fix                                                                                       |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| Why did this sign-in fail?                        | Sign-in logs or the sign-in diagnostic                                                            |
| Which policy blocked or challenged the user?      | The sign-in entry's Conditional Access tab                                                        |
| Which policies will hit a future sign-in?         | What If tool                                                                                      |
| IMAP/POP/SMTP basic auth blocked                  | Client app shows a legacy protocol; move the user to modern auth, keep the policy                 |
| Lost the phone with Authenticator, knows password | Authentication methods page: **Require re-registration of MFA** (delete the old method if needed) |
| Sign-in flagged as risky                          | ID Protection risky sign-ins / risky users                                                        |

- A password reset leaves the lost method in place; revoking sessions only signs the user out. Neither gives a working second factor.
- **ID Protection (full reports and risk policies need P2):**

|                  | Sign-in risk                                                       | User risk                                                                                                                 |
| ---------------- | ------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------- |
| Question         | Was this sign-in made by someone else?                             | Is the account likely compromised?                                                                                        |
| Detections       | Anonymous IP, atypical travel, unfamiliar properties, malicious IP | Leaked credentials, threat intel on the account                                                                           |
| Self-remediation | Require MFA                                                        | Require risk remediation (now recommended) or Require password change: MFA then secure password change for password users |

- Risk policies are configured as Conditional Access policies with the user-risk or sign-in-risk condition (the older ID Protection policies were retired in October 2026). Self-remediation needs users already registered for MFA. A **block** policy can't be self-remediated: an admin resets the password or dismisses the risk.
- **Identity Secure Score:** the percentage of available points earned from Microsoft's recommended identity practices (48% ≈ half the points). Entra ID > Identity Secure Score; recalculated about every 24 hours. Built from improvement actions (MFA for admins, block legacy auth, enable SSPR, fewer Global Admins), some partially earned. Measures configuration, not breach probability.

| Status                                | Points? |
| ------------------------------------- | ------- |
| To address                            | No      |
| Planned                               | No      |
| Risk accepted                         | No      |
| Resolved through third party          | Yes     |
| Resolved through alternate mitigation | Yes     |

- **Audit logs:**

| Log                      | Records                                                                                    | Default retention              |
| ------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------ |
| Entra audit logs         | Directory changes: users, groups, role assignments, apps, policies                         | 7 days (Free), 30 days (P1/P2) |
| Entra sign-in logs       | Authentication attempts, MFA and Conditional Access outcomes                               | 7 days (Free), 30 days (P1/P2) |
| Entra provisioning logs  | Automatic provisioning to and from apps and HR systems                                     | Same                           |
| Purview Audit (Standard) | Unified audit log across Entra ID, Exchange, SharePoint, OneDrive, Teams, Copilot and more | 180 days                       |
| Purview Audit (Premium)  | Longer retention and extra events for investigations                                       | 1 year by default              |

- For a role change **and** a file deletion from months ago → Purview Audit. Keep Entra logs longer by exporting to Log Analytics, storage or a SIEM.
- **PIM (P2 or Entra ID Governance):** just-in-time, time-bound, approval-based access to Entra roles, Azure resource roles and privileged groups.
  - **Eligible:** nothing until the user activates, for a maximum duration, optionally with MFA, justification and approval.
  - **Active:** the role immediately; no activation, so no approval step. Can be permanent or time-bound.
  - Either type can have start and end dates. PIM also notifies on activation, runs access reviews, raises alerts and keeps activation history. Role-assignable groups use assigned membership only.
- **Traps:**
  - "Small org, no extra licenses, MFA for everyone" → security defaults. "Exclude one user" or "only for sign-ins from some countries" → Conditional Access.
  - Grant controls decide access; session controls limit it afterwards; conditions are only the "if".
  - "See impact on real traffic without blocking anyone" → report-only. "Will this user's sign-in tomorrow be blocked?" → What If.
  - "Must ask and wait for approval each time" → PIM eligible assignment with approval, not a time-bound active one.
  - Identity Secure Score status "Planned" or "Risk accepted" earns nothing.

📖 Full lesson: [AB-900 Microsoft Entra ID Security Features: Conditional Access, SSO, PIM, Secure Score and Logs](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/ab-900-microsoft-entra-id-security-features/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

[← Back to the study guide](../README.md)
