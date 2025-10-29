# **Trader Performance and Market Sentiment Analysis**

## **Project Objective**

This project analyzes trader data to explore the relationship between profitability, market sentiment, and behavioral patterns. The goal is to uncover hidden trader profiles using machine learning and deliver actionable insights that can drive smarter, data-driven trading strategies.

## **Methodology**

The analysis was conducted in three main parts:

1. **Trader Segmentation (K-Means Clustering):**  
   * Traders were segmented based on their total\_profit\_loss, average\_profit\_loss, and win\_rate.  
   * The "Elbow Method" (elbow\_method.png) was used to determine the optimal number of clusters, which was identified as **k=3**.  
   * The resulting clusters represent three distinct trader personas.  
2. **Impact Analysis (Group-by):**  
   * Profitability (average P\&L and win rate) was analyzed across different **Market Sentiment** classifications (e.g., "Extreme Greed", "Fear", "Neutral").  
   * Profitability was also analyzed across different **Leverage Groups** ("Low", "Medium", "High").  
3. **Statistical Validation (ANOVA):**  
   * Analysis of Variance (ANOVA) tests were run to confirm that the differences in profitability between the identified clusters, sentiment groups, and leverage groups were statistically significant.

## **Key Findings**

### **1\. Three Distinct Trader Personas**

The K-Means clustering revealed three statistically significant trader profiles (F-statistic: 35.59, p-value: $1.56 \\times 10^{-8}$):

| Persona | Cluster ID | Trader Count | Avg. P\&L per Trade | Avg. Win Rate | Key Characteristic |
| :---- | :---- | :---- | :---- | :---- | :---- |
| **The High-Profit Whales** | 1 | 6 | **$324.25** | 34.4% | High-risk, high-reward. Wins big but infrequently. |
| **The Active Grinders** | 0 | 15 | $62.68 | **48.2%** | Consistent, high-volume, and high win rate. |
| **The Struggling Scalpers** | 2 | 11 | $19.25 | 32.7% | Active but ineffective. Low profit and low win rate. |

### **2\. Market Sentiment is a Major Driver**

Sentiment has a highly significant impact on profitability (p-value: $2.57 \\times 10^{-7}$).

* **Most Profitable:** "Extreme Greed" ($67.89 avg. P\&L, 46.5% win rate).  
* **Least Profitable:** "Neutral" ($34.31 avg. P\&L) and "Extreme Fear" ($34.54 avg. P\&L).

### **3\. Leverage is a Double-Edged Sword**

Leverage choice significantly impacts outcomes (p-value: $1.69 \\times 10^{-12}$).

* **High Leverage:** Highest avg. P\&L ($67.81) but **lowest win rate (38.6%)**.  
* **Medium Leverage:** Best balance, with the **highest win rate (43.4%)** and strong P\&L ($44.81).

## **Strategic Recommendations**

* **A "one-size-fits-all" strategy is ineffective.** Strategies must be tailored to both the trader's persona and the current market sentiment.  
* **"High-Profit Whales" (Cluster 1):** Your strategy works. Focus your high-leverage trades during **"Extreme Greed"** markets to mitigate your low win rate.  
* **"Active Grinders" (Cluster 0):** Your strength is consistency. Protect your high win rate by using **Medium Leverage** and avoiding low-profit "Neutral" markets.  
* **"Struggling Scalpers" (Cluster 2):** Your current strategy is failing. You must pivot. **Stop using High Leverage.** Switch to Medium/Low Leverage and wait patiently for high-probability "Extreme Greed" conditions.

## **Data Files in This Repository**

### **Raw Data & Clustering**

* trader\_profiles.csv: The raw dataset listing each trader's total\_trades, total\_profit\_loss, average\_profit\_loss, and win\_rate.  
* cluster\_summary.csv: Summary statistics for each of the three identified clusters (trade counts, mean P\&L, mean win rate).  
* cluster\_centers.csv: The normalized centers for each of the three K-Means clusters.

### **Visualizations**

* elbow\_method.png: A plot showing the "elbow" at k=3, justifying the choice of three clusters.  
* trader\_segment\_pairplot.jpg: A pairplot visualizing the distinct separation of the three trader clusters.

### **Analysis & Results**

* sentiment\_profitability.csv: Table showing average\_profit\_loss, number\_of\_trades, and win\_rate broken down by market sentiment.  
* leverage\_profitability.csv: Table showing average\_profit\_loss, number\_of\_trades, and win\_rate broken down by leverage group.  
* cluster\_anova\_table.csv: ANOVA test results confirming the statistical significance of the trader clusters.  
* sentiment\_anova\_table.csv: ANOVA test results confirming the statistical significance of market sentiment on profitability.  
* leverage\_anova\_table.csv: ANOVA test results confirming the statistical significance of leverage on profitability.