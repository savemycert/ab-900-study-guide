# Domain 3: Perform basic administrative tasks for Copilot and agents (29%)

This domain covers what Copilot, Copilot Chat and agents can do, how each is paid for, which features an admin can switch on or off, and the routine work of assigning licenses, running pay-as-you-go billing, reporting on usage, managing prompts and governing agents. Microsoft publishes the weight as a 25–30% range. Names in this area change often (Microsoft 365 Copilot is being renamed Microsoft Copilot), so learn what each tier or setting does rather than its label.

## 3.1 Copilot and Agent Features and Capabilities

- **Agent = Copilot scoped to one job**, packaged with its own **instructions**, chosen **knowledge sources** and, for advanced agents, **actions**. Same foundation models, same orchestration, same route to organizational data.

|              | Copilot                                     | An agent                                                           |
| ------------ | ------------------------------------------- | ------------------------------------------------------------------ |
| Purpose      | Any task                                    | A specific, repeated job                                           |
| Instructions | The user's prompt each time                 | Saved instructions (tone, format, rules) plus the prompt           |
| Knowledge    | Depends on license (web, or web plus Graph) | Sources the maker chose: websites, SharePoint, files, connectors   |
| Actions      | Built-in app actions                        | Optional actions such as calling external systems (Copilot Studio) |
| Permissions  | The signed-in user's                        | The signed-in user's, **never the maker's**                        |

- A knowledge source tells the agent where to look; it grants nobody access. A non-director asking a finance agent gets answers without the board pack only directors can open. Organizational content grounds answers; it doesn't train a separate model.
- **Copilot Chat (included) vs Microsoft 365 Copilot (add-on license):**

|                                                    | Copilot Chat (included)                                                                   | Microsoft 365 Copilot license         |
| -------------------------------------------------- | ----------------------------------------------------------------------------------------- | ------------------------------------- |
| Web grounding                                      | Yes, if allowed                                                                           | Yes, if allowed                       |
| User's mail, meetings, chats, files                | Only what's uploaded or pasted, plus own inbox and calendar when Chat runs inside Outlook | Automatically through Microsoft Graph |
| Copilot in Word, Excel, PowerPoint, Teams meetings | No full in-app Copilot                                                                    | Yes, with priority access             |
| Agents                                             | Instruction and public-web agents free; tenant-data agents metered                        | Included, including work-data agents  |
| Researcher and Analyst                             | No                                                                                        | Yes, pre-installed                    |

- The license is an **add-on**: no Microsoft 365 or Office 365 suite includes it. A middle tier, **Microsoft 365 Copilot (Basic)**, gives some unlicensed users standard, non-priority Copilot in Word, Excel, PowerPoint and OneNote, still without automatic Graph grounding.
- **Monthly license vs pay-as-you-go:**

|           | License                          | Pay-as-you-go                                                                                     |
| --------- | -------------------------------- | ------------------------------------------------------------------------------------------------- |
| Pay       | Fixed, per named user, per month | Actual usage, after it happens, through Azure meters                                              |
| Billed to | The Microsoft 365 subscription   | The Azure subscription in a **billing policy**                                                    |
| Unlocks   | The full licensed experience     | Metered services only: Copilot Chat agents on tenant data, SharePoint agents for unlicensed users |
| Fits      | Heavy, daily users               | Occasional users, large groups with light use, measuring demand before buying                     |
| Default   | Active once assigned             | Off until a billing policy is connected                                                           |

- Pay-as-you-go never gives the in-app experience in Word, Excel or Teams meetings, and it isn't a prepaid commitment. Many organizations mix the two. Azure meters include Copilot Chat (agents), SharePoint agents and the Microsoft 365 Copilot Retrieval API. Prepaid **Copilot Studio capacity** is an alternative for metered agent use.
- **Free vs metered agents for unlicensed users:** decided by the **knowledge**, not the builder.
  - Instructions and/or public web only → included at no extra cost.
  - Shared tenant data (SharePoint, connectors) → metered, **off by default**, needs pay-as-you-go or Copilot Studio capacity.
  - Licensed users: covered by the license either way.
- **SharePoint agents:**

| Person                              | Create?           | Use? | Who pays      |
| ----------------------------------- | ----------------- | ---- | ------------- |
| Licensed, can add files to the site | Yes               | Yes  | Their license |
| Licensed, view-only                 | No                | Yes  | Their license |
| Unlicensed, pay-as-you-go set up    | No, even as owner | Yes  | Pay-as-you-go |
| Unlicensed, no pay-as-you-go        | No                | No   | n/a           |

