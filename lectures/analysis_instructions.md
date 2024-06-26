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

Upload coordinates of mouse genes using genome version `mm10` and `NCBI RefSeq` as the gene track.

![image](https://github.com/nekrut/BMMB582/assets/4291636/8c371584-30b6-49a2-a452-c4e70167e4af)

#### 4. Create upstream and downstream regions

Our goal is to identify ATAC-seq peaks in genes as well as in upstream and downstream reagion. To do this we need toi create additional datasets containing coordinates of (1) upstream and (2) downstream regions in addition the coordinates of genes that we've downloaded at the previous step. 

To create upstream and downstream regions use `bedtools FlankBed` tool. You will need to run this tool twice to create upstream and downstream regions. Upstream and downstream regions should be 500bp. 

For upstream:

![image](https://github.com/nekrut/BMMB582/assets/4291636/6b5f3645-2213-4bc3-9a86-9125d30c7f9d)

For downstream:

![image](https://github.com/nekrut/BMMB582/assets/4291636/28828e78-054b-40b0-8555-29f46f1bd871)

> [!NOTE]
> Use [Name Tags](https://training.galaxyproject.org/training-material/topics/galaxy-interface/tutorials/name-tags/tutorial.html) to mark your datasets! This will make your life much easier!

#### 4. Compute intersect

Calculate intersect between (1) genes, (2) ustream, (3) downstream regions and peaks (from Step 2). 

#### 5. Select an interesting gene

Pick a gene that has the highest number of peaks within itself or upstream/downstream regions. Write a short discussion of why this gene may be associated with open chromatin. 

#### 6. Submit your results

Use [this form](https://forms.gle/f7FFkZgu2hZgv7Pc7) to submit you results. You must login with your PSU credentials to use this form.


