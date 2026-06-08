# Vehicle-Design-Complexity-Cost-Optimization-Platform
Analytics product that quantifies vehicle design complexity cost and uses machine learning and optimization to recommend lower-cost design portfolios while meeting business and market constraints.


## Why Design Complexity Matters

Vehicle design complexity directly impacts:
- Bill of Material (BOM) cost
- Manufacturing efficiency
- Supplier coordination
- Inventory and warranty risk

As vehicle programs introduce more trims, features, and regional variants, complexity-driven cost often grows non-linearly. This analytics product is designed to help decision-makers identify where complexity adds value — and where it only adds cost.


## Business Questions This Product Answers

- Which trims and feature combinations drive the highest cost per unit?
- What is the marginal cost of adding a new design variant?
- Which configurations can be eliminated with minimal impact on market coverage?
- What is the lowest-cost design portfolio that still meets demand and regulatory constraints?


## Data Overview

This project uses synthetic and publicly inspired data to simulate:
- Vehicle trims and feature combinations
- Component-level cost contributions
- Production volumes and demand distribution
- Supplier and complexity indicators

The data structure is designed to mirror real-world automotive design and cost datasets while avoiding proprietary information.


| Data Element        | Description |
|--------------------|-------------|
| Trim ID            | Vehicle trim identifier |
| Feature Count      | Number of unique features |
| Shared Components  | % of components shared across trims |
| Unit Cost          | Estimated BOM cost |
| Volume             | Production volume |


## Analytics & Optimization Approach

### Cost Modeling
Statistical and machine learning models are used to estimate unit cost as a function of:
- Design complexity
- Feature uniqueness
- Production scale
- Supplier fragmentation

### Optimization
Mathematical programming techniques are applied to:
- Minimize total design portfolio cost
- Subject to market coverage, demand, and regulatory constraints
- Provide multiple feasible solutions for business trade-off discussions


## Product Mindset

This solution is built as an analytics product rather than a one-time analysis:
- Modular architecture for reuse and extension
- Clear separation between data, models, and optimization logic
- Designed for collaboration with Data Engineers and Software Engineers
- Balances analytic rigor with speed to delivery


## How This Would Be Used in Practice

- Design teams explore cost vs complexity trade-offs early in the lifecycle
- Product managers evaluate trim rationalization scenarios
- Complexity analytics partners support data-driven decision forums
- Leadership reviews optimized portfolios with quantified cost impact


## Implementation

### Notebook: `vehicle_complexity_analysis.ipynb`

A full end-to-end implementation using the **Car Features and MSRP** dataset (11,914 vehicles × 16 features):

| Section | Description |
|---------|-------------|
| Data Cleaning | Handle missing HP/cylinders, remove MSRP outliers |
| Complexity Score | Composite index: HP (35%) + Cylinders (25%) + Feature Count (25%) + Transmission (15%) |
| EDA | MSRP distribution, complexity vs cost scatter, correlation heatmap |
| ML Models | Linear, Ridge, Random Forest, Gradient Boosting — predict MSRP from complexity features |
| Feature Importance | Top cost drivers ranked by Random Forest importance |
| Portfolio Optimization | Select lowest-cost trim per Make × Vehicle Size, filter low-popularity configs |
| Business Output | Cost reduction % and config rationalization potential per Make |

### Key Results

- **Gradient Boosting achieves R² ~0.93** on MSRP prediction
- **Engine HP** is the single strongest cost driver
- **Luxury and High-Performance market flags** add significant price premium beyond mechanical specs
- Portfolio rationalization reduces trim count by **30–60%** for most makes with **10–25% average cost reduction**

## Dataset

**Car Features and MSRP** (Kaggle / CooperUnion)  
11,914 vehicles | 16 features | Makes: Chevrolet, Ford, BMW, Toyota, and 45+ more  
Source: https://www.kaggle.com/datasets/CooperUnion/cardataset

## Roadmap

- [x] Implement baseline cost prediction model (Linear, Ridge, RF, GBM)
- [x] Build Design Complexity Score composite index
- [x] Portfolio optimization — lowest-cost trim selection per segment
- [ ] Add constraint-based optimization with market coverage requirements (OR-Tools)
- [ ] Enable scenario-based simulations (what-if trim elimination)
- [ ] Build interactive Streamlit dashboard
- [ ] Prepare cloud deployment artifacts

![Python](https://img.shields.io/badge/Python-3.10-blue)
![Optimization](https://img.shields.io/badge/Optimization-OR--Tools-green)
![Status](https://img.shields.io/badge/Status-Active-brightgreen)
