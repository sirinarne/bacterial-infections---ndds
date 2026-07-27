# Bacterial Infections & Neurodegenerative Disease Risk Across National Biobanks 

## Introduction 
In this project, we evaluated the associations between a set of bacterial infections and five neurodegenerative diseases: Alzheimer's, Parkinson's, Dementia, Vascular Dementia, and Amyotrophic Lateral Sclerosis using national biobank data from FinnGen, UK Biobank (UKB), and All of Us (AoU). 

This README is a brief overview of how we did our analysis and provides a breakdown of each of the notebooks in this repository. 

### UKB 


### FinnGen 


### AoU 
01_pull_NDD_rule_of_two_MAY_15_2026 (2).ipynb - This notebook pulls all cases for each of the five NDDs using the rule of two, meaning that in order for the diagnosis of an NDD to be counted, the individual must have two diagnoses. 

02_controls_ (1).ipynb - This notebooks creates the controls by selecting individuals who have a valid sex and are listed as white to match UKB data. Additionally, there is code to double check that this only includes those who are not apart of the NDD cases list created in notebook 1. 

03_pull_ICD10_data (2) (2).ipynb - This notebook pulls all of the ICD10 codes that will be used to assess relationships with NDDs. 

04_prep_CONTROL_JUNE_01_2026 (1) (1).ipynb - This notebook loads the controls that were created in the second notebooks and combines them into a dataframe with the cases. It pulls people who have died and have a recorded death data. It then adds the death date to the dataframe and eliminates thsoe who were diagnosed at death. In addition, the primary consent and recruit dates are also added. Finally, additional calculated fields are also added to the dataframe including tenure and age at tenure for dead and alive participants. Early onset cases (before the age of 60) and those who don't have a sex or date of birth are removed. 

04_prep_NDD_june_01_26_rule_of_two (1) (1).ipynb - This notebooks loads the NDD cases files that were created in the first notebook, eliminates those who were diagnoses at death, adds recruit year, tenure, age at tenure, and removes those who were diagnosed at death, those who recieved an NDD diagnosis before they joind the study, those without a sex or date of birth, and early onset cases (before age of 60). 

05_prep_COMBO(FinnGen) (1).ipynb - This notebooks preps combo files for each NDD and the controls. After ensuring that there are no duplicate IDs, the bacterial codes (based on FinnGen groupings are added. Additionally, the lag times are created for when we evaluate the impact of the timing of infection on NDD risk. The APOE gene status is also added to the data frame as that is a covariate used for our model. 

05_prep_COMBO(ICD10) (1).ipynb - This notebook also preps combo files for each NDD and the controls. However, after ensuring that there are no duplicate IDs, the direct ICD10s are added. The lag tiems are created in the same way and the APOE gene status is added. 

06_run_COX(FinnGen).ipynb - This notebook is where the cox model is created and run. The first model is for lag 0, meaning that it's assessing bacterial infection data at ANY time before tenure. The second model then asssess all lags (0-1 years before tenure, 1-5 before tenure, and 5+ years before end of the study)

06_run_COX-Copy1(ICD10).ipynb - This notebook was created to run the same model but with direct ICD10 codes. We only looked at lag 0 (bacterial infection cases anytime before tenure). 

07_Plots.ipynb - This notebooks creates forest plots and other figures.  

07_Tables.ipynb - This notebook create data tables for subsets of data we collected. 








