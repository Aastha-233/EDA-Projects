# Bank Marketing Campaign & Customer Segmentation Analysis

*UCI Bank Marketing dataset | 45,211 customer contacts | target: term-deposit subscription*

## 1. Objective and data

A bank wants to make its telephone marketing for term deposits more effective. The dataset has 45,211 contacts and 17 columns. The target is whether the client subscribed.

Cleaning: 0 duplicate rows and 0 missing cells were found. The label 'unknown' (e.g. in poutcome and contact) is a hidden missing value and was kept as its own category. pdays = -1 (never contacted) was converted to a missing value for statistics. Outliers in balance, duration and contacts are plausible real cases and were kept; medians and log/clipped views are used.

## 2. Target and distributions

11.70% of contacts subscribed (5,289 of 45,211), so the target is imbalanced. Median age is 39, median balance €448, median call 180s and median contacts 2; balance, duration and contacts are strongly right-skewed.

## 3. Age, job, education and marital status

Age: highest rate 65+ (42.1%), lowest 45–54 (9.3%). Job: highest 'student' (28.7%), lowest 'blue-collar' (7.3%). Education: highest tertiary (15.0%), lowest primary (8.6%). Marital status: highest single (14.9%), lowest married (10.1%). Group sizes differ, and these variables overlap, so differences are associations only.

## 4. Balance

Median balance is €733 for subscribers and €417 for non-subscribers (means €1,804 vs €1,304). The distributions overlap heavily.

## 5. Campaign contacts and channel

The subscription rate by number of contacts falls from 14.6% at one contact to 3.9% for the highest group. The most effective known channel is cellular (14.9%).

## 6. Previous campaign and seasonality

Clients with a successful previous campaign respond far more often than average.

Best month by conversion (n≥200): mar; busiest month by call volume: may. The data has no year, so only calendar seasonality can be assessed.

## 7. Correlations and relationships

No single numeric variable is strongly correlated with subscription, so outcomes depend on combinations of factors. Call duration is longer for subscribers but is only known after the call, so it cannot be used for targeting.

## 8. Customer segmentation

Best segment: 25–34 | €2,001–5,000 | no housing loan at 29.7% (n=649, lift 2.5x). Lowest: 45–54 | ≤ €0 | housing loan at 5.2% (n=869). Only segments with at least 300 customers are ranked.

## 9. Recommendations

Prioritise high-propensity audiences: the best segment (25–34 | €2,001–5,000 | no housing loan) subscribes at 29.7% versus 11.7% overall (lift 2.5x, n=649). Pilot campaigns on segments like this first.

Target by age and occupation: 65+ is the strongest age group (42.1%) and 'student' the strongest job group (28.7%), while 'blue-collar' is the weakest (7.3%). Shift call effort towards the former and use cheaper channels for the latter.

Re-contact previous successes first: clients with a successful earlier campaign subscribe at 64.7% versus 9.2% for clients with no recorded history (n=1,511).

Cap repeated contacts: the subscription rate is 14.6% at one contact and 3.9% at 11+ contacts. Set a contact limit and stop calling unresponsive clients to save cost.

Prefer the more effective channel: cellular contacts convert at 14.9%; improve recording of the contact channel because 'unknown' (4.1%) hides what was used.

Schedule by season: the best month for conversion (n≥200) is mar while the busiest month for calls is may. Test moving some call capacity towards high-conversion months.

Use balance as a screening aid: median balance is €733 for subscribers vs €417 for non-subscribers, but the overlap is large so combine it with other signals.

Do not use call duration for targeting (median 426s for subscribers vs 164s): it is only known after the call. Use it to evaluate call scripts and agent training instead.

## 10. Limitations

Findings are associations, not causes. The target is imbalanced. 'unknown' labels hide missing information. Duration is known only after the call. The data has no year. One Portuguese bank, 2008-2010; results may not transfer. Segments are rule-based and should be validated with a pilot campaign.

## 11. Dataset check

6 of 6 sanity checks against the standard bank-full.csv matched.