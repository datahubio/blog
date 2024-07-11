---
title: Systems Change Lab data
image: https://github.com/datasets/awesome-data/assets/180658/c4e7b317-292f-40b5-8503-4ba1d62c2d85
created: 2023-10-29
tags:
  - is-it-opendata
---

There's a great new (?) project called Systems Change Lab https://systemschangelab.org that seem to be doing a lot of data-driven work looking at climate crisis. Tagline: "Protecting People and Planet".

My interest here is a) what data they have and b) whether it's open. **Spoiler: a) answer not that much b) kind-of (most of the data comes from third parties and they ask you to find out from them 😬)**

![image](https://github.com/datasets/awesome-data/assets/180658/c4e7b317-292f-40b5-8503-4ba1d62c2d85)

## Data Access

### You can download the data 👍

Nice big "Download Data" button which is great: https://systemschangelab.org/download

> Here you can download and explore data from Systems Change Lab. Not all data shown across the platform is available for download. Visit the [permissions and licensing](https://systemschangelab.org/licensing) page for more information and refer to the original data source to determine licensing for each dataset. Please contact our team at [data@systemschangelab.org](mailto:data@systemschangelab.org) for assistance with dataset availability, bulk downloads and other data needs.

![image](https://github.com/datasets/awesome-data/assets/180658/2fa3341b-7ea5-4ea9-a6ef-809006e9edcf)

### Let's click that nice big download button

So if you click that nice big "download all the data button" you get a nice zip with lots of tasty csvs.

Here's a capture of their data as of 2023-10-29 [scl_data_all.zip](https://github.com/datasets/awesome-data/files/13197730/scl_data_all.zip)

- Consists of approx 30 folders each being one dataset.
- CSV file of data
- CSV file of metadata

### However most of the data is from 3rd parties and you need to work out licensing on per dataset basis

> .... refer to the original data source to determine licensing for each dataset

That means reading the license info or source info on each dataset. The datasets metadata (in a CSV!) often just tells you source not license status e.g.

> Access to clean cooking in urban area
>
> "Goal 7 | Indicator 7.1.2 Proportion of population with primary reliance on clean fuels and technologies","World Health Organization"

So you'd need to go there and look at the WHO licensing ...


### One example data file

Explored using [xsv](https://github.com/BurntSushi/xsv)

```
scl_data_all/acss_cln_cook
```

`xsv headers`

```
1   year
2   geo
3   value
4   projections
5   benchmark_low
6   benchmark_mid
```

## Permissions and Licensing

![image](https://github.com/datasets/awesome-data/assets/180658/85590401-b09d-4adb-823a-a2e204e1458e)

### They license their own stuff under CC-By

> Data, maps and visualizations on the Systems Change Lab website are under a [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/) license, which allows for any commercial or non-commercial use as long as you cite Systems Change Lab.

NB: I don't think they actually produce much data so for the data not sure how much this means.

### International Energy Agency data

> Data by the International Energy Agency (IEA) is not available for download on the Systems Change Lab website and falls under the IEA Terms and Conditions, which limits reuse. To access IEA data, please visit the [IEA website](https://www.iea.org/data-and-statistics).

For IEA see existing discussion https://github.com/orgs/datasets/discussions/372 - current sense is not open, though may be changing.
