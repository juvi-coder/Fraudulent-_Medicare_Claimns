# Fraudulent-_Medicare_Claims
By leveraging data analysis and machine learning, we can proactively identify potential medicare fraud cases, thus preserving resources for those truly in need.


# Healthcare Fraud: An Unseen Epidemic Impacting Medicare's Effectiveness

# Problem Statement
Healthcare fraud is a persistent issue in the US, with certain providers exploiting Medicare for personal gain. This problem limits Medicare's capacity to serve the healthcare needs of elderly and other qualifying individuals effectively.
Despite efforts by the Centers for Medicare and Medicaid Services (CMS) to minimize fraudulent activities, identifying patterns of fraudulent claims remains a challenge.

# Objective
Our goal is to examine patterns of fraudulent claims activity in the CMS Medicare dataset, using the list of fraudulent providers from LEIE.
We aim to identify specific features distinguishing fraudulent physicians from non-fraudulent ones and develop a classifier model for fraud detection.

# Significance
Addressing healthcare fraud is vital for the equitable distribution of Medicare resources, ensuring maximum reach and effectiveness of the program.
By leveraging data analysis and machine learning, we can proactively identify potential fraud cases, thus preserving resources for those truly in need.


Medicare fraud and abuse can occur everywhere, increasing everyone's taxes and health care expenditures. Many instances include: 

A healthcare professional charges Medicare for goods or services you never received, such as billing you for a visit or a back brace you never received. 
A provider who bills Medicare twice for a good or service you only received once. 
A person who uses your Medicare card or number to submit false claims on your behalf. 
A business that proposes a Medicare drug plan to you that Medicare hasn't approved.

CMS has released  datasets, including the Medicare Provider Utilization and Payment Data: Physician and Other Supplier.

The Office of the Inspector General provides a dataset of List of Excluded Individuals and Entities (LEIE), signifying fraudulent providers.

**Using the above two datasets, levraging the power of Altreyx, Tableau and Python**, **I have built an Gradient Boosted Model, with 76% Accuracy and 71% AUC Scores.**

# DATA PREP Workflow
<img width="943" alt="Data Prep Workflow" src="https://github.com/juvi-coder/Fraudulent-_Medicare_Claimns/assets/100660932/3bfc4aff-cd14-42fc-9502-127a4c1ceaf6">




# Looking into each step of Data Prep Workflow

<img width="581" alt="Dataprep_fraud" src="https://github.com/juvi-coder/Fraudulent-_Medicare_Claimns/assets/100660932/690f72aa-f93e-40c1-9fc1-a4a28b448439">

# Feature Engineering


<img width="270" alt="feature Engineering" src="https://github.com/juvi-coder/Fraudulent-_Medicare_Claimns/assets/100660932/4e3508e8-b5be-4707-97b1-c1aec0b7b92b">


The whole point of feature engineering is to capture the abnormal behavior that an medicare provider may commit. After an literature study, I found that these are important variables in the data set that can capture abnormalities.

Using the variables
 
Average Medicare Amount Allowed: 
Average of the Medicare allowed amount for the service; this figure is the sum of the amount Medicare pays, the deductible and coinsurance amounts that the beneficiary is responsible for paying, and any amounts that a third party is responsible for paying.

Average Medicare Payment Amount:	Average amount that Medicare paid after deductible and coinsurance amounts have been deducted for the line item service.

Average Submitted Charge Amount:	Average of the charges that the provider submitted for the service.

Number of Medicare Beneficiary/Day Services	Number of distinct Medicare beneficiary/per day services.

**I created the following features:**

**total_amount_claimed**
[Number of Medicare Beneficiary/Day Services]*[Average Submitted Charge Amount]
This captures the total amount of money charged by the provider for all the services that were performed and submitted for claim.

**Total_amount_recevied**
[Number of Medicare Beneficiary/Day Services]*[Average Medicare Payment Amount]
This captures the total average amount received by the provider that medicare paid after deductible  and coinsurance amounts.

**total_amount_allowed**
[Number of Medicare Beneficiary/Day Services]*[Average Medicare Allowed Amount]
This captures the total average amount approved and covered by Medicare for the service.

**Using the above features I again created the below features:**

**final_amount_recevied**
[total_amount_claimed]-[Total_amount_recevied]
This captures the total amount recevied by the medicare provider after the copayment and dedcutiable payed by the patient

**excess_amount_claimed**
[total_amount_claimed]-[total_amount_allowed]
This captures the excess amount claimed to the approved medicare costs 

**payout_ratio****

[Average Medicare Payment Amount]/[Average Submitted Charge Amount]
This feature captures the total of average amount paid by the medicare to the total average cost of services for a claim by provider


**allowance_ratio**
[Average Medicare Allowed Amount]/[Average Submitted Charge Amount]
This captures average  deviation in the amount approved by medicare and the total amount charged by the provider. 




# Final Data Modeling Workflow for EDA
<img width="378" alt="EDA" src="https://github.com/juvi-coder/Fraudulent-_Medicare_Claimns/assets/100660932/d298c77e-2fa3-489a-b683-6c1aa4c48017">


In this stage, I am grouping data by NPI Code, Gender, Provider Type, and Fraud Label to consolidate all data related to each unique provider.

The final features for model construction, derived from multiple claim rows per provider, are as follows:

Count of HCPCS Code: This reflects the diversity of services provided by each provider. Larger providers may offer a variety of services, while smaller ones might only provide a few. This feature could highlight abnormalities in the model, such as smaller providers attempting to claim large amounts.

Average of Payout Ratio: This measures the average ratio of the amount paid by Medicare to the amount charged by the provider. It can help identify abnormalities.

Average of Allowance Ratio: This feature represents the average ratio of the amount approved by Medicare to the amount charged by the provider.

Average of Final_amount_received: This captures the average amount received by the provider from Medicare. It can highlight anomalies such as unusually high or low reimbursement rates.

Average of Excess_amount_claimed: This measures the average excess amount claimed by the provider, which can help in detecting abnormalities.

Average of Medicare Beneficiary/Day Services: This captures the average number of patients a single provider serves per day. Abnormally high values could suggest fraudulent activity.

Sum of Total_Amount_Claimed

Sum of Total_amount_received

Sum of Total_amount_allowed

The above features will assist in the development of a model aimed at identifying fraudulent Medicare claims. By effectively distinguishing between normal and abnormal provider behavior, this model can help ensure Medicare funds are used appropriately and efficiently.


# Final Modelling Workflow
<img width="956" alt="Modelling Workflow" src="https://github.com/juvi-coder/Fraudulent-_Medicare_Claimns/assets/100660932/fc2906f4-6649-45d9-8072-b0ec962c85f3">



## Modeling Results

<img width="511" alt="Comparison Report" src="https://github.com/juvi-coder/Fraudulent-_Medicare_Claimns/assets/100660932/56090f4e-11b9-444c-aea3-173122e37b12">


# T Tests, CHI Square are present in the presentation Deck

# I have attached my presentation deck, altreyx flows, Tableau BI Solution and Python code for the problem.
