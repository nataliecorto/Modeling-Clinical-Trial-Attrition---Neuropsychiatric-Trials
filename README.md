# modelingClinicalTrialAttrition_NeuropsychiatricTrials
SQL script to pull neuropsychiatric trials / Python to clean and model data from the Aggregate Analysis of Clinicaltrials.gov (AACT)

## Abstract : 
the lifecycle of drug development, the clinical trial phases have a huge impact on the efficiency of the development and successful launch of that novel therapeutic in the marketplace. One of the major barriers of the successful completion of each clinical trial phase and eventual FDA approval is attrition of trial subjects. Clinical trial subject attrition levels directly affect the generalizability and validity of the results of a trial. If trials are lacking generalizability and validity the likelihood, they go to market and find success in the patients of interest decreases. To address this problem, we have pulled a unique dataset from the open-source database Aggregate Analysis of ClinicalTrials.gov (AACT) to create a sponsor-independent dataset representing neuropsychiatric clinical trials. The dataset pulled from the AACT included 16,220 trials of interest, of which 1,359 trials had complete data entered that supported the percent attrition target variable representing 377,378 trial subjects in the neuropsychiatric domain. To our knowledge this data-driven sponsor-independent approach to identify top features influencing subject attrition in neuropsychiatric trials is novel in the literature. Top features predicting clinical trial attrition included inclusion/exclusion criteria issue, study duration, lost to follow-up, and adverse event. Top regression models included Random Forest Regressor and Gradient Boosting Regressor with top performance at 79% accuracy (r2 = 0.79) score predicting percent attrition in the master neuropsychiatric clinical trial dataset.

## Introduction : 
We are proposing with this project a sponsor agnostic, data-driven approach to address the problem of patient attrition in neuropsychiatric clinical trials using machine learning algorithms trained on publicly available data from the AACT database sponsored by the Clinical Trial Transformation Initiative (CTT). Machine learning is a key part of this project because of its excellent ability in the handling of large numbers of predictors - in this case, more predictors than observations - and allows for the combination of those predictors in a non-linear manner (Obermeyer, 2016). This machine learning approach is particularly important for attempting to predict something like patient attrition which has multiple factors involved in the process. 
 
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
    - Load two files generated previously including 1. Distinct adverse reported events 2. Standardised MedDRA Queries 
- adverse_Events.ipynb 
- adverseEventTable.ipynb
    - Clean table so each individual trial has the number of affected patients per adverse event for that trial after adverse events have been recategorized from the free text.

Next : Compile all disease types into three distinct clean master files (generic features, adverse events, dropout reasons) 
- V3_Master.ipynb

Next : Execute modeling both with and without feature selection 
- test_feature.ipynb
- test_noFeature.ipynb


