# 🏛️ Multi-Agent AI Policy Evaluation and Consensus System

An n8n workflow that simulates a multi-stakeholder policy debate using Google Gemini AI. Enter any policy proposal and get back a fully scored evaluation report — debated from four societal perspectives — rendered as a styled visual report inside n8n.
---

## Demo Video
https://github.com/user-attachments/assets/5cb4dfec-47a9-48e9-bf61-3bbecb329d5c

---
## 🧠 What It Does

Four AI agents each evaluate your policy from a different angle:

| Agent | Perspective | Focuses On |
|---|---|---|
| 🏛️ Government | Policy-maker | Feasibility, budget, political risk |
| 💼 Business | Corporate | Cost, regulation, market impact |
| ✊ Civil Society | NGO/Advocacy | Fairness, ethics, inclusion |
| 🧑 Citizen | Everyday person | Lived experience, accessibility |

The results are combined, cross-analyzed for agreements and conflicts, then a final verdict is generated:

- ✅ **Approve** / ❌ **Reject** / 🔧 **Modify**
- Feasibility, Equity, and Risk scores (1–10)
- Executive summary + implementation considerations
- Full stakeholder interaction breakdown

---

## ⚙️ Setup — 3 Steps Only

### 1. 🔑 Gemini API Key

1. Go to [https://aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey) and sign in
2. Click **Create API Key** and copy it
3. In the workflow, open each of these nodes and replace `YOUR_GEMINI_API_KEY` in the query parameters:
   - `Initial Gemini Processing`
   - `Government Agent`
   - `Business Agent`
   - `Civil Society Agent`
   - `Citizen Agent`
   - `Analyze Interactions`
   - `Generate Final Evaluation`

> Gemini 2.5 Flash has a free tier — no billing needed to get started.

---

### 2. 📝 Set Your Policy

1. Open the **`Set Policy Input`** node (second node from the left)
2. Change the `policy` string value to whatever you want to evaluate

**Example inputs to try:**
```
Four-day work week mandatory for all private sector companies with over 50 employees
```
```
Ban all single-use plastics including food packaging within 6 months
```
```
Free public WiFi in all cities with population over 1 million
```

---

### 3. 📄 Install the HTML to PDF Node (Optional)

Only needed if you want to export the report as a PDF file. If you just want to view the report inside n8n, skip this step.

#### Option A — n8n Cloud (Recommended)
1. Go to **Settings → Community Nodes** in your n8n instance
2. Click **Install a community node**
3. Enter: `n8n-nodes-htmlcsstopdf`
4. Click **Install**

#### Option B — Self-hosted / Local
```bash
cd ~/.n8n/nodes
npm install n8n-nodes-htmlcsstopdf
```
Then restart your n8n instance.

#### Get your PDFMunk API Key
1. Go to [https://pdfmunk.com](https://pdfmunk.com) and sign up
2. Navigate to **Dashboard → API Key** and copy it
3. In n8n, go to **Credentials → New Credential**
4. Search for `HTML CSS to PDF` and enter your PDFMunk API key
5. Link this credential to the **Convert HTML to PDF** node in the workflow

---

## ▶️ Running the Workflow

1. Import `Multi-Agent_AI_Policy_Evaluation_and_Consensus_System.json` into n8n
2. Add your Gemini API key to all 7 nodes (see Step 1)
3. Set your policy text in **Set Policy Input**
4. Click **Execute workflow**
5. Open the final **HTML** node to see the rendered report

---

## 📊 Output Preview

The report renders directly inside n8n and includes:

- Colour-coded verdict badge — 🟢 Approve / 🔴 Reject / 🟡 Modify
- Score bars for Feasibility, Equity, and Risk
- Executive summary in plain English
- Key implementation considerations
- Full stakeholder interaction breakdown

---

## ⚠️ Notes

- The workflow makes **7 Gemini API calls** per run — keep an eye on free tier limits
- To change the policy just edit the one string value in **Set Policy Input** — nothing else needs to change
- The workflow uses `gemini-2.5-flash`
