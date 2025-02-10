---

# **Intern Data Challenge 2025 – Population Movement Simulation**

### **Prepared by:** Richel Ohenewaa Attafuah  

---

## **Project Description**

This project is a submission for OKI's Data Science Internship Challenge. The goal was to estimate the population distribution across ten geographic regions after one year, simulating internal movement based on predefined probabilities. The analysis explores two movement distribution models: **equal distribution** and **weighted distribution**.

This notebook includes exploratory data analysis (EDA), movement logic, simulation implementation, and detailed visualization of results.

---

## **Table of Contents**
1. [Objective](#objective)  
2. [Approach](#approach)  
3. [Dataset Overview](#dataset-overview)  
4. [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)  
5. [Movement Logic and Simulation](#movement-logic-and-simulation)  
6. [Results and Visualizations](#results-and-visualizations)  
7. [Statistical Testing](#statistical-testing)  
8. [Limitations and Recommendations](#limitations-and-recommendations)  
9. [Conclusion](#conclusion)  

---

## **Objective**

The objective of this project was to:
1. Simulate internal population movement between regions using `MoveProb` (movement probability).  
2. Compare two methods of outgoing resident distribution:
   - **Equal Distribution:** Residents are evenly distributed to all adjacent regions.
   - **Weighted Distribution:** Residents are distributed based on the population size of adjacent regions.
3. Analyze the impact of movement on regional population dynamics.

---

## **Approach**

The project follows these steps:
1. **Data Exploration:** Examine the dataset to understand key variables and detect anomalies.  
2. **Define Movement Logic:** Establish adjacency relationships between regions and calculate outgoing residents.  
3. **Simulation:** Simulate population changes using both equal and weighted movement methods.  
4. **Results Analysis:** Visualize the population before and after movement, comparing the two methods.  
5. **Statistical Testing:** Conduct a paired t-test to assess whether the distribution methods result in statistically significant differences.  
6. **Limitations and Recommendations:** Identify potential model improvements and areas for further research.

---

## **Dataset Overview**

The dataset contains the following columns:
- `RegionID`: Unique identifier for each region.  
- `Population`: Initial population in each region.  
- `MoveProb`: Probability of residents moving out of each region.

---

## **Exploratory Data Analysis (EDA)**

The EDA section summarizes key findings from the dataset:
- **Population Distribution:**  
  - Population ranges from **1,847** to **8,510** across regions.  
  - The distribution shows multiple peaks, with no extreme outliers.

- **Move Probability Distribution:**  
  - `MoveProb` ranges from **0.003** to **0.022** and is right-skewed, indicating that movement is generally low across most regions.

- **Correlation:**  
  A weak negative correlation (**-0.20**) exists between `Population` and `MoveProb`.

Visualizations include histograms, pair plots, and box plots to highlight these trends.

---

## **Movement Logic and Simulation**

### **Assumptions**:
1. Movement occurs between **adjacent regions only**, based on a defined adjacency structure.
2. Outgoing residents are calculated as:  
   `Outgoing = Population * MoveProb`.
3. The simulation does not account for natural population growth (births, deaths) or external migration.

### **Movement Models**:
1. **Equal Distribution:** Outgoing residents are divided equally among all adjacent regions.  
2. **Weighted Distribution:** Outgoing residents are distributed based on the population size of adjacent regions.

The adjacency structure for the regions is defined as follows:

```python
adjacency = {
    1: [2, 4],
    2: [1, 3, 5],
    3: [2, 6],
    4: [1, 5, 7],
    5: [2, 4, 6, 8],
    6: [3, 5, 9],
    7: [4, 8],
    8: [5, 7, 9, 10],
    9: [6, 8, 10],
    10: [8, 9]
}
```

The notebook calculates the **outgoing** and **incoming** populations, then updates the population for each region using both distribution models.

---

## **Results and Visualizations**

Key visualizations include:
1. **Population Comparison:**  
   A side-by-side bar plot compares the initial population with the new population after movement.

2. **Outgoing, Incoming, and Net Change:**  
   A bar plot visualizes the number of outgoing residents, incoming residents, and net population change across regions.

3. **Equal vs. Weighted Distribution:**  
   A comparison plot shows how the two methods influence population changes in each region.

### **Summary Table of Population Changes**
| Region ID | Initial Population | Population (Equal) | Population (Weighted) | Difference |
|-----------|---------------------|---------------------|------------------------|------------|
| 9         | 8,510               | 8,530.50            | 8,549.82               | +19.32     |
| 4         | 1,847               | 1,890.88            | 1,875.55               | -15.33     |
| 1         | 2,205               | 2,220.61            | 2,207.72               | -12.89     |
| 5         | 4,422               | 4,461.29            | 4,452.86               | -8.43      |
| 6         | 5,230               | 5,174.06            | 5,181.61               | +7.55      |

---

## **Statistical Testing**

A paired t-test was conducted to determine if the differences between the two distribution methods were statistically significant.

### **Results:**
- **T-statistic:** 0.00  
- **P-value:** 1.00000

Since **p ≥ 0.05**, we conclude that the differences between the methods are **not statistically significant**.

---

## **Limitations and Recommendations**

### **Limitations**:
1. Static movement probabilities do not reflect real-world changes in migration patterns.
2. The weighted distribution model only considers population size, excluding other factors like distance and infrastructure.
3. The analysis covers a single time period without accounting for long-term trends.

### **Recommendations**:
1. Incorporate dynamic migration factors (e.g., economic conditions).
2. Conduct multi-year simulations to capture long-term trends.
3. Enhance the analysis with geospatial visualization.

---

## **Conclusion**

The analysis indicates that both equal and weighted distribution methods yield similar outcomes, with no significant difference in overall population trends. However, localized variations in regions with larger populations highlight the importance of adjacency and movement probabilities. These insights can guide OKI’s strategic planning for infrastructure and transportation.

---

Feel free to explore the code, visualizations, and results in the attached Jupyter Notebook. 😊

---

