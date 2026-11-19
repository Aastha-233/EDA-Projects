# Bank Marketing Campaign & Customer Segmentation Analysis

> Analyzed 45K+ bank telemarketing contacts using Python, pandas, NumPy, Matplotlib and Seaborn to profile term-deposit subscribers by age, job, education, balance, contact history and channel, segment customers, and recommend how to target campaigns more effectively.

## Project objective
A bank wants to improve the effectiveness of its term-deposit marketing campaigns. The analysis identifies which customers and campaign conditions are associated with subscription and converts the patterns into recommendations.

## Dataset
**Bank Marketing**, UCI Machine Learning Repository: <https://archive.ics.uci.edu/dataset/222/bank+marketing> (Moro, Cortez & Rita, 2014; CC BY 4.0).
File used: `bank-full.csv` (semicolon-separated), 45,211 rows x 17 columns; target `y` = subscribed to a term deposit (yes/no).
The notebook downloads it automatically if missing (see `data/README_DATA.txt`).

## Project structure
```
Bank Marketing Analysis/
  data/                 README_DATA.txt  (+ bank-full.csv once downloaded)
  notebooks/            bank_marketing_analysis.ipynb
  reports/              17 charts (.png), EDA_report.pdf, presentation.pptx, final_report.md, results.json  (created by running the notebook)
  README.md
  requirements.txt
```

## Analysis performed
- **Data understanding:** data dictionary, descriptive statistics, missing values (including hidden `unknown` labels), duplicates.
- **Cleaning:** `unknown` kept as its own category; `pdays = -1` converted to "never contacted"; engineered `age_group`, `balance_band`, `campaign_group`; month ordered Jan-Dec; outliers investigated and kept (medians / clipped / log views used).
- **Target analysis:** subscription rate, class imbalance.
- **Univariate:** histograms and box plots of age, balance, duration, contacts.
- **Bivariate:** subscription rate (with 95% intervals and group sizes) by age group, job, education, marital status, balance band, number of contacts, channel and previous outcome; cross-tabulations; box plots by outcome; scatter plots.
- **Time pattern:** calls and conversion by month.
- **Multivariate:** correlation heatmap; age x balance heatmap.
- **Segmentation:** rule-based segments (age | balance | housing loan) ranked by rate and lift (n >= 300).
- **Recommendations:** generated from the computed results at the end of the notebook.

## Key findings (from running the notebook on bank-full.csv)
- 45,211 contacts, no duplicates and no true missing values (all dataset checks match); **11.7% subscribed** (5,289 clients) - an imbalanced target.
- **Age is U-shaped:** subscription is highest for clients **65+ (42.1%)** and **under 25 (25.6%)**, and lowest at 45-54 (9.3%) (the oldest and youngest groups are small, n≈810 each).
- **Job:** students (28.7%) and retired clients (22.8%) respond best; blue-collar (7.3%), entrepreneurs (8.3%) and housemaids (8.8%) respond worst.
- **Education:** tertiary 15.0%, secondary 10.6%, primary 8.6%. **Marital status:** single 14.9%, divorced 11.9%, married 10.1%.
- **Balance:** median €733 for subscribers vs €417 for non-subscribers, but the distributions overlap heavily.
- **Contacts:** the rate falls steadily from 14.6% at one contact to 3.9% at 11+ contacts.
- **Channel:** cellular 14.9%, telephone 13.4%, unknown 4.1% (the "unknown" channel is a data gap).
- **Previous campaign:** a previous success converts at **64.7%**, versus 12.6% after a failure and 9.2% when there is no history.
- **Seasonality:** the busiest calling month is May, while March has the highest conversion (among months with n >= 200).
- **Segments:** the best segment is aged 25-34 with a €2,001-5,000 balance and no housing loan (29.7%, 2.5x the average, n=649); clients aged 35-54 with a housing loan and low balance convert at about 5%.
- **Duration** is longer for subscribers (median 426s vs 164s) and has the strongest correlation with subscription (0.39), but it is only known after the call, so it cannot be used for targeting.

## Key insights and recommendations
Prioritise high-propensity segments and previous responders; set a cap on repeated contacts; use the more effective channel and record the channel properly; rebalance call effort towards high-conversion months; use duration only to evaluate call quality. See the notebook's *Insights, recommendations and limitations* section.

## Limitations
Associations, not causes; imbalanced target; `unknown` values hide missing information; `duration` is known only after the call; no year in the data (seasonality only); one Portuguese bank, 2008-2010; segments are rule-based and should be piloted.

## How to run (Windows)
1. **Install Python** from <https://www.python.org/downloads/>. On the first installer screen tick **"Add python.exe to PATH"**, then click *Install Now*.
2. Unzip the project to an easy place, e.g. `C:\Users\YourName\Documents\Bank Marketing Analysis`.
3. *(Optional - the notebook tries to download the data itself.)* Put the dataset in the `data` folder as described in `data/README_DATA.txt`.
4. Open the project folder in File Explorer, click the address bar, type `cmd`, press **Enter**.
5. Create a virtual environment: `python -m venv venv`
6. Activate it: `venv\Scripts\activate`  (you should now see `(venv)`).
7. Install libraries: `pip install -r requirements.txt`
8. Start Jupyter: `jupyter notebook` (your browser opens).
9. Open `notebooks` -> `bank_marketing_analysis.ipynb`.
10. Choose **Kernel -> Restart & Run All** (or **Run -> Run All Cells**) and wait for the last cell to finish.
11. Open the `reports` folder: charts (`.png`), `EDA_report.pdf`, `presentation.pptx`, `final_report.md`, `results.json`.

**Troubleshooting:** *"python is not recognized"* -> reinstall Python and tick "Add to PATH". *FileNotFoundError* -> check the dataset file name and folder. *Module not found* -> make sure `(venv)` is active and re-run step 7.

## Upload to GitHub
1. Create a free account at github.com -> **New repository** (name: `bank-marketing-campaign-analysis`, Public, no template).
2. On the new repository page click **uploading an existing file**, drag in the whole project contents (`notebooks`, `reports`, `data/README_DATA.txt`, `README.md`, `requirements.txt`, `.gitignore`), and click **Commit changes**.
3. *(Skip uploading the large raw dataset - the README links to it.)* Paste the repository URL in your submission.