# Continuous Intelligence Portfolio

Rucmanidevi Sethu

04/20/2026

Overview

This page summarizes my work on **continuous intelligence** projects. THroughout this course I had the practical experience to  design monitoring pipelines and transform raw data into meaningful signals and detect unusual behaviour and assess the state of the system.

## 1. Professional Project

### Repository Link

(https://github.com/RucuAvinash/cintel-06-continuous-intelligence)

### Brief Overview of Project Tools and Choices
1. Git - TO track changes to code
2. VS Code - Editor to run Python code
3. uv- Python manager that controls Python version and dependencies.

In each of the Project , we worked with a src/folder that holds the Python logic, a data folder with input files, an artifact folder where the processed data is saved. The documentation files are stored in the docs/ which describes the project, the data, and the results.

## 2. Anomaly Detection

### Repository Link

(https://github.com/RucuAvinash/cintel-02-static-anomalies)

### Techniques

WHen we find unusual values in data that is called Anomaly Detection. The simple technique used is "Rule-based Approach" which means defining cutoffs or thresholds to catch obvious errors.

### Artifacts

(https://github.com/RucuAvinash/cintel-02-static-anomalies/tree/main/artifacts)

### Insights

The results generated helped identify the number of anamolies per range that did not meet the threshold.

## 3. Signal Design

### Repository Link

(https://github.com/RucuAvinash/cintel-03-signal-design)

### Signals

I added two derived signals:
1. Weighted Load Index: This field combines the metrics from the requests and the errors field and assigns a weightage to the fields and multiply them to analyze the impact of errors on the system load.
2. I added a Classification Signal for each row , based on the calculated metrics from the Weighted Load Index column.

### Artifacts

(https://github.com/RucuAvinash/cintel-03-signal-design/tree/main/artifacts)

### Insights

Signals reveal the system trends and these trends help in capacity planning and monitoring of the error.

## 4. Rolling Monitoring

### Repository Link

https://github.com/RucuAvinash/cintel-04-rolling-monitoring

### Techniques

Rolling window is a fixed size view that moves through a time of series. The window holds the most recent N values, as new values arrive the old values get dropped and the new one is added.

### Artifacts

https://github.com/RucuAvinash/cintel-04-rolling-monitoring/tree/main/artifacts

### Insights

After applying the rolling window mean and SD to my custom project, I was able to analyze the profit, the expense and wait time for each branch based on the trends.

## 5. Drift Detection

### Repository Link

https://github.com/RucuAvinash/cintel-05-drift-detection

### Techniques

In this project techniques like Signals were setup to identify drift in the system.
Based on signals, difference was calculated between the current and reference metrics.
After a Drift was identified, drift flags was added based on the Threshold set to understand the system changes and percentage of drift from the current system behaviour.

### Artifacts

https://github.com/RucuAvinash/cintel-05-drift-detection/tree/main/artifacts

### Insights

Initially I lowered the existing threshold to see the relative change in the Threshold flag. I added percentage recipes to calcute the difference between current and reference metrics .I added a percentage drift threshold flag to detect changes easily. I also experimented by adding more fields to the existing dataframe.When a threshold was set to lower metrics , those thresholds were not flagged. When a higher threshold was set the metrics were flagged correctly.

## 6. Continuous Intelligence Pipeline

### Repository Link

https://github.com/RucuAvinash/cintel-06-continuous-intelligence

### Techniques

The Techniques used for this project were setting up signals from the existing data . Along with sigals, Thresholds were also set to monitor the System state.

### Artifacts

https://github.com/RucuAvinash/cintel-06-continuous-intelligence/tree/main/artifacts

### Assessment

Based on the Signals and the thresholds set for this Hospital project, the output values were still within the threshold limits and hence the system still showed a stable performance.
