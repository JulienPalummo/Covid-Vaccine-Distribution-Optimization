# 📘 COVID-19 Vaccine Distribution Optimization

This repository contains a decision analytics project focused on **optimizing the distribution of COVID-19 vaccines in Montréal**.  
Using mathematical modeling and the **Gurobi Optimizer**, the project minimizes procurement, transportation, and unmet demand penalties while prioritizing high-urgency neighborhoods.

The work was completed as part of **MGSC 662 – Decision Analytics** at McGill University.

---

## 📂 Project Structure

- **`Code_Group-Project_Vaccines-Optimization.ipynb`** → Jupyter Notebook implementing the optimization model (data import, formulation, constraints, optimization, sensitivity analysis).  
- **`Group-Project_Covid-Data.xlsx`** → Dataset containing vaccine supply, demand, population, and COVID-19 case/death statistics.  
- **`Project Final Report (MGSC662).pdf`** → Detailed project report with methodology, mathematical formulation, results, and recommendations.  

---

## ⚙️ Problem Description

Montréal faced the challenge of **allocating limited vaccine supply** across multiple suppliers, vaccination centers, and neighborhoods. The model addresses:

- Supply limits from 6 vaccine providers  
- Demand across 17 vaccination centers in 9 neighborhoods  
- Transportation costs  
- Public health urgency based on COVID-19 cases and deaths  
- A 5-week planning horizon (Oct–Nov 2023)  

The problem is formulated as an **unbalanced inventory optimization** with constraints on supply, demand, equity, and urgency.

---

## 🔢 Mathematical Model

### Decision Variable
- $X_{ijt}$: number of vaccines shipped from supplier *i* to center *j* at time *t*.  

---

### Objective Function  

Minimize total cost:

$$
Z = \sum_{i,j,t} (p_i + t_{ij}) \cdot X_{ijt} \;+\;
\sum_{n,t} (h + u_{nt}) \cdot \Big(D_{nt} - \sum_{i \in I(n), j} X_{ijt}\Big)
$$

---

### Parameters:  

- $p_i$: purchase cost  
- $t_{ij}$: transport cost  
- $h$: unmet demand penalty  
- $u_{nt}$: urgency weight (based on cases & deaths)  
- $D_{nt}$: demand in neighborhood *n* at time *t*  

---

### Constraints: 
- Supply limits per supplier  
- Demand fulfillment per neighborhood  
- Minimum 10% demand coverage in each neighborhood  
- Equal distribution within neighborhoods  
- Non-negativity  

---

## 📊 Results

- **Optimal cost:** CAD **13.99M** over 5 weeks  
  - Procurement & transport ≈ CAD 8.54M  
  - Penalties ≈ CAD 5.45M  
- Annualized cost ≈ CAD 2.9B → consistent with Canadian COVID-19 expenditures  
- Strategic allocations:  
  - **Moderna** → urban centers (e.g., Parc-Extension)  
  - **Pfizer-BioNTech** → suburban sites (e.g., Laval, Kirkland)  
- Sensitivity analysis revealed:  
  - Surpluses (e.g., Moderna)  
  - Shortages (e.g., Centre-Sud)  

---

## 🔍 Key Extensions

Potential extensions considered:  
- Historical allocation urgency (time-dependent demand weighting)  
- Budget constraints from government funding  
- Vaccine wastage penalties  
- Age-based restrictions  
- Temperature-sensitive logistics  

---

## 🛠️ Tech Stack

- **Language:** Python  
- **Optimization Tool:** Gurobi Optimizer  
- **Libraries:** `pandas`, `numpy`, `matplotlib`, `gurobipy`  
- **Techniques:** Linear & integer programming, sensitivity analysis, scenario testing  

