# Gene-Expression-Analysis-ColonCancer
Analysis of gene expression to understand differentially expressed genes (DEGs) in colon cancer patients 

### 1. Research Question/Objective

- Goal of this analysis is to contrast the gene expression outcomes of 20 patients who experienced relapse with those of 20 patients who did not.
- Objective: To understand DEGs (Differentially Expressed Genes) of relapsed patients

### 2. Dataset
- CRC_PILOT_clinical_data_HIDS.tsv
    - Clinical data with 40 patients. 
    - All patient information de-identified. 
    - Columns include age, gender, primary disease, disease area, tumor grade, and recurrence. 
    - Clinical attribute of interest: column name “RECURRENCE_ANY”
- CRC_PILOT_withGeneAnno.tsv
    - 80 rows
    - Processed gene expression data in log2 scale. 
    - Column of genes with gene code names as column names. (Column attributes are data to be analyzed.) 
    - Patient ID column includes ‘_Tumor’ or ‘_Normal’
 
### 3. Inclusion/Exclusion Criteria
- From CRC_PILOT_withGeneAnno.tsv file, exclude patient data of which ID ends with ‘_Normal’, to include only tumor samples.
- From CRC_PILOT_clinical_data_HIDS.tsv file, include all patients since these patients are all diagnosed with colon cancer.

### 4. Analysis Method
- Clean/filter data.
    - Exclude data with normal tumor samples.
- Identify groups to be compared.
    - Baseline group: group with “RECURRENCE_ANY=NO” & Tumor sample
    - Comparison group: group with “RECURRENCE_ANY=YES” & Tumor sample
- Sanity check
    - Check if clinical data IDs match the gene expression data IDs. 
- Prep data
    - Transpose data required. 
    - Make sure total number of patients (baseline+comparison) is 40. 
    - Data must be numeric and in data frame datatype. 
- Result analysis
    - Conduct t-test to check difference in sample means between both groups for each gene. 
    - Order the t test result data by p-value (in ascending order). 
    - Filter the top 20 genes.   
