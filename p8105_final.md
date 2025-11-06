P8105: Final Project Proposal
================
November 7, 2026

Nelson Gaillard (ng3005), Matariya Rattanapan (mkr2158), Mahitha Jangeti
(mj3229), Jefferson Remo (jr4550), Jonathan Huynh (jkh2157)

``` r
library(tidyverse)
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.4     ✔ readr     2.1.5
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.1
    ## ✔ ggplot2   3.5.2     ✔ tibble    3.3.0
    ## ✔ lubridate 1.9.4     ✔ tidyr     1.3.1
    ## ✔ purrr     1.1.0     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
library(p8105.datasets)
```

## Riding Out the Storm: MTA Ridership Through the COVID and Weather

#### Motivation for this project

The COVID-19 pandemic altered patterns of public transit use, exposing
the sensitivity of urban mobility to both public-health and
environmental conditions. Examining how MTA ridership fluctuated with
changing case counts and weather conditions can help identify which
factors most strongly affected transit demand, and how long recovery
took across time and boroughs. These nsights can guide policy around
public health preparedness, transit safety, and infrastructure planning
under climate variability.

#### Intended final products

- Website
- Report
- Screecast Video

#### Anticipated data sources

MTA Ridership Data

``` r
MTA_df =
  read_csv("data/MTA.csv", na = c("NA", ".", "")) |> 
  janitor::clean_names()
```

    ## Rows: 14791 Columns: 3
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (2): Date, Mode
    ## num (1): Count
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

Pre-Covid MTA Ridership Data

``` r
pre_COVID_MTA_df = 
  read_csv("data/Monthly(from 2008).csv", na = c("NA", ".", "")) |>
  janitor::clean_names()
```

    ## Rows: 933 Columns: 3
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr  (1): Agency
    ## num  (1): Ridership
    ## date (1): Month
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

COVID-19

``` r
COVID_df =
  read_csv("data/COVID19.csv", na = c("NA", ".", "")) |> 
  janitor::clean_names()
```

    ## Rows: 2054 Columns: 55
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr  (1): date_of_interest
    ## dbl (26): DEATH_COUNT, DEATH_COUNT_7DAY_AVG, BX_HOSPITALIZED_COUNT, BX_DEATH...
    ## num (28): CASE_COUNT, PROBABLE_CASE_COUNT, HOSPITALIZED_COUNT, CASE_COUNT_7D...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

Weather

``` r
weather_df = 
  data("weather_df")
```

#### Planned analyses

##### Individual descriptive analyses of our datasets

- MTA Ridership Overview
  - Aggregate daily ridership in monthly averages (2018-2025) and look
    at trends overall across all different types of transportation (AAR,
    SIR, MNR, Subway, LIRR, Bus)
    - Line graph
  - Visualize pre-pandemic baseline, pandemic, post-pandemic, ‘pandemic
    recovery’
    - Cam make these each into separate graphs
  - Weekday vs weekend ridership volume
    - Boxplot or violin graph
- COVID-19 Overview
  - Plot daily and weekly average
    - Line graph
    - Highlight specific areas of the graph that align with locdown
      start, vaccine rollout, omicron surge, etc.
  - Identify major NYC waves and define peaks by calculating maximums
  - Correlation analysis between cases, hospitalizations, and death
    - Heat map
- Weather Overview
  - Can compute average_temp, rain, snow
  - Plot of temperature, vs. time, histogram for rainy and snowy days

##### Comparative / Paired Analyses

- Bus vs Subway vs others recovery post pandemic
  - Stacked area chart
- COVID-19 vs Ridership
  - Merge data by date
- Lag analysis: to see the time between when COVID risk increases (by
  case numbers) and when people change ridership behaviors
- Weather vs MTA usage
  - Look at which temps = decrease or increase in ridership
  - Which mode of transportation was used most as weather changed
- Regression analysis: MTA ridership vs. COVID-19 vs. Weather

#### Visualizations

- Plots and Plotly
  - Line plots: daily/monthly ridership trends 2008 - 2025
  - Density plot: pre vs. post covid distributions 2021 - 2025
  - Scatterplot: temperature vs. monthly ridership
  - Boxplots comparing weekday vs weekend ridership distributions
  - Stacked area charts
  - Heat map
- Dashboard
- Subway map

#### Coding challenges

- There may be presence of missing data between datasets when merging.
- Temporality may also present a challenge if metrics of time are
  inconsistent.
- Data availability between boroughs may differ in frequency and weight;
  we can remedy this with data imputation
- Geospatial mismatch between MTA stations, boroughs, and zip codes may
  present issues when making relationship analyses
- May need to consider whether to model certain variables as numerical
  or categorical.
- Aggregating variables relevant to answering our research question.
- Need to know how to handle extreme values of variable(s) in question

#### Planned timeline

- November 10-14: Project Review Meeting
- November 22: Finish Coding
- November 23: Begin Report
  - November 23: Group meeting
- December 1: Finish Website / Screencast
- December 6: Submit Report, Webpage, and Screencast
