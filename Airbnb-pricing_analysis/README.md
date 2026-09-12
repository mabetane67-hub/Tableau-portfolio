# Seattle Airbnb Pricing Analysis (Tableau)

An interactive Tableau dashboard exploring how Airbnb nightly prices in Seattle, WA vary by bedroom count, zip code, and time of year, built on the [(https://www.kaggle.com/datasets/alexanderfreberg/airbnb-listings-2016-dataset)] Seattle dataset (listings + calendar data).

## 📊 Dashboard

**Airbnb Pricing Analysis** — one dashboard, five views:

| View                               |          What it shows                      |     
| Avg Price per Bedroom's Number     | Average nightly price by number of bedrooms |
| Distinct Count of Bedrooms Listing | Number of unique listings per bedroom count |
| Price per Zipcode                  | Average nightly price across Seattle zip codes |
| Price by Zipcode                   | Average nightly price by zip code, sorted descending |
| Price per Year                     | Weekly price trend across the calendar year, split by Peak (Jun–Aug) vs. Off-Peak season |

🔗 **Live dashboard:** [(https://public.tableau.com/app/profile/mohamed.ahmed.betane/vizzes)]

## 🔑 Key findings

- Across ~2,870 Seattle listings, nightly price scales steadily with bedroom count — from **~$102/night for 1BR** up to **~$661/night for 6BR** listings.
- The priciest zip codes cluster around downtown/central Seattle (**98134, 98101, 98121, 98119, 98109**), averaging **$180–$205/night**.
- **67% of listings are entire home/apt**, 30% are private rooms, and 3% are shared rooms.
- Prices show a clear **seasonal lift in the summer months (Jun–Aug)** compared to the rest of the year.

## 🧮 Calculated fields

```
Price per Bedroom = IF [Bedrooms] > 0 THEN [Price] / [Bedrooms] ELSE NULL END

Season = IF DATEPART('month', [Date]) IN (6, 7, 8) THEN "Peak" ELSE "Off-Peak" END
```

## 🗂️ Data

- **Source:** Inside Airbnb Seattle open dataset (`listings.csv` + `calendar.csv`, joined in Excel before loading into Tableau)
- **Fields used:** price, bedrooms, zip code, room type, date/availability (96 columns available in total, most unused by this analysis)

**Known limitation:** the merged listings + calendar workbook tops out at exactly 1,048,575 rows — Excel's per-sheet row limit. That caps this analysis at ~2,873 of the ~3,818 listings in the full Seattle dataset (roughly 75%), so the zip-code and time-based views slightly undercount. A future version could avoid this by using Tableau's native multi-table relationships to join listings and calendar data directly, instead of pre-joining in Excel.

## 🛠️ Tools

- Tableau Desktop / Tableau Public
- Microsoft Excel (data prep / join)

## 📁 File

seattle-airbnb-pricing-analysis.twbx

## ▶️ How to view

1. Download seattle-airbnb-pricing-analysis.twbx
2. Open it in [Tableau Desktop](https://www.tableau.com/products/desktop) or the free [Tableau Public](https://public.tableau.com/) app
3. Or click the live dashboard link above to view it in your browser — no software needed
