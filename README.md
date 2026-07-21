# 🚀 Startup Idea Validator

A **Claude Skill** that turns a raw business idea into a polished, investor-style validation report — complete with a scored rubric, SWOT analysis, market sizing, financial modeling, and a phased go-to-market plan.

> Built for [Claude](https://claude.ai) / [Claude Code](https://claude.com/claude-code). Drop it into your skills folder and Claude will interview you about your idea, research the market, and generate a professional PDF report.

---

## ✨ What It Does

Give Claude a business idea, and this skill will:

1. **Interview you** — guided questions to extract the idea, target market, pricing, and costs
2. **Research** — pulls in market size, competitor, and legal/regulatory context
3. **Score it** — evaluates the idea across weighted rubric categories, visualized as a radar chart
4. **Model the finances** — gross margin, LTV:CAC ratio, break-even volume, and startup costs
5. **Generate a report** — a complete, polished PDF ready to share or pitch

---

## 📄 Report Contents

Each generated report includes:

| Section | Description |
|---|---|
| 🎯 **Overall Score** | Weighted score across rubric categories + radar chart |
| 🔲 **SWOT Analysis** | Full 2x2 quadrant — Strengths, Weaknesses, Opportunities, Threats |
| 👤 **Ideal Customer Profiles** | Who the product is really for |
| 📊 **Market Sizing** | Market stats with an optional TAM / SAM / SOM funnel chart |
| 💰 **Financial Model** | Startup costs (itemized table + pie chart), gross margin, LTV:CAC, and break-even analysis |
| ⚖️ **Legal & Regulatory** | Key considerations for the idea's industry/geography |
| 🏷️ **Brand Names** | AI-suggested naming options |
| 📈 **Marketing Strategy** | Phased go-to-market plan |

---

## 📂 Structure

```
startup-idea-validator/
├── SKILL.md                     # Skill definition & trigger conditions
├── references/
│   ├── scoring_rubric.md        # Weighted scoring categories & criteria
│   └── interview_guide.md       # Question flow for extracting idea details
└── scripts/
    ├── generate_report.py       # Builds the PDF report from structured input
    └── sample_input.json        # Example input covering every field
```

---

## ⚙️ How It Works

1. Claude interviews you (or ingests a filled-out brief) and assembles a structured JSON object describing the idea, market, and finances.
2. `generate_report.py` consumes that JSON and computes the derived metrics:
   - **Gross margin %** = `(price_per_unit − cost_per_unit) / price_per_unit`
   - **LTV:CAC ratio** = `ltv / cac`
   - **Break-even volume/month** = `monthly_fixed_costs / contribution_margin_per_unit`
3. The script renders everything — score bars, radar chart, SWOT grid, funnel chart, cost pie chart — into a single polished PDF.

See `scripts/sample_input.json` for a complete example of the expected input shape.

---

## 🛠️ Installation

1. Clone or download this repository.
2. Package it as a `.skill` (zip the `startup-idea-validator/` folder) or place the folder directly in your Claude Skills directory.
3. Upload/enable it in Claude — it will trigger automatically when you ask Claude to validate, score, or write a business plan for a startup idea.

---

## 🧩 Requirements

- Python 3 (for `generate_report.py`)
- A Claude environment with code execution / file creation enabled (Claude.ai or Claude Code)

---

## 📜 License

MIT — free to use, modify, and share.
