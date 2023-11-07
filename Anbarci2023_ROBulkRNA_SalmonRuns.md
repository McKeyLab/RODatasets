# Install Salmon in a Rosetta environment
```
CONDA_SUBDIR=osx-64 conda create -n rosetta
conda activate rosetta
conda env config vars set CONDA_SUBDIR=osx-64
conda deactivate 
conda activate rosetta
conda install salmon
```

# Create Salmon folder
```
mkdir salmon_test
cd salmon_test
```

# Download cDNA fasta and associated gene GTF from Ensembl
```
curl ftp://ftp.ensembl.org/pub/release-110/fasta/mus_musculus/cdna/Mus_musculus.GRCm39.cdna.all.fa.gz	 -o Mmus.fa.gz
curl ftp://ftp.ensembl.org/pub/release-110/gtf/mus_musculus/Mus_musculus.GRCm39.110.gtf.gz	 -o Mmus.gtf.gz
```

# Build Salmon index based on cDNA fasta
```
salmon index -t Mmus.fa.gz -i Mmus_index
```

# Run Salmon on each RO sample
## Fetal RO
```
salmon quant -i /Users/jen/salmon_test/Mmus_index -l A \-1 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/6019-S1-2_E16_Rep1_R1_001.fastq.gz \-2 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/6019-S1-2_E16_Rep1_R2_001.fastq.gz \-p 8 --validateMappings -o /Users/jen/Documents/RO-BulkRNAseq/SalmonRuns/E16_Rep1
```

```
salmon quant -i /Users/jen/salmon_test/Mmus_index -l A \-1 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/6019-S2-2_E16_Rep2_R1_001.fastq.gz \-2 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/6019-S2-2_E16_Rep2_R2_001.fastq.gz \-p 8 --validateMappings -o /Users/jen/Documents/RO-BulkRNAseq/SalmonRuns/E16_Rep2
```

```
salmon quant -i /Users/jen/salmon_test/Mmus_index -l A \-1 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/6019-S3-2_E16_Rep3_R1_001.fastq.gz \-2 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/6019-S3-2_E16_Rep3_R2_001.fastq.gz \-p 8 --validateMappings -o /Users/jen/Documents/RO-BulkRNAseq/SalmonRuns/E16_Rep3
```


## Adult RO
```
salmon quant -i /Users/jen/salmon_test/Mmus_index -l A \-1 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/6019-S4-2_2M_Rep1_R1_001.fastq.gz \-2 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/6019-S4-2_2M_Rep1_R2_001.fastq.gz \-p 8 --validateMappings -o /Users/jen/Documents/RO-BulkRNAseq/SalmonRuns/2M_Rep1
```

```
salmon quant -i /Users/jen/salmon_test/Mmus_index -l A \-1 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/6019-S5-2_2M_Rep2_R1_001.fastq.gz \-2 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/6019-S5-2_2M_Rep2_R2_001.fastq.gz \-p 8 --validateMappings -o /Users/jen/Documents/RO-BulkRNAseq/SalmonRuns/2M_Rep2
```

```
salmon quant -i /Users/jen/salmon_test/Mmus_index -l A \-1 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/6019-S6-2_2M_Rep3_R1_001.fastq.gz \-2 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/6019-S6-2_2M_Rep3_R2_001.fastq.gz \-p 8 --validateMappings -o /Users/jen/Documents/RO-BulkRNAseq/SalmonRuns/2M_Rep3
```

# Ovary data
## Adult ovary (Hohos et al, 2018 - PMID 29097167 - GSE101906)
### Download data (SRP113611)
```
curl ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR587/000/SRR5870970/SRR5870970.fastq.gz -o /Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOva-Rep1.fastq.gz
curl ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR587/001/SRR5870971/SRR5870971.fastq.gz -o /Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOva-Rep2.fastq.gz
curl ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR587/002/SRR5870972/SRR5870972.fastq.gz -o /Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOva-Rep3.fastq.gz
```

### Run Salmon on each replicate
```
salmon quant -i /Users/jen/salmon_test/Mmus_index -l A -r /Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOva-Rep1.fastq.gz  \-p 8 --validateMappings -o /Users/jen/Documents/RO-BulkRNAseq/SalmonRuns/AdOva_Rep1
```
```
salmon quant -i /Users/jen/salmon_test/Mmus_index -l A -r /Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOva-Rep2.fastq.gz  \-p 8 --validateMappings -o /Users/jen/Documents/
RO-BulkRNAseq/SalmonRuns/AdOva_Rep2
```
```
salmon quant -i /Users/jen/salmon_test/Mmus_index -l A -r /Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOva-Rep3.fastq.gz  \-p 8 --validateMappings -o /Users/jen/Documents/RO-BulkRNAseq/SalmonRuns/AdOva_Rep3
```

## Fetal ovary (Wu et al, 2019 - PMID 31636514)
### Download data (SRR7586665)
Downloaded with Chrome from https://www.ebi.ac.uk/ena/browser/view/SRR7586665
   - E16Ova-Rep1
   - E16Ova-Rep2
   - E16Ova-Rep3

