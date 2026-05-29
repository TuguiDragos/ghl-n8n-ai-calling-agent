<p align="center">
  <a href="https://n8n.partnerlinks.io/cpqi2mcvtjxx"><img src="https://img.shields.io/badge/Built%20with-n8n-EA4B71?style=flat&logo=n8n&logoColor=white" alt="n8n"></a>
  <img src="https://img.shields.io/badge/CRM-GoHighLevel-2A2D7C?style=flat&logo=gohighlevel&logoColor=white" alt="GoHighLevel">
  <img src="https://img.shields.io/badge/AI-OpenAI-412991?style=flat&logo=openai&logoColor=white" alt="OpenAI">
  <img src="https://img.shields.io/badge/Voice-Vapi-8B5CF6?style=flat&logo=audiomack&logoColor=white" alt="Vapi">
  <img src="https://img.shields.io/badge/Telephony-Twilio-F22F46?style=flat&logo=twilio&logoColor=white" alt="Twilio">
  <img src="https://img.shields.io/badge/Data-Google%20Sheets-34A853?style=flat&logo=google-sheets&logoColor=white" alt="Google Sheets">
  <img src="https://img.shields.io/badge/status-live-2E7D32?style=flat" alt="Status">
</p>

<h1 align="center">AI Call Agent for GoHighLevel: Turn Leads into Booked Appointments on Autopilot</h1>

<p align="center"><i>A fully autonomous AI sales agent that calls your GoHighLevel contacts, qualifies them, books appointments straight into your calendar, and updates your CRM, all while you sleep. Built in n8n with Vapi, Twilio & OpenAI. Updated May 2026.</i></p>

<p align="center">
  <a href="https://tuguidragos.gumroad.com/l/ghl-n8n-vapi-ai-calling-agent">
    <img src="https://img.shields.io/badge/Get%20the%20Full%20Workflow-on%20Gumroad-FF90E8?style=for-the-badge&logo=gumroad" alt="Purchase on Gumroad">
  </a>
</p>


> Stop letting valuable leads die in your CRM. This is not just another workflow. It's a **fully autonomous AI sales agent** designed to turn your GoHighLevel contact lists into qualified, booked appointments.

Imagine a world where every single lead is contacted within minutes by a professional, human-like voice. A world where your sales pipeline fills up while you sleep. That's exactly what this AI automation system delivers.

**This is what a fully automated sales pipeline looks like:**

