# modelingClinicalTrialAttrition_NeuropsychiatricTrials
SQL script to pull neuropsychiatric trials / Python to clean and model data from the Aggregate Analysis of Clinicaltrials.gov (AACT)

## Abstract : 
Throughout the lifecycle of drug development, the clinical trial phases have a huge impact on the efficiency of the development and successful launch of that novel therapeutic in the marketplace. One of the major barriers of the successful completion of each clinical trial phase and eventual FDA approval is attrition of trial subjects. Clinical trial subject attrition levels directly affect the generalizability and validity of the results of a trial. If trials are lacking generalizability and validity the likelihood, they go to market and find success in the patients of interest decreases. To address this problem, we have pulled a unique dataset from the open-source database Aggregate Analysis of ClinicalTrials.gov (AACT) to create a sponsor-independent dataset representing neuropsychiatric clinical trials. The dataset pulled from the AACT included 16,220 trials of interest, of which 1,359 trials had complete data entered that supported the percent attrition target variable representing 377,378 trial subjects in the neuropsychiatric domain. To our knowledge this data-driven sponsor-independent approach to identify top features influencing subject attrition in neuropsychiatric trials is novel in the literature. Top features predicting clinical trial attrition included inclusion/exclusion criteria issue, study duration, lost to follow-up, and adverse event. Top regression models included Random Forest Regressor and Gradient Boosting Regressor with top performance at 79% accuracy (r2 = 0.79) score predicting percent attrition in the master neuropsychiatric clinical trial dataset.

## Introduction : 
The historical trend of bringing novel therapeutics to market has seen sharp, steady increases in time and money invested without a positive association of successful treatments reaching patients. The annual budget for Research and Development (R&D) teams in pharmaceutical companies have been reported by ClinicalTrials.gov to have increased 10-fold when compared to the budget in 1980, after adjusting for inflation (clinicalTrial.gov, 2022). The congressional Budget Office reported in 2021, that pharmaceutical companies spent approximately one quarter of their revenues on R&D in 2019 which was nearly double the size spent in this sector when compared to what was spent in 2000 (congressional budget office, 2021). This exceptional growth of industry has not yet translated into the same growth reflected in FDA approvals of said novel therapeutics. 
 
Researchers have shown that nine out of ten drug candidates fail during phases I, II, and III clinical trials (Sun et al., 2022; Takebe et al., 2018). Approximately 50% of that 90% failure rate in phases I-III trials can be attributed to lack of proving clinical efficacy (Harrison, 2016). A failure to prove efficacy in a clinical trial can be the result of many different factors; however, the existing literature has shown subject attrition is a major reason trials fail to prove efficacy and generalizability of final results. Patient recruitment and retention are major contributors to the amount of money spent, length of projected timeline, and successful outcome of a clinical trial. The successful enrollment in enough subjects of interest and retention of those subjects is critical to obtaining final evaluative data that supports statistical power to prove therapeutic effect. 
 
We are proposing with this project a sponsor agnostic, data-driven approach to address the problem of patient attrition in neuropsychiatric clinical trials using machine learning algorithms trained on publicly available data from the AACT database sponsored by the Clinical Trial Transformation Initiative (CTT) (Alexander, Corrigan-Curay, & McClellan, 2018; Zarin, Tse, Williams, Califf, & Ide, 2011). Machine learning is a key part of this project because of its excellent ability in the handling of large numbers of predictors - in this case, more predictors than observations - and allows for the combination of those predictors in a non-linear manner (Obermeyer, 2016). This machine learning approach is particularly important for attempting to predict something like patient attrition which has multiple factors involved in the process. 
 
If we can provide insight into key features leading to participant dropout in neuropsychiatric trials this research has the potential to provide that information to trial designers to aid in the creation of protocols that support subject retention. Better and more informed trial protocols that lead to higher rates of subject retention will undoubtedly result in more representative and higher-powered trials. Ultimately, leading to increased likelihood of trial success meaning better therapeutics for more patients in the marketplace. The models generated from this work could also be applied in a way that the researchers of a clinical trial enter in their assumptions for a future trial into the model feature fields (i.e., length of trial, number of arms, number of predicted serious adverse events) and get a prediction of the level of subject attrition they can expect with those entered features with a certain amount of accuracy. The application of the machine learning models from this project would allow for better planning of subject enrollment size in neuropsychiatric clinical trials keeping in mind accurate dropout rates to be expected and a smaller chance of encountering the negative effects associated with unaccounted for high attrition, attrition bias and underpowered results


## Order to view and run code :
 First pulled trials from AACT 
- AACT_Depression.Rmd
- AACT_Anxiety.Rmd
- AACT_Bipolar.Rmd
- AACT_Alzheimers.Rmd
- AACT_Parkinsons.Rmd

*this will pull generic features, dropout reasons, and adverse events for each individual disease type - 3 .csv files per disease type*

Next : Load AACT files into python, EDA, and export clean .csv files 
- V2_depression.ipynb
- V2_anxiety.ipynb
- V2_bipolar.ipynb
- V2_alzheimers.ipynb
- V2_parkinsons.ipynb

Next : NLP using K-Mean clustering on dropout reasons
- Master Dropout Reason Notebook.ipynb

Next : Adverse Events using MedDRA ontology mapping 
    - Load two files : 1. Distinct adverse reported events (distinct_reported_events.csv) 2. Standardised MedDRA Queries (smq_edited.csv)
- adverse_Events.ipynb 
- adverseEventTable.ipynb
    - Clean table so each individual trial has the number of affected patients per adverse event for that trial after adverse events have been recategorized from the free text.

Next : Compile all disease types into three distinct clean master files (generic features, adverse events, dropout reasons) 
- V3_Master.ipynb

Next : Execute modeling both with and without feature selection 
- test_feature.ipynb
- test_noFeature.ipynb


