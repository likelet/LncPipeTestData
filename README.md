# LncPipeTestData

This repo contains a test case for running LncPipe.  
Testdata can be download [here](http://cancerbio.info/pub/lncpipe/testdata.tar.gz)


## Run test data of LncPipe   

As lncpipe involved integrated analysis of multi samples, we provided a four-sample packaged test data that have two different  experiment conditions. To run the test of lncpipe, plz run the following command step by step :  

* __Step 1__. Download the test data 
```shell
      #prepare test data 
      wget http://cancerbio.info/pub/lncpipe/testdata.tar.gz
      tar -xvzf testdata.tar.gz 
      cd testdata
```
* __Step 2__. Get the lastest lncPipe  

        git clone https://github.com/likelet/LncPipe.git 

* __Step 3__. Run the analysis command  (about 10 mins)

        #(run the this `cmd` if your are using a centos 7.0 linux system , this cmd can temperally set the selinux into permissive mode )
        sudo setenforce 0 
        
        nextflow run LncPipe/LncRNAanalysisPipe.nf -with-trace -resume -with-timeline timeline.html
## Test data content 


```
      ├── design.file
      ├── Fastq
      │   ├── dPDLSCs1_1.fastq.gz
      │   ├── dPDLSCs1_2.fastq.gz
      │   ├── dPDLSCs2_1.fastq.gz
      │   ├── dPDLSCs2_2.fastq.gz
      │   ├── uPDLSCs1_1.fastq.gz
      │   ├── uPDLSCs1_2.fastq.gz
      │   ├── uPDLSCs2_1.fastq.gz
      │   └── uPDLSCs2_2.fastq.gz
      └── Genome
          ├── chr22.fa
          ├── gencode.chr22.gtf
          ├── hisat_index
          │   ├── chr22.1.ht2
          │   ├── chr22.2.ht2
          │   ├── chr22.3.ht2
          │   ├── chr22.4.ht2
          │   ├── chr22.5.ht2
          │   ├── chr22.6.ht2
          │   ├── chr22.7.ht2
          │   └── chr22.8.ht2
          └── lncipedia.chr22.gtf
```  
      
* `design.file` stored the test exprimental design for performing comparision   

```
      D:dPDLSCs1,dPDLSCs2
      u:uPDLSCs1,uPDLSCs2
```  
* `Fastq` folder contains paired, compressed fastq files, also known as raw reads.   

* `Genome` folder contains several files explained below:  

     * `chr22.fa` genome reference of chromosome 22 with fasta format.  
      
     * `hisat_index` folder contains the hisat2 index file build from chr22.fa
      
     * `lncipedia.chr22.gtf` GTF files grepped from [lncpedia_4.0.gtf](https://lncipedia.org/downloads/lncipedia_5_0_hc_hg38.gtf)  
     
     * `gencode.chr22.gtf` GTP files grepped from [Genecode](ftp://ftp.ebi.ac.uk/pub/databases/gencode/Gencode_human/release_27/gencode.v27.annotation.gtf.gz)
     

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

![timeline](https://github.com/likelet/LncPipeTestData/blob/master/timeplot.png)
