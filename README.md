# Market Basket Analysis: Comparative Study of Apriori and FP-Growth Algorithms

A comprehensive retail analytics project comparing two prominent frequent pattern mining algorithms for discovering product associations in grocery transaction data.

## Project Overview

This project implements and compares **Apriori** and **FP-Growth** algorithms to analyze retail grocery transactions and uncover meaningful product associations. The analysis examines 130,769 transactions from 1,762 households across 25,994 unique products, aggregated into 291 commodity categories over a 3-month period.

### Key Findings

- Both algorithms identified identical patterns: **2,477 frequent itemsets** and **2,220 association rules**
- Apriori demonstrated superior computational efficiency (**1.81 seconds** vs **86.19 seconds**)
- Strong complementary purchasing patterns discovered, particularly around meal components (pasta, sauce, beef)
- Highest lift value of **14.16** indicates powerful cross-selling opportunities
- Pasta meal ecosystem shows lifts of 12-14x, representing genuine revenue growth opportunities

## Business Applications

Market Basket Analysis provides actionable insights for:

- **Product placement optimization** - Strategic store layout based on purchase patterns
- **Cross-selling strategies** - Bundle recommendations and promotions
- **Inventory management** - Synchronized stock levels for associated products
- **Personalized recommendations** - Data-driven customer targeting

## Dataset Characteristics

| Metric | Value |
|--------|-------|
| Unique Households | 1,762 |
| Unique Products | 25,994 |
| Total Transactions | 130,769 |
| Average Basket Size | 9.2 items |
| Median Basket Size | 5 items |
| Analysis Period | Weeks 1-14 (90 days) |
| Categories | 291 |
| Matrix Dimensions | 14,219 × 291 |
| Matrix Sparsity | 97.68% |

## Methodology

### Algorithm Selection

**Apriori Algorithm**
- Breadth-first search approach
- Level-by-level candidate generation
- Uses Apriori principle: if an itemset is infrequent, all its supersets are infrequent

**FP-Growth Algorithm**
- Divide-and-conquer strategy
- Pattern growth method
- Builds compact FP-tree data structure

### Parameters

| Parameter | Value | Justification |
|-----------|-------|---------------|
| **Minimum Support** | 0.01 (1%) | Captures patterns appearing in >131 transactions, balancing rare vs common patterns |
| **Minimum Confidence** | 0.50 (50%) | Ensures rules are correct at least half the time for reliable business decisions |
| **Minimum Lift** | 2.0 | Requires associations to be at least 2× better than random chance |

### Data Preprocessing

- Used first 90 days of 2-year dataset for computational efficiency
- Grouped by BASKET_ID and COMMODITY_DESC
- Converted to binary matrix (purchase/no purchase)
- Reduced dimensionality by aggregating to commodity categories (25,994 → 291)

## 📊 Results

### Top 10 Most Frequent Itemsets

| Rank | Itemset | Support | Transactions |
|------|---------|---------|--------------|
| 1 | Soft Drinks | 27.55% | 3,916 |
| 2 | Fluid Milk Products | 23.78% | 3,380 |
| 3 | Baked Bread/Buns/Rolls | 21.34% | 3,047 |
| 4 | Cheese | 15.66% | 2,227 |
| 5 | Bag Snacks | 15.28% | 2,172 |
| 6 | Beef | 13.98% | 1,988 |
| 7 | Tropical Fruit | 12.36% | 1,757 |
| 8 | Refrigerated Juices/Drinks | 10.10% | 1,436 |
| 9 | Fluid Milk + Bread | 10.09% | 1,435 |
| 10 | Candy - Checklane | 9.99% | 1,421 |

### Top 10 Association Rules (by Lift)

| Rank | Antecedent | Consequent | Support | Confidence | Lift |
|------|------------|------------|---------|------------|------|
| 1 | Milk + Cheeses | Deli Meats + Bread | 1.01% | 54.37% | 14.16 |
| 2 | Dry Noodles + Beef | Pasta Sauce | 1.41% | 58.60% | 14.10 |
| 3 | Dry Noodles + Soft Drinks | Pasta Sauce | 1.09% | 56.99% | 13.71 |
| 4 | Pasta Sauce + Beef | Dry Noodles | 1.41% | 64.42% | 13.51 |
| 5 | Cheese + Dry Noodles | Pasta Sauce | 1.36% | 54.65% | 13.15 |

### Algorithm Performance Comparison

| Metric | Apriori | FP-Growth | Winner |
|--------|---------|-----------|--------|
| Execution Time | 1.81 seconds | 86.19 seconds | **Apriori** (47.64× faster) |
| Frequent Itemsets | 2,477 | 2,477 | Identical |
| Association Rules | 2,220 | 2,220 | Identical |
| Memory Efficiency | High | Moderate | **Apriori** |
| Scalability | Moderate | High (theoretically) | Dataset-dependent |

## Strategic Business Insights

### 1. Pasta Meal Ecosystem
**Finding**: Strongest associations involve pasta, sauce, and beef (lifts 12-14)

**Recommendations**:
- Place pasta, sauce, and beef in proximity or sight lines
- Bundle pasta + sauce + beef at discounted price
- Display easy pasta recipes near these sections
- Maintain synchronized stock levels

**Expected Impact**: 10-15% increase in basket size for pasta purchasers

### 2. Dairy + Deli + Bakery Connection
**Finding**: Milk + Cheese → Deli Meats + Bread (lift 14.16, highest)

**Recommendations**:
- "Complete Breakfast" cross-department marketing campaigns
- Deli samples near dairy section
- Pre-assembled sandwich ingredient packages
- Triggered digital coupons when scanning milk/cheese

**Expected Impact**: 5-8% increase in deli department sales

### 3. Staple Items Strategy
**Finding**: 20-28% of baskets contain milk, bread, and soft drinks

**Recommendations**:
- Competitive pricing as loss leaders to drive traffic
- Position at store perimeter to maximize exposure
- Place premium/complementary items nearby
- Tie loyalty program rewards to staple purchases

## Technologies Used

- **Python** - Core programming language
- **mlxtend** - Apriori and FP-Growth implementations
- **pandas** - Data manipulation and analysis
- **matplotlib/seaborn** - Data visualization
- **numpy** - Numerical computing

## Additional Resources
- [Notebook](https://github.com/thant-thiha/market-basket-analysis/blob/main/Market_Basket_Analysis_Retail_Store_Report.ipynb)
- [Report](https://github.com/thant-thiha/market-basket-analysis/blob/main/Market_Basket_Analysis_Retail_Store_Report.docx)

