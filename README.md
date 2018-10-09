# LncPipeTestData

This repo contains a test case for running LncPipe.  

## Data Information   

Only a subset of the whole dataset (trimmed for chrX only) were put on this repo for improving testing efficiency for LncPipe. 
The file includes  

* Fastq files with properly named `Fastq/*.gz`  

* Genome reference from GENCODE `Genome/chrX.fa` 

* Hisat2 index of the genome reference `Genome/hisat2Index*.ht2`, generated by following command  

        hisat2-build chrX.fa chrX  
    
* GENCODE ANNOTATION file `Genome/gencode.v25.annotation.chrX.gtf`

* LncPipedia ANNOTATION file `Genome/lncipedia_4_0.chrX.gtf`

* Experimental design file `design.file`

* nextflow running config file `docker.config`

* A singularity image `lncPipe.image` that storing all required environment


## Test command  (Assume that docker and nextflow were properly preinstalled )

* __Step 1__. Download the test data 

        wget http://cancerbio.info/pub/LncPipeTestData.tar.gz
        tar -xvzf LncPipeTestData.tar.gz
        cd LncPipeTestData

* __Step 2__. Get the lastest lncPipe  

        git clone https://github.com/likelet/LncPipe.git 

* __Step 3__. Run the analysis command  (about 30mins)

        nextflow -c docker.config run LncPipe/LncRNAanalysisPipe.nf -with-trace -resume -with-timeline timeline.html


## Result content (expected result)
        ```
        ├── hisat_alignment
        │   ├── R1126N.hisat2_summary.txt
        │   ├── R1126N.sort.bam
        │   ├── R1126T.hisat2_summary.txt
        │   ├── R1126T.sort.bam
        │   ├── R1130N.hisat2_summary.txt
        │   ├── R1130N.sort.bam
        │   ├── R1130T.hisat2_summary.txt
        │   ├── R1130T.sort.bam
        │   ├── R1134N.hisat2_summary.txt
        │   ├── R1134N.sort.bam
        │   ├── R1134T.hisat2_summary.txt
        │   ├── R1134T.sort.bam
        │   ├── S483N.hisat2_summary.txt
        │   ├── S483N.sort.bam
        │   ├── S483T.hisat2_summary.txt
        │   ├── S483T.sort.bam
        │   ├── S502N.hisat2_summary.txt
        │   ├── S502N.sort.bam
        │   ├── S502T.hisat2_summary.txt
        │   └── S502T.sort.bam
        ├── Identified_lncRNA
        │   ├── all_lncRNA_for_classifier.gtf
        │   ├── final_all.fa
        │   ├── final_all.gtf
        │   ├── lncRNA_classification.txt
        │   ├── lncRNA.fa
        │   ├── protein_coding.fa
        │   └── protein_coding.final.gtf
        ├── LncPipeReports
        │   ├── figures
        │   ├── libs
        │   ├── reporter_files
        │   ├── reporter.html
        │   └── tables
        ├── Merged_assemblies
        │   └── merged.gtf
        ├── QC
        │   ├── R1126N_fastp.html
        │   ├── R1126T_fastp.html
        │   ├── R1130N_fastp.html
        │   ├── R1130T_fastp.html
        │   ├── R1134N_fastp.html
        │   ├── R1134T_fastp.html
        │   ├── S483N_fastp.html
        │   ├── S483T_fastp.html
        │   ├── S502N_fastp.html
        │   └── S502T_fastp.html
        └── Quantification
            ├── kallisto.count.txt
            └── kallisto.tpm.txt
        ```
## Run information 

[timeline](https://github.com/likelet/LncPipeTestData/blob/master/timeplot.png)
