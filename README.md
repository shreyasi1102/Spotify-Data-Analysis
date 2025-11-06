# 🎵 Decoding Music Popularity — An End-to-End Spotify Analytics Workflow

### SQL • Python • Pandas • Plotly • Streamlit • Git • Data Storytelling

---

## 📖 Overview
This project explores **what makes songs popular on Spotify** using a complete, industry-style data analytics workflow — from SQL data modeling and analysis to Python visualization and dashboarding.  

It demonstrates **the full lifecycle of a data analytics project**:
1. **Data ingestion** into a relational SQL schema  
2. **Exploratory data analysis and transformation** using Python (Pandas, NumPy)  
3. **Statistical & modeling insights** into feature-driven song popularity  
4. **Interactive Streamlit dashboard** for exploration and storytelling  
5. **Git-based version control and documentation** for reproducibility  

> **Goal:** Identify which musical and production features (e.g., energy, valence, tempo, loudness) most strongly correlate with track popularity — and how these trends shift across genres and years.

---

## 🧠 Skills Demonstrated
| Area | Tools & Concepts |
|------|------------------|
| **Data Engineering** | SQL schema design, joins, CTEs, window functions, cohort analysis |
| **Analytics** | Python (Pandas, NumPy, SciPy), feature engineering, statistical testing |
| **Visualization** | Plotly, Seaborn, Matplotlib |
| **Modeling** | Logistic regression for top-decile hit prediction |
| **Dashboarding** | Streamlit app for interactive genre & feature exploration |
| **Version Control** | Git branching workflow, commits, README, GitHub Actions |
| **Communication** | Executive summary, visual storytelling, markdown documentation |

---

## 🗂️ Repository Structure
```
spotify-analytics/
├─ data/
│  ├─ raw/                 # Original CSVs or API pulls
│  └─ processed/           # Cleaned or aggregated datasets
├─ sql/
│  ├─ schema.sql           # Table creation and indexing
│  └─ queries/             # Analytical SQL queries
├─ notebooks/
│  ├─ 01_ingest_model.ipynb        # Data import + schema validation
│  ├─ 02_explore_sql.ipynb         # Core SQL exploration
│  ├─ 03_analysis_python.ipynb     # EDA + feature analysis
│  ├─ 04_modeling_interpret.ipynb  # Simple modeling and interpretation
│  └─ 05_report.ipynb              # Visual storytelling and insights
├─ dashboard/
│  └─ app.py              # Streamlit dashboard
├─ docs/
│  ├─ executive_summary.pdf
│  ├─ data_dictionary.md
│  └─ schema_diagram.png
├─ requirements.txt
└─ README.md
```

---

## 🧩 Data Sources
- **Spotify Tracks Dataset** — [Kaggle: Spotify Dataset 1921–2023, 600k+ tracks](https://www.kaggle.com/datasets)
- Includes audio features: `danceability`, `energy`, `valence`, `tempo`, `acousticness`, `loudness`, etc.
- Optionally enriched with **artist genre mappings** or **playlist metadata**.

---

## 🧮 Analysis Highlights
**Key Questions**
1. What audio features correlate most strongly with popularity?  
2. How do those features vary by **genre**, **decade**, and **playlist presence**?  
3. Can we predict which songs are likely to be in the top 10% of popularity?  
4. How have energy, tempo, and valence trends changed over time?  

**Example Insights**
- Tracks with **high energy** and **mid-to-high valence** dominate top charts in pop genres.  
- Popularity distributions differ significantly between **danceable vs. acoustic** songs.  
- Average **tempo** and **loudness** have risen steadily from 1990–2020.  
- Simple logistic regression achieves interpretable results (e.g., 65–70% accuracy) and highlights the most influential features.

---

## 📊 Dashboard Preview
Interactive dashboard built with **Streamlit** — visualize popularity trends by feature, genre, and decade.  
*(Screenshot placeholder — add after deployment)*  

```
streamlit run dashboard/app.py
```

---

## 🧱 SQL Highlights
Sample complex query (from `/sql/queries/genre_popularity.sql`):

```sql
WITH genre_rank AS (
    SELECT
        g.genre,
        t.track_name,
        t.release_year,
        t.popularity,
        PERCENT_RANK() OVER (PARTITION BY g.genre ORDER BY t.popularity) AS pr
    FROM tracks t
    JOIN genres g ON t.artist_id = g.artist_id
)
SELECT genre, AVG(popularity) AS avg_popularity
FROM genre_rank
WHERE pr >= 0.9
GROUP BY genre
ORDER BY avg_popularity DESC;
```

---

## ⚙️ Setup & Reproducibility

**Clone the repository**
```bash
git clone https://github.com/<yourusername>/spotify-analytics.git
cd spotify-analytics
```

**Create environment & install dependencies**
```bash
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows
pip install -r requirements.txt
```

**Run the analysis**
```bash
jupyter lab
```

**Launch dashboard**
```bash
streamlit run dashboard/app.py
```

---

## 🧾 Deliverables
- 📊 Jupyter notebooks with reproducible analysis  
- 📈 Streamlit dashboard (`/dashboard/app.py`)  
- 🧱 SQL schema + analytical queries  
- 📘 Executive summary (PDF) with key findings  
- 🧩 Data dictionary and schema diagram  

---

## 🧭 Future Improvements
- Integrate **Spotify Web API** for real-time track updates  
- Add **listener region / playlist graph analysis**  
- Implement **dbt / DuckDB** for scalable SQL transformations  
- Deploy dashboard via **Streamlit Cloud or GitHub Pages**  

---

## 👩‍💻 Author
**Shreya Singh**  
Data Analyst • Bioengineer • Python Enthusiast  
[LinkedIn](https://www.linkedin.com/in/) • [GitHub](https://github.com/)

---
© 2025 Shreya Singh — MIT License
