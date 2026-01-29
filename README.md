# Coffee Sales Dashboard - Excel Analytics Project

End-to-end Excel solution transforming raw coffee order data into an interactive sales dashboard for customer, product, and geographic analysis.

## Executive Summary

This Excel dashboard consolidates 1,000+ coffee orders into a single interactive view to support sales and marketing decision-making.

Key outcomes:
- United States identified as dominant market (78% of revenue, $35,639)
- Top customer analysis highlighted high-value profiles (Allis Wilmore: $317)
- Multi-dimensional analysis by Coffee Type, Roast, Size, and Loyalty status
- Automated dashboard replacing manual Excel reporting

Project Resources: [Download Excel Dashboard](https://github.com/elenaderensis/excel-coffee-sales-dashboard/blob/main/Coffee%20orders%20data.xlsx)

**Dashboard Overview**
<img width="871" height="501" alt="Coffee Sales Dashboard" src="https://github.com/user-attachments/assets/c1a343ff-8bb6-474d-a386-ca5afbe267f8" />


## Business Context and Objectives

The Challenge:<br>
Sales teams managed customer, product, and order data in separate spreadsheets, creating visibility gaps in customer value, product performance, and geographic distribution.

Project Scope:<br>
This Excel dashboard consolidates 1,000+ transactions across orders, customers, and products, enabling:
- Sales trends (2019-2020) and geographic distribution
- Customer segmentation and loyalty analysis  
- Product performance across Coffee Type, Roast, and Size
- Interactive filtering via slicers


## Data Architecture

### Data Structure

**Orders Table (Fact table):** 1,000 transactional records
- Core Fields: Order ID, Order Date, Customer ID, Product ID, Quantity, Sales
- Enriched Fields: Customer Name, Email, Country, Coffee Type, Roast Type, Size, Unit Price, Loyalty Card

**Customers Table (Dimension):** 1,000 unique customer records
- Fields: Customer ID, Customer Name, Email, Phone, Address, City, Country, Postcode, Loyalty Card

**Products Table (Dimension):** 48 product SKUs
- Fields: Product ID, Coffee Type (Arabica, Excelsa, Liberica, Robusta), Roast Type (Light, Medium, Dark), Size (0.2kg, 0.5kg, 1.0kg, 2.5kg), Unit Price, Profit

### Data Model

**Star schema** with Orders as the central fact table connected to Customers and Products dimensions via XLOOKUP, enabling efficient filtering and scalable data integrity.


## Technical Implementation

### Excel Formulas & Functions

**XLOOKUP for Data Enrichment:** Dynamically pulls customer and product data into the Orders table from master tables, ensuring consistency without manual updates.
```excel
=XLOOKUP([@[Customer ID]], customers[Customer ID], customers[Customer Name], "Not Found")
```

### Pivot Tables & Data Aggregation

**Total Sales Over Time (Line Chart):** Time hierarchy (Year > Month) with Coffee Type columns reveals seasonal patterns and product performance—Arabica consistently leads.

**Sales by Country (Horizontal Bar Chart):** Reveals geographic concentration with United States dominating at $35,639 (78% of revenue).

**Top 5 Customers (Horizontal Bar Chart):** Identifies high-value customers for retention programs. Top customer ($317) to #5 ($278) shows balanced distribution.

### Interactive Dashboard Elements

**Slicers:** Timeline (2019-2020), Roast Type (Dark/Light/Medium), Loyalty Card (Yes/No), and Size (0.2-2.5 Kg) enable synchronized filtering across all charts for multi-dimensional analysis.


## Key Findings & Insights

### Finding 1: Geographic Revenue Concentration
United States dominates with **$35,639 (78%)** of sales, followed by Ireland (15%) and UK (6%). This concentration—driven by 60%+ of customers being US-based—creates vulnerability to market disruptions. **Business Impact:** Diversification through targeted UK/Ireland campaigns could reduce risk while leveraging existing logistics.

### Finding 2: Coffee Type Performance Disparity
Arabica consistently generates 2-3x higher sales than other varieties, with peak months showing $800+ vs $200-400 for Excelsa, Liberica, and Robusta. This heavy skew toward premium products indicates either strong preference or undermarketing of alternatives. **Business Impact:** Either expand Arabica offerings or launch educational campaigns positioning Robusta as value option and Liberica as unique specialty.


## Recommendations & Business Impact

**1. Geographic Diversification (UK/Ireland):** Allocate 20% of marketing budget to targeted digital campaigns and localized product offerings. Partner with EU distributor to reduce shipping costs. **Target:** Reduce US concentration from 78% to 65%, generating +$4,000 annual revenue.

**2. Loyalty Program Expansion:** Streamline enrollment at checkout, increase signup bonus to 10%, and introduce Bronze/Silver/Gold tiers ($200/$500/$1000 thresholds). **Target:** Increase enrollment from 45% to 60%, generating +$882 annual revenue from 14% higher spending by new members.

**3. Product Mix Optimization:** Launch educational campaigns positioning Robusta as value option and Liberica as specialty variety. Include samples in Arabica orders over $50 to drive trial.

**4. Premium Customer Retention:** Implement quarterly check-ins and exclusive previews for top 20 customers (~$4,500 annual revenue). Alert system for customers exceeding 60


## Future Enhancements

### 1. Profitability Analysis Integration
Add gross profit calculations by integrating Products[Profit] column into Orders table. This reveals whether high-sales products are also high-margin products, enabling strategic focus on margin optimization beyond revenue growth.

### 2. Customer Lifetime Value (CLV) Calculation
Create pivot table tracking Total Orders, Average Order Value, Days Since Last Order, and Projected Annual Value. Distinguishes high-frequency customers from one-time purchasers and identifies at-risk high-value customers for reactivation.

### 3. Cohort Analysis for Loyalty Program ROI
Track revenue retention curves by enrollment cohort (Month 1, 3, 6, 12) to prove loyalty program ROI with hard retention metrics rather than aggregate snapshots.

### 4. Inventory Management Integration
Connect sales data to inventory levels with conditional formatting alerts (Red/Yellow/Green) for reorder points. Prevents stockouts on high-demand SKUs (0.5kg Arabica) and reduces carrying costs for slow-movers.

**Business Value:** Proves loyalty program ROI by showing enrolled customers retain longer and spend more over 12-month horizon. Justifies expansion investment with hard retention metrics, not just snapshot averages.


### 4. Inventory Turnover & Stockout Prevention
**Current Limitation:** Sales data exists but not connected to inventory levels.

**Enhancement:**
Add Inventory table tracking:
- Current stock levels by Product ID
- Reorder point thresholds
- Lead time from supplier

Build conditional formatting alerts:
- **Red:** Stock below reorder point
- **Yellow:** Stock projected to hit reorder point within lead time based on current sales velocity
- **Green:** Healthy inventory

**Business Value:** Prevents lost sales from stockouts (current issue: 0.5kg Arabica frequently out of stock based on operational feedback). Reduces excess inventory carrying costs for slow-moving SKUs (Large sizes of Excelsa/Liberica).


## Project Reflection

This project demonstrates the complete Excel analytics lifecycle with focus on translating technical capability into actionable business strategy. Key design decisions solve real commercial challenges: **star schema** enables easy data refresh, **XLOOKUP** eliminates manual errors, **slicers** enable self-service analysis, and **horizontal bar charts** make rankings instantly digestible.

The dashboard's value isn't in reporting the $35K US revenue—it's in immediately answering strategic questions: "Why did June 2020 spike?" (Arabica orders doubled), "Should we expand to Germany?" (UK/Ireland as proxy), "Is our loyalty program worth it?" (14% higher AOV proves ROI).

**Result:** Sales meetings shifted from "What happened?" to "What should we do differently?"—exactly the outcome analytics should deliver.
