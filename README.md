# WGU-DataAnalytics-Capstone
D502 Coursework for Jupyter notebook progress completed separately. Reuploaded to Github for sharing purposes.

# PDX vs. DFW: Home Value & Growth Rate Comparison

**WGU B.S. Data Analytics Capstone (D502)** · Elijah Moos

Which metro area, Portland (PDX) or Dallas–Fort Worth (DFW), offers the
"safer" home investment based on historical home values and growth rates
across each region's largest cities?

## Key Findings

| Test | t-statistic | p-value | Result |
|---|---|---|---|
| Home values (PDX vs. DFW) | 7.34 | < 0.001 | PDX values are significantly higher |
| Growth rate, 2012–2025 | -1.74 | 0.11 | DFW grew faster, but not significantly (α = 0.05) |

- **PDX** cities grew **114%–159%** from 2012 to 2025. Portland grew the
  least of any city studied, trailing its own suburbs.
- **DFW** cities grew **143%–207%**. Growth ran almost exactly inverse to
  price: Dallas and Garland (the cheapest) grew most, while Frisco and
  Plano (the priciest) grew least.
- **Bottom line:** Neither region is a clearly superior investment on
  value or growth alone, so other factors (jobs, cost of living, lifestyle)
  can reasonably drive the decision.

![PDX vs DFW comparison](images/pdx_vs_dfw_comparison.png)
![Growth rate box plot](images/growth_rate_boxplot.png)

## Data

[Zillow Home Value Index (ZHVI)](https://www.zillow.com/research/data/),
city-level, single-family homes, mid-tier (33rd–67th percentile), smoothed
and seasonally adjusted. Monthly values from January 2000 through
November 2025.

The raw CSV is not included in this repo. To reproduce, download the
City-level ZHVI file from Zillow Research and save it as `city_data.csv`
in the project root.

**Cities analyzed** (7 largest per metro by Zillow size rank):
- **PDX:** Portland, Beaverton, Gresham, Hillsboro, Tigard, Oregon City, Milwaukie
- **DFW:** Dallas, Fort Worth, Arlington, Plano, Garland, Frisco, McKinney

## Methodology

1. **Cleaning:** Dropped rows with missing values (21,444 → 7,239 cities)
   and filtered to the two metro areas.
2. **Reshaping:** Melted wide monthly columns into long format and
   aggregated to yearly averages per city.
3. **Visualization:** Per-region line charts, a combined PDX vs. DFW
   trend chart, and a growth-rate box plot.
4. **Growth rates:** Percent change in yearly average value, 2012 to 2025.
5. **Hypothesis testing:** Welch's two-sample t-tests (unequal variance)
   on home values and on growth rates, at α = 0.05.

Project management followed the ADDIE framework (Analysis, Design,
Development, Implementation, Evaluation).

## Tools

Python · pandas · NumPy · SciPy · Matplotlib · Seaborn · Jupyter Notebook

## Repository Structure

    ├── README.md
    ├── requirements.txt
    ├── DFW_PDX_Comp.ipynb        # full analysis notebook
    ├── Capstone_Report.pdf       # written report
    └── images/                   # exported charts

## How to Run

    pip install -r requirements.txt
    jupyter notebook DFW_PDX_Comp.ipynb

## Limitations

- Home value is the only variable considered. Taxes, wages, and local
  policy were out of scope.
- 2025 figures average January–November only.
- The study covers the 7 largest cities per metro, not the full metro area.

## Possible Next Steps

- Compare specific cities or price tiers rather than whole regions.
- Add affordability context such as income, property tax, and rent ratios.
- Forecast future values with time-series models.
