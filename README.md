# 780-project
State-level analysis of U.S. adult obesity using CDC BRFSS (2011–2024) and the USDA Food Environment Atlas. Shows that obesity depends on where you live, not just what you earn — and what a public-health department should do about it. BA780 team project (Python/pandas, Colab).


# U.S. Obesity and the Food Environment

**Team B09 · BA780 Intro to Data Analytics** — Bhavya Kandhari, Zoya Salman, Danyang Qin (Lucy), Sanjay Kumar, Dylan Rubinstein

One in three U.S. adults has obesity, but in West Virginia it's 41% and in Colorado it's 25%.
This project asks why obesity depends so much on where Americans live, and where a public-health
department with a limited budget should place food-access programs.

## Guiding question

How are food environment, socioeconomic status, demographic characteristics and geographic
location associated with adult obesity rates across the United States, and where should a
public health department place food access programs?

## Data

| Dataset | Source | Size | What it gives us |
|---|---|---|---|
| CDC BRFSS Obesity Data (2011–2024) | [data.gov](https://catalog.data.gov/dataset/nutrition-physical-activity-and-obesity-behavioral-risk-factor-surveillance-system) | 110,880 rows | Adult obesity, overweight, inactivity and diet by state and by income, education, age, sex and race |
| USDA Food Environment Atlas (2025) | [USDA ERS](https://ers.usda.gov/data-products/food-environment-atlas/data-access-and-documentation-downloads) | 957,753 rows, 304 variables, 3,156 counties | Stores and restaurants per 1,000 people, food access, income, poverty |

The two datasets are cleaned separately (Parts A and B of the notebook), the Atlas is rolled up
from counties to states, and the two are merged on state abbreviation into a table of
51 states × 136 variables.

## Key findings

- **Obesity is concentrated by place.** In 2022, rates ranged from 24.3% (DC) to 41.0% (West Virginia); 22 states are at 35% or higher, clustered in the South and Appalachia.
- **It isn't population makeup.** Comparing the same age group across states, the highest-obesity states are already ~9 points above the lowest at ages 18–24, widening to ~14 points by middle age.
- **It isn't personal income either.** Wealthier states are leaner (r = −0.71), yet adults in the same income bracket differ by up to 17 points depending on their state. In West Virginia, Louisiana and Oklahoma even college graduates, young adults and high earners sit above the national average.
- **What people in a state share is their food and activity environment.** Dollar stores per 1,000 residents go with higher obesity (r = +0.62); full-service restaurants (−0.69) and recreation facilities (−0.49) go with lower obesity. Distance to a supermarket shows no relationship (r ≈ 0).
- **Nine food-environment factors explain about two-thirds of the variation between states** (R² = 0.69). West Virginia and Louisiana are higher than their food environment predicts, so other factors are also at play.

## Recommendations

1. Start with West Virginia, Louisiana and Oklahoma, and reach whole communities, not only low-income residents.
2. Put healthy food in the stores people already use (dollar stores, SNAP incentives) rather than building new supermarkets.
3. Invest in recreation facilities and walkable spaces.
4. Tailor programs to high-risk groups and start young — the state gap is already visible at 18–24.

Pilot first in one state, measure, then scale.

## Repository contents

- `B09_Obesity_and_Food_Environment_Analysis.ipynb` — full notebook: data cleaning (Parts A & B), merge, 15 charts, conclusion, limits and next steps
- `B09_Obesity_Presentation.pptx` — 10-minute class presentation
- `data/` — raw CSV files (`BRFSS_Obesity.csv`, `StateAndCountyData.csv`, `VariableList.csv`)

## How to run

Open the notebook in Google Colab, set `DATA_DIR` in the setup cell to the folder containing
the three CSV files, and run all cells. Requires pandas, numpy, matplotlib, seaborn and scikit-learn.

## Limits

All relationships are correlations across states, not causal effects. County values were averaged
to states without population weights, the two datasets cover different years (2020–2024), and
BRFSS height and weight are self-reported. Next step: add county-level obesity data (CDC PLACES)
to ask the same questions within states.