### Run Salmon on each replicate
```
salmon quant -i /Users/jen/salmon_test/Mmus_index -l A \-1 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/E16Ova-Rep1_1.fastq.gz \-2 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/E16Ova-Rep1_2.fastq.gz \-p 8 --validateMappings -o /Users/jen/Documents/RO-BulkRNAseq/SalmonRuns/E16Ova_Rep1
```
```
salmon quant -i /Users/jen/salmon_test/Mmus_index -l A \-1 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/E16Ova-Rep2_1.fastq.gz \-2 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/E16Ova-Rep2_2.fastq.gz  \-p 8 --validateMappings -o /Users/jen/Documents/RO-BulkRNAseq/SalmonRuns/E16Ova_Rep2
```
```
salmon quant -i /Users/jen/salmon_test/Mmus_index -l A \-1 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/E16Ova-Rep3_1.fastq.gz \-2 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/E16Ova-Rep3_2.fastq.gz  \-p 8 --validateMappings -o /Users/jen/Documents/RO-BulkRNAseq/SalmonRuns/E16Ova_Rep3
```


# Adult Oviduct and Ovarian Surface Epithelium (Zheng and Neel, 2019 - PMID 31772167)
## Use SRAToolkit to download data (GSM4052300)
Download and install SRA toolkit following instructions on Github: https://github.com/ncbi/sra-tools/wiki/02.-Installing-SRA-Toolkit
```
cd sratoolkit.3.0.7-mac64/bin
```

### Oviduct Replicate 1
```
./prefetch SRR10042992
```
```
./fasterq-dump SRR10042992 -o /Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOvi-Rep1.fastq.gz
```
Since this is paired-end data, this will generate 2 fastq files that will automatically have the _1 or _2 in the fastq extension. Remember to change the filename prior to running Salmon for clarity. Example: Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOSE-Rep1.fastq_1.gz --> Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOSE-Rep1_1.fastq.gz

```
./prefetch SRR10042993
```
```
./fasterq-dump SRR10042993 -o /Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOvi-Rep2.fastq.gz
```

```
./prefetch SRR10042994
```
```
./fasterq-dump SRR10042994 -o /Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOvi-Rep3.fastq.gz
```

### OSE Replicate 1
```
./prefetch SRR10042995
```
```
./fasterq-dump SRR10042995 -o /Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOSE-Rep1.fastq.gz
```

### OSE Replicate 2
```
./prefetch SRR10042996
./fasterq-dump SRR10042996 -o /Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOSE-Rep2.fastq.gz
```
### OSE Replicate 3
```
./prefetch SRR10042997
./fasterq-dump SRR10042997 -o /Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOSE-Rep3.fastq.gz
```

## Run Salmon on each sample
```
salmon quant -i /Users/jen/salmon_test/Mmus_index -l A \-1 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOvi-Rep1_1.fastq.gz \-2 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOvi-Rep1_2.fastq.gz \-p 8 --validateMappings -o /Users/jen/Documents/RO-BulkRNAseq/SalmonRuns/AdOvi_Rep1
```
```
salmon quant -i /Users/jen/salmon_test/Mmus_index -l A \-1 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOvi-Rep2_1.fastq.gz \-2 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOvi-Rep2_2.fastq.gz \-p 8 --validateMappings -o /Users/jen/Documents/RO-BulkRNAseq/SalmonRuns/AdOvi_Rep2
```
```
salmon quant -i /Users/jen/salmon_test/Mmus_index -l A \-1 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOvi-Rep3_1.fastq.gz \-2 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOvi-Rep3_2.fastq.gz \-p 8 --validateMappings -o /Users/jen/Documents/RO-BulkRNAseq/SalmonRuns/AdOvi_Rep3
```

```
salmon quant -i /Users/jen/salmon_test/Mmus_index -l A \-1 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOSE-Rep1_1.fastq.gz \-2 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOSE-Rep1_2.fastq.gz \-p 8 --validateMappings -o /Users/jen/Documents/RO-BulkRNAseq/SalmonRuns/AdOSE_Rep1
```
```
salmon quant -i /Users/jen/salmon_test/Mmus_index -l A \-1 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOSE-Rep2_1.fastq.gz \-2 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOSE-Rep2_2.fastq.gz \-p 8 --validateMappings -o /Users/jen/Documents/RO-BulkRNAseq/SalmonRuns/AdOSE_Rep2
```
```
salmon quant -i /Users/jen/salmon_test/Mmus_index -l A \-1 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOSE-Rep3_1.fastq.gz \-2 /Users/jen/Documents/RO-BulkRNAseq/FASTQ/AdOSE-Rep3_2.fastq.gz \-p 8 --validateMappings -o /Users/jen/Documents/RO-BulkRNAseq/SalmonRuns/AdOSE_Rep3
```

# Versions: 
- Genome assembly: Mus musculus GRCmm39 (June 2020)
- Environment: MacOSX Monterey 12.0.1 arm64 (M1 Max)
- salmon v1.10.2 (https://github.com/COMBINE-lab/salmon)
- SRA Toolkit v3.0.7 (https://github.com/ncbi/sra-tools)
