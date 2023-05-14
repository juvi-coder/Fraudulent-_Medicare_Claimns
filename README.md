# Fraudulent-_Medicare_Claimns
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

## DATA PREP Workflow
<img width="943" alt="Data Prep Workflow" src="https://github.com/juvi-coder/Fraudulent-_Medicare_Claimns/assets/100660932/3bfc4aff-cd14-42fc-9502-127a4c1ceaf6">

**Looking into each step**:
<img width="581" alt="Dataprep_fraud" src="https://github.com/juvi-coder/Fraudulent-_Medicare_Claimns/assets/100660932/690f72aa-f93e-40c1-9fc1-a4a28b448439">


**Fraud Data Input LEIE**
The LEIE (List of Excluded Individuals/Entities) file contains comprehensive information about providers who have committed fraud.

Each provider is uniquely identified by their National Provider Identifier (NPI).

In this analysis, I am exclusively selecting the NPI column for further scrutiny using the Select tool in Alteryx.

Additionally, I'm employing the Filter tool to eliminate records with an NPI Code of zero, as all medicare claims data have a unique, non-zero NPI Code to identify provider.

Finally, to pinpoint the fraudulent Medicare providers in the dataset, I'm using the Unique tool in Alteryx. This process allows us to isolate and identify providers with fraudulent activity, which can be helpful to flag 🚩 fraudulent providers in the claims dataset. 

**Medicare Data Input**
In this step, I'm utilizing the Union Tool in Alteryx to vertically stack the Medicare data files spanning the years 2012 through 2015. This process consolidates these annual datasets into a single comprehensive file for further analysis


**Identifying Fraudulent Medicare Data**


 In this phase, I am merging the Fraudulent Providers Data with the Claims Data using the "NPI" Column as the key for joining.

The 'J' Anchor of the Join tool in Alteryx outputs records that successfully matched from both the 'L' (Left) and 'R' (Right) inputs. These represent the fraudulent claims.

The 'R' Anchor outputs records from the 'R' input that didn't find a match in the 'L' input, signifying non-fraudulent claims.

I'm employing the Formula tool to create a new column named 'Fraud_Label'. Data stemming from the 'J' Anchor is assigned a label of 1 (indicating fraud), while data from the 'R' Anchor is assigned a label of 0 (indicating non-fraud).

Next, I use the Union tool to combine both sets of labeled data. This is followed by removing any duplicate rows that may have been created due to the join operation.

In my dataset, multiple claims are associated with the same provider. However, for my analysis, I only require a single row per provider. To achieve this, I'm selecting unique rows based on the combination of 'NPI' and 'HCPCS' codes.

**I have attached my presentation deck, altreyx flows, Tableau BI Solution and Python code for the problem.**
