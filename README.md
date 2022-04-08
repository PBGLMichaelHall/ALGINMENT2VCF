# ALGINMENT2VCF

# First Download Brachypodium Genome reference file
https://www.ncbi.nlm.nih.gov/guide/howto/dwn-genome/
# Select Genomes FTP site .....
![Screenshot from 2022-04-07 14-42-21](https://user-images.githubusercontent.com/93121277/162201241-016fece4-424a-45a1-829f-6922c8633a1b.png)
# Select /refseq index
![Screenshot from 2022-04-07 14-43-21](https://user-images.githubusercontent.com/93121277/162201383-9d71979e-e673-42c0-88ad-15c1dd7f8b56.png)
# Select /plant Index
![Screenshot from 2022-04-07 14-44-11](https://user-images.githubusercontent.com/93121277/162201534-0c632c45-2247-4e7b-a10e-998fc60c7612.png)
# Select /Brachypodium _distachyon
![Screenshot from 2022-04-07 14-44-43](https://user-images.githubusercontent.com/93121277/162201757-4efb17a3-f10f-4507-bce8-56a429fcdba7.png)
# Select /all_assembly_versions
![Screenshot from 2022-04-07 14-45-53](https://user-images.githubusercontent.com/93121277/162201906-afd6b462-e9cd-413c-8f6f-46f00bc0798c.png)
# I choose version one v1
![Screenshot from 2022-04-07 14-46-34](https://user-images.githubusercontent.com/93121277/162202037-175dd435-2f68-41e6-82cc-efc096732a41.png)

# I choose an ascension run ERR4835478 and used fastq-dump ERR4835478 to generate a fastq file
![Screenshot from 2022-04-08 08-29-47](https://user-images.githubusercontent.com/93121277/162377667-e2775020-c0c4-42aa-bfd6-62522038b835.png)

# Take a look at the HEader of The FASTQ file
![Screenshot from 2022-04-08 08-32-01](https://user-images.githubusercontent.com/93121277/162377910-b62c2eb7-6e81-4dce-aee6-877d504047cb.png)

# We run fastqc R package on our FASTQ file with the following R script
```r
setwd("/home/michael/Desktop/Alignment")
install.packages("fastqcr")
library(fastqcr)
fastqc_install()
fastqc(fq.dir = "/home/michael/Desktop/Alignment/FASTQ",threads = 4)
qc.file <- "/home/michael/Desktop/Alignment/FASTQ/FASTQC/ERR4835478_fastqc.zip"
qc <- qc_read(qc.file)
names(qc)
qc_plot(qc, "summary")
qc_plot(qc, "Basic statistics")
qc_plot(qc, "Per base sequence quality")
qc_plot(qc, "Per base sequence content")
qc_plot(qc, "Per sequence GC content")
qc_plot(qc, "Per sequence quality scores")
qc_plot(qc, "Sequence duplication levels")
qc_plot(qc, "Per base N content")
qc_plot(qc, "Sequence length distribution")
qc_plot(qc, "Sequence duplication levels")
qc_plot(qc, "Overrepresented sequences")
qc_plot(qc, "Adapter content")
qc_plot(qc, "Kmer content")

```


# Index your reference genome FASTA file first
![Screenshot from 2022-04-07 14-23-55](https://user-images.githubusercontent.com/93121277/162197997-c8a3b0d8-7c50-4135-81bb-16e35ea959a6.png)

# Check the Data Structure
![Screenshot from 2022-04-07 14-24-25](https://user-images.githubusercontent.com/93121277/162198026-c31e3b62-69bf-44eb-a23f-55f20921e238.png)
