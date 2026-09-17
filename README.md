# Induction_Therapy_Breakthrough_Activity
Code underlying the descriptive analysis for treatments strategy after breakthrough disease on induction therapies in MS. 

# Research Question: What is the optimal treatment following treatment failure on induction therapies alemtuzumab and cladribine? 

# Descriptive Statistics 
Primary and secondary outcome analyses, as well as data on subsequent treatment use following breakthrough relapse were described. Analyses were conducted using the MSOutcomes package (v0.2.1) in R (v4.2.2). 

# Propensity-Score Matching
From patients who relapsed after their second cycle of alemtuzumab/cladribine, (“index” relapse) those that subsequently received a third cycle of alemtuzumab/cladribine were matched to those subsequently receiving another high-efficacy DMT, based on their propensity of receiving further DMT. Baseline was defined as the day of starting a new DMT (or third cycle).

A multivariate logistic regression model using baseline age, sex, disease duration, EDSS score, number of relapses in the two years before baseline, highest efficacy DMT prior to alemtuzumab/cladribine (if prior DMT was given), and whether alemtuzumab/cladribine was first line or escalation was used to estimate the propensity of treatment at baseline for relapse outcomes. To mitigate the impact of time taken to start new treatment after the index relapse, patients were also matched on the time from index relapse to treatment commencement.

Patients were matched in a variable matching ratio (10:1 to 1:1) by nearest neighbour matching using a narrow caliper of 0.1 standard deviations of propensity score (Austin, 2011; Austin & Stuart, 2015) to increase matching precision. Therefore, an individual patient could be used multiple times in one analysis. Replacement was permitted in these matching models to account for this. All subsequent analyses were paired with weighted outcomes to account for individual patients used multiple times (overall maximum individual patient cumulative weight of 1). We determined the common follow-up period in each matched pair as the shorter of the two patient follow-up periods (pairwise censoring). This mitigates informative censoring, attrition bias, and the effect of differential treatment persistence (Deltuvaite‐Thomas et al., 2022).

We compared proportion free from relapse with weighted conditional proportional hazards models (Cox). All models were adjusted for any variable with a Cohen d value ≥0.2 (Cohen, 1988), indicating residual imbalance following matching with a <92% overlap between groups. To account for the variable matching ratio, weights were calculated as the inverse of the number of times a patient was included in an analysis. The Schoenfeld global test was utilised to detect violation of the proportional hazard’s assumption (Schoenfeld, 1982). Weibull accelerated failure-time regression models were used when the proportional hazards assumption was violated. Graphs were censored at the latest point that each group contained at least 10 patients or less than 10% of the original group, whichever came first. 

# Code
All analyses were performed in R (Survival package v3.4-0) and results were considered significant at the p < .05 level.

