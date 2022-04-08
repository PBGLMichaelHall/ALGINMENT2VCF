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
fastq-dump ERR4835478

# I use BWA to align Fasta with FASTQ and generate BAM file
![Screenshot from 2022-04-08 08-29-47](https://user-images.githubusercontent.com/93121277/162377667-e2775020-c0c4-42aa-bfd6-62522038b835.png)
# ~9 Hours @ 18.1 GB

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
#These commands are only necessary to plot in RStudio Viewer, otherwise the most important plots are automatically genearted to HTML file in FASTQC directory

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
# Open the HTML file in the FASTQC directory Generated by fastqc function
# I have taken several screenshots

![Screenshot from 2022-04-08 08-54-24](https://user-images.githubusercontent.com/93121277/162381369-7768bcc0-01a7-4a86-bf3a-771e14a433e6.png)
![Screenshot from 2022-04-08 08-54-35](https://user-images.githubusercontent.com/93121277/162381367-97ec9e7e-ab48-4773-beeb-1dee09c6e2a1.png)
![Screenshot from 2022-04-08 08-54-46](https://user-images.githubusercontent.com/93121277/162381366-ffec19c1-f637-4a52-b30a-1a07435a33a9.png)
![Screenshot from 2022-04-08 08-54-58](https://user-images.githubusercontent.com/93121277/162381363-a8a52f1d-1f58-4cef-a9b9-44be515b8131.png)
![Screenshot from 2022-04-08 08-55-08](https://user-images.githubusercontent.com/93121277/162381360-92a4fad5-8d36-49da-963e-5f965e3fc46c.png)
![Screenshot from 2022-04-08 08-55-18](https://user-images.githubusercontent.com/93121277/162381359-7c0298e3-cd4d-40f6-8a03-7665726a34dc.png)
![Screenshot from 2022-04-08 08-55-28](https://user-images.githubusercontent.com/93121277/162381358-374e7f9c-810c-44a2-a431-be197b96ef3b.png)
![Screenshot from 2022-04-08 08-55-38](https://user-images.githubusercontent.com/93121277/162381356-cbaa9de7-26b3-435d-984b-e64e5c547b56.png)
![Screenshot from 2022-04-08 08-55-49](https://user-images.githubusercontent.com/93121277/162381353-03dd6c55-fccf-4a43-9c7d-2db74e7d5e50.png)
![Screenshot from 2022-04-08 08-55-59](https://user-images.githubusercontent.com/93121277/162381351-93374041-cc0a-47da-938d-7302ddb5d5a7.png)
![Screenshot from 2022-04-08 08-56-07](https://user-images.githubusercontent.com/93121277/162381346-cdd83627-3eaa-4170-9868-87e141aa816c.png)














# Check the Data Structure
![Screenshot from 2022-04-08 09-01-13](https://user-images.githubusercontent.com/93121277/162381931-b1c018b3-39c2-4a6f-a76f-7bc8b9b21a56.png)


# Index your reference genome FASTA file first
![Screenshot from 2022-04-07 14-23-55](https://user-images.githubusercontent.com/93121277/162197997-c8a3b0d8-7c50-4135-81bb-16e35ea959a6.png)

# Use samtools to sort BAM file


