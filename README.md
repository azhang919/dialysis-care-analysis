# Difference in Dialysis Patient Care Between Large Chain Clinics and Independent Firms

Last Update: Jan 20, 2022\
Owners: Alison Zhang, Rahul Narvekar, Alex Ozhakanat, Shivangi Shah, Justin Geletko

## References
Inspired by previous research, specifically, “How Acquisitions Affect Firm Behavior and Performance: Evidence from the Dialysis Industry” by Eliason, Heebsh, McDevitt, and Roberts.
Data downloaded from the National Bureau of Economic Research, Health Cost Report Information System (HCRIS), from 1998 to 2010.

## Background


## Analysis
The goal of our analyses was to compare clinics operated by chains with independent clinics to find any discrepancies in costs and behaviors. To accomplish this, we investigated potential differences in three areas: EPO costs and rebates, clinic employee salaries, and non-Medicare sessions.

### EPO Costs, Net Costs, and Rebates
We first set out to run separate linear regressions based on chain and independent firms and regress them for epo_net_cost against all numeric features. We found that EPO cost and EPO rebates are strong significant predictors of EPO net cost based on our regression. This should come as no surprise, as _EPO total cost - rebate_ should give us net cost. From this, we created box plots that visualized the EPO rebates and EPO costs for the different chain categories and the independent clinics. This showed that, on average, EPO rebates and costs were higher for chain clinics than independent ones. However, we also found that, on average, the net costs for chains were lower than independent counterparts by about $34,000. This aligns with previous studies on EPO, which found that dosage more than doubled post-acquisition.

Since Medicare reimbursement for drugs like EPO are determined by quantity administered, firms would be incentivized to increase dosage in their patients, despite medical evidence that excessive EPO increases risk for cardiovascular events. Although we cannot conclusively attribute a causal effect to our findings, our regression does match the research paper's study. Given more granular patient and treatment data, we could better analyze this relationship.

### Employee Salaries
We found that there was a consistent difference between the average salaries of independent clinics compared to chain clinics from 1998 to 2010. Our first graph illustrates this difference, with independent clinics paying higher salaries on average than chain clinics on average each year, even with increases in salaries
across the board.

Our second graph shows how the chain clinics differ in their average salaries. The gap is further emphasized, with Davita and Fresenius consistently paying at or below the average calculated salary compared to other chains. Overall, this aligns with the findings reported in the research paper and podcast, as researchers concluded that chain clinics were cutting costs by moving towards more low-skill technicians and less highly-trained nurses. Typically, nurses are more qualified and provide better care for patients than technicians, which translates into higher salaries. From aggregate salary-collecting websites like Glassdoor (founded 2007) and Ziprecruiter (founded 2010), dialysis nurse salaries in the US have been around \$60-75k over the past decade, while dialysis technician salaries have ranged from \$40-50k. These external statistics, in tandem with our findings, corroborate with previous research.

### Non-Medicare Sessions
#### Linear Regression on Non Medicare Sessions for Chains
```
##
## Call:
## glm(formula = non_medicare_sessions ~ total_costs_hd_drugs +
## total_treatments_hd + total_costs_hd_labs + dialyser_reuse_times +
## total_costs_hd_benefits + total_costs_hd_housekeeping + total_costs_hd_machines +
## total_costs_hd_other + total_costs_hd_salaries + total_costs_hd_supplies,
## data = chains)
##
## Deviance Residuals:
## Min 1Q Median 3Q Max
## -13157 -819 -196 458 88079
##
## Coefficients:
## Estimate Std. Error t value Pr(>|t|)
## (Intercept) -2.270e+02 3.658e+01 -6.207 5.56e-10 ***
## total_costs_hd_drugs 2.106e-03 7.482e-04 2.815 0.00489 **
## total_treatments_hd 1.103e-02 1.868e-03 5.904 3.62e-09 ***
## total_costs_hd_labs 1.694e-02 2.284e-03 7.420 1.24e-13 ***
## dialyser_reuse_times -4.199e-06 2.209e-06 -1.901 0.05734 .
## total_costs_hd_benefits 1.863e-04 4.096e-04 0.455 0.64921
## total_costs_hd_housekeeping 1.953e-04 1.751e-04 1.116 0.26462
## total_costs_hd_machines -4.462e-03 4.218e-04 -10.579 < 2e-16 ***
## total_costs_hd_other 1.235e-03 1.102e-04 11.210 < 2e-16 ***
## total_costs_hd_salaries 5.265e-03 1.421e-04 37.046 < 2e-16 ***
## total_costs_hd_supplies -2.549e-04 3.047e-04 -0.836 0.40292
## ---
## Signif. codes: 0 ’***’ 0.001 ’**’ 0.01 ’*’ 0.05 ’.’ 0.1 ’ ’ 1
##
## (Dispersion parameter for gaussian family taken to be 4246822)
##
## Null deviance: 1.3680e+11 on 15029 degrees of freedom
## Residual deviance: 6.3783e+10 on 15019 degrees of freedom
## (25828 observations deleted due to missingness)
## AIC: 272049
##
## Number of Fisher Scoring iterations: 2
```

