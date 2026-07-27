# 🎸 Ecos Progressivos — Marketing Performance Analytics

[🌐 Visit the Ecos Progressivos website](https://ecosprogressivos.carrd.co/)

## Project Overview

This end-to-end **Marketing Analytics** project was developed to analyse a real subscriber acquisition campaign for a progressive rock newsletter.

The project integrates data from **Meta Ads**, **Google Analytics 4** and **Mailchimp** through a complete analytics pipeline:

```text
Meta Ads + GA4 + Mailchimp → Python ETL → SQL Server → Power BI
```

The data was imported and transformed in Python, consolidated into a standardised structure, loaded into SQL Server and used to build an interactive Power BI dashboard.

## Technologies

- Python and Pandas
- SQLAlchemy and pyodbc
- SQL Server
- Power BI and DAX
- Meta Ads
- Google Analytics 4
- Mailchimp

## What Was Developed

- Created the landing page and Meta Ads campaign
- Collected website and subscriber data through GA4 and Mailchimp
- Built an ETL process in Python
- Integrated multiple data sources into a standardised vertical model
- Loaded the transformed data into SQL Server
- Created DAX measures
- Built an interactive dashboard in Power BI
- Analysed the conversion funnel and developed strategic recommendations

## Key Results

| Metric | Result |
|---|---:|
| Meta Ads investment | €64.79 |
| Impressions | 25,386 |
| Reach | 16,338 |
| Website sessions | 532 |
| New users | 481 |
| Form starts | 43 |
| Confirmed subscriptions | 16 |
| Session conversion rate | 3.01% |
| Cost per result attributed by Meta | €9.26 |
| Overall cost per subscription | €4.05 |

## Conversion Funnel

```text
532 Website Sessions
        ↓
43 Form Starts
        ↓
16 Confirmed Subscriptions
```

The largest drop-off occurred before the form-start stage: only **8.08% of website sessions** progressed to this point.

The ratio between the **43 form starts** and the **16 confirmed subscriptions** was **37.21%**.

This value should be interpreted as an operational approximation because it compares GA4 events with unique confirmed contacts recorded in Mailchimp.

## Dashboard

The dashboard presents the main campaign KPIs and allows users to switch between absolute values and funnel percentages.

![Marketing Analytics Dashboard](https://github.com/fmcoelho91-prog/Ecos-Progressivos-Marketing-Analytics/blob/main/Dashboard.png)

## Key Recommendations

- Implement consistent UTM parameters across all campaign links
- Validate events such as `form_start`, `form_submit` and `sign_up`
- Improve the visibility and simplicity of the subscription form
- Optimise the mobile user experience
- Run A/B tests on the landing page
- Strengthen alignment between the advertisements and the landing page
- Test Google Search as an intent-based acquisition channel

## Limitations

The platforms use different measurement and attribution methods. For this reason, the **7 results attributed by Meta** are not directly equivalent to the **16 confirmed subscriptions recorded in Mailchimp**.

Form starts represent GA4 events and do not necessarily correspond to unique users.

The ratio between form starts and confirmed subscriptions should therefore be interpreted as a cross-platform operational approximation rather than a strict user-level conversion rate.

## Conclusion

This project demonstrates the integration of marketing data through a complete analytics pipeline, covering data collection, transformation, storage, visualisation and interpretation.

The analysis showed that campaign improvement does not depend exclusively on generating more traffic. The clarity of the value proposition, landing-page experience, form visibility, mobile usability and measurement quality also have a direct impact on conversion performance.
