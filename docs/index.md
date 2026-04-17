# Continuous Intelligence

This site provides documentation for this project.
Use the navigation to explore module-specific materials.

## How-To Guide

Many instructions are common to all our projects.

See
[⭐ **Workflow: Apply Example**](https://denisecase.github.io/pro-analytics-02/workflow-b-apply-example-project/)
to get these projects running on your machine.

## Project Documentation Pages (docs/)

- **Home** - this documentation landing page
- **Project Instructions** - instructions specific to this module
- **Glossary** - project terms and concepts

## Additional Resources

- [Suggested Datasets](https://denisecase.github.io/pro-analytics-02/reference/datasets/cintel/)

When finished, add this section to your docs/index.md page:

## Custom Project

### Dataset
I used a Hospital Patient Flow dataset of 20 observations. The dataset consists of three attributes:
1. number of patients admitted- This field consists of data of number of patients admitted during the shift.
2. number of patience_delayed_discharge:This field consists data of number of patient whose discharge was delayed.
3. total_wait_time_mins: This field consists of data of the total wait time in minutes across all admissions for that shift.

### Signals
There were three signals that were derived from the existing data to help analyze the data.
delayed_rate-This field is calculated based on the unmber of admissions that experience a discharge delay. This expression was calculated based off of the following calculation.("number of patience_delayed_discharge") / pl.col("number of patients admitted").
avg_wait_mins: This field is calculated to find the average wait time per admitted patient. (total_wait_time_mins/admissions)
admissions_per_delay: This field was calculated to find the number of admissions after each delay.(admission/discharge_delays).If the number of admissions are more after a delay, it is likely that the hospital has fewer delays.
ALong with the above signals I added 2 thresholds:
When delay_rate>0.10 & avg_wait_mins >40.0 I set different hospital status accordingly. Only when the Hospital reaches both these thresholds the code indicates the hospital is degrade, if only one value is off the hospital will still show it is STABLE.


### Experiments
1. I added a new derived field (admissions_per_delay). This field is a inverse calculation of the delayed_rate field. THis helps to analyse the number of admissions accepted after a delay is esperienced. I added a safe division to handle the calculation incase there were 0 delays in the Hospital.
2. I changed the | condition to & to mark the system as DEGRADED only when the system hits both the Thresholds.

### Results
After running the pipeline, the summary output was
avg_admissions	avg_discharge_delays	avg_delay_rate	avg_wait_mins	avg_admissions_per_delay	system_state
48.7	4.15	0.07	48.75	16.77	STABLE																		The Hospital still showed a Stable performance because it did not hit both the thresholds. The average delay was under the threshold but the average wait time exceeded the threshold. The results show that for every 17 admission there is a discharge delay.

### Interpretation
Since the discharge delays are not occuring at an alarming rate, the system was still considered stable, but I think in real time the signal should be set more tight, so the hospital will be able to make changes immediatly when the delay or the high wait time occurs. A tightned signal helps to analyze the cause immediatly, since this as experimental design I was able to understand how setting up signals work.
