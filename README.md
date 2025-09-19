# Energy Efficiency Analysis  
**Predicting Heating & Cooling Loads from Building Design Parameters**

This project uses the **UCI Energy Efficiency (ENB2012)** dataset (768 simulated buildings) to understand how design choices (e.g., roof area, overall height, glazing) affect **Heating Load (HL)** and **Cooling Load (CL)**.  
I walk through a full, single notebook workflow: **preprocessing → EDA → modeling → evaluation** and export a viewer friendly **HTML report**.

---

## 👀 Quick Links
- **HTML report:** `reports/dataanalysis.html`
  You may view this directly through the link: https://dhruvdotc.github.io/energy-efficiency/dataanalysis.html
---

## 🔎 Dataset (UCI ENB2012)
- **Samples:** 768 simulated buildings  
- **Feature Variables (8):** Relative Compactness, Surface Area, Wall Area, Roof Area, Overall Height, Orientation, Glazing Area, Glazing Area Distribution  
- **Target Variables (2):** Heating Load, Cooling Load  
- `Orientation` and `Glazing Area Distribution` are integer encoded categoricals in the source; I map them to more interpretable labels.

--- 

> Note: The dataset is synthetic with discrete design levels → after normalization, scatterplots form vertical “bands” (expected behavior).

---

## 📈 Key Plots (in report / figures)
- **Regression fits & residuals:**  
  - Roof Area vs HL (simple linear)  
  - Residual plot (diagnostics)
- **Actual vs Predicted (scatter)** for pipeline model with 45° reference line
- **Distribution overlap:** KDE of Actual vs Predicted
- **Overfitting check:** Train vs Test R² across polynomial degrees
- **Ridge curve:** Test R² vs α (log scale)
- **Categorical heatmap:** Cooling Load by Orientation × Glazing Distribution
---

## 🧠 Takeaways
- **Roof Area (−)** and **Overall Height (+)** are the strongest continuous drivers of energy loads; **Relative Compactness (+)** and **Surface Area (-)** also matter.  
- **Glazing Area Distribution** has a **clear categorical effect**; **Orientation** is comparatively minor.  
- **MLR** generalizes well (Test R² ≈ **0.90**).  
- **Polynomial features (deg=2)** dramatically improve in-sample fit; use regularization and validation to keep generalization in check.

---