- Creating needs a license **and** permission to add files. Billing and permissions follow the **user**, not the agent.
- **Admin switches** (mostly Microsoft 365 admin center > Settings > Copilot):

| Setting                   | Where the control lives                                                                                              | Default                           | Controls                                                                               |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------- | --------------------------------- | -------------------------------------------------------------------------------------- |
| Copilot image generation  | Microsoft 365 admin center (Copilot actions)                                                                         | Not stated by Microsoft           | Creating and editing images; off → only PowerPoint falls back to stock or brand images |
| Screen and camera sharing | Microsoft 365 admin center (Copilot actions)                                                                         | On                                | Vision: showing Copilot the screen or camera                                           |
| Copilot Frontier          | Microsoft 365 admin center (User access)                                                                             | No access                         | Preview features, for all users or specific groups                                     |
| Self-service purchases    | Microsoft 365 admin center (User access)                                                                             | Admin's choice                    | Allow / Allow trials only / Do not allow                                               |
| Web search                | **Allow web search in Copilot** cloud policy, Microsoft 365 Apps admin center (the admin center entry is a shortcut) | Allowed                           | Web grounding for Copilot and Copilot Chat                                             |
| Copilot in Teams meetings | Teams admin center meeting policy (shortcut from M365)                                                               | On with saved transcript required | Whether and how Copilot works in meetings                                              |
| Researcher / Analyst      | Agents page, Microsoft 365 admin center                                                                              | Available to licensed users       | Block either one individually                                                          |

