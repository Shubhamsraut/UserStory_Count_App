# 📄 **User Story Extractor – Streamlit Web App**

Transform **Epics**, **User Stories**, and **Acceptance Criteria (AC)** from Microsoft Word `.docx` documents into an interactive dashboard.  
Upload a `.docx`, parse instantly, filter by Epic or Story, and export clean summaries to **CSV/Excel** – all within a modern Streamlit interface.

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://userstorycountapppy-fromdoc.streamlit.app)

---

## ✨ **Features**
- **Automatic Parsing** – Detects Epics, Stories, and AC tables directly from `.docx`.  
- **Smart Header Handling** – Handles inconsistent headers (`Sr. No`, `S.No`, `Expected Result`, etc.).  
- **Summary Metrics** – Totals for Epics, Stories, ACs, and Avg AC per Story.  
- **Filters & Search** – Filter by **Epic**, **Story ID**, or keywords.  
- **One-Click Exports** – Download filtered **Stories** or **ACs** as CSV or Excel.  
- **Modern UI** – Clean, tabbed, and responsive Streamlit interface.

---

## 🧠 **How It Works**
1. **Identify Epics** – Matches lines like `Epic 12: Payments`.  
2. **Identify Stories** – Matches lines like `User Story 2.1: Add UPI option`.  
3. **Locate AC Tables** – Finds tables containing keywords (`acceptance`, `criteria`, `given`, `then`, etc.).  
4. **Normalize Headers** –  
   - `Sr. No`, `S.No`, `#`, `ID` → **AC #**  
   - `Scenario`, `Expected Result` → **Scenario**  
5. **Generate Outputs** –  
   - `stories_df`: Module, Epic, Story ID, Story Title, Acceptance Criteria Count  
   - `ac_df`: Module, Epic, Story ID, Story Title, AC #, Scenario  

---

## 📦 **Requirements**
- **Python** ≥ 3.9  

Create a `requirements.txt`:  
```txt
streamlit>=1.31
pandas>=2.0
python-docx>=1.0
XlsxWriter>=3.0

```
---

## 🚀 **Quickstart (Run Locally)**
1️⃣ **Clone the Repository**
git clone https://github.com/Shubhamsraut/UserStory_Count_App.git
cd UserStory_Count_App

2️⃣ **(Optional) Create & Activate Virtual Environment**
```txt
python -m venv .venv
```

### Windows 
```txt
.venv\Scripts\activate
```

### macOS/Linux
```txt
source .venv/bin/activate
```

3️⃣ **Install Dependencies**
```txt
pip install -r requirements.txt
```

4️⃣ **Run the App**
```txt
streamlit run Userstory_count_APP.py
```

👉 Visit http://localhost:8501
 if the browser doesn’t open automatically.

---

## 🗂 **Example: Payments Module**  

### 📂 **Module:** Payments  
#### 🏷 **Epic 1:** Wallet Top-up  

**User Story 2: Add Money Using UPI**  
*AS A* **wallet user**  
*I WANT* **to add money to my wallet using UPI**  
*SO THAT* **I can quickly top-up my balance for transactions.**

---

### ✅ **Acceptance Criteria**

| **Sr. No** | **Scenario**         | **Acceptance Criteria**                                                                 |
|-------------|--------------------|-----------------------------------------------------------------------------------------|
| **2.1**     | Navigate to Wallet  | **Given** the user is logged in<br>**When** they click “Wallet Top-up” in the Payments section<br>**Then** the top-up dashboard loads |
| **2.2**     | Successful UPI      | **Given** a valid UPI handle is entered<br>**When** the user confirms payment<br>**Then** the wallet balance increases and a success message is displayed |
| **2.3**     | Invalid UPI         | **Given** an invalid UPI handle is entered<br>**When** the user attempts payment<br>**Then** an error message appears prompting the user to correct the UPI |
| **2.4**     | View Top-up History | **Given** previous top-ups exist<br>**When** the user opens the history tab<br>**Then** a list of past top-ups is displayed with columns *(Transaction ID, Amount, Date, Status)* |


## 🌐 **Deployment**  
- ▶ **Streamlit Community Cloud**:  
  1. Push your code (`Userstory_count_APP.py` and `requirements.txt`) to GitHub.  
  2. Visit [share.streamlit.io](https://share.streamlit.io) → **Create App** → Select your repo, branch, and file.  
  3. Click **Deploy** – Streamlit redeploys automatically on each `git push`.  
- ▶ **Alternatives**: Hugging Face Spaces (Streamlit deployment) • Render (private repo support).

---

## 🧪 **Known Limitations**  
- Supports **`.docx` only** (not `.pdf` or legacy `.doc`).  
- Non-standard formats may not parse perfectly.  
- Exports focus on key columns for simplicity.


---

## 👥 **Contributing**  
- Issues and PRs are welcome!  
- Provide minimal `.docx` samples for bug reports.  
- Enhancements to parsing logic or UI are appreciated.

---

## 🧾 **Credits**  
Built with **Streamlit**, **pandas**, **python-docx**, and **XlsxWriter**.  
Custom CSS applied for a polished, intuitive UI.

---

### 📜 **License: MIT © 2025 Shubham Raut**


