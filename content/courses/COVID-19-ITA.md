---
title: COVID-19 ITA
linktitle: COVID-19 ITA
toc: true
type: docs
date: "2020-12-02T00:00:00+01:00"
draft: false
menu:
  example:
    parent: Data analysis with R
    weight: 1

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 
---

The **AIM** of this project is to model the incidence and calculate the [basic reproduction number (R0)](https://en.wikipedia.org/wiki/Basic_reproduction_number) for [COVID-19](https://www.thelancet.com/journals/lancet/article/PIIS0140-6736(20)30183-5/fulltext) in Italy. 

You can navigate through the different steps which brought me to generate the figures below in [this HTML report](/courses/COVID-19-ITA/2019-nCoV.html). The Rmd source is available [here](https://github.com/eugeniozoni/COVID-19_ITA/blob/master/2019-nCoV.Rmd).

## **Total incidence divided by groups**

<img src="/courses/COVID-19-ITA/total_incidence_ITA.png" alt="COVID-19-ITA" width="600"/>

In this plot I represented the daily incidence for three groups of patients:

* **home**: these are patients who tested positive for COVID-19 and that are followed at home
* **hospital**: these are patients who required hospitalization
* **icu**:  these are patient who required intensive care treatment

## **Model of daily incidence**

<img src="/courses/COVID-19-ITA/new_incidence_model.png" alt="COVID-19-ITA" width="600"/>

In this plot I modelled the incidence based on the new daily cases. I used a log-linear regression in the form: log(y) = r x t + b where y is the incidence, r is the growth rate, t is the number of days since the start of the outbreak and b is the intercept. I have splitted the interval at 2020-04-21 which is the highest peak in the curve up to this moment.

## **Effective reproduction number**

<img src="/courses/COVID-19-ITA/estimated_R.png" alt="COVID-19-ITA" width="600"/>

In this plot you can visualize the epidemic curve (top panel), the serial interval distribution used to model the incidence (middle panel) and the estimated R0 (lower panel).

The conclusion of this calculation is that the R number decreased during lockdown, however, upon re-opening, the R number started to grow again in the first half of June 2020 and after summertime the cases are rising again.

## **Credits**

Credit for the feasibility of this project should be given to the authors of the [**projection**](https://www.repidemicsconsortium.org/projections/) and [**incidence**](https://www.repidemicsconsortium.org/incidence/) R packages and to [**Tim Churches**](https://timchurches.github.io/blog/posts/2020-02-18-analysing-covid-19-2019-ncov-outbreak-data-with-r-part-1/) who generated a complete tutorial for the analysis of COVID-19 early in Febraury 2020.


