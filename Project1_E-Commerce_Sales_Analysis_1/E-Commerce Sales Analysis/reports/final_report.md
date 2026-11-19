# E-Commerce Sales & Customer Behavior Analysis using Python

*UCI Online Retail dataset | 2010-12-01 to 2011-12-09 | 541,909 transaction lines | GBP*

## 1. Objective and data

An online gift retailer wants to understand its sales performance, customer purchasing behaviour, product demand and geographic mix. The dataset has 541,909 transaction lines and 8 columns covering 2010-12-01 to 2011-12-09.

Cleaning: 5,268 exact duplicate rows were removed (536,641 remain). Completed sales (not cancelled, quantity and price above zero) total 524,878 lines. Postage/manual codes (DOT, POST, M) are excluded from product, country and order-value analysis. Rows with a missing CustomerID or Description were kept except where an analysis needs them.

## 2. Outliers and distributions

Quantity, unit price and line revenue are strongly right-skewed. 114 lines have a quantity of 1,000 or more; these are genuine bulk orders and were kept, so medians and log scales are used.

## 3. Revenue over time

Monthly revenue (all completed sales, including postage/manual lines) peaked in 2011-11 at £1,503,867 and was lowest in 2011-02 at £522,546 (complete months only). 2011-12 is a partial month (data ends 2011-12-09).

The weekly view peaks in the week ending 2011-11-20 (£387,065) against a median week of £176,362.

## 4. Products

Top product by revenue: Regency Cakestand 3 Tier (£174,157). Top by units: Paper Craft , Little Birdie (80,995 units, 100% from one order line, so this ranking is sensitive to bulk orders).

Fastest-rising top products (linear trend in monthly units): Rabbit Night Light (+37%/month), Popcorn Holder (+35%/month), Paper Chain Kit 50'S Christmas (+26%/month). Fastest-declining: Medium Ceramic Top Storage Jar (-35%/month), Wood Black Board Ant White Finish (-8%/month), Regency Cakestand 3 Tier (-5%/month). With about one year of data, seasonality can look like a trend.

## 5. Countries

The United Kingdom contributes £8,751,656 (85.1% of product revenue) out of 38 countries.

## 6. Orders

There are 19,792 product-only invoices; the median order is £302.25 and the mean £519.40 (a few very large orders pull the mean up). Orders peak on Thursday and around 12:00.

## 7. Customers

4,338 customers have a known ID (covering 84% of completed-sales revenue). The top 10 produce 17.3% and the top 20% produce 75% of known-customer revenue; 66% ordered more than once. Orders and revenue have a Spearman correlation of 0.81.

## 8. Cancellations

3,836 of 25,900 invoices are cancellations (14.81%), crediting back £893,980 (8.4% of completed-sales revenue).

## 9. Price and quantity

Spearman correlation between unit price and quantity is -0.407 (moderate negative association; higher-priced items tend to be bought in smaller quantities). This is an association only; it does not prove that price changes cause changes in quantity.

## 10. Recommendations

Plan stock and campaigns around the seasonal peak: revenue was highest in 2011-11 (£1,503,867) versus a low of £522,546 in 2011-02; build inventory and start promotions in the months before the peak.

Reduce dependence on the UK (85% of product revenue): test marketing and shipping offers in the strongest overseas markets (Netherlands, EIRE, Germany).

Protect high-value customers: the top 20% of known customers generate 75% of known-customer revenue - introduce account management, loyalty tiers or volume discounts for them.

Cut cancellations (14.8% of invoices): review the most-cancelled products for quality, description or packaging problems and check the process for wholesale orders.

Use the typical order (median £302) as a benchmark: free-shipping thresholds or bundles slightly above it can lift basket size.

Price and quantity show a moderate negative association; higher-priced items tend to be bought in smaller quantities (Spearman -0.41): offer multi-buy/bundle pricing on low-priced items that customers already buy in volume.

Time promotions and support to demand: orders peak on Thursday and around 12:00.

Watch demand trends: Rabbit Night Light is rising fastest among top products and Medium Ceramic Top Storage Jar is declining fastest - confirm with more than one year of data before acting.

## 11. Limitations

One retailer's historical data (Dec 2010 - Dec 2011); one year cannot separate seasonality from growth. The last month is partial. About a quarter of rows lack a CustomerID, so customer results cover identifiable customers only. Many customers are wholesalers. Cancellations are not linked to their original orders. Correlations show association, not causation.

## 12. Cross-check

16 of 19 supplied reference values matched exactly (see the cross-check table in the notebook).