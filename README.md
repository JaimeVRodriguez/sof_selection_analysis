# Special Operations Forces Assessment and Selection 
TO BE OR NOT TO BE SELECTED

***
<br />

## Table of Contents
- [Introduction](#introduction)
- [Data Processing](#data-processing)
- [Overview](#overview)
    - [Results by Age](#age)
    - [Key Features](#key-features)
- [Correlation](#correlation)
- [Hypothesis](#hypothesis)
    - [Distribution](#distribution)
    - [T-Test](#t-test)
- [Logistic Model](#logistic-model)
    - [POAS](#poas)
    - [SFAS](#sfas)
    - [Significant Features](#significant-features)
<br />
<br />
<br />

***
## **Introduction**
***
This data is comprised of 12 different excel files spanning 6 years of selection and assesment results for the Special Operations (SOF) fields of Special Forces (SF) and Psychological Operations (PSYOP). The data is aggreted through a series of people from the application and selection process for these SOF fields. <br />
<br />
<br />
<br />

***
## **Data Processing**
***
Due to the aggregation process of this data, there were several human errors and difference in much of the data. Several steps where needed in the data cleaning process.

- 19 columns were removed
    - Personal Data: Personal Identifiable Information such as name, DOB, SSN's, etc were removed in order to not identify individuals as well as comply with Special Operations personal identity policies.
    - Additional columns were deemd unneeded for the purposes of this analyis. These columns were either additional non-identifiable personal information or information that related specifically to selection and not to the individuals attending selection
- Missing Information
    - Records not containing all information pertained to an individual were removed in order to non alter or skew the data
    - 16 POAS Records removed
    - 231 SFAS Records removed

***
## ***Overview***
***
<span style='color:green'> **Key Highlights** </span> <br />
- **~2635** individuals attended POAS
    - 748 selected: **28.3%** Select Rate
- **~8116** individuals attended SFAS
    - 1363 selected: **16.8%** Select Rate

<p float='left'>
    <img src='images/poas_selects.png' width='500' />
    <img src='images/poas_annual.png' width='500' />
</p>

<p float='left'>
    <img src='images/sfas_selects.png' width='500' />
    <img src='images/sfas_annual.png' width='500' />
</p>
<br />
<br />
<br />

### Age
<span style='color:green'> **Key Highlights** </span> <br />
- POAS
    - Average age of **28.5**
- SFAS
    - Average age of **29**

<p float='left'>
    <img src='images/poas_select_age.png' width='500' />
    <img src='images/sfas_select_age.png' width='500' />
</p>
<br />
<br />
<br />

### Key Features
<span style='color:green'> **Key Highlights** </span> <br />
- POAS
    - PT Median score of **271**
    - GT Median score of **117**
    - CO Median score of **117**
- SFAS
    - PT Median score of **285**
    - GT Median score of **117**
    - CO Median score of **117**

- POAS CO Q3 matched that of SFAS at **124**

<p float='left'>
    <img src='images/pt_scores.png' width='325' />
    <img src='images/gt_scores.png' width='325' />
    <img src='images/co_scores.png' width='325' />
</p>
<br />
<br />
<br />

***
## ***Correlation***
***

![](images/correlation.png)
<br />
<br />
<br />

***
## ***Hypothesis***
***
$H_O$: GT Score does not determine whether someone is selected <br />
$H_A$: GT Score determines whether someone is selected

$H_O$: PT Score does not determine whether someone is selected <br />
$H_A$: PT Score determines whether someone is selected

$H_O$: Age does not determine whether someone is selected <br />
$H_A$: Age determines whether someone is selected

$H_O$: Exisiting Language skill does not determine whether someone is selected <br />
$H_A$: Exisiting Language skill determines whether someone is selected
<br />
<br />
<br />

### T-Test
T-Test conducted on features based on whether or not an individual was selected.

The following are the p-values with their corresponding feature: <br />
GT: **2.5269360674271627e-40** <br />
- Reject $H_O$

PT: **7.822031090768901e-09** <br />
- Reject $H_O$

AGE: **4.113012469721914e-06** <br />
- Reject $H_O$

LANG: **0.6882465259249742** <br />
- Cannot reject $H_O$

### Distribution

![](images/distributions.png)
<br />
<br />
<br />

***
## ***Logistic Model***
***
### **POAS** <br />
### <span style='color:green'> **Significant Features** </span> <br />
- Whether someone is **AIRBORNE** qualified
- Someones **AGE**
- **GT** Score
- **SC** Score
- Whether someone needed a **Waiver**

Single Logistic Regression Model PSYOP <br />
![](images/models/poas_single_curve.png)
<br />

Logistic Regression with KFold <br />
![](images/models/poas_multi_curve.png)
<br />
<br />

### **SFAS** <br />
### <span style='color:green'> **Significant Features** </span> <br />
- Someones **RANK**
- Whether someone is **AIRBORNE** qualified
- Whether someone is **RANGER** qualified
- The amount of **DEPENDENTS** someone has
- Someones **AGE**
- **ST** Score
- Whether someone needed a **WAIVER**

Single Logistic Regression Model PSYOP <br />
![](images/models/sfas_single_curve.png)
<br />

Logistic Regression with KFold <br />
![](images/models/sfas_multi_curve.png)
<br />
<br />
<br />

### ***Significant Features***
Model with all features only performed slightly better than chance. Meaning there is no better result than a random guess. There could be a couple of different factors. Lack of data, only 10,000 records is not a sufficiant amount in order to properly train a model. 
Secondly, there are additional factors that should be included or considered when determining the selection results of an individual. These features include things like team work, leadership, communication, etc.

However, when narrowing down the model to only existing features that are significant, the model does perform better. However, one must take into consideration what they want out of the model. A predictive model is not always the "best" model.

<p float='left'>
    <img src='images/models/poas_sig_feature.png' width='500' />
    <img src='images/models/sfas_sig_feature.png' width='500' />
</p>

