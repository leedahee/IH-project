# Computable knowledge in Healthcare
#### Calculating the Mortality Rate of Patients with Cancer within 30 Days of Admission

#####Introduction
Cancer is the second leading cause of death in the United States. According to the National Cancer Institute, an estimated 1,685,210 new cases of cancer will be diagnosed and  595,690 cases will die in 2016 alone. In terms of end-of-life care, patients with cancer have reported a preference for spending their last days at home over the hospital. This creates a greater need for the improvement of patients’ clinical experience in terms of communication with their physician so that patients can take the appropriate steps that are mostly aligned with their preferences. Ramchandran et al. have developed a regression model to predict 30-day mortality based on collected electronic medical record (EMR) data. This regression model was developed in order to provide patients an accurate and realistic view of their prognosis. This model offers potential to minimize emotional cost to patients and their families, and financial cost to healthcare centers. Using the prediction model, physicians would be able to identify higher risk patients whose care may need to be prioritized. Patients with cancer thus would be more empowered to make their own decisions on how to receive the appropriate end-of-life care.

#####Purposes & Uses of the Program
The program requires inputs from data collected from EMRs within 24 hours of admission. After responses for the variables have been entered, the program generates a score that is used to standardize patient data that is manually inputted by a clinician or pulled from an EMR. The code then passes the score through a probability model and outputs the probability of mortality within 30 days of admission for  patients with cancer. This metric informs clinicians about the probability that their patient has of surviving a month after admission based on data collected when the patient is first admitted. In acute care cases, this statistic will help providers and patients mutually decide on the course of treatment (inpatient, outpatient or in-home care) in light of the predictive statistic and the patient’s preferences. The general purpose of this code is to simulate the predictive model of the study and establish that EMR data can be used to accurately model endpoint statistics that will inform clinical decisions in meaningful ways.

#####Making of the Code
The code for this program is designed to take inputs from clinicians based on prompts that ask for eight of the original fourteen variables that were found to be statistically significant in the study by Ramchandran et al. The eight variables included are: age, temperature, heart rate (BPM), oximetry value (%), systolic blood pressure (mmHg), admission type: elective or routine, functional status as defined by difficulties with activities of daily living (ADL), and oxygen use upon admission.

The logistic regression model below was used to obtain a score that standardized the data on a case-by-case basis:

Score = 18.2897 + 0.6013*(admit type) + 0.4518*(ADL) + 0.0325*(admit age) - 0.1458*(temperature) + 0.019*(heart rate) - 0.0983*(pulse oximetry) - 0.0123 (systolic blood pressure) + 0.8615*(O2 on admission)

The predictive model below was used to obtain a probability based on the score calculated above that predicted probability of death within 30 days: 

p = exp(score)/(1+exp(score))	

Entering the values for qualitative variables, ADL, admit type, and oxygen on admission, into the regression initially produced a type compatibility error. The qualitative answers are coded so that the values are applicable within the context of the problem when these are implemented into the regression equation. ADL and oxygen on admission had binary responses where if the response was “no,” there was no value added to the score. Quantifying the admit type was more difficult because there is little data on the relative importance of having an elective versus routine procedure in the context of patients with cancer who were admitted in these settings.

#####Lessons Learned 
There are a number of takeaways in crafting of the code for this program. It is important for the code to navigate around data entry errors or discrepancies. Any error present directly affects the results. As such, the code must be proactive in a way that minimizes errors that may occur when clinicians enter the data into the EMR or directly into the program. This would mean accounting for differences in input for qualitative responses and ensuring that capitalization or abbreviating the response (entering “y” or “Y” or “yes” for example) does not impede on the function of the program. Units also need to be specified so that the right calculation is inputted. Temperature in Fahrenheit or Celsius, for example, would have drastic effects on the results of the program. 
The study that provides the equations that this program simulates also contains a number of limitations that affect the accuracy of this program. First, the sample for the study was recruited from a single care institution, which limits generalizability for larger populations. Next, validation of the equation has not been studied thoroughly. While the model is useful, it was tested using retrospective data, which may not be as useful for prediction. As such, this equation needs to be studied with a prospective cohort in order to show the predictive value that this model adds to clinical decision support. Lastly, the equation is missing confounding factors and other variables that could also affect mortality rates in patients with cancer. These include the stage of cancer and other physiological factors of the tumor. 

#####Conclusion
	To develop a regression equation, Ramchandran et al. focused on all cancer-related admissions and on variables collected within 24 hours of admission. These variables were found to be statistically associated with mortality within 30 days after admission. The program developed calculates the 30-day mortality probability for patients with cancer upon certain admission criteria stored in EMRs. This allows physicians to isolate higher-risk patients and ultimately allows patients with cancer to make their own decisions on how to receive the appropriate end-of-life care.

#####References 
1.	Cancer Statistics. (n.d.). Retrieved November 11, 2016, from https://www.cancer.gov/about-cancer/understanding/statistics

2.	Bruera, E., Russell, N., Sweeney, C., Fisch, M., & Palmer, J. L. (2002). Place of death and its predictors for local patients registered at a comprehensive cancer center. Journal of Clinical Oncology, 20(8), 2127-2133.

3.	Ramchandran, K. J., Shega, J. W., Von Roenn, J., Schumacher, M., Szmuilowicz, E., Rademaker, A., ... & Weitzman, S. (2013). A predictive model to identify hospitalized cancer patients at risk for 30‐day mortality based on admission criteria via the electronic medical record. Cancer, 119(11), 2074-2080.
