# 🎯 Remote Jobs Auto-Apply — Free Stack (RSS + Gemini + Gmail + Telegram)

![Status](https://img.shields.io/badge/status-working%20workflow-brightgreen)
![Type](https://img.shields.io/badge/type-n8n%20automation-blue)
![Platform](https://img.shields.io/badge/platform-n8n-orange)
![AI](https://img.shields.io/badge/AI-Google%20Gemini%202.5%20Flash-blueviolet)
![Email](https://img.shields.io/badge/email-Gmail-D14836)
![Delivery](https://img.shields.io/badge/delivery-Telegram-2CA5E0)
![Cost](https://img.shields.io/badge/cost-100%25%20free%20stack-brightgreen)
![License](https://img.shields.io/badge/license-MIT-green)

An **n8n workflow** that automatically **finds remote jobs**, **scores them against your CV**, **writes a tailored cover letter**, and **sends the application via Gmail** — then **notifies you on Telegram**. Everything runs on a **free stack**: RSS feeds + Gemini 2.5 Flash free tier + Gmail + Telegram.

> ⚠️ **Dry-run mode is ON by default** (`dryRun: true`). No emails are sent until you explicitly turn it off. **Read the safety section before changing that flag.**

---

## ⚠️ What this project is and is not

### ✅ What this is
- A **working end-to-end n8n workflow** covering discovery → scoring → writing → sending → notification.
- A **free-stack** solution: RSS feeds, Gemini free tier, Gmail OAuth, Telegram bot. No paid APIs required.
- A **CV-grounded evaluator** — Gemini scores jobs **only against evidence in your uploaded CV**.
- A **strict scorer** — 90+ is only allowed when core skills, domain, and seniority all clearly match.
- A **cover-letter writer** — Gemini drafts 170–230 words, no invented employers, no invented numbers.
- A **safety-first design** — dry run on by default, human-readable Telegram summary of every decision.

### ❌ What this is not
- ❌ **Not a mass-apply bot.** Max 3 applications per run, max 12 jobs evaluated per run.
- ❌ **Not a scraping tool.** It reads **public RSS feeds** only.
- ❌ **Not a guarantee of interviews.** It applies; you still get hired by humans.
- ❌ **Not compliant-by-default.** Sending unsolicited applications may violate some employers' ToS or local laws. You are responsible.
- ❌ **Not zero-config.** You must upload a CV, set your personal data, and connect 3 credentials.
- ❌ **Not persistent across restarts** unless the workflow is **Active** (see “Static state” below).

---

## 🎯 Purpose

Applying to remote jobs is a volume game that punishes honest effort:

- 90% of listings are irrelevant or on-site.
- Writing a **good** cover letter takes 20–40 minutes each.
- The **best** listings are gone within hours.

This workflow compresses the whole loop into one scheduled run:

> **Read RSS → score every job against your CV → write a real cover letter → send it (or tell you why not) → notify you on Telegram.**

Every design decision protects one thing: **you never send a bad application.**

---

## 🚀 Quick start

### 1. Import the workflow
```text
n8n → Workflows → ⋯ menu → Import from File → select the JSON file# 🎯 Remote Jobs Auto-Apply — Free Stack (RSS + Gemini + Gmail + Telegram)

![Status](https://img.shields.io/badge/status-working%20workflow-brightgreen)
![Type](https://img.shields.io/badge/type-n8n%20automation-blue)
![Platform](https://img.shields.io/badge/platform-n8n-orange)
![AI](https://img.shields.io/badge/AI-Google%20Gemini%202.5%20Flash-blueviolet)
![Email](https://img.shields.io/badge/email-Gmail-D14836)
![Delivery](https://img.shields.io/badge/delivery-Telegram-2CA5E0)
![Cost](https://img.shields.io/badge/cost-100%25%20free%20stack-brightgreen)
![License](https://img.shields.io/badge/license-MIT-green)

An **n8n workflow** that automatically **finds remote jobs**, **scores them against your CV**, **writes a tailored cover letter**, and **sends the application via Gmail** — then **notifies you on Telegram**. Everything runs on a **free stack**: RSS feeds + Gemini 2.5 Flash free tier + Gmail + Telegram.

> ⚠️ **Dry-run mode is ON by default** (`dryRun: true`). No emails are sent until you explicitly turn it off. **Read the safety section before changing that flag.**

---

## ⚠️ What this project is and is not

### ✅ What this is
- A **working end-to-end n8n workflow** covering discovery → scoring → writing → sending → notification.
- A **free-stack** solution: RSS feeds, Gemini free tier, Gmail OAuth, Telegram bot. No paid APIs required.
- A **CV-grounded evaluator** — Gemini scores jobs **only against evidence in your uploaded CV**.
- A **strict scorer** — 90+ is only allowed when core skills, domain, and seniority all clearly match.
- A **cover-letter writer** — Gemini drafts 170–230 words, no invented employers, no invented numbers.
- A **safety-first design** — dry run on by default, human-readable Telegram summary of every decision.

### ❌ What this is not
- ❌ **Not a mass-apply bot.** Max 3 applications per run, max 12 jobs evaluated per run.
- ❌ **Not a scraping tool.** It reads **public RSS feeds** only.
- ❌ **Not a guarantee of interviews.** It applies; you still get hired by humans.
- ❌ **Not compliant-by-default.** Sending unsolicited applications may violate some employers' ToS or local laws. You are responsible.
- ❌ **Not zero-config.** You must upload a CV, set your personal data, and connect 3 credentials.
- ❌ **Not persistent across restarts** unless the workflow is **Active** (see “Static state” below).

---

## 🎯 Purpose

Applying to remote jobs is a volume game that punishes honest effort:

- 90% of listings are irrelevant or on-site.
- Writing a **good** cover letter takes 20–40 minutes each.
- The **best** listings are gone within hours.

This workflow compresses the whole loop into one scheduled run:

> **Read RSS → score every job against your CV → write a real cover letter → send it (or tell you why not) → notify you on Telegram.**

Every design decision protects one thing: **you never send a bad application.**

---

## 🚀 Quick start

### 1. Import the workflow
```text
n8n → Workflows → ⋯ menu → Import from File → select the JSON file
2. Connect 3 credentials
Credential	Type in n8n	Where to get it
Gemini API key	httpHeaderAuth	https://aistudio.google.com/app/apikey
Gmail OAuth2	gmailOAuth2	n8n → Credentials → Gmail OAuth2
Telegram Bot	telegramApi	https://t.me/BotFather
Gemini header credential must be:

text
Name:  x-goog-api-key
Value: <your Gemini API key>
3. Fill in the Config node
Field	What to put
minScore	90 (minimum match score, 0–100)
maxAgeDays	7 (ignore jobs older than this)
maxJobsToEvaluate	12 (cap on Gemini calls per run)
maxApplicationsPerRun	3 (cap on actual applications)
dryRun	true (leave ON until verified)
targetRegions	e.g. Algeria, Europe (EU/UK/EEA), USA, Canada, Worldwide/Anywhere
telegramChatId	your Telegram chat ID
candidateName	your full name
candidateEmail	your Gmail
candidatePhone	your phone
candidateLinkedIn	your LinkedIn URL
cvLink	public link to your CV
4. Upload your CV (first run only)
Open the workflow → click CV Upload Form → copy the webhook URL.

Open the URL in a browser.

Upload PDF / PNG / JPG of your CV.

The workflow:

sends the file to Gemini Read CV

extracts plain text

stores it in workflow static data ($getWorkflowStaticData('global').cvText)

This text is reused by every subsequent scheduled run.

5. Unpin the sample data
The following nodes ship with pinData for safe testing:

Node	Pinned content
CV Source	sample CV text
RemoteOK RSS	1 sample job (remote, worldwide)
WWR RSS	1 sample job (on-site → should be filtered)
Remotive RSS	1 sample job (React, remote EU)
Before real runs: right-click each pinned node → Unpin. Otherwise the workflow never hits the real feeds.

6. Test in dry run
Keep dryRun = true.

Click Execute Workflow.

Watch Telegram: you'll receive what would have been sent, but no email leaves Gmail.

7. Go live
Set dryRun = false.

Add a Schedule Trigger in front of Config (e.g. every 6 hours) or replace the CV form trigger with a schedule.

Activate the workflow (required for static data to persist and for the schedule to fire).

In Workflow Settings → Error Workflow, select this same workflow — that wires the built-in Error Trigger.

Requirements: n8n 1.x+, a Gemini API key (free tier is fine), a Gmail account with OAuth2, a Telegram bot, and internet access.

🔄 Workflow Overview
text
Branch 1 — CV ingestion (one-time)
┌──────────────────┐   ┌──────────────────┐   ┌──────────────────┐   ┌────────────────┐
│ CV Upload Form   │──►│ Prepare CV Req.  │──►│ Gemini Read CV   │──►│ Extract CV Text│
└──────────────────┘   └──────────────────┘   └──────────────────┘   └────────┬───────┘
                                                                              │ (writes static state)
Branch 2 — Main pipeline                                                      ▼
┌────────┐   ┌───────────┐   ┌───────────┐   ┌───────────┐   ┌──────────┐   ┌────────┐
│ Config │──►│ CV Source │──►│ RemoteOK  │──►│           │──►│ Normalize│──►│ Build  │
└────────┘   └───────────┘   │ WWR       │   │ Merge     │   │ + Filter │   │ Eval   │
                             │ Remotive  │   │ Feeds     │   └────┬─────┘   │ Prompt │
                             └───────────┘   └───────────┘        │         └───┬────┘
                                                                             ▼
   ┌────────────────────┐   ┌────────────────────┐   ┌────────────────────┐
   │ Gemini Evaluate    │──►│ Parse & Select     │──►│ Build Letter Prompt│
   │ Match              │   │ Best (top N)       │   └─────────┬──────────┘
   └────────────────────┘   └────────────────────┘             ▼
   ┌────────────────────┐   ┌────────────────────┐   ┌────────────────────┐
   │ Gemini Write       │──►│ Prepare Email      │──►│ Can Send Email?    │
   │ Cover Letter       │   └────────────────────┘   └────┬───────────┬───┘
   └────────────────────┘                                 │ yes       │ no
                                                          ▼           ▼
                                              ┌──────────────┐  ┌──────────────────┐
                                              │ Gmail Send   │  │ Format Telegram  │
                                              │ Application  │  │ (manual reason)  │
                                              └──────┬───────┘  └────────┬─────────┘
                                                     └──────────┬────────┘
                                                                ▼
                                                       ┌──────────────────┐
                                                       │ Telegram Notify  │
                                                       └──────────────────┘

Branch 3 — Errors
┌───────────────┐   ┌──────────────┐   ┌──────────────────────┐
│ Error Trigger │──►│ Format Error │──►│ Telegram Error Alert │
└───────────────┘   └──────────────┘   └──────────────────────┘
🧩 Feature breakdown by node
⚙️ Config — single source of truth
Holds all tunable parameters. Every other node reads from it via $('Config').first().json. Change something here; the entire pipeline adapts.

📄 CV Source — static-state gate
Reads cvText from workflow static data.

Throws a clear error if no CV was uploaded yet (< 200 chars).

Prevents silent "empty CV" evaluations.

📡 RemoteOK RSS, WWR RSS, Remotive RSS — free feeds
Feed	URL
RemoteOK	https://remoteok.com/remote-jobs.rss
We Work Remotely	https://weworkremotely.com/remote-jobs.rss
Remotive	https://remotive.com/remote-jobs/feed
All three:

Retry 3× with 5s delay on failure.

Never fail the whole workflow (onError: continueRegularOutput).

🔀 Merge Feeds — 3-input fan-in
Concatenates all sources into one stream.

🧹 Normalize and Filter — the first line of defense
Runs before any Gemini call (cheap filtering first):

javascript
✅ Normalizes:
   - strips HTML, decodes entities, trims
   - extracts emails (filters noreply/example/wixpress/sentry)
   - parses dates, sorts newest-first

✅ Keeps only:
   - title + link present
   - no duplicate links in this run
   - not seen in the last 30 days (static state)
   - published within maxAgeDays

❌ Drops:
   - on-site / in-office / hybrid posts that never mention "remote"
   - non-URL items, empty items, errored items

✂️ Trims result to maxJobsToEvaluate (default 12)
🧠 Build Eval Prompt — strict recruiter prompt
Uses a very strict ATS-style system prompt with:

match_score — evidence-based only, 90+ only if all core skills + domain + seniority match

job_quality_score — clarity, seriousness, realistic requirements

is_remote — true only if explicitly fully remote

location_ok — true only if open to target regions

contact_email — must literally appear in the posting

summary_ar — 1–2 sentence Arabic summary

Output mode: responseMimeType: application/json — no markdown, no extra text.

🤖 Gemini Evaluate Match — batched HTTP call
Model: gemini-2.5-flash

batchSize: 1, batchInterval: 7000 — respects the free-tier rate limit

Timeout: 90s

Retries: 4× with 5s delay

Failure: onError: continueRegularOutput (a failed eval doesn't kill the run)

🎯 Parse and Select Best — scoring & selection
Parses Gemini JSON ("```json" fences stripped defensively).

On parse failure: does NOT mark job as seen → retried next run.

Applies minScore gate + 
is_remote
 + 
location_ok
.

Computes a weighted final score:

text
finalScore = match * 0.60 + quality * 0.25 + recency * 0.15
Filters contact email: only accepts it if it literally appears in the description.

Sorts by finalScore desc.

Caps at maxApplicationsPerRun (default 3).

Throws if every Gemini call in the batch failed (surfaces error to Telegram).

✉️ Build Letter Prompt — cover-letter writer
System prompt enforces:

Facts only from the CV — no invented employers, degrees, numbers, certifications, or tools.

170–230 words, plain text, no markdown, no placeholders.

Structure: greeting → purpose → 2 evidence paragraphs → call proposal → sign-off.

Language matches the job posting (defaults to English).

Explicit statement of remote availability.

Returns JSON: { "subject": string, "body": string }.

✍️ Gemini Write Cover Letter — batched HTTP call
Same batching (7s interval), same retries, same onError: continue.

📧 Prepare Email — assembly + dry-run gate
Builds signature from Config (name | email | phone, LinkedIn, CV link).

emailReady = contactEmail && body && !dryRun.

Computes a human-readable manualReason when it cannot send:

"No email in posting — apply via the link"

"Could not generate cover letter"

"Dry run enabled — no email sent"

🔀 Can Send Email — IF gate
true → Gmail Send Application

false → Format Telegram (manual apply notification)

📨 Gmail Send Application — real send
Sends to contactEmail

Subject + body from the previous node

senderName from Config

Retries 3× with 5s delay

onError: continueRegularOutput — a failed send doesn't crash the run

💬 Format Telegram — HTML summary
Builds an HTML message with:

✅ / ❌ / 📝 status line

💼 Job title, 🏢 Company, 🌐 Source

🎯 Match / Quality / Final scores

🔗 Job URL

📧 Contact email (or "none")

📝 Arabic summary

✔️ Strengths, ⚠️ Missing requirements

✉️ Cover-letter subject + body (up to 1,800 chars)

📲 Telegram Notify — delivery
Chat ID from Config

HTML parse mode

Retries 3× with 4s delay

🚨 Error Trigger → Format Error → Telegram Error Alert
Wired via Workflow Settings → Error Workflow → this same workflow.

Sends a compact error card: workflow name, node, message, execution URL.

Uses the same Telegram bot.

🏗️ Architecture
Layer	Role	Implementation
Ingestion	Fetch raw jobs	3 × RSS nodes
Normalization	Clean, dedupe, age-filter	Normalize and Filter (JS)
Reasoning	Score, decide, write	Gemini 2.5 Flash × 2
Selection	Rank + cap	Parse and Select Best (JS)
Delivery	Send email	Gmail node
Notification	Human summary	Telegram node
State	Remember CV + seen links	$getWorkflowStaticData('global')
Safety	Dry run, caps, error alerts	Config + Error Trigger
📱 Sample Telegram Output
text
✅ تم إرسال التقديم عبر Gmail

💼 Senior Automation & AI Engineer — Polymer Manufacturing
🏢 PolyTech Systems
🌐 المصدر: remoteok.com
🎯 نسبة التوافق: 94% | الجودة: 88 | التقييم النهائي: 92.1
🔗 https://remoteok.com/remote-jobs/...
📧 careers@polytech-systems.example.com

📝 وظيفة عن بُعد بالكامل لشركة في تصنيع البوليمرات،
تبحث عن مهندس أتمتة وخبرة في PLC وPython والتعلم الآلي.

✔️ نقاط القوة: PLC, Python, polymer processing, ML
⚠️ نواقص: none

✉️ الموضوع: Application - Senior Automation & AI Engineer - Your Name
[cover letter body preview up to 1800 chars]
🔧 Customization
Change the region filter
Edit Config.targetRegions. Example:

text
Algeria, MENA, Europe (EU/UK/EEA), Worldwide/Anywhere
Tune the scoring weights
In Parse and Select Best:

javascript
const finalScore = Math.round(
  (match * 0.6 + quality * 0.25 + recency * 0.15) * 10
) / 10;
Add a new RSS source
Add a RSS Feed Read node.

Point it to a new feed URL.

Connect it to a new input on Merge Feeds (increase numberInputs).

Change the Gemini model
Replace in both HTTP nodes:

text
gemini-2.5-flash   →   gemini-2.5-pro   (or any supported model)
Change the rate limit
Both Gemini HTTP nodes have:

json
{ "batchSize": 1, "batchInterval": 7000 }
Lower the interval to speed up (risk 429s), raise it to be safer.

Change the cover-letter tone
Edit the system prompt in Build Letter Prompt — but keep the constraint "facts only from the CV" intact.

🛡️ Safety mechanisms
This workflow has five independent safety layers:

dryRun: true by default — no email sent until explicitly disabled.

maxApplicationsPerRun: 3 — hard cap on real applications per run.

maxJobsToEvaluate: 12 — cap on Gemini calls per run.

minScore: 90 — strict match threshold; most jobs fail it.

Error workflow — every crash is reported to Telegram with the failing node name.

Additionally:

Contact-email verification — only accepts emails that literally appear in the posting.

No email → manual apply — the workflow refuses to invent a contact.

Failed evaluation ≠ seen — a failed Gemini call is retried next run instead of being silently marked applied.

⚠️ Known limitations
Static state requires an Active workflow. If you run it manually and reload n8n, cvText and the seen-links store may reset. Activate the workflow for persistent state.

pinData ships with the template. Remember to unpin the four nodes (CV Source + 3 RSS) before real runs, or the workflow will keep processing sample jobs forever.

No true deduplication across feeds. Two RSS sources may list the same job with different URLs — they'll be treated as two jobs.

No company/URL-level deduplication. Same employer, different postings = two applications.

Gmail sending account must match candidateEmail. Otherwise replies land in the wrong inbox.

Free tier limits. Gemini free tier can be throttled; the 7-second interval helps but doesn't guarantee zero 429s.

No application tracking. Once sent, nothing records whether the employer replied.

No unsubscribe / no opt-out handling. Employers have no way to stop future applications.

No GDPR / privacy controls. Your CV, email, phone are sent to Gemini and to employers — check local law before enabling.

onlyPostsNewerThan-style date filters don't exist for RSS. Age is filtered after fetching, so the first run may spend Gemini quota on stale posts.

dryRun string comparison is lenient. "true" and true both work; other truthy strings don't.

🐛 Troubleshooting
Issue	Likely cause	Fix
لا توجد سيرة ذاتية محفوظة	No CV uploaded yet, or state lost	Open the CV Upload Form, re-upload
فشلت كل طلبات Gemini	Wrong header name, expired key, or quota hit	Verify x-goog-api-key header credential; check Google AI Studio quota
No Telegram message	Chat ID wrong, or bot not started	Send /start to the bot once, then re-run
No Gmail sent	dryRun = true still on	Set dryRun = false
Gmail sends but not received	Gmail spam filter, or sender ≠ candidateEmail	Check spam; align sender and candidateEmail
Sample jobs still appear	pinData still attached	Right-click each pinned node → Unpin
seen store grows forever	Expected — pruned after 30 days automatically	No action needed
Every run finds 0 jobs	minScore too strict, or maxAgeDays too short	Lower minScore to 85, raise maxAgeDays to 14
Gemini reads the CV every run	Workflow not Active, or static state not persisting	Activate the workflow
📁 File structure
text
.
├── Remote Jobs Auto-Apply (Free Stack RSS + Gemini + Gmail + Telegram).json
└── README.md
🤝 Contributing
Fork the repository

Create a feature branch

Submit a pull request

📄 License
MIT License. See LICENSE file for details.

Disclaimer:

This workflow sends real emails on your behalf when dryRun is false. Test thoroughly in dry-run mode first.

Scraping/sending against public RSS + employer emails may violate some employers' terms or local anti-spam laws. Use responsibly.

Your CV, contact info, and job posting texts are sent to Google's Gemini API. Review Google's data handling policy before enabling.

📞 Support
Open a GitHub issue

Check n8n community forums
