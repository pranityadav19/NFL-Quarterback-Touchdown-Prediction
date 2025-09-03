# NFL Quarterback Touchdown Prediction

This project applies **predictive modeling** to NFL quarterback statistics to estimate the number of touchdown passes a quarterback will throw in a season. Using real player performance data from ESPN, I compared multiple models to determine which variables best explain touchdown performance.

---

## 📌 Project Overview
- **Research Question**: Can a quarterback’s completions, attempts, passing yards per game, and team predict their total touchdown passes in a season?  
- **Motivation**: Touchdowns are a key measure of QB success. Predicting them helps with:
  - Draft and trade decisions for NFL teams.
  - Coaching strategy and game planning.
  - Fantasy football analysis and predictions.
- **Dataset**: Season performance stats for NFL quarterbacks (2024 season), sourced from ESPN. Variables include completions, attempts, passing yards, touchdowns, and team:contentReference[oaicite:0]{index=0}.

---

## 🗂 Data Preparation
- **Data Collection**: Pulled via `rvest` (R web scraping package) from ESPN’s NFL passing stats page.  
- **Cleaning & Wrangling**:
  - Split combined *player + team* field into separate columns.  
  - Converted passing yards from strings with commas to numeric format.  
  - Verified no missing values (dataset was clean from source).  
- **Exploration**:
  - Built correlation matrix to examine relationships between completions, attempts, yards, and TDs.  
  - Visualized distributions and checked multicollinearity.  
- **Data Split**:
  - **Decision Tree**: 70% train / 30% test.  
  - **Random Forest**: 80% train / 20% test:contentReference[oaicite:1]{index=1}.

---

## ⚙️ Modeling Approach
I used regression-based predictive models since touchdown passes are a continuous outcome.

1. **Decision Tree Regression**  
   - Simple and interpretable model.  
   - Visualized splits to see how predictors impact touchdowns.

2. **Random Forest Regression**  
   - Ensemble method combining many trees.  
   - Reduced variance vs. single tree.  
   - Tuned hyperparameters (`ntree`, `mtry`) using caret’s grid search:contentReference[oaicite:2]{index=2}.

---

## 📊 Results

| Model               | MSE   | RMSE   | R²    |
|----------------------|-------|--------|-------|
| Decision Tree        | 21.58 | 4.65   | **0.72** |
| Random Forest        | 25.25 | 5.02   | 0.69  |

**Takeaways**:
- Decision Tree **outperformed Random Forest** on this dataset.  
- The tree achieved higher accuracy (lower MSE/RMSE) and explained more variance (R²).  
- This result challenges the assumption that Random Forest always beats a single tree:contentReference[oaicite:3]{index=3}.

---

## 🔑 Insights
- **QB Environment Matters**: A quarterback’s team context + passing metrics strongly predict TD outcomes.  
- **Fantasy Football Application**: These variables are reliable predictors for fantasy drafting.  
- **Modeling Lesson**: More complex models don’t always win — testing multiple approaches is critical.  

---

## 📝 Reflection
- Learned to transform raw scraped data into clean, structured inputs for predictive modeling.  
- Experienced the tradeoffs between interpretability (Decision Tree) vs. complexity (Random Forest).  
- Gained confidence in R for end-to-end workflow: scraping → wrangling → visualization → modeling.  

---

## 🔧 Tools & Tech
- **Language**: R  
- **Libraries**: tidyverse, rvest, caret, corrplot  
- **Methods**: Decision Tree Regression, Random Forest Regression
