# Global Sales & Margin Analytics Dashboard

An interactive Power BI dashboard analyzing multi-region sales revenue, profit margins, and product performance against targets. Built on a Star Schema data model with automated Power Query ETL pipelines and dynamic DAX time-intelligence measures.

---

## Dashboard Preview

### Executive Overview
![Overview Report Page](Images/Overview%20Report%20Page.png)
*Tracks Total Sales vs. Target, Total Margin %, regional revenue by continent, and category profitability.*

### Product Details (Drill-Through)
![Drill Through](Images/Drill%20Through.png)
*Drill-through navigation from category summary bars to subcategory-level performance.*

![Product Info](Images/Product%20Info.png)
*Subcategory profitability matrix with Year-over-Year (YoY) variance indicators.*

### Regional & Web Service Views
![Report By Continent](Images/Report%20By%20Continent.png)
*Continental sales and margin breakdown.*

![Second Report Page on PowerBI Web](Images/Second%20report%20Page%20on%20PowerBI%20Web.png)
*Published Power BI Service view.*

---

## Data & Architecture

* **ETL (Power Query):** Combines multi-file regional sales exports (`United States` and `Other Countries`) via Folder Connector, cleans text/delimited fields (`CustomerList`), and disables load on intermediate staging queries.
* **Data Model (Star Schema):** Connects a central `Sales` fact table to `Product` (*Category > Subcategory > Product* hierarchy), `Customer`, `Sales Territories`, `Sales Performance`, and a custom `Order Date` table using integer surrogate keys.
* **DAX Measures:** Calculates dynamic margins (`SUMX`, `DIVIDE`), percent-of-total distributions (`CALCULATE`, `ALL`), and time intelligence (`TOTALYTD`, `TOTALQTD`, `SAMEPERIODLASTYEAR`).
* **Design & UX:** Styled with a custom JSON theme (`Theme.json`) and background layout templates, featuring cross-filter controls, bookmarks, and drill-through navigation.

---

## Repository Structure

```text
├── Data/
│   ├── Dimensions/     # Customer, Product, Territories & Target files
│   └── Sales Data/     # Regional sales CSVs (US & Other Countries)
├── Images/             # Report screenshots
├── Template/           # Custom JSON theme & canvas background grids
├── pbix/               # Power BI Desktop (.pbix) file
└── README.md
