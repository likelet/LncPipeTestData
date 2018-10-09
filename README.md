# LncPipeTestData
This repo contains a test case for running LncPipe.  

# Data Information   

Only a subset of the whole dataset (trimmed for chrX only) were put on this repo for improving testing efficiency for LncPipe. 
The file includes  

* Fastq files with properly named `*.gz`  

* Genome reference from GENCODE `chrX.fa` 

* Hisat2 index of the genome reference `*.ht2`, generated by following command  

        hisat2-build chrX.fa chrX  
    
* GENCODE ANNOTATION file `gencode.v25.annotation.chrX.gtf`

* LncPidia ANNOTATION file ``

* Experimental design file `design.file`

* nextflow running config file `running.config`

* A singularity image `lncPipe.image` that storing all required environment

# Test command  

