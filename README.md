# 📊 Airbnb Global Performance Dashboard (Power BI)

## 📌 Project Overview

This project analyzes **Airbnb listings, reviews, pricing, and host trust signals across major global cities** using Power BI.
The goal is to uncover **market trends, customer behavior, and seasonal demand patterns** that can help understand how Airbnb performs across different markets.

The dashboard integrates multiple datasets and uses **data modeling, DAX measures, and interactive visualizations** to provide insights into listings distribution, review frequency, ratings, and host credibility.

---

## 📂 Data Sources

The datasets used in this project were obtained from **Mapple Analytics**.

Due to file size limitations, the raw datasets are not included in this repository.

* `listings.csv`
* `reviews.csv`

These datasets contain information on listings, hosts, prices, locations, and customer reviews.

---

## Key Metrics

* **Total Listings:** 279,712
* **Total Hosts:** 182,024
* **Cities Analyzed:** 10
* **Total Reviews:** 5.37M
* **Property Types:** 144

---

## Business Questions Addressed

This dashboard answers important analytical questions such as:

* Which cities dominate Airbnb listings and reviews?
* How frequently do customers leave reviews?
* Which cities have the highest ratings?
* What seasonal patterns exist in Airbnb demand?
* How trustworthy are hosts based on profile verification signals?

---

## Dashboard Features

### Market Share Analysis

Analyzes how listings are distributed across cities and identifies dominant markets such as **Paris, New York, and Sydney**.

### Property Type Pricing

Compares average prices across property types:

* Entire place
* Hotel room
* Private room
* Shared room

### Review Frequency Analysis (Pareto)

Identifies reviewer behavior patterns.
Findings show that **most customers leave only one review**, while only a small fraction write multiple reviews.

### Ratings Analysis

Compares cities based on rating categories such as:

* Accuracy
* Cleanliness
* Communication
* Location
* Value

### Trust Signals

Examines host credibility indicators such as:

* Profile picture availability
* Identity verification

### Seasonality Analysis

Shows monthly review trends to identify peak travel periods across different cities.

---

## Key Insights

* **Paris, New York, and Sydney account for nearly half of total listings and reviews.**
* Most customers write **only one review**, indicating low repeat review frequency.
* **Mexico City and Rio de Janeiro** show the highest overall ratings.
* Review activity peaks during **European summer (April–August)**.
* Over **two-thirds of hosts are fully verified**, indicating strong trust signals within the platform.

---

## Data Model

The dashboard uses a **data model connecting listings and reviews datasets** through listing identifiers.

Example relationships include:

* Listings → Reviews (via listing_id)

This structure enables deeper analysis of **customer behavior and listing performance**.

---

## Key DAX Measures

Example measures used in this project:

```DAX

Total Listings = COUNT(Listings[listing_id])

Total Reviews = COUNT(Reviews[review_id])

Hosts Total = DISTINCTCOUNT(Listings[host_id])

Reviews per Reviewer =
CALCULATE(
COUNT(Reviews[review_id]),
ALLEXCEPT(Reviews, Reviews[reviewer_id])
)

Cumulative Reviewers =
VAR CurrentReviews =
MAX(Reviews[Reviews per Reviewer])
RETURN
CALCULATE(
DISTINCTCOUNT(Reviews[reviewer_id]),
FILTER(
ALL(Reviews[Reviews per Reviewer]),
Reviews[Reviews per Reviewer] <= CurrentReviews
)
)

Cumulative % review frequency =
DIVIDE(
[Cumulative Reviewers],
CALCULATE([Reviewers], ALL(Reviews[Reviews per Reviewer]))
)
```

---
 
## Skills Demonstrated

* Data Cleaning & Preparation
* Data Modeling
* DAX Calculations
* Pareto Analysis
* Market Share Analysis
* Time Series & Seasonality Analysis
* Business Insight Generation
* Dashboard Design

---


## Author

**Anushka Mishra**
CSE Student | Aspiring Data Analyst

This project is part of my portfolio demonstrating skills in **Power BI, data analysis, and business intelligence**.