![Booked appointments pipeline in GoHighLevel](https://raw.githubusercontent.com/TuguiDragos/ghl-n8n-ai-calling-agent/refs/heads/main/Opportunities%20GHL.png)

> **A note on demo results:** the pipeline stages shown in the demo screenshots are from campaigns targeting warm, opt-in leads (users who previously filled out a form to express interest). Your own results will vary and depend on the quality, source, and temperature of your contact list.

<details>
<summary><strong>🆕 What changed in the May 2026 update (full n8n v2 migration)</strong></summary>

<br/>

Full migration to n8n v2 with updated APIs, error handling, documentation, and the complete removal of complex dependencies.

**Added**
- **Zero GHL Developer Apps required:** removed the dependency on the native n8n GoHighLevel node. The workflow now runs purely on standard HTTP Requests using a simple GHL Private API Key (Bearer token).
- **Auto-Mapping Custom Fields:** no more hunting down Custom Field IDs. A new `18.5 Get Custom Fields` Smart Scan node reads your GHL account and maps the correct IDs dynamically.
- **In-canvas interactive tutorials:** 4 beginner-friendly sticky-note tutorials placed directly on the workflow canvas. Setup is visual and takes minutes.
- **Error handling with retry** on all 6 HTTP Request nodes: `retryOnFail: true` with configurable `maxTries` (3–5), `onError: continueRegularOutput` to prevent crashes on transient API failures, and `waitBetweenTries` (2000–5000ms) per node.
- **Quick Setup Guide** sticky note listing every field that requires credentials, node by node.

**Changed**
- **GHL Contacts API migrated** from deprecated `GET /contacts` to `POST /contacts/search` (nodes `GHL Paginated Request` and `GHL Paginated Updated`). Cursor-based pagination replaced with page-based (`meta.nextPage`); request body now includes `locationId`, `pageLimit`, and `page`.
- **GHL Notes API:** call transcript logging moved to the dedicated `POST /notes` endpoint for cleaner CRM profiles.
- **All HTTP Request nodes** upgraded from `typeVersion 4.2` to `4.4`/`4.6`.
- **All If nodes** upgraded from `typeVersion 2.2` to `2.3`.
- **Schedule Trigger** upgraded from `typeVersion 1.2` to `1.3`.

**Fixed**
- **Vapi "Ended" polling:** the call-status loop now accurately handles Vapi's terminal statuses, preventing infinite loops.
- **Critical bug in `Check Final Status + shouldContinue` logic:** the Code node returned a plain `{count, status, shouldContinue}` object (incompatible with n8n v2). Corrected to the proper item format `[{json: {count, status, shouldContinue}}]`.

**Deprecated**
- `GET /contacts` is no longer used (GoHighLevel marked it deprecated in favor of `POST /contacts/search` with advanced filters).
- GHL API Keys auth: GoHighLevel is removing the ability to generate new API Keys. Migrate to **Private Integration Tokens** or **OAuth 2.0**. *(This workflow now natively uses Private Integration Tokens.)*

**Compatibility**
- **n8n:** v2.0+ (tested on v2.x, May 2026)
- **GoHighLevel API:** v2 (Version header: 2023-02-21)
- **Vapi API:** current stable (api.vapi.ai)
- **Node.js:** v24+ (n8n v2 default)

</details>

---

##  Who is this for?

This workflow is engineered specifically for **call centers, high-volume sales agencies, real estate teams, and outreach professionals** who need to dial hundreds or thousands of contacts per day. It completely replaces the manual top-of-funnel dialing process, on autopilot.

> ⚠️ **Legal disclaimer:** this workflow is provided strictly for educational and workflow-automation purposes. We do not encourage or endorse spam calling, robocalling, or unsolicited telemarketing. Anyone who implements this system is solely responsible for ensuring their campaigns comply with all local, federal, and international telephony laws (e.g. TCPA, GDPR). Always ensure you have proper consent to contact your leads.


##  The Engine: A Battle-Tested Automation Core Built for Scale & Reliability

The results in the GHL pipeline aren't magic. They're the product of this n8n workflow, an enterprise-grade automation engine designed for one purpose: to run relentlessly and turn your leads into opportunities.

![n8n workflow overview](https://raw.githubusercontent.com/TuguiDragos/ghl-n8n-ai-calling-agent/refs/heads/main/Workflow%20n8n.png)

This isn't just a simple chain of nodes. It's a complete system with advanced logic for routing, error handling, and data processing, ensuring smooth and reliable operation from start to finish.

### Proven in real-world conditions

We don't just promise performance. We prove it. This workflow has been rigorously tested in live environments to handle high-volume campaigns without failure.

- **Built for endurance:** tested and proven to run for **over 9 hours straight (580+ minutes)** in a single execution without crashes or interruptions, methodically processing contact lists.
- **High-volume throughput:** a single AI agent consistently makes **~300 non-stop calls** in a standard 9:00 AM – 7:30 PM workday. Scale this by simply adding more agents.

![AI agent running](https://raw.githubusercontent.com/TuguiDragos/ghl-n8n-ai-calling-agent/refs/heads/main/Agent%20working.png)

![Live execution runtime](https://raw.githubusercontent.com/TuguiDragos/ghl-n8n-ai-calling-agent/main/Agent1.png)

![Live execution runtime](https://raw.githubusercontent.com/TuguiDragos/ghl-n8n-ai-calling-agent/main/Agent2.png)

#### Key architectural features

- **Smart Caller ID rotation:** to maximize call deliverability and bypass carrier spam filters, the agent automatically rotates calls across a pool of multiple phone numbers (the current setup uses 6 different numbers). This protects your number reputation and dramatically increases the chance of connecting with your lead.
- **Scalable by design:** the workflow is ready for multi-agent deployment. Add new agents and phone numbers without rebuilding the core logic.
- **Bulletproof duplicate prevention:** an advanced GHL tag-locking mechanism guarantees a contact is never called twice, even when processing thousands of leads under parallel conditions.
- **Smart error handling:** logic paths gracefully manage common API issues, ensuring the workflow continues its mission without stopping unexpectedly.

---

##  The Brain: An AI That Understands, Analyzes, and Acts

The system's intelligence goes far beyond the live conversation. The moment a call is finished, a powerful analysis and automation ecosystem takes over directly within your GoHighLevel account, turning raw data into actionable results and qualified appointments.

### 1. Automated call summarization & classification

You don't have to listen to hours of call recordings. Every conversation is automatically transcribed, a concise AI summary is generated, and a custom GHL workflow then analyzes that summary to determine the lead's intent and sorts them for you.

![GHL call classifier workflow](https://raw.githubusercontent.com/TuguiDragos/ghl-n8n-ai-calling-agent/main/Call%20Summary%20Classifier%20GHL.png)
*(This GHL workflow automatically reads call summaries and tags contacts as `Interested`, `Not Interested`, `Appointment Booked`, etc.)*

### 2. Direct-to-calendar appointment booking

When a lead agrees to a meeting, the agent doesn't just take a note. It accesses your GHL calendar via API, finds an available slot, and books the appointment **directly and instantly**. The entire history, from call recording to summary to confirmed appointment, appears seamlessly in the contact's activity feed.

![Confirmed appointment in GHL](https://raw.githubusercontent.com/TuguiDragos/ghl-n8n-ai-calling-agent/refs/heads/main/GHL%20appointment.png)
*(A real appointment booked by the AI, visible directly in the GHL contact view.)*

### 3. A full suite of automations

This isn't just one workflow. It's a suite of interconnected automations designed to handle the entire lead-engagement lifecycle. From voicemail detection to post-call analysis, you get a complete system, not just a single tool.

![GHL workflow suite](https://raw.githubusercontent.com/TuguiDragos/ghl-n8n-ai-calling-agent/refs/heads/main/Workflow%20List%20GHL.png)
*(The package includes multiple, specialized GHL workflows that work together.)*

### 4. Real-time automated tagging

Based on the outcome of every single call, the system applies the correct tags to your contacts in real time. This keeps your CRM perfectly organized and allows for instant lead segmentation and follow-up automation.

![Automated GHL tagging](https://raw.githubusercontent.com/TuguiDragos/ghl-n8n-ai-calling-agent/refs/heads/main/GHL%20tag-VAPI.png)
*(Contacts being automatically tagged based on call events like `customer-ended-call` or `busy`.)*

### 5. Automated multi-channel follow-up (SMS & WhatsApp)

Because each contact is tagged based on the call outcome, you can easily extend the workflow in GHL to trigger automated follow-ups:

- A lead is tagged `No Answer` → the system automatically sends an SMS: *"Hi [Name], this is Daniel from [Company]. I just tried calling about your inquiry. Is there a better time to chat?"*
- A lead is tagged `Interested` → the system sends a WhatsApp message with a link to your brochure or website.

This creates a persistent, automated nurturing sequence that engages leads across multiple platforms, dramatically increasing your chances of conversion.

### A true conversational AI, battle-tested at scale

What makes this system special isn't just the automation. It's the intelligence. The agent's ability to hold natural conversations, handle objections, and interact with your GHL calendar comes from a meticulously crafted Vapi prompt: a set of rules, personality traits, and logical instructions that let the AI think, adapt, and react in real time.

The agent has been deployed in real-world campaigns, successfully handling **thousands of calls** and hundreds of minutes of talk time.

![Vapi analytics dashboard](https://raw.githubusercontent.com/TuguiDragos/ghl-n8n-ai-calling-agent/refs/heads/main/vapi%20dashboard.png)
*(Real performance data showing over 1,700 calls made by the system.)*

![Vapi prompt configuration](https://raw.githubusercontent.com/TuguiDragos/ghl-n8n-ai-calling-agent/refs/heads/main/VAPI%20promt%20model.png)
*(The prompt serves as the central brain, containing all the logic, from personality traits to complex tool integrations.)*

---

## 🎁 The Complete Ecosystem: A "Set It & Forget It" Solution

What good is an AI agent if you have to manually feed it new leads? To make this a truly set-it-and-forget-it lead-conversion system, this package includes a crucial **bonus workflow**.

It automatically syncs **300–400 of your newest unprocessed leads** from a simple Google Sheet into your GoHighLevel CRM every single night. At 9 AM the next morning, the AI Calling Agent automatically wakes up and starts calling the fresh list. You don't have to lift a finger.

![Automated lead importer workflow](https://raw.githubusercontent.com/TuguiDragos/ghl-n8n-ai-calling-agent/main/Upload%20GHL%20contacts.png)

#### Why this is a custom-engineered solution

A technical note for power users: the standard GoHighLevel node in n8n is limited to fetching only the last 100 contacts, a major bottleneck for any serious campaign. We bypassed this limitation by building a custom solution that interacts **directly with the GHL API using pagination**, reliably fetching a large, fresh batch of leads every day. It's a tested, 100% functional method designed for stability and performance, protecting your system from being overloaded while ensuring your agent never runs out of work.

<p align="center">
  <a href="https://tuguidragos.gumroad.com/l/ghl-n8n-vapi-ai-calling-agent">
    <img src="https://img.shields.io/badge/Get%20the%20Full%20Workflow-on%20Gumroad-FF90E8?style=for-the-badge&logo=gumroad" alt="Purchase on Gumroad">
  </a>
</p>

---

## ❓ Frequently Asked Questions

**Why should I buy this product instead of building it myself?**

You're acquiring a production-ready, battle-tested AI automation system that represents **hundreds of hours of research, development, debugging, and real-world testing**: from bypassing GHL API limitations with custom pagination, to engineering a bulletproof "locking" system to prevent duplicate calls, to refining the AI's conversational nuance over thousands of live interactions. It saves you **months of frustration** and lets you start booking appointments tomorrow, not next quarter.

**What are the ongoing operational costs?**

Besides your standard `GHL` and `n8n` subscriptions, the operational costs for `Vapi` and `Twilio` are very low. On average, a call costs between **$0.05 – $0.10**, depending on its duration. The system is designed to be highly efficient to keep your costs minimal.


##  About the Creator

Built by **Țugui Dragoș** `|QC⟩`. I build automation that runs without supervision: n8n workflows, AI agents, and the quiet machinery behind a business.

<p align="center">
  <a href="https://www.tuguidragos.com/"><img src="https://img.shields.io/badge/Website-2E7D32?style=flat&logo=safari&logoColor=white" alt="Website"></a>
  <a href="https://blog.tuguidragos.com"><img src="https://img.shields.io/badge/Blog-738A05?style=flat&logo=ghost&logoColor=white" alt="Blog"></a>
  <a href="https://n8n.io/creators/tuguidragos/"><img src="https://img.shields.io/badge/n8n%20Creator-EA4B71?style=flat&logo=n8n&logoColor=white" alt="n8n Creator"></a>
  <a href="https://tuguidragos.gumroad.com"><img src="https://img.shields.io/badge/Gumroad-FF90E8?style=flat&logo=gumroad&logoColor=black" alt="Gumroad"></a>
  <a href="https://www.linkedin.com/in/tuguidragos"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
  <a href="https://github.com/TuguiDragos"><img src="https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white" alt="GitHub"></a>
</p>

**contact@tuguidragos.com** for questions, custom builds, or smart automation work.
If this project helped or inspired you, leave a ⭐ and share it with your crew.

---

## 🧩 Tags & Search Keywords

GoHighLevel AI call agent, GHL n8n workflow, AI phone agent for GoHighLevel, automated appointment booking GHL, n8n Vapi Twilio integration, AI voice agent GoHighLevel, autonomous SDR system, high-volume AI dialer, lead qualification voice AI, GHL API v2 pagination, n8n v2 AI workflow, AI cold calling automation, real estate AI calling agent, call center automation n8n, Vapi GoHighLevel integration, OpenAI smart caller, automated CRM tagging, direct-to-calendar AI booking, TCPA-aware auto dialer concepts, no-code AI sales agent, appointment setter AI, GHL voicemail detection, multi-agent calling system, caller ID rotation n8n, AI rep that never sleeps.
