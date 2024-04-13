# Triage model

We want to optimise the triage of covid patients. Most patients can be treated from home, however some patients can become seriously ill and require hospitalisation to recover. Covid patients can be very contagious therefore we want to reduce the contact medical staff need with each patient. 

The triage model should identify patients 
* with low risk these are sent home straight away with instructions to monitor their symptoms and return if they worsen.
* with high risk these are sent to the covid ward and closely monitored
* with unknown risk these are traiged by a medical professional.

![](Pasted%20image%2020240412164716.png)

# Required treatment

Patiences definitely required treatment if they were died, icu or were put on a ventelator.

Ideally we do not want false negatives in our model as these patients would be sent home in error.

# Analysis of data
### Medical Facility

- patient type: type of care the patient received in the unit. 1 for returned home and 2 for hospitalization.
- usmr: Indicates whether the patient treated medical units of the first, second or third level.
- medical unit: type of institution of the National Health System that provided the care.

Some medical units only offer second level care
![](Pasted%20image%2020240412134735.png)

Second level care more likely to send home than first level car
![](Pasted%20image%2020240412135345.png)
### Patient Details
- sex: 1 for female and 2 for male.
- age: of the patient.
- classification: covid test findings. Values 1-3 mean that the patient was diagnosed with covid in different  
    degrees. 4 or higher means that the patient is not a carrier of covid or that the test is inconclusive.

### Conditions
- pneumonia: whether the patient already have air sacs inflammation or not.
- pregnancy: whether the patient is pregnant or not.
- diabetes: whether the patient has diabetes or not.
- copd: Indicates whether the patient has Chronic obstructive pulmonary disease or not.
- asthma: whether the patient has asthma or not.
- inmsupr: whether the patient is immunosuppressed or not.
- hypertension: whether the patient has hypertension or not.
- cardiovascular: whether the patient has heart or blood vessels related disease.
- renal chronic: whether the patient has chronic renal disease or not.
- other disease: whether the patient has other disease or not.
- obesity: whether the patient is obese or not.
- tobacco: whether the patient is a tobacco user.
# Effects
- intubed: whether the patient was connected to the ventilator.
- icu: Indicates whether the patient had been admitted to an Intensive Care Unit.
- date died: If the patient died indicate the date of death, and 9999-99-99 otherwise.

# Notes on the data

https://www.kaggle.com/datasets/meirnizri/covid19-dataset/discussion/373795

Hi everyone!
I would like to share with you my findings about missing data.
The dataset has a description that all values like 97, 98, 99 are missing values.
Only 3 columns contain records with value = 97. They are PREGNANT, ICU, INTUBED.

All men have value = 97 for pregnant feature. It means that men can't be pregnant. As I understand value = 99 for this column is really missing value when doctors didn't have enough information about pregnancy or they had some misleading analysis results they put 99 for this feature.

We can see that columns ICU and INTUBED are connected with PATIENT_TYPE column and we can see that patients who have value = 1 for PATIENT_TYPE column have value = 97 for both ICU and INTUBED columns. It means that patients who had home treatment didn't have a chance to get ICU and to be intubed as well. Value = 99 for these two columns looks like really missing value.

All other columns have only one number for missing value. PNEUMONIA column has value = 99 all others have value = 98. I considered them as missing values and droped observations containing them.

Please add a comment if you have other findings.
