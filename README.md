# Are Movie Sequels Actually More Profitable?

An analysis of financial and audience-rating performance across 272 films
in movie franchises — comparing originals to sequels, each installment to
the last, and modeling what predicts a sequel's returns.

## Key Findings

Within franchises, originals outperform sequels overall (median
income-to-budget ratio 4.0 vs 3.7; median IMDb rating 6.9 vs 6.2).

The installment-level breakdown reveals the sharper pattern:

| Installment | Median income/budget | Median IMDb rating | n |
|---|---|---|---|
| 1st (Original) | 4.01 | 6.9 | 128 |
| 2nd | 3.30 | 6.4 | 76 |
| 3rd+ | 3.96 | 6.1 | 68 |

Audience ratings decline monotonically with each installment, but
financial returns recover by the third film. **Franchise earning power
decouples from audience reception over time** — audiences keep paying
for films they rate progressively lower. (Note: the 3rd+ group carries
survivorship bias, since only successful franchises reach a third film.)

An exploratory regression on 44 franchise pairs confirms the decoupling
in predictive form: **the original film's profitability strongly predicts
its sequel's returns (elasticity ≈ 0.53), while the original's audience
rating predicts nothing** once profitability is known. Both results are
robust to excluding outliers. The original's budget also positively
predicts sequel returns, consistent with budget proxying for studio
commitment to franchise-building.

The outliers put faces on the pattern: *Paranormal Activity 2* returned
59x its budget with a 5.6 rating, while *Basic Instinct 2* — arriving
fourteen years after a hit original — lost nearly half its \$70M budget.
Sequels survive declining quality; they don't survive broken momentum.

## Data

- [IMDb movies & ratings, 1893–2020](https://www.kaggle.com/datasets/sharathmudigoudr/imdb-movie-dataset-from-year-1893-to-2020/data)
- [Sequels dataset](https://www.kaggle.com/code/cpbdev/sequels-dataset/input)

Datasets were joined on title with a ±2-year tolerance window to handle
release-year discrepancies; all 272 franchise films matched successfully.

## Methods

Financial success is measured as worldwide gross / production budget,
normalizing for the larger budgets sequels typically receive. Films are
classified by franchise installment order. Sequel returns are modeled via
linear regression on the original film's characteristics (log-log
specification, with outlier robustness checks). Analysis in R (dplyr,
ggplot2, broom, and friends), rendered with Quarto — full report in
`index.qmd`.

## Reproducing

Open `project.Rproj` in RStudio and render `index.qmd`, or run
`quarto render` from the project root. Requires: dplyr, readr, tidyr,
ggplot2, stringr, janitor, lubridate, knitr, broom.

## Credits

Originally developed as a team project for STA 199 at Duke University
with Isha Omer, Lexi Payne, and David Boham. Installment-level analysis,
outlier analysis, and regression modeling added subsequently by
Camden Chin.