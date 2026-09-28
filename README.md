# 🎸 Ecos Progressivos — End-to-End Marketing Analytics

[🌐 Visit the Ecos Progressivos website](https://ecosprogressivos.carrd.co/)

## Project Overview

**Ecos Progressivos** is an end-to-end Marketing Analytics project built around a real subscriber acquisition campaign for a progressive rock newsletter.

The objective was not only to generate subscribers, but also to build a reliable analytics process capable of measuring the complete acquisition funnel, validating marketing data across different platforms and supporting optimisation decisions.

The project integrates data from **Meta Ads**, **Google Analytics 4** and **Mailchimp** through the following pipeline:

```text
Meta Ads + GA4 + Mailchimp
            ↓
        Python ETL
            ↓
        SQL Server
            ↓
         Power BI
```

The workflow covered data collection, cleaning, transformation, validation, storage, visualisation and interpretation.

A major part of the project also involved auditing tracking quality after a discrepancy was identified between conversions reported by Meta Ads and confirmed subscribers recorded in Mailchimp.

---

## Business Objective

The campaign was designed to test the viability of acquiring subscribers within a highly specific niche: progressive rock vinyl collectors.

The main objectives were to:

- Generate qualified newsletter subscribers
- Measure the true cost of acquisition
- Analyse the complete conversion funnel
- Identify friction points in the user journey
- Compare campaign creatives
- Validate tracking accuracy across platforms
- Use data to support campaign optimisation decisions

---

## Technologies

- Python
- Pandas
- SQLAlchemy
- pyodbc
- SQL Server
- Power BI
- DAX
- Meta Ads
- Google Analytics 4
- Meta Pixel
- Mailchimp

---

## Data Sources

### Meta Ads

Used to analyse paid acquisition performance, including:

- Spend
- Impressions
- Reach
- Campaign results
- Cost efficiency
- Creative performance

### Google Analytics 4

Used to analyse website behaviour and funnel activity, including:

- Sessions
- New users
- Scroll activity
- Form starts

### Mailchimp

Used as the reference source for confirmed newsletter subscriptions.

Confirmed contacts were used to validate the real number of acquired subscribers.

---

## Data Preparation & ETL

Each source required separate treatment before the data could be consolidated.

### Meta Ads

Campaign data was filtered to include only the relevant campaign.

The preparation process included:

- Standardising campaign identifiers
- Removing unnecessary whitespace
- Converting date fields into consistent datetime formats
- Aggregating campaign performance metrics
- Recalculating key efficiency metrics rather than relying exclusively on platform-reported values

### Mailchimp

Subscriber data required additional standardisation before confirmed subscriptions could be counted reliably.

The process included:

- Converting email values to a consistent format
- Removing leading and trailing spaces
- Converting email addresses to lowercase
- Validating confirmation timestamps
- Excluding invalid or missing confirmations
- Counting unique confirmed subscribers to avoid duplicate contacts

### Google Analytics 4

The GA4 export contained multiple sections within the same file, so only the relevant event data was selected.

The preparation process included:

- Selecting the required section of the exported dataset
- Converting event counts into numeric values
- Extracting relevant events such as:
  - `session_start`
  - `first_visit`
  - `scroll`
  - `form_start`
- Validating the semantic meaning of each metric before using it in the analysis

An important correction was distinguishing **sessions** from **new users**:

- `session_start` was used to measure website sessions
- `first_visit` was interpreted as new users rather than total visits

This validation prevented different GA4 metrics from being treated as equivalent.

---

## Data Integration

After processing each source independently, the main metrics were consolidated into a standardised vertical structure.

The final dataset followed a structure similar to:

```text
date | platform | metric | value
```

This made it possible to combine heterogeneous data sources while preserving the meaning and origin of each metric.

The transformed dataset was then loaded into **SQL Server**, creating a structured storage layer between Python and Power BI.

During development, the destination table was replaced during each execution to prevent duplicate records.

In a production environment, this process could be improved through an incremental loading strategy.

---

## Data Quality & Tracking Audit

One of the most important parts of the project was identifying a major discrepancy between platform-reported conversions and actual subscriber records.

During the initial campaign phase, **Meta Ads reported an unrealistically high number of conversions at a very low cost**, while Mailchimp recorded significantly fewer confirmed subscribers.

Instead of assuming that the advertising platform was correct, the tracking setup was audited.

The investigation included:

- Comparing Meta Pixel event timestamps with Mailchimp subscription records
- Reviewing the custom conversion configuration
- Comparing platform-reported conversions against actual CRM records

The analysis identified that the custom conversion event was firing on a **generic Page View** instead of only after a successful subscription.

### Corrective Actions

The tracking setup was revised by:

- Reconfiguring the conversion event
- Restricting the conversion trigger to the **Thank You Page**
- Improving the form integration to reduce possible data leakage
- Revalidating campaign performance against confirmed subscriber records

This reinforced an important principle of the project:

> Marketing KPIs should not be trusted solely because they appear correctly inside an advertising platform. Critical metrics should be validated against the underlying business outcome.

---

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
| Overall cost per confirmed subscription | €4.05 |

---

## Conversion Funnel

```text
532 Website Sessions
        ↓
43 Form Starts
        ↓
16 Confirmed Subscriptions
```

The largest drop-off occurred before the form-start stage.

Only **8.08% of website sessions** progressed to a form start.

The ratio between the **43 form starts** recorded in GA4 and the **16 confirmed subscriptions** recorded in Mailchimp was approximately **37.21%**.

However, this should not be interpreted as a strict user-level conversion rate because the two values originate from different platforms and measurement systems.

Instead, it is treated as an operational approximation for funnel analysis.

---

## Experimentation & Campaign Optimisation

The campaign also included an A/B comparison between two creative approaches.

### Variant A — Classic Progressive Rock

Creative based on **King Crimson — In the Court of the Crimson King**.

### Variant B — Modern Progressive Rock

Creative based on **King Gizzard — Nonagon Infinity**.

The Classic variant generated a **cost per intent approximately 4.5x lower** than the Modern variant.

Based on the observed performance, the budget was reallocated towards the better-performing creative.

This demonstrated how analytics could be used during campaign execution, rather than only for retrospective reporting.

> The result was treated as a campaign-performance signal rather than a formal statistical significance test.

---

## Dashboard

The final Power BI dashboard consolidates the main campaign and funnel metrics.

It allows users to monitor acquisition performance and move between absolute values and funnel percentages.

![Marketing Analytics Dashboard](https://github.com/fmcoelho91-prog/Ecos-Progressivos-Marketing-Analytics/raw/main/Dashboard.png)

---

## Key Insights

### 1. Traffic generation was not the only constraint

The analysis showed that increasing traffic alone would not necessarily solve the conversion problem.

A significant proportion of website sessions did not progress to the form-start stage.

This suggested that areas such as:

- Value proposition
- Landing-page clarity
- Form visibility
- Mobile experience
- Message consistency

could influence conversion performance.

### 2. Platform attribution should be validated

Meta Ads attributed **7 results**, while Mailchimp recorded **16 confirmed subscribers**.

Because both platforms use different attribution and measurement methods, these values should not be considered directly equivalent.

### 3. Tracking quality directly affects business decisions

The initial tracking problem demonstrated that an incorrect event configuration could lead to misleading acquisition metrics and incorrect optimisation decisions.

### 4. Creative performance differed substantially

The Classic creative produced a considerably lower cost per intent than the Modern creative, providing a clear signal for budget reallocation.

---

## Business Decision

The campaign was voluntarily paused before the **Black Week / Black Friday** period.

The reasoning was based on the expected increase in advertising competition and CPMs during this period.

Given the limited campaign budget, continuing acquisition during a more expensive advertising period could have reduced efficiency and increased the cost per lead.

The decision was therefore made to:

- Protect acquisition efficiency
- Pause paid acquisition temporarily
- Focus on nurturing the existing subscriber base through email marketing

---

## Key Recommendations

Based on the analysis, the following improvements were identified:

- Implement consistent UTM parameters across all campaign links
- Validate events such as `form_start`, `form_submit` and `sign_up`
- Improve the visibility and simplicity of the subscription form
- Optimise the mobile user experience
- Strengthen message alignment between advertisements and the landing page
- Run controlled A/B tests on landing-page elements
- Continue validating advertising-platform conversions against CRM records
- Introduce stronger monitoring of tracking quality
- Test Google Search as a higher-intent acquisition channel

---

## Future Development

The next planned acquisition phase would include testing **Google Ads Search**.

The objective would be to compare a higher-intent search channel against paid social acquisition.

Relevant comparison metrics could include:

- Cost per Lead
- Conversion Rate
- Lead quality
- Acquisition volume
- Funnel progression

This would provide a stronger basis for deciding how acquisition budget should be distributed across channels.

---

## Limitations

The project combines data from platforms with different attribution and measurement methodologies.

For this reason:

- The **7 results attributed by Meta Ads** are not directly equivalent to the **16 confirmed subscriptions recorded in Mailchimp**
- GA4 `form_start` events do not necessarily represent unique users
- Cross-platform funnel ratios should therefore be interpreted as operational approximations
- The campaign sample size was relatively small
- The creative comparison should not be interpreted as a formal statistically validated A/B experiment
- Campaign performance over a short period may not generalise to different seasons or larger budgets

These limitations were considered when interpreting the results and developing recommendations.

---

## Conclusion

Ecos Progressivos demonstrates an end-to-end Marketing Analytics workflow that extends beyond dashboard creation.

The project covered:

**Campaign → Tracking → Data Collection → Validation → ETL → SQL Storage → BI → Analysis → Optimisation**

A key lesson from the project was that reliable analysis depends on reliable measurement.

The tracking discrepancy between Meta Ads and Mailchimp demonstrated why data validation and reconciliation should take place before business decisions are made.

The project also showed how campaign, behavioural and CRM data can be combined to identify funnel friction, evaluate acquisition efficiency and support evidence-based marketing decisions.
