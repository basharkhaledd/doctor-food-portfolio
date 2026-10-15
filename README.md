# Doctor Food analytics

A public snapshot of a nutrition analytics dashboard. The page is a static HTML report. It does not include the application source code, a database, or production user records.

**The dataset is synthetic.** It is not a copy of real members. The dashboard states this in the gold label: “SYNTHETIC — not production user data.”

## What the dashboard shows

The report covers a 12-week window ending 2026-10-14. Grain is one food on one meal, and one member-day from signup through the snapshot, including days with no meal.

Headline results on this extract:

- 178 members and 7,213 meals
- Logging rate 33.6% of member-days
- Calorie adherence 90.3% on logged days
- Day-7 logging retention 41.2%
- Catalog match 85.9%

Quality checks passed 42 of 42. Cleaning removed 28 invalid rows, removed 585 rows that depended on them, and repaired 5 confidence values.

## How it was built

- **Python** generates a repeatable synthetic population from the application’s table grain and checks the warehouse before export.
- **Pandas** profiles the extract, applies the data-quality rules, and shapes the star schema.
- **SQL** defines the warehouse tables and the KPI calculations: logging rate, calorie adherence, protein and fiber goal rates, retention, catalog match, and vision outcomes.
- **Data quality checks** reject impossible nutrients, portions, timestamps, duplicate keys, and orphaned child rows. Confidence values outside 0–1 are repaired and counted.
- **Power BI** uses the same KPI definitions for the Desktop report. Calorie adherence is the average of daily intake-to-target ratios on logged days. Sodium at 2,300 mg is a descriptive flag, not medical advice. The AI cost is an illustrative token price, not an invoice.

## View it

Open the published page:

https://basharkhaledd.github.io/doctor-food-portfolio/

The numbers on that page are the synthetic snapshot. They are not a live connection to an application database.


## Executive dashboard

The same synthetic snapshot is also published as an executive page: KPI cards, a weekly calorie and protein trend, meal-type distribution, and the top foods by calories.

https://basharkhaledd.github.io/doctor-food-portfolio/executive/

GitHub Pages cannot render a Power BI Desktop file in the browser. The `.pbix` is not in this repository. Its refresh steps contain a local Windows path, so the public page is the static presentation above, not a live connection.
