# SQL-learning-journal-day---25

# Day 25 - SQL + BI Learning Journal: Moneyball Project (Part B Begins)

**Project:** MLB Player Efficiency - ROI via Performance Stats (2001)  
**Focus Today:** Part B - Hits Per Salary Efficiency

---

## 📈 What I Did Today:

- Kicked off **Part B** of my Moneyball SQL + Tableau project.
- Focused on calculating ROI using **Hits per Salary** (H/S) for the 2001 MLB season.
- Wrote a fresh SQL query to:
  - Join `performances`, `salaries`, and `players` tables.
  - Calculate a scaled `efficiency_percentage` for Hits per $100,000 of salary.
  - Retrieve and export the **Top 50 most efficient players**.
- Identified and resolved Tableau sorting issues caused by **duplicate first names**.
  - Used `GROUP BY` and `HAVING` in SQL to find duplicates.
  - Renamed only the duplicates in SQLite using `UPDATE` and `player_id` for precise targeting.
- Exported cleaned data to `.csv` for Tableau import.
- Postponed visualization due to fatigue after a long workday.

.headers on
.mode csv
.output h_roi_2001.csv
SELECT pf.player_id, p.first_name, p.last_name, pf.h, s.salary,
       ROUND((1.0 * pf.h) / s.salary * 100000, 4) AS efficiency_percentage
FROM performances pf
JOIN salaries s ON pf.player_id = s.player_id AND pf.year = s.year
JOIN players p ON s.player_id = p.id
WHERE pf.year = 2001
ORDER BY efficiency_percentage DESC
LIMIT 50;
.output stdout


---

## 🧠 Key Skills Practiced:
- Data cleansing with SQL (`UPDATE`, `GROUP BY`, `HAVING`)
- Real-world debugging and diagnosis of data visualization issues
- Structured querying and export via `.csv` for BI tools
- Modular approach to building BI reports (Part A: HR, Part B: Hits)

---

## 🔜 Next Steps:
- Import new dataset into Tableau
- Create a dual-axis or clustered bar chart comparing HR vs Hits efficiency
- Begin building a full dashboard for final presentation

---

**Still on track, still learning—excited to keep going!**
