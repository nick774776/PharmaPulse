# 💊 PharmaPulse — Automated LinkedIn Content Workflow

> An **n8n** automation that posts daily pharma industry insights with AI-generated images to LinkedIn — boosting engagement, visibility, and thought leadership on autopilot.

---

## 🧬 Overview

**PharmaPulse** is a fully automated LinkedIn content pipeline built with [n8n](https://n8n.io/). Every morning at **7:00 AM**, the workflow fires up, researches the latest hot topics in the pharmaceutical industry, generates a compelling post with an AI-crafted image, appends relevant hashtags for SEO, and publishes it directly to your LinkedIn profile — all without manual intervention.

This workflow is ideal for:
- Pharma professionals looking to build a personal brand on LinkedIn
- Marketing teams in pharma/biotech wanting consistent thought leadership content
- Consultants who want to stay visible in the industry without spending time on content creation

---

## 🗺️ Workflow Architecture

```
Schedule Trigger (7AM Daily)
        │
        ▼
Content Topic Generator
  ├── OpenAI Chat Model        ← Identifies trending pharma topics
  └── Structured Output Parser ← Parses topic into structured data
        │
        ▼
Content Creator
  ├── OpenAI Chat Model1       ← Generates the LinkedIn post body
  └── Structured Output Parser1← Structures the post content
        │
        ├─────────────────────────┬─────────────────────────┐
        ▼                         ▼                         │
  OpenAI (Generate Image)   Hashtag Generator /SEO         │
  (DALL·E image for post)    ├── OpenAI Chat Model2         │
                             └── Structured Output Parser2  │
        │                         │                         │
        └──────────────┬──────────┘                         │
                       ▼
                 Merge (append)
                       │
                       ▼
              Remove Duplicates
                       │
                       ▼
            Create a Post (LinkedIn)
```

---

## ✨ Key Features

| Feature | Description |
|---|---|
| ⏰ **Scheduled Automation** | Triggers daily at 7:00 AM — no manual work needed |
| 🧠 **AI Topic Discovery** | GPT identifies the latest trending pharma topics each day |
| ✍️ **AI Content Writing** | Generates engaging, professional LinkedIn posts |
| 🖼️ **AI Image Generation** | DALL·E creates a unique, relevant image for each post |
| #️⃣ **SEO Hashtag Engine** | Auto-generates relevant hashtags to maximize reach |
| 🔗 **Direct LinkedIn Posting** | Publishes directly to LinkedIn via API — no copy-paste |
| 🧹 **Duplicate Prevention** | Deduplication step ensures no repeated content |

---

## 🛠️ Tech Stack

- **[n8n](https://n8n.io/)** — Workflow automation platform
- **OpenAI GPT** — Topic discovery, content generation, hashtag creation
- **OpenAI DALL·E** — AI image generation
- **LinkedIn API** — Automated post publishing

---

## 📋 Prerequisites

Before setting up this workflow, ensure you have:

- [ ] An **n8n** instance (self-hosted or n8n Cloud)
- [ ] An **OpenAI API key** (for GPT + DALL·E)
- [ ] A **LinkedIn Developer App** with posting permissions
- [ ] LinkedIn OAuth2 credentials configured in n8n

---

## 🚀 Setup Guide

### 1. Clone / Import the Workflow

Download the workflow JSON and import it into your n8n instance:

```
n8n → Workflows → Import from File → Select workflow.json
```

### 2. Configure Credentials

Add the following credentials in n8n (`Settings → Credentials`):

| Credential | Used By |
|---|---|
| OpenAI API Key | All OpenAI nodes |
| LinkedIn OAuth2 | "Create a Post" node |

### 3. Customize the Content Topic Prompt

In the **Content Topic Generator** node, update the system prompt to target your niche:

```
Examples:
- "Focus on oncology drug approvals and clinical trials"
- "Cover FDA regulatory updates and drug safety news"
- "Highlight generics, biosimilars, and pricing trends"
```

### 4. Set Your Posting Schedule

The **Schedule Trigger** is pre-configured for **7:00 AM daily**. To adjust:

```
Schedule Trigger node → Edit → Set your preferred timezone and time
```

### 5. Activate the Workflow

Toggle the workflow to **Active** and you're live! 🎉

---

## 📁 Project Structure

```
pharmapulse-linkedin-workflow/
│
├── workflow.json              # Main n8n workflow export
├── README.md                  # This file
├── docs/
│   ├── workflow-diagram.png   # Visual architecture diagram
│   └── setup-guide.md         # Detailed setup instructions
└── prompts/
    ├── topic-generator.txt    # System prompt for topic discovery
    ├── content-creator.txt    # System prompt for post writing
    └── hashtag-generator.txt  # System prompt for SEO hashtags
```

---

## 🔧 Customization Options

### Changing the Post Tone

Edit the **Content Creator** system prompt to adjust tone:
- `Professional & analytical` — for regulatory/clinical audiences
- `Conversational & engaging` — for general pharma professionals
- `Data-driven` — for investors and business audiences

### Targeting Specific Pharma Niches

Update the topic generator prompt to focus on:
- Clinical trials & drug approvals
- Pharmacovigilance & drug safety
- Biotech & biosimilars
- Pharma marketing & commercialization
- Healthcare policy & pricing

### Posting Frequency

Adjust the schedule trigger for different cadences:
- Daily (current default)
- Weekdays only
- Multiple posts per day

---

## 📊 Expected Outcomes

Consistent daily posting using this workflow can help you achieve:

- 📈 **Increased profile views** from showing up in your network's feed daily
- 🤝 **Higher connection requests** from industry peers engaging with your content
- 💬 **More comments & shares** through relevant, timely topics + visual content
- 🏆 **LinkedIn Creator Mode** eligibility through consistent posting
- 🔍 **Improved discoverability** via optimized hashtags and keyword-rich posts

---

## ⚠️ Important Notes

- **LinkedIn API Rate Limits**: LinkedIn allows a limited number of posts per day via API. This workflow is designed for 1 post/day, which is within safe limits.
- **OpenAI Costs**: Each run uses GPT (3 calls) + DALL·E (1 call). Monitor your OpenAI usage dashboard to manage costs.
- **Content Review**: Although the workflow runs autonomously, it's recommended to periodically review posts for accuracy, especially for regulatory or clinical claims.

---

## 🤝 Contributing

Contributions are welcome! Feel free to:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-feature`)
3. Commit your changes (`git commit -m 'Add new feature'`)
4. Push to the branch (`git push origin feature/new-feature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 👤 Author

**Nikhil Kumar**
Pharmacologist | Marketing & Consulting Enthusiast
[NIPER SAS Nagar, India]

> *"Automating thought leadership so the science speaks — every single day."*

---

## ⭐ Support

If this workflow helped you, consider giving it a **star** on GitHub!

Found a bug or have a feature request? [Open an issue](../../issues).