#### Linear Regression on Non Medicare Sessions for Independents
```
##
## Call:
## glm(formula = non_medicare_sessions ~ total_costs_hd_drugs +
## total_treatments_hd + total_costs_hd_labs + dialyser_reuse_times +
## total_costs_hd_benefits + total_costs_hd_housekeeping + total_costs_hd_machines +
## total_costs_hd_other + total_costs_hd_salaries + total_costs_hd_supplies,
## data = independent)
##
## Deviance Residuals:
## Min 1Q Median 3Q Max
## -10545.9 -760.5 -111.7 551.9 21055.7
##
## Coefficients:
## Estimate Std. Error t value Pr(>|t|)
## (Intercept) -3.922e+02 8.788e+01 -4.463 8.59e-06 ***
## total_costs_hd_drugs -1.871e-03 5.519e-04 -3.391 0.000712 ***
## total_treatments_hd 3.839e-01 1.871e-02 20.518 < 2e-16 ***
## total_costs_hd_labs 4.053e-02 5.202e-03 7.792 1.12e-14 ***
## dialyser_reuse_times 6.125e-06 2.950e-06 2.076 0.038043 *
## total_costs_hd_benefits 3.895e-03 6.319e-04 6.164 8.76e-10 ***
## total_costs_hd_housekeeping 1.067e-03 3.636e-04 2.933 0.003396 **
## total_costs_hd_machines -1.314e-03 7.586e-04 -1.733 0.083311 .
## total_costs_hd_other -5.327e-04 2.516e-04 -2.117 0.034361 *
## total_costs_hd_salaries -1.112e-03 2.416e-04 -4.604 4.44e-06 ***
## total_costs_hd_supplies -3.060e-03 5.535e-04 -5.527 3.74e-08 ***
## ---
## Signif. codes: 0 ’***’ 0.001 ’**’ 0.01 ’*’ 0.05 ’.’ 0.1 ’ ’ 1
##
## (Dispersion parameter for gaussian family taken to be 3279694)
##
## Null deviance: 1.5775e+10 on 1766 degrees of freedom
## Residual deviance: 5.7591e+09 on 1756 degrees of freedom
## (4163 observations deleted due to missingness)
## AIC: 31538
##
## Number of Fisher Scoring iterations: 2
```

We used multiple costs variables to look at changes in the number of sessions done through private (non-Medicare) insurance. From our regressions, we can see that the total cost for hemodialysis drugs has a positive relationship with nonmedicare session for chain clinics (coefficient = 2.106e-03), while this relationship became negative for independent clinics (coefficient = -1.871e-03). The same trend can be found for the total 'other' and salary costs for hemodialysis, changing from 1.235e-03 to -5.327e-04 and 5.265e-03 to -1.112e-03, respectively between chain and independent clinics.

In general, large dialysis chains have more market and bargaining power, and are thus able to negotiate higher reimbursement rates from private insurers. Chain firms would then be incentivized move towards non-medicare sessions as their costs increase, in order to receive more reimbursements. In contrast, independent chains are forced to revert to Medicare's flat rates, having less bargaining power. Prior studies and articles touch on the role that Medicare plays in the dialysis industry, and our findings seem to align with these general economic trends.
