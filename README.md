# Digital Advertising Attribution: A/B Testing & Regression Analysis

An end-to-end data analytics and statistical modeling project analyzing a year-long (365 daily observations) performance dataset comparing the conversion efficiency, visibility, and acquisition costs of **Facebook Ads** versus **Google AdWords**.

---

## 🚀 1. Project Overview & Business Strategy

### 1.1 Context & Business Objectives

In digital marketing, tracking superficial metrics like raw impressions or click volumes often creates an illusion of performance. This project models a structured dataset representing a year-long market attribution experiment. The primary objective is to move beyond top-of-funnel indicators and evaluate true marketing channel efficiency.

By leveraging statistical hypothesis testing (A/B testing frameworks) and regression modeling, this analysis delivers data-driven insights to answer the core business question: **How should budget allocation be optimized to minimize the Cost-Per-Acquisition (CPA) and maximize conversion volume?**

### 1.2 The Strategy-First Funnel Framework

The data is structured and evaluated using a standard **four-stage marketing acquisition funnel** to break down user drop-off metrics sequentially:

1. **Awareness (Top of Funnel):** Quantifies pure reach and brand exposure via *Ad Views*.
2. **Engagement (Middle of Funnel):** Evaluates ad creative relevance and user intent via *Ad Clicks* and *Click-Through Rate (CTR)*.
3. **Conversion (Bottom of Funnel):** Measures landing page efficacy and target goal completions via *Ad Conversions* and *Conversion Rate (CVR)*.
4. **Efficiency (Cost Optimization):** Cross-references performance against actual financial expenditure via *Cost per Click (CPC)* to isolate ROI.

---

## 📊 2. Feature Dictionary & Formulations

The dataset contains **365 synchronized rows** tracking key parameters across both platforms on a daily tracking grain.

| Feature Name | Data Type | Description |
| --- | --- | --- |
| `Date` | Datetime | Chronological tracking date. |
| `Facebook Ad Campaign` / `AdWords Ad Campaign` | Categorical | Identifiers tracking monthly campaign variations (e.g., `FB_Jan25`). |
| `Facebook Ad Views` / `AdWords Ad Views` | Int64 | Total daily displays/impressions per platform. |
| `Facebook Ad Clicks` / `AdWords Ad Clicks` | Int64 | Total daily recorded user clicks. |
| `Facebook Ad Conversions` / `AdWords Ad Conversions` | Int64 | Daily successful target goal completions (e.g., sign-ups/purchases). |
| `Cost per Facebook Ad` / `Cost per AdWords Ad` | Float | Total financial spend allocated to that channel daily. |

### Core Mathematical Indicators Evaluated:

* **Click-Through Rate (CTR):** $\text{CTR} = \frac{\text{Ad Clicks}}{\text{Ad Views}}$
* **Conversion Rate (CVR):** $\text{Conversion Rate} = \frac{\text{Ad Conversions}}{\text{Ad Clicks}}$
* **Cost per Click (CPC):** $\text{CPC} = \frac{\text{Cost per Ad}}{\text{Ad Clicks}}$

> **Methodology Note:** A/B testing frameworks strictly require **same-day synchronized observations** to isolate experimental variances from external macro shocks, day-of-week cyclicality (weekdays vs. weekends), or auction marketplace volatility.

---

## 🛠️ 3. Data Preprocessing & Exploratory Data Analysis (EDA)

Before running models, data was thoroughly preprocessed using `pandas` and `numpy`:

* **Data Type Casting:** Cleaned string formatting (stripping out `$`, `%`, and commas) to cast financial figures and rates to functional floats.
* **Sanity Checks:** Bound constraints validated to ensure logical integrity ($\text{Clicks} \le \text{Views}$ and $\text{Conversions} \le \text{Clicks}$).

### Empirical Summary Statistics (Daily Averages):

* **Google AdWords** dominated upper funnel metrics, pulling an average of **~4,760 views** and **60 clicks per day**.
* **Facebook Ads** maintained significantly tighter visibility (averaging **~2,181 daily views**) but explicitly crushed bottom-funnel completions with **11.5 conversions per day** compared to AdWords' **5.5**.

---

## 🧪 4. Statistical Methodology

### 4.1 A/B Testing Framework (Hypothesis Testing)

The repository implements two-sample independent T-tests (`scipy.stats`) to measure statistical significance between the conversion rates and cost efficiencies of the two platforms.

* **Null Hypothesis ($H_0$):** There is no significant difference in performance metrics between Facebook Ads and Google AdWords.
* **Alternative Hypothesis ($H_1$):** Facebook Ads yield significantly higher bottom-funnel performance relative to financial variance.

### 4.2 Linear Regression & Modeling

Using `scikit-learn` and `statsmodels`, parametric models evaluate how scaling daily expenditures affects user actions across different stages of the funnel. This mapping identifies structural diminishing returns on ad spend across both channels.

---

## 📈 5. Core Insights & Business Recommendations

1. **Volume vs. Intent Split:** While Google AdWords acts as a massive top-of-funnel exposure engine (generating more than double the daily impressions), its users convert at a lower rate. Facebook Ads captures a higher level of user intent per click, producing roughly **double the average daily conversion volume** despite tighter reach restrictions.
2. **Budget Optimization:** Data strongly suggests shifting capital weight away from low-converting AdWords display networks into highly optimized Facebook custom audience sequences to reduce overall organization Cost-Per-Acquisition (CPA).

---

## 💻 6. Project Environment & Requirements

The execution pipeline relies on the standard Python Data Science stack.

### Key Libraries Utilized:

* **Data Wrangling:** `pandas`, `numpy`
* **Statistical Analysis:** `scipy.stats`, `statsmodels`
* **Machine Learning:** `scikit-learn`
* **Visualization:** `matplotlib`, `seaborn`

### To Install and Run:

1. Clone this repository:
```bash
git clone https://github.com/yourusername/marketing-campaign-analysis.git

```


2. Setup environment dependencies:
```bash
pip install pandas numpy scipy scikit-learn statsmodels matplotlib seaborn

```


3. Run the analysis notebook:
```bash
jupyter notebook Marketing-Campaign-Analysis-ABTesting-Regression.ipynb

```



---

### 💡 Recommendation for personal adjustments:

Since this README captures all the critical mathematical formulations, preprocessing details, and analytical conclusions documented inside your notebook, you can safely drop it directly into your GitHub repository. If you have run any specific plots (like funnel visualizations or regression residual plots), save them as images inside your repo and update the markdown image placeholder (``) to reference them!
