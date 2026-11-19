# E-Commerce Sales & Customer Behavior Analysis using Python

> Analyzed 500K+ retail transactions (Dec 2010 - Dec 2011) using Python, pandas, NumPy, Matplotlib and Seaborn to uncover sales trends, top-performing products, geographic revenue distribution, customer value concentration, cancellation behaviour and price-quantity relationships, and turned the findings into business recommendations.

## Project objective
An online gift retailer wants to understand its sales performance, customer purchasing behaviour, product demand and geographic distribution. This end-to-end EDA answers 10+ business questions and ends with data-driven recommendations.

## Dataset
**Online Retail**, UCI Machine Learning Repository: <https://archive.ics.uci.edu/dataset/352/online+retail> (Daqing Chen, 2015; CC BY 4.0).
541,909 rows x 8 columns (`InvoiceNo, StockCode, Description, Quantity, InvoiceDate, UnitPrice, CustomerID, Country`), 1 Dec 2010 - 9 Dec 2011, amounts in GBP.
The notebook downloads it automatically if missing (see `data/README_DATA.txt`).

## Project structure
```
E-Commerce Sales Analysis/
  data/                 README_DATA.txt  (+ Online Retail.xlsx once downloaded)
  notebooks/            ecommerce_sales_analysis.ipynb
  reports/              17 charts (.png), EDA_report.pdf, presentation.pptx, final_report.md, results.json  (created by running the notebook)
  README.md
  requirements.txt
```

## Analysis performed
- **Data understanding:** shape, data types, descriptive statistics, data dictionary, missing values, duplicates.
- **Cleaning:** exact duplicates removed into a new dataframe (original kept unchanged); cancellations (`C` invoices), `Quantity <= 0` and `UnitPrice <= 0` excluded from completed sales; postage/manual codes `DOT`, `POST`, `M` excluded from product/country/order analysis; missing CustomerID/Description kept unless needed.
- **Outliers:** IQR flags + inspection of the largest lines; genuine bulk orders kept, so medians and log scales are used.
- **Univariate:** distributions of quantity, unit price and line revenue (histograms, box plots).
- **Bivariate / multivariate:** price vs quantity (Spearman), orders vs revenue, customer-level correlation heatmap, order value by country/weekday.
- **Time series:** monthly and weekly revenue; weekday x hour ordering heatmap; product demand trends (rising/declining).
- **Customer & product analysis:** top products by revenue and units, top customers, revenue concentration (top 20%), cancellations.
- **Business recommendations:** generated from the computed numbers at the end of the notebook.

### Definitions
Revenue = `Quantity * UnitPrice`. **Monthly/weekly revenue** = all completed sales *including* postage/manual lines. **Product revenue** (rankings, countries, order value) *excludes* DOT/POST/M, so it is slightly lower than the monthly total. **Customer analysis** uses completed sales with a known CustomerID. **Order value** = product-only revenue per invoice.

## Key findings (from running the notebook on the full dataset)
- 541,909 rows -> 5,268 exact duplicates removed -> 536,641 rows; 524,878 completed-sales lines. Completed sales total £10.64M; **product revenue £10.28M** (postage/manual lines excluded).
- Monthly revenue is lowest in **Feb 2011 (£522,546)** and highest in **Nov 2011 (£1,503,867)**; the busiest week ends 20 Nov 2011 (£387k). **Dec 2011 is partial** (data ends 9 Dec).
- Top product by revenue: **REGENCY CAKESTAND 3 TIER** (£174,157). Top by units: **PAPER CRAFT, LITTLE BIRDIE** (80,995 units - all from a single order line, so it is a one-off bulk order).
- The **United Kingdom provides 85.1%** of product revenue (£8.75M) among 38 countries; next are the Netherlands, EIRE and Germany.
- 19,792 product invoices: **average £519.40, median £302.25** - a few very large orders pull the mean up.
- 4,338 known customers: the **top 20% generate 74.7%** of known-customer revenue; 65.6% ordered more than once; orders and revenue are strongly related (Spearman 0.81).
- **14.8%** of invoices (3,836 of 25,900) are cancellations, crediting back £894k (8.4% of completed-sales revenue).
- Unit price vs quantity: Spearman **-0.41** (moderate negative association; not proof of cause).
- Orders peak on Thursdays and around midday.
- Rising demand among top products: Rabbit Night Light, Popcorn Holder, Paper Chain Kit; falling: Medium Ceramic Top Storage Jar (seasonality can look like a trend with one year of data).

**Cross-check against the reference values:** 16 of 19 match exactly. Three differ slightly and are explained: product revenue (£10,280,007.33 vs £10,280,009.88) and UK revenue (£8,751,655.68 vs £8,751,658.23) differ by exactly £2.55 because one lowercase stock code `m` ("Manual", invoice 539736) is treated as a manual line here; the median invoice is £302.25 vs the quoted £302.20.

## Key insights and recommendations
Plan inventory/campaigns around the seasonal peak; reduce UK dependence; protect the high-value customers who drive most revenue; investigate the most-cancelled products; use bundle/volume pricing; time promotions to busy days/hours. See the *Insights and business recommendations* section of the notebook.

## Limitations
One retailer's historical data (2010-2011); one year cannot separate seasonality from growth; December 2011 is partial; ~25% of rows lack CustomerID; many buyers are wholesalers; cancellations are not linked to original orders; correlation does not prove causation.

## How to run (Windows)
1. **Install Python** from <https://www.python.org/downloads/>. On the first installer screen tick **"Add python.exe to PATH"**, then click *Install Now*.
2. Unzip the project to an easy place, e.g. `C:\Users\YourName\Documents\E-Commerce Sales Analysis`.
3. *(Optional - the notebook tries to download the data itself.)* Put the dataset in the `data` folder as described in `data/README_DATA.txt`.
4. Open the project folder in File Explorer, click the address bar, type `cmd`, press **Enter**.
5. Create a virtual environment: `python -m venv venv`
6. Activate it: `venv\Scripts\activate`  (you should now see `(venv)`).
7. Install libraries: `pip install -r requirements.txt`
8. Start Jupyter: `jupyter notebook` (your browser opens).
9. Open `notebooks` -> `ecommerce_sales_analysis.ipynb`.
10. Choose **Kernel -> Restart & Run All** (or **Run -> Run All Cells**) and wait for the last cell to finish.
11. Open the `reports` folder: charts (`.png`), `EDA_report.pdf`, `presentation.pptx`, `final_report.md`, `results.json`.

**Troubleshooting:** *"python is not recognized"* -> reinstall Python and tick "Add to PATH". *FileNotFoundError* -> check the dataset file name and folder. *Module not found* -> make sure `(venv)` is active and re-run step 7.

## Upload to GitHub
1. Create a free account at github.com -> **New repository** (name: `ecommerce-sales-customer-analysis`, Public, no template).
2. On the new repository page click **uploading an existing file**, drag in the whole project contents (`notebooks`, `reports`, `data/README_DATA.txt`, `README.md`, `requirements.txt`, `.gitignore`), and click **Commit changes**.
3. *(Skip uploading the large raw dataset - the README links to it.)* Paste the repository URL in your submission.