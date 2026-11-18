# AI Data Analyst Agent

I built a chat assistant that answers questions about customer churn and revenue.
You type a question in plain English, and it looks up the data, does the math, and
replies with numbers, a chart, or a short report.

I built it to learn how AI works in practice: what it does well, where it makes
mistakes, and how to check its answers before trusting them. I started from a video
tutorial and adapted it to a telecom customer dataset.

## How it works

1. Loaded 7,043 customer records into n8n.
2. Connected Claude with clear rules: use only company data and never guess.
3. Gave it two tools: a customer lookup and a churn and revenue calculator.
4. Code calculates all numbers for charts and reports; the AI explains them.

## How I set it up

- Installed n8n on my own computer (Node.js) and fixed an install error caused by a
  missing Python package.
- Created an Anthropic API key and stored it securely inside n8n, never in my files
  or code.
- Connected Claude Sonnet 4.6 as the AI model. I chose this version because newer
  models did not work with my n8n version.
- Built three connected workflows: the chat assistant, a churn calculator, and a
  chart builder.
- Exported the workflows to this repo and checked them for keys and personal data
  before sharing.

## How I checked the answers

- Calculated control totals from the source file before testing.
- Checked every AI answer against those totals.
- Re-ran six test questions after every change.

## What I learned

1. **AI needs the right tools.** It could only read 50 rows at a time, so I added a
   step that calculates across all customers.
2. **AI fills gaps with outside information.** It quoted industry numbers that were
   not in our data. A specific rule fixed it.
3. **AI can put the right number on the wrong group.** I added a rule that each
   number only describes the group it was calculated for.
4. **AI arithmetic is not reliable enough for finance.** I moved all calculations
   into code.

**Main lesson:** use AI to answer and explain, but calculate numbers in code and
check every answer against the data.

## Skills I used

Data validation and reconciliation, writing clear instructions for AI, testing AI
answers against source data, basic JavaScript for calculations, and building
workflows in n8n.

## Future improvements

- Answer questions about combined groups (for example, monthly contracts and new
  customers together).
- Show money values on charts in dollar format.

## Credits

- Tutorial: "How to Build an AI Agent for Data Analysis, Visualization, AND Reporting
  (n8n)" by Nick Puru | AI Automation (YouTube)
- Data: IBM Telco Customer Churn sample dataset (fictional customers)
- Tools: n8n, Claude (Anthropic), QuickChart
- I used Claude (Anthropic) as a coding and writing assistant on this project.
