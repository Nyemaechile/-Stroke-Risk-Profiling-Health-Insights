# Stroke-Risk-Profiling-Health-Insights

## 📁 Project Overview
This project uses patient health indicator data to analyze risk factors and predictors of stroke. The goal is to empower healthcare professionals and public health planners with actionable insights through data visualization, KPI tracking, and interactive Excel dashboards.

## 🎯 Objective
- Identify critical health indicators associated with stroke occurrences.
- Create new, readable, and interpretable features from raw data.
- Design KPIs and visualize them using pivot tables.
- Develop an interactive dashboard in Excel for pattern recognition and decision-making.
- Address public health concerns with data-driven recommendations.

## 🧾 Dataset

- **Source**: [Stroke Prediction Dataset](#)  
- **Total Records**: 510+
- **Key Columns**:  
  - `gender`, `age`, `hypertension`, `heart_disease`, `ever_married`, `work_type`, `Residence_type`, `avg_glucose_level`, `bmi`, `smoking_status`, `stroke`

 ## 🛠️ Data Cleaning & Transformation

### ✅ Tasks Completed:

1. **Missing Values**  
   - `bmi`: Handled missing values using **mean imputation**.
     ```excel
     =IF(ISBLANK(E2), AVERAGE($E$2:$E$511), E2)
     ```
     → New Column: `cleaned_bmi`

2. **Label Transformation**
   - `hypertension` and `heart_disease` (0 = No, 1 = Yes)
     ```excel
     hypertension_label: =IF(C2=1, "Yes", "No")
     heart_disease_label: =IF(D2=1, "Yes", "No")
     ```

3. **Age Grouping**
   - Created age categories:
     ```excel
     =IF(B2<18, "Child", IF(B2<40, "Young Adult", IF(B2<60, "Middle Age", "Senior")))
     ```
     → New Column: `age_group`

4. **Glucose Level Categories**
   - For clinical classification:
     ```excel
     =IF(K2<100, "Normal", IF(K2<140, "Prediabetic", "Diabetic"))
     ```
     → New Column: `glucose_level_category`

   ## 📊 Key Performance Indicators (KPIs)

| KPI | Description | Formula |
|-----|-------------|---------|
| **Stroke Rate** | % of patients who had a stroke | `=COUNTIF(L2:L511,1)/COUNTA(L2:L511)` |
| **Hypertension Rate** | % of patients with hypertension | `=COUNTIF(C2:C511,1)/COUNTA(C2:C511)` |
| **Heart Disease Rate** | % of patients with heart disease | `=COUNTIF(D2:D511,1)/COUNTA(D2:D511)` |
| **Average BMI (cleaned)** | BMI average after imputation | `=AVERAGE(F2:F511)` |
| **Average Glucose (Stroke)** | Avg glucose for stroke patients only | `=AVERAGEIF(L2:L511,1,K2:K511)` |
| **Smoker Stroke %** | Stroke rate among smokers | `=COUNTIFS(J2:J511,"smokes",L2:L511,1)/COUNTIF(J2:J511,"smokes")` |

## 📈 Pivot Tables

| Pivot Table | Field List Setup |
|-------------|------------------|
| **1. Stroke by Age Group** | Rows: `age_group`, Values: Count of `stroke`, Filter: `stroke` = 1 |
| **2. Stroke by Smoking Status** | Rows: `smoking_status`, Columns: `stroke`, Values: Count of any ID or gender |
| **3. Stroke by Work Type** | Rows: `work_type`, Values: Count of `stroke`, Filter: `stroke` = 1 |
| **4. Stroke by Glucose Category** | Rows: `glucose_level_category`, Values: Count of `stroke` |
| **5. Stroke by Gender** | Rows: `gender`, Values: Count of `stroke`, Calculated Field: `% Stroke = stroke/total` |

## 📊 Dashboard Design (in Excel)

- **Filters (Slicers)**:
  - Gender
  - Age Group
  - Smoking Status
  - Work Type
- **Top Cards / KPIs**:
  - Total Patients
  - Stroke Rate
  - Hypertension Rate
  - Avg Glucose
  - Avg BMI
- **Charts**:
  - Bar: Stroke Rate by Age Group
  - Pie: Stroke Distribution by Gender
  - Column: Stroke by Work Type
  - Bar: Stroke by Smoking Status

 ## ❓ Business Questions Addressed

1. What age group has the highest stroke incidence?
2. Do smokers have a higher chance of stroke?
3. How do hypertension and heart disease affect stroke risk?
4. Is there a lifestyle/work-type pattern to stroke occurrence?
5. Are urban dwellers more prone to stroke than rural dwellers?

## 🧠 Insights & Recommendations

- Seniors and middle-aged patients exhibit the highest stroke occurrence.
- Patients with hypertension or heart disease are at significantly higher risk.
- Smokers show a disproportionate number of strokes compared to non-smokers.
- Glucose levels above 140 ("Diabetic") have a stronger link with stroke.
- Preventive screening should prioritize high-risk groups for early intervention.

## 📂 Project Files

- `stroke_prediction_dataset_cleaned.xlsx` — cleaned dataset + dashboard
- `Stroke_Dashboard.pptx` — insights & strategy presentation
- `README.md` — this report
- `Documentation.pdf` — step-by-step explanations, logic, and formulas
## 🧑‍💻 Author

**Nyema Roland Amadi**  
Public Health Analyst | Data Enthusiast  
[GitHub Profile](#) • [LinkedIn](www.linkedin.com/in/nyema-amadi-827417242)

