P8105: Final Project Proposal
================
2025-11-05

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

Nelson Gaillard (ng3005), Matariya Rattanapan (mkr2158), Mahitha Jangeti
(mj3229), Jefferson Remo (jr4550), Jonathan Huynh (jkh2157)

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

MTA Ridership Data from

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

- Covid vs. Subway ridership
  - Visualize how different MTA systems recovered post-covid. Which ones
    were in usage first (i.e. bus vs. subway)
  - Pre/post covid trends
- Weather vs. Subway ridership
  - How usage differs across different weather; how it impacts which
    type of transport is used more often
- MTA data
  - Which station never sleeps: hourly activity analysis
  - Borough division
  - Weekday vs. weekend ridership
  - Rats in each stop

#### Visualizations

- Plots and Plotly
- Dashboard
- Subway map

#### Coding challenges

- There may be presence of missing data between datasets when merging.
- Temporality may also presnt a challenge if metrics of time are
  inconsistent.
- Data availability between boroughs may differ in frequency and weight;
  we can remedy this with data imputation
- Geospatial mismath between MTA stations, boroughs, and zip codes may
  present issues when making relationship analyses
- May need to consider whether to model certain variables as numerical
  or categorical.
- Aggregating variables relevant to answering our research question.

#### Planned timeline

- Project Review Meeting: November 10-14
- Finish Coding: November 22nd
- Begin Report: November 23rd
- Finish Website/Screencast by December 1 (5 days for revisions)
- Submit Report: December 6, 11:59pm
- Submit Webpage and Screencast: by December 6, 11:59pm
