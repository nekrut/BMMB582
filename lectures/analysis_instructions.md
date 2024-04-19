# Finalizing analyses results for the final week

## Assumptions

1. Everyone knows their group
2. Everyone completed the initial analysis in which we:
   - QC'ed the reads
   - Mapped them against `mm10`
   - Filtered data to remove unpaired and non-uniquely mapped reads
   - Have a final output: a collection with several (2 or 3) BAM files. **THIS DATASET IS THE INPUT TO THE TWO WORKFLOWS MENTIONED BELOW**.
  
## Next steps

To complete **before** Tuesday, Apr 23.

### Manual analysis using Jupyter

1. Go to "Workflows" on usegalaxy.org, click on "Public workflows" and select `computing_cvrg_per_strand`  to compute coverage for *plus* and *minus* strands.
2. Load plus and minus datasets into this notebook -> https://colab.research.google.com/drive/110ERibDr4pSMGK5viRPlq2XYd3zc4LTq?usp=sharing and create plots

### Galaxy analysis using MACS2

1. Go to "Workflows" on usegalaxy.org, click on "Public workflows" and select `Macs2 analysis` to create merged peak calls
2. This datasets will be used for analyses we will perform on Tuesday

   
