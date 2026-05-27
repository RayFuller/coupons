# Required Assignment 5.1: Will the Customer Accept the Coupon?

| | |
|---|---|
| **School:** | UC Berkeley Engineering |
| **Course:** | Professional Certificate in Machine Learning and Artificial Intelligence |
| **Session:** | April 2026 |
| **Date of Submission** | May 28, 2026 |
| **Student Name** | Ray Fuller |
| **Jupyter Notebook** | https://github.com/RayFuller/coupons/blob/main/prompt.ipynb |
| **Data Source** | https://doi.org/10.24432/C5GS4P |
---

## Project Overview

Will the Customer Accept the Coupon? This application is an Exploratory Data Analysis (EDA) of drivers who (while driving) received coupons via cell phone for various restaurants, bars and coffee houses. It examines the relationship between driver and contextual factors (age, gender, marital status, income, time of day, and more) and coupon acceptance. It is an initial attempt to better understand which factors appear to influence certain drivers, under certain circumstances, to either accept or reject each type of coupon.

## Data

The data is sourced from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/) (see above link) and was collected via a survey on [Amazon Mechanical Turk](https://www.mturk.com). The survey describes different driving scenarios (destination, time of day, weather, passenger, etc.) and asks whether the driver would accept the coupon. The dataset contains roughly 12,600 responses across five coupon types: less expensive restaurants (under \$20), coffee houses, carryout, bar, and more expensive restaurants (\$20–\$50).

## Methodology

I started by cleaning the data. One column ('car') was missing for almost every record, so I dropped it entirely since it had too little information to tell me anything useful. A handful of other columns, mostly describing how often a driver visited certain businesses, had a small number of missing entries. Since those accounted for less than 5% of the rows in total, I chose to remove the affected rows rather than guess at replacement values, which left me with about 12,000 complete records to work with.

From there, my approach was to compare acceptance rates (the proportion of drivers who said "yes") across the five coupon types and against the driver and situational details the survey recorded. I relied on bar charts and simple summary statistics rather than anything more complex, since the goal at this stage was to *understand* the data, not to predict with it. When I wanted to know which factors mattered most, rather than guessing I measured the "spread" for each one: the gap between the highest- and lowest-accepting groups within that category. My assumption was that a factor with a wide spread has more influence on a driver's decision than one where every group accepts at roughly the same rate. The notebook walks through all of this in detail.

## Findings

Here is what stood out to me once I started exploring the data:

- **Overall, about 57% of the coupons offered were accepted** (a little more than half). That alone tells me coupons "work" more often than not, but the average hides how much the answer changes depending on the situation.
- **Acceptance varied sharply by the type of coupon.** Carryout and cheap-restaurant coupons were accepted most often (about 74% and 71%), while bar and expensive-restaurant coupons were accepted the least (about 41% and 45%). My takeaway is that the type of business matters a great deal and not all coupons are accepted at the same rate.
- **For bar coupons, the single biggest factor I found was how often a driver already goes to bars.** Frequent bar-goers accepted about 76% of the time, compared to only about 37% for those who rarely or never go — nearly double the rate. Age, income, and marital status appeared to matter far less; once I knew how often someone visited bars, adding those other details barely moved the number.
- **For my own investigation I looked at restaurant coupons, expecting income to be the main driver, but it was not.** Acceptance stayed fairly flat across income levels. What did appear to matter was the *situation* a driver was in: sunny weather, an afternoon time of day, and a coupon that stayed valid for a full day. On their own each helped a little; combined, they pushed acceptance of cheap-restaurant coupons up to about 90%, compared to roughly 65% the rest of the time.
- **There is no one-size-fits-all answer.** That same winning combination did far less for expensive-restaurant coupons, and when I looked across all coupon types together, no single factor stood out. This convinced me that what makes a driver say "yes" really does depend on the kind of coupon being offered.

## Recommendations

Based on what I found, here is the advice I would give to someone deciding how to send these coupons:

- **Send coupons for places a driver already goes.** The clearest pattern in the whole project was that familiarity matters. Bar coupons in particular worked well for regular bar-goers and poorly for everyone else.
- **Do not treat every coupon the same.** Because the factors that drive a "yes" change from one coupon type to the next, I would run each type as its own campaign rather than applying a single rule across all of them.
- **For cheap-restaurant coupons, pay attention to timing.** Sending them on a sunny afternoon, with a full day to use them, was by a wide margin the best-performing combination I found.
- **Spend less effort on demographics.** Details like income, gender, and age told me very little about who would accept. I would put that effort into timing and context instead.

## Next Steps

If I had more time or more data, there are a few things I would want to follow up on. First, I would re-run the bar coupon comparisons using a stricter definition of a "frequent" visitor, since the survey's categories left some room for interpretation and I want to be confident in that result. Second, I would apply the same approach to the coffee house and carryout coupons, which I did not explore in as much depth here. Finally, because everything in this project is based on survey responses rather than real driving behavior, I would want to test these ideas with an actual coupon campaign before relying on them too heavily.

## Repository Contents

- `prompt.ipynb` — Jupyter notebook containing the full exploratory data analysis
- `README.md` — this file
- `data/coupons.csv` — the source dataset (included per the assignment instructions)