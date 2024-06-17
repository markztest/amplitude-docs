---
id: 93038e5f-a8ed-4401-8da3-308d21ed17ad
blueprint: experiment
title: 'Key Terms'
source: 'https://help.amplitude.com/hc/en-us/articles/360061651452-Amplitude-Experiment-key-terms'
this_article_will_help_you:
  - 'Find definitions of important terms for working with Amplitude Experiment'
landing: false
exclude_from_sitemap: false
updated_by: 0c3a318b-936a-4cbd-8fdf-771a90c297f0
updated_at: 1716917156
---
## Glossary of key experimentation terms

|  |  |
| --- | --- |
| **Term** | **Definition** |
| Allocation | The percent or number of targeted users you want to get this variant. |
| Assignment Event | Another name for Enrollment event.  |
| Audience | A group of users that will be targeted for the experiment. This audience will typically be split evenly into “control” and “variant” groups. |
| Baseline conversion rate | The current rate of your primary success metrics prior to this experiment. |
| Bonferroni correction | A statistical technique used to counteract the multiple comparisons problem (also known as multiplicity or the look-elsewhere effect).  |
| Confidence interval | A range of plausible values that contains the parameter of interest. In our case, the true parameter we’re trying to estimate is the difference in means between the treatment and control/baseline. For example: if the confidence level is set to 95 and we ran the same experiment 100 times, the confidence interval–in each run–would contain the true parameter at least 95 times. |
| Confidence / significance level | The probability you will get a false positive. For example, if you have a 95% confidence level, there is a 5% chance of detecting a change to your success metric when there was really no change. |
| Counter metric | A metric you want to ensure does not suffer at the expense of increasing your success metrics. For example, if you drive users to a free trial of your business product, trials of your consumer product could be a counter metric. If business trials go up, consumer trials will likely go down. You want to make sure there's a net positive effect. |
| CUPED | Controlled-experiment using pre-existing data, also known as CUPED, is an optional statistical technique meant to reduce variance in experimentation.  |
| Exposure Event | The event that indicates when a user has actually seen a change based on a experiment. |
| Hypothesis | An assumption of what methods could be taken to solve or alleviate the problem statement and why.  |
| p-value | The probability of observing data as extreme as what you saw or more assuming that there is no difference between treatment and control. |
| Payload | Variables attached to a variant, that can be used to remote change flags and experiments without a code change. |
| Primary success metric | The main metric you hope to move by running this experiment. Should ideally drive both customer and business success. |
| Problem statement | An explanation of the internal business or user problem you are trying to solve. |
| Run time | Based on the sample size needed per variant and your traffic levels, how long your experiment will take to run. |
| Sample size | The number of users/amount of traffic you need in each of your experimental variants in order to soundly detect statistical significance. |
| Secondary success metric | An additional metric you hope/expect to move with this experiment. |
| Sequential testing | A statistical analysis where the sample size is not fixed in advance, allowing you to: conduct an A/B test, peek at your results, and conclude them without inflating your false positives. |
| Statistical power | The probability that you will detect a change to your success metric when there is a change to be detected. |
| T-test | A statistical analysis that is a comparison of means amongst two populations of data to determine if the difference is statistically significant.  |
| Target lift / minimum detectable effect (MDE) | The percentage change you expect to drive on your primary success metric as a result of this experience. |
| Type 1 error | Incorrectly classifying that there is a statistically significant difference between treatment and control, when there is not. |
| Type 2 error | Incorrectly classifying that there is no difference between treatment and control, when there is. |