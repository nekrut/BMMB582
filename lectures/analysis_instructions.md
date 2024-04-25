# Finalizing analyses results for the final week

## Assumptions

1. Everyone knows their group
2. Everyone completed the initial analysis in which we:
   - QC'ed the reads
   - Mapped them against `mm10`
   - Filtered data to remove unpaired and non-uniquely mapped reads
   - Have a final output: a collection with several (2 or 3) BAM files. **THIS DATASET IS THE INPUT TO THE TWO WORKFLOWS MENTIONED BELOW**.
  
## Next steps

> [!NOTE]
> To complete **before** Tuesday, Apr 23.

![image](https://github.com/nekrut/BMMB582/assets/4291636/c2da6fe1-6058-41d7-b96e-fe129b228dc5)


### Step 1: Manual analysis using Jupyter

1. Go to "Workflows" on usegalaxy.org, click on "Public workflows" and select `computing_cvrg_per_strand`  to compute coverage for *plus* and *minus* strands.
2. Load plus and minus datasets into this notebook -> https://colab.research.google.com/drive/110ERibDr4pSMGK5viRPlq2XYd3zc4LTq?usp=sharing and create plots

### Step 2: Galaxy analysis using MACS2

1. Go to "Workflows" on usegalaxy.org, click on "Public workflows" and select `Macs2 analysis` to create merged peak calls
2. This datasets will be used for analyses we will perform on Tuesday

### Step 3: The final project

#### 1. Filter

Using dataset from Step 2 filter it to retain only those rows that contain intervals (peaks) shared across all replicates in your experiment. This information is containewd within column 4. The number you want is the number of replicates in your dataset (2 or 3, depending whether you are analyzing D0, D3, D5 etc.)

```
chr19	3082621	3082832	1	1	1	0					
chr19	3083413	3083421	1	1	1	0					
chr19	3083421	3083690	2	1,2	1	1					
chr19	3083690	3083707	1	1	1	0
```

#### 2. Remove unnecessary columns (optional)

Use `cut` tool to remove columns 4, 5, 6 and 7 from the relting dataset. You will no longer need them.

#### 3. Upload gene info

Upload coordinates of mouse genes using genome version `mm10` 

![image](https://github.com/nekrut/BMMB582/assets/4291636/8c371584-30b6-49a2-a452-c4e70167e4af)


