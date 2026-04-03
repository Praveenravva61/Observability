# 🚀 Catalyst Agent – Multi-Agent Observability & Evaluation System

A production-ready **multi-agent system** built using **Google ADK**, integrated with **Phoenix (Arize)** for deep observability, tracing, and automated hallucination evaluation.

---

## 🧠 Overview

This project demonstrates:

* 🤖 Multi-agent orchestration (Sequential + Parallel)
* 🔍 Real-time observability using Phoenix
* 🧪 Automated LLM evaluation (Correctness & Faithfulness)
* 🧠 LLM-as-a-Judge + LLM-as-a-Teacher architecture
* 📊 Hallucination detection and scoring

---

## 🏗️ Architecture

```
Root Agent
   ↓
Sequential Agent
   ↓
Parallel Agent (Discovery Layer)
   ├── Corporate Profiler Agent
   ├── Market Data Analyst
   └── Strategy (Forecast) Agent
   ↓
Lead Strategist (Final Summary)
```

---

## ⚙️ Tech Stack

* **Google ADK**
* **Gemini Models**
* **Phoenix (Arize)**
* **OpenTelemetry**
* **Pandas**
* **Python**

---

## 📦 Installation

```bash
git clone https://github.com/Praveenravva61/Observability.git
cd Observability

python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate

pip install -r requirements.txt
```

---

## ▶️ Running the Application

### 1. Start Phoenix Server

```bash
phoenix serve
```

Open:

```
http://localhost:6006
```

---

### 2. Run the Agent App

```bash
python main.py
# or
adk web
```

---

## 🔍 Observability (Phoenix)

Phoenix provides:

* 📊 LLM traces
* 🔗 Agent execution graph
* 🧠 Tool usage tracking
* ⏱️ Latency monitoring

---

## 🧪 Evaluation Pipeline

This project includes a custom evaluation system:

### ✔ Features

* Automatic trace extraction from Phoenix
* Input/output cleaning
* Forecast vs Non-forecast splitting
* Dual evaluation strategy:

  * **Correctness** → Forecast agents
  * **Faithfulness** → Other agents
* Annotation logging back to Phoenix

---

## ▶️ Run Evaluation

```bash
python evaluator.py
```

---

## 🔬 Evaluation Logic

### 1. Fetch Traces

```python
df = px_client.spans.get_spans_dataframe(project_name="default")
```

---

### 2. Clean Data

* Extract readable text from ADK responses
* Normalize input/output

---

### 3. Split Data

* Forecast queries → correctness evaluation
* Other queries → faithfulness evaluation

---

### 4. Generate Ground Truth

Uses **Teacher LLM** to fetch realistic answers.

---

### 5. Evaluate

* LLM Judge compares:

  * Output vs Ground Truth
  * Output vs Context

---

### 6. Log Results

Results are sent back to Phoenix as annotations:

* Score
* Label (Correct / Hallucinated)
* Explanation

---

## 📊 Example Output (Phoenix UI)

* ✅ Score: 0.92 → Correct
* ❌ Score: 0.12 → Hallucinated
* 🧠 Explanation: "Prediction unrealistic compared to financial data"

---

## ⚠️ Known Limitations

* Teacher LLM may hallucinate without tools
* Regex-based agent detection (can be improved)
* High evaluation cost for large datasets

---

## 🚀 Future Improvements

* ✅ Agent-level tagging instead of regex
* ⚡ Caching ground truth responses
* 📊 Evaluation dashboard
* 🧠 Root-cause hallucination detection
* 💰 Cost optimization

---

## 🤝 Contributing

Contributions are welcome!

---

## 📜 License

MIT License

---

## 👤 Author

**Praveen Ravva**
