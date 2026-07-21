# Startup Idea Validator — Claude Skill

A [Claude Skill](https://support.claude.com/en/articles/12512176-what-are-skills) that turns a rough business idea into a full validation report: an interview, real web research, a weighted score across 7 categories, and a polished PDF with a radar chart, full SWOT, ideal customer profiles, market sizing, competitor analysis, and a financial model (startup costs, unit economics, break-even).

![Score radar chart and SWOT quadrant](readme_assets/preview-radar-swot.png)
![Financial model: startup costs, unit economics, break-even](readme_assets/preview-financials.png)

## What it does

Describe a business idea to Claude (with this skill enabled) and it will:

1. Ask clarifying questions about the idea, target customer, pricing, and market
2. Research the market, competitors, and legal/regulatory landscape with web search
3. Score the idea across 7 weighted categories (problem-solution fit, market size, differentiation, business model, execution feasibility, legal risk, go-to-market)
4. Generate a PDF report with:
   - Overall score + at-a-glance radar chart
   - Full SWOT (strengths, weaknesses, opportunities, threats)
   - Ideal customer profiles
   - Market size (TAM/SAM/SOM) with an optional funnel chart
   - Competitive landscape
   - Financial model — startup costs (with pie chart), unit economics (gross margin, LTV:CAC), break-even analysis
   - Legal considerations, brand name ideas, phased marketing strategy, and a final verdict

## Requirements

- A Claude account (Free, Pro, Max, Team, or Enterprise all support Skills)
- **Code execution and file creation** enabled in your Claude settings (this skill runs a Python script to build the PDF)

## How to install

1. Download **`startup-idea-validator.zip`** from this repo (or from the [Releases](../../releases) page if you've published one)
2. In Claude, go to **Settings → Capabilities** (or **Customize**, depending on your plan) **→ Skills**
3. Click **Upload skill** and select the downloaded zip — don't unzip it first, upload it as-is
4. Toggle the skill on
5. Start a new chat and describe a business idea, e.g. *"I want to validate an idea for a subscription meal-prep service for students"* — Claude will invoke the skill automatically

No need to say "use the skill" explicitly — Claude picks it up from the description of what you're asking for.

## Repo structure

```
startup-idea-validator/
├── SKILL.md                       # Core instructions Claude follows
├── references/
│   ├── scoring_rubric.md          # Defines the 7 scoring categories
│   ├── interview_guide.md         # What to ask the user before scoring
│   └── report_schema.md           # Full JSON schema for the report data
└── scripts/
    ├── generate_report.py         # Builds the PDF (charts, tables, layout)
    └── sample_input.json          # Example input covering every field
```

`startup-idea-validator.zip` is this same folder pre-packaged for upload — that's the file to download if you just want to use the skill. The unzipped files above are here so anyone can read, fork, or modify the skill's instructions and code directly on GitHub.

## Customizing

- Edit `SKILL.md` to change the workflow, tone, or scoring approach.
- Edit `scripts/generate_report.py` to change the PDF's layout, charts, or add new sections.
- Edit `references/scoring_rubric.md` to change what each of the 7 categories rewards.

After editing, re-zip the **`startup-idea-validator` folder itself** (not its contents) to re-package it for upload. The zip must contain the folder as its root — see [Claude's skill packaging docs](https://support.claude.com/en/articles/12512198-how-to-create-custom-skills) if you hit an upload error.

## License

Add a license of your choice here (MIT is a common default for a project like this) if you want to make reuse terms explicit.
