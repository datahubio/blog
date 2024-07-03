---
title: "Data Literate Documents: an initial outline" 
description: "This 
date: 2021-05-17
authors: ['Rufus Pollock']
filetype: blog
---

This is a "braindump" of a vision for "data literate documents" derived from the experience i would like to have publishing and sharing data and data driven documents.

## What I want ...

The basic need I have is:

> I want to write something like a README (in markdown)  with data and vis in it, preview it and publish it ...

I want to do this in a way that is simple and sustainable - I want to know this material will still be around and accessible in 5 or 10y (at the least). This likely means not doing this in a proprietary format or in a proprietary platform.

## Observations

* Markdown is becoming a lingua franca for writing developer and even research docs
  * It's quick and ascii-like
  * It's widely supported
  * It's extensible ...
* Frontend tooling is rapidly evolving ...
  * The distant between code and a tool is declining => I might as well write code ... (rather than using a specific tool to analysis and visualize data)
* MDX = Markdown + react
* RStudio did this a while ago ...
* Missing part is data ...
  * You have juputer notebooks etc ... => they are quite high end / geeky ...

Notebooks (jupyter, literate programming) ⟹

- Write text and code together
- Write code like in a terminal
- Data oriented

## Here the kinds of doc i want to write

### A Dataset Example


```md
# Global Solar Supply (Annual)

Solar energy supply globally.

Source: International Energy Association https://www.iea.org/reports/solar-pv.

| Year | Generation (TWh) | % of total energy |
|--|--|
|2008|12|
|2009|20|
|2010|32|
|2011|63|
|2012|99|
|2013|139|
|2014|190|
|2015|251|
|2016|329|
|2017|444|
|2018|585|
|2019|720| 2.7 |
```

Europe Brent Spot Prices (Annual/ Monthly/ Weekly/ Daily) from U.S. Energy Information Administration (EIA).

Source: https://www.eia.gov/dnav/pet/hist/RBRTEd.htm


## Notes

R Markdown - https://rmarkdown.rstudio.com

> Use a productive notebook interface to weave together narrative text and code to produce elegantly formatted output. 