- **Allow trials only:** users can try but not buy, and the trial doesn't convert to paid. **Do not allow:** no purchases and no self-service trial.
- Preview Copilot features are governed only by Copilot Frontier, not Targeted release or Insider channels. **Restricted Content Discovery** hides whole SharePoint sites from Copilot for everyone; it can't target mailboxes or one library.
- Disabling web search removes web grounding for all license types. It doesn't block mailbox or file grounding and doesn't stop Researcher, which then uses work content only. There is no per-site web list for Researcher.
- **Copilot in Teams meetings** (set by the **organizer's** policy):

| Value                                       | Organizer's default                           | Organizer can change?    |
| ------------------------------------------- | --------------------------------------------- | ------------------------ |
| On                                          | Only during the meeting (no saved transcript) | Yes                      |
| On with saved transcript required (default) | During and after (transcript saved)           | **No, enforced**         |
| On with transcript saved by default         | During and after (transcript saved)           | Yes                      |
| Off                                         | Off                                           | Yes, can turn it back on |

- **Off is not a hard block.** Attendees' policies don't decide it; a transcription policy doesn't override the Copilot value.
- **Researcher:** built-in reasoning agent for complex, multi-step research across work content (files, email, meetings, chats, connectors the user can access) and the web if allowed. Produces a **structured report with citations**; deliberately slower. Not for quick summaries (standard Copilot), number crunching (Analyst) or fixed-rule site Q&A (custom agent).
- **Analyst:** built-in reasoning agent for raw data across **several files** (Excel, CSV), **runs Python** and **shows the code**, producing forecasts, trends, outliers and charts.
- Both: pre-installed with the license, **not customizable** (not even in Copilot Studio), not removable by users, **blockable individually** by an admin. Blocking one leaves the other.

| Need                                                                      | Fit              |
| ------------------------------------------------------------------------- | ---------------- |
| Quick summary, reply or first draft                                       | Standard Copilot |
| Deep, cited report from many work and web sources                         | Researcher       |
| Forecasts, trends, charts from raw data with visible code                 | Analyst          |
| Same job for many people, fixed instructions, scoped knowledge or actions | Custom agent     |
| Find a file or message across Microsoft 365                               | Copilot Search   |

- **Where to build a custom agent:**

|                   | SharePoint agent         | Agent Builder                                | Copilot Studio                                     |
| ----------------- | ------------------------ | -------------------------------------------- | -------------------------------------------------- |
| For               | Q&A over one site        | Lightweight Q&A for yourself or a small team | Organization-wide agents, complex solutions        |
| Knowledge         | The site or chosen files | Websites, SharePoint, files, connectors      | All of those plus external data via connectors     |
| Actions/workflows | No                       | No multi-step workflows                      | Yes: multi-step logic, approvals, external systems |

- **Traps:**
  - A user without a license asking about their own mailbox in Copilot Chat outside Outlook gets no automatic grounding.
  - "Metered" follows knowledge source, not the tool used to build the agent.
  - Pay-as-you-go doesn't put Copilot into Word.
  - "Make Researcher follow our rules" → build a custom agent; Researcher can't be modified.

📖 Full lesson: [AB-900 Copilot and Agent Features: Licensing vs Pay-As-You-Go, Admin Settings, Researcher and Analyst](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/ab-900-copilot-agent-features-researcher-analyst/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

## 3.2 Copilot and Agent Administration

- **Assigning Copilot licenses:** only in the **Microsoft 365 admin center**, from **Billing > Licenses** (select Microsoft 365 Copilot) or a user's **Licenses and apps** tab under Users > Active users. Assign to users or groups. Group assignment follows membership with no admin step per change.
- Not in the Power Platform admin center (environments, Copilot Studio), Purview (compliance) or the Microsoft 365 Apps admin center (app policies and updates).

| Role                  | For                                                       | Copilot license work?                 |
| --------------------- | --------------------------------------------------------- | ------------------------------------- |
| License Administrator | Assign, remove, update license assignments                | Yes, least privilege                  |
| Billing Administrator | Purchases, subscriptions, billing, pay-as-you-go policies | Buys; not the role for assigning      |
| Reports Reader        | View usage reports                                        | No, read-only                         |
| Global Administrator  | Everything                                                | Works, but far beyond least privilege |

- **License assigned, no Copilot yet:**
  - Up to **24 hours** to appear in some apps; restart or refresh.
  - **Guests and cross-tenant users** can't be assigned Copilot licenses; they get Copilot through their home organization.
  - Copilot is in every Microsoft 365 Apps channel **except Semi-Annual Enterprise Channel**. Move to Current or Monthly Enterprise Channel.
- **Pay-as-you-go billing policy** links metered usage to an Azure subscription. Created in the Copilot billing settings of the Microsoft 365 admin center (menu names are moving under cost management).
  - Microsoft 365 role: **Billing Administrator, AI Administrator or Global Administrator**.
  - An **Azure subscription in the same tenant** and a **resource group** (can be created in the wizard).
  - **Owner or Contributor** on the subscription and resource group (Azure RBAC, separate from Microsoft 365 roles). The wizard lists only subscriptions where you have one of these; read-only can view costs but not link.
  - Scope: **all users** or a **specific group**. Licensing the users isn't part of setup; serving unlicensed users is the point.
- **Budgets notify; they don't stop usage.** Amount, reset period (month, quarter, year), recipient groups, extra alert percentages beside the default 100%. To limit charges, scope the policy to a group or disconnect it.
- **Connect the policy to a service** (Copilot Chat, SharePoint agents) or it bills nothing. "Policy exists, unlicensed users still can't use metered agents" → missing connection. Disconnecting can take up to two hours. Policies can be edited or deleted.
- **Where spend shows:** the policy's **Budget** tab (current month and last six months) and **Microsoft Cost Management** in Azure (needs at least read on the billing resource group). Usage and adoption reports show people and activity, not cost.
- **Microsoft Copilot usage report** (Reports > Usage):
  - **Enabled** users (hold a license) vs **active** users over 7, 28, 90 or 180 days, an active-users rate, breakdown **by app**.
  - Active needs an **intentional action** such as submitting a prompt; opening the pane doesn't count. Active in one app counts in the overall total too.
  - Names are **concealed by default**; reveal them tenant-wide in Settings > Org settings > Reports (applies to every view and download).
  - Reports Reader is the read-only role. The Purview audit log records Copilot interactions but isn't meant for usage reporting.
- **Copilot Analytics:**

| Tool                     | Where                      | For                                                                                                                  |
| ------------------------ | -------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| Copilot readiness report | Microsoft 365 admin center | IT planning who gets licenses next                                                                                   |
| Copilot usage report     | Microsoft 365 admin center | IT measuring licensed use by app                                                                                     |
| Copilot Dashboard        | Viva Insights (web, Teams) | Leaders: readiness, adoption, impact, sentiment; aggregated with a minimum group size; no admin center access needed |
| Advanced reporting       | Viva Insights              | Analysts building custom reports                                                                                     |

- Senior leaders identified from Entra organizational data get **automatic access** to the Dashboard; others get **delegated access**.
- **Prompts:**

| Type               | Created by                                          | Seen by                                        | Runs on its own? |
| ------------------ | --------------------------------------------------- | ---------------------------------------------- | ---------------- |
| Saved              | Any user                                            | Only that user                                 | No               |
| Shared with a team | Any user, from Copilot Prompt Gallery               | Members of one Teams team                      | No               |
| Scheduled          | A licensed user                                     | Only that user; results in their Copilot chats | Yes              |
| Organizational     | AI Administrator or Search Editor (or Global Admin) | Everyone, as suggestions                       | No               |

- Scheduled prompts run at chosen times and repeats, with the scheduler's access, with optional email notification. Users manage, turn off or delete them in Copilot settings.
- **Admins turn scheduled prompts off org-wide** by setting **Allow the use of connected experiences in Office** to Disabled in Cloud Policy. It also turns off other connected experiences. It isn't retroactive: existing schedules **keep running** to completion, past sessions remain, and users lose the controls to manage them.
- **Organizational prompts:** Microsoft 365 admin center > **Copilot > Prompts**: create, import, edit, pin (up to four shown) and delete. Shown in Copilot Chat, the prompt lab and autosuggestions. **Deletion is permanent**, no restore window: use **Export all prompts** (CSV) first.
- **Agent access settings** (agent settings page, Microsoft 365 admin center):

| Setting                 | Controls                                     | Options                                                 |
| ----------------------- | -------------------------------------------- | ------------------------------------------------------- |
| User access             | Which people can access and install agents   | All users (default), No users, specific users or groups |
| Agent and plugin access | Which publisher types can be installed       | Microsoft, your organization, external publishers       |
| Sharing                 | Org-wide sharing of **Agent Builder** agents | All users, No users, specific users or groups           |

- Pilot with one group → User access, specific group (Copilot Chat stays for everyone). Keep out third-party agents, including future ones → clear external publishers. Sharing with named people stays possible regardless; Copilot Studio agents follow Copilot Studio's sharing controls. Individual agents can also be blocked or pinned.
- **Creating an agent with Agent Builder** (from the Microsoft 365 Copilot app or Teams desktop and web): **describe** it in plain language → **configure** name, instructions, knowledge, starter prompts → **test** in the test pane, then keep private, share or submit to the organization. Needs custom actions or workflows → copy to **Copilot Studio**. Starter prompts appear only inside that agent.
- **Approval:** submitted agents appear under **Requests** on the agents page: Pending review (new), Pending update, Pending activate, and requests to install a blocked Microsoft agent.
  - **Publish to store** wizard: audience (who can install) → preinstall (who gets it installed; optional, set separately) → policy template → consent to requested permissions.
  - **Reject submission** lets the maker revise and resubmit.
  - An update to a published agent needs its own approval; until then everyone keeps the **previous approved version**.
- **Monitoring:**

|                | Microsoft 365 admin center (Agent Registry, usage)                | Power Platform admin center                                        |
| -------------- | ----------------------------------------------------------------- | ------------------------------------------------------------------ |
| Agents covered | All tenant agents, including Agent Builder and Copilot Studio     | Copilot Studio only; Agent Builder agents missing                  |
| Shows          | Name, creator, created, host products, availability; usage        | Active agents (28 days), session success rate, message consumption |
| Actions        | Block, unblock, delete, restore, assign owners, pin, availability | Environments and capacity for Copilot Studio                       |

- **Lifecycle:**
  - **Block:** stops everyone using an Agent Builder or Copilot Studio agent everywhere it's hosted, no time limit, configuration intact. For SharePoint or Microsoft Foundry agents it affects only Copilot Chat availability. Unblock returns it.
  - **Delete:** soft delete, restorable for **30 days** (ownership included), then permanent; or delete permanently at once.
  - **Uninstall:** removes an admin-installed copy from people's apps; store availability is separate.
  - **Assign new owner:** for ownerless or active agents; new owner gets full rights and the previous owner's uploaded files; the previous owner loses access. **Add owner:** adds an owner to an Agent Builder agent, keeping existing ones.
- **Traps:**
  - Budget reached ≠ spending stopped.
  - License Administrator assigns; Billing Administrator buys.
  - Billing policy needs both a Microsoft 365 role and Azure Owner/Contributor.
  - Organizational prompts delete permanently; agents delete softly for 30 days.
  - "Pause an agent" → block. "Retire it" → delete.

📖 Full lesson: [AB-900 Copilot and Agent Administration: Licenses, Pay-As-You-Go Billing, Usage Reports, Prompts and Agent Governance](https://www.savemycert.com/revision/copilot-and-agent-administration-fundamentals/ab-900-copilot-agent-admin-licenses-billing-monitoring/?utm_source=github&utm_medium=readme&utm_campaign=ab-900-study-guide)

[← Back to the study guide](../README.md)
