📄 User Story Extractor (Streamlit)

Extract Epics, User Stories, and Acceptance Criteria (AC) from a .docx (Microsoft Word) document and explore them in a clean Streamlit UI. Export summaries to CSV/Excel with a click.

https://github.com/Shubhamsraut/UserStory_Count_App

✨ Features

Parse .docx documents that contain Epics, Stories, and AC tables

Smart detection of AC tables even with noisy headers (e.g., Sr. No, S.No, Expected Result)

Robust header canonicalization (maps variants → Scenario, Given/When/Then, AC #, Acceptance Criteria)

Summary metrics: total Epics, Stories, ACs, average ACs per story

Interactive filters: by Epic, Story ID, keyword search

One-click export to CSV and Excel for both Stories and ACs

Clean, responsive Streamlit UI with tabs

🧠 How it works (quick peek)

Epics are recognized by lines like:
Epic 12: Payments

Stories are recognized by lines like:
User Story 2.1: Add UPI option or Story 3: Search

AC tables are found by scanning tables where the first/second row includes AC-related keywords (acceptance, criteria, scenario, given, when, then, expected, result).

Column aliases are normalized. Examples that map correctly:

Sr. No, S.No, Sr.No., #, ID → AC #

Scenario, Acceptance Criteria, Expected, Result → Scenario

Outputs:

stories_df: Module, Epic, Story ID, Story Title, Acceptance Criteria Count

ac_df: Module, Epic, Story ID, Story Title, AC #, Scenario

📦 Requirements

Python 3.9+

streamlit, pandas, python-docx, xlsxwriter

Create a requirements.txt (example):

streamlit>=1.31
pandas>=2.0
python-docx>=1.0
XlsxWriter>=3.0

🚀 Quickstart
# 1) Clone your repo
git clone https://github.com/Shubhamsraut/UserStory_Count_App.git
cd your-repo-name

# 2) (Optional) create & activate a virtual env
python -m venv .venv
# Windows:
.venv\Scripts\activate
# Mac/Linux:
source .venv/bin/activate

# 3) Install deps
pip install -r requirements.txt

# 4) Run the app
streamlit run app.py


By default Streamlit opens in your browser; if not, visit http://localhost:8501.

🗂️ Input document format (example)

A minimal .docx that will parse well:

Module: Payments

Epic 1: Wallet Top-up

User Story 1.1: Add money using UPI

| Sr. No | Scenario                                   | Given             | When                 | Then                    | Expected Result                 |
|--------|--------------------------------------------|-------------------|----------------------|-------------------------|---------------------------------|
| 1      | UPI handle is valid                        | ...               | ...                  | ...                     | Payment succeeds                |
| 2      | UPI handle is invalid                      | ...               | ...                  | ...                     | Error is shown                  |

User Story 1.2: View top-up history

| AC # | Acceptance Criteria                           |
|------|-----------------------------------------------|
| 1    | Shows last 10 transactions                    |
| 2    | Includes amount, date, and status             |


Notes

“Module” can appear anywhere in the doc and will be captured once (defaults to Unknown if absent).

AC tables can have different headers; the app infers AC # and Scenario when possible.

Rows that are completely empty are ignored.

🧭 Using the App

Upload a .docx file in the sidebar / uploader.

See the Summary metrics and switch to:

Story Details tab: filter by Epic, search by title, export stories.

Acceptance Criteria tab: filter by Epic & Story ID, keyword search (matches Scenario or AC #), export ACs.

Download CSV/Excel using the provided buttons.

🧩 Project Structure
.
├─ app.py                 # Streamlit app (paste your code here)
├─ requirements.txt
├─ README.md
└─ .streamlit/
   └─ config.toml         # optional Streamlit configuration


Optional .streamlit/config.toml:

[server]
headless = false
port = 8501

🛠️ Packaging Tips

Add a .gitignore to keep the repo clean:

.venv/
__pycache__/
*.pyc
*.xlsx
*.csv
.DS_Store


If you have example docs, place them under samples/ and reference them in the README.

🌐 Deploy (optional)

Streamlit Community Cloud

Push to GitHub (include requirements.txt and app.py).

In Streamlit Cloud, Create app → select repo/branch/file → Deploy.

Add secrets in the platform UI if needed.

Hugging Face Spaces

Create a Space → select Streamlit.

Add app.py and requirements.txt.

The app builds & serves automatically on each commit.

🧪 Known Limitations

Only .docx is supported (not .pdf/.doc).

If a document deviates heavily from the expected patterns, detection may skip tables or mislabel columns.

AC parsing intentionally returns a minimal set of columns: AC # and Scenario.

❓ FAQ

Q: My AC table headers are odd; will it still work?
A: Likely yes. The app normalizes many header variants (Sr. No, Expected Result, etc.). If it still fails, try renaming to common forms like AC #, Scenario, Acceptance Criteria.

Q: Can I include Given/When/Then?
A: Yes—these can exist in the table and won’t break parsing. The app focuses exports on AC # + Scenario for simplicity.

Q: How is “Module” determined?
A: It’s extracted once from any line like Module: <name>. If not found, it defaults to Unknown.

📜 License

Choose a license (e.g., MIT) and add a LICENSE file. Example MIT header:

MIT License — Copyright (c) 2025 Shubham Raut

👥 Contributing

Issues and PRs welcome! Please:

Open an issue with a minimal sample .docx if parsing fails.

Keep functions pure and add unit tests for regex/header handling where possible.

🧾 Credits

Built with Streamlit, pandas, python-docx, and XlsxWriter.

UI styling via custom CSS in Streamlit.

Tip: Want a one-click launcher? Create a desktop script that runs:
streamlit run app.py --server.port 8501 and opens http://localhost:8501.
