# AI Performance Monitor
Un dashboard simplu care colectează și afișează metrici de performanță ale unui model AI de clasificare în timp real, cu analiză de trend și forecast.

## Cuprins
1. [Project Overview](#project-overview)
2. [Tech Stack](#tech-stack)
3. [Prerequisites](#prerequisites)
4. [Installation & Setup](#installation--setup)
5. [Usage](#usage)
6. [Folder Structure](#folder-structure)
7. [Configuration](#configuration)
8. [API Reference](#api-reference)
9. [Features](#features)
10. [Tests & CI](#tests--ci)
11. [Roadmap & Contribuții](#roadmap--contribuții)
12. [Licență & Contact](#licență--contact)

---

## Project Overview
Acest proiect oferă un dashboard web care:
- Monitorizează metrici: **F1-score**, **AUC**, **latency (ms)** și **cost per call (USD)**.
- Afișează grafice de trend și detectează eventual drift.
- Generează un forecast liniar al metricilor pentru următoarele zile.

---

## Tech Stack
- **Backend:** Python 3.10+, Flask
- **Frontend:** HTML/CSS, Chart.js
- **Data Processing:** pandas, scikit-learn
- **CI/CD:** GitHub Actions
- **Storage:** JSON files în `/data/`

---

## Prerequisites
- Python 3.10+
- pip (sau pipenv/virtualenv)
- Node.js (opțional pentru bundling frontend)

---

## Installation & Setup
1. Clonează repository:
   ```bash
   git clone https://github.com/<username>/ai-performance-monitor.git
   cd ai-performance-monitor
   ```
2. Crează și activează un mediu virtual:
   ```bash
   python -m venv venv
   source venv/bin/activate   # Linux/Mac
   venv\Scripts\activate    # Windows
   ```
3. Instalează dependențele:
   ```bash
   pip install -r requirements.txt
   ```
4. Rulează aplicația:
   ```bash
   export FLASK_APP=app/main.py      # Linux/Mac
   set FLASK_APP=app/main.py         # Windows
   flask run
   ```

---

## Usage
- Deschide browser la `http://127.0.0.1:5000`.
- Dashboard-ul va afișa graficele pentru metrici și forecast.
- Poți modifica datele simulate în `data/metrics_log.json`.

---

## Folder Structure
```
ai-performance-monitor/
├── app/
│   ├── main.py         # Flask entrypoint
│   ├── metrics.py      # Colectare și calcul KPI
│   └── forecast.py     # Model regressie liniară
│
├── data/               # Date simulate
│   └── metrics_log.json
│
├── frontend/
│   ├── index.html      # UI dashboard
│   └── scripts.js      # Chart.js + API fetch
│
├── tests/
│   ├── test_metrics.py
│   └── test_forecast.py
│
├── .github/workflows/
│   └── ci.yml          # Pipeline CI
│
├── requirements.txt
├── README.md           # Acest fișier
└── .gitignore
```

---

## Configuration
Editează fișierul `.env` (creează-l în root):
```ini
FLASK_ENV=development
METRICS_FILE=data/metrics_log.json
```

---

## API Reference
- `GET /api/metrics` – returnează lista de metrici sub formă JSON:
  ```json
  [
    {
      "timestamp": "2025-04-21T10:00:00",
      "f1_score": 0.85,
      "auc": 0.90,
      "latency_ms": 120,
      "cost_usd": 0.002
    }
  ]
  ```

---

## Features
- **Metrici live:** F1-score, AUC, latency, cost
- **Trend analysis:** detectare drift (z-score)
- **Forecast:** regresie liniară pentru următoarele 7 zile

---

## Tests & CI
Rulează local:
```bash
pytest
```
CI rulată prin GitHub Actions (`.github/workflows/ci.yml`) include:
- Instalare dependențe
- Rulează `pytest`
- Salvează `metrics_log.json` ca artifact

---

## Roadmap & Contribuții
- **Backlog:** am creat un board Kanban în Projects.
- **Contribuții:** deschide un issue sau pull request cu sugestii.

---

## Licență & Contact
- Licență: MIT
- Contact: [email@example.com](mailto:email@example.com) | [LinkedIn](https://www.linkedin.com/in/username)

