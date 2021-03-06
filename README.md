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
![Screenshot from 2022-04-08 09-36-32](https://user-images.githubusercontent.com/93121277/162387820-63846ab2-4929-473a-8ab1-6f1ed827f312.png)

# Index the Sorted Reads
![Screenshot from 2022-04-08 09-40-36](https://user-images.githubusercontent.com/93121277/162388885-97a1e191-31c0-48a3-a0fb-da8e5b9da221.png)


# Make a VCF file with BAM, Indexed Bam, and Reference Genome FASTA
![Screenshot from 2022-04-08 12-58-22](https://user-images.githubusercontent.com/93121277/162423567-ff43d996-3a2d-4734-97a4-705a6cf164d1.png)

# At this point you should have 6 directories and 17 files
![Screenshot from 2022-04-08 13-05-08](https://user-images.githubusercontent.com/93121277/162423814-b938fc05-0a25-4ad8-bfb3-572506f8f2dd.png)

# Rename the sample to match Ascension Identifier
![Screenshot from 2022-04-08 13-30-06](https://user-images.githubusercontent.com/93121277/162427212-e5232b6f-86b2-4f58-9eee-e8ff3fa1a605.png)

# VCF Header and Info Fields
![Screenshot from 2022-04-08 13-30-48](https://user-images.githubusercontent.com/93121277/162427343-d3aedb2d-b8d1-4685-a582-2e2e15e510ee.png)

# Use ChromQual to plot important figures with R Script
```r
setwd("/home/michael/Desktop/Alignment/plots")
library(QTLseqr)
library(tinytex)
library(vcfR)
library(tidyr)
library(ggplot2)
library(dplyr)
library(ggrepel)
library(ggpubr)
library(data.table)
# Define a vector of Chromosomes
Chroms <- c("NC_016131.3","NC_016132.3","NC_016133.3","NC_016134.3","NC_016135.3")
file <- "vcfnewsamplename.vcf.gz"
QTLseqr::ChromQual(file = file,chromlist = Chroms, windowSize = 1e+05, HighLimQuality = 15000, scalar = 1, ncol = 5, binwidth1 = 10, binwidth2 = 100, p1 = TRUE, p2 = TRUE, p3 = TRUE, p4 = TRUE, p5 = TRUE)
```

# Standard R Console Output

![Screenshot from 2022-04-08 15-07-32](https://user-images.githubusercontent.com/93121277/162441867-f466f130-b44e-44d6-ad79-9f270e8d5ba0.png)

# And Plots p1, p2, and p5 as Generated in View Panel
![Screenshot from 2022-04-08 15-21-54](https://user-images.githubusercontent.com/93121277/162447191-dc5caa84-6a62-4636-bd8b-b0496c0b0296.png)

![Screenshot from 2022-04-08 15-26-48](https://user-images.githubusercontent.com/93121277/162447203-247d6abc-e561-4ef0-afb6-e1e48adb6445.png)

![Screenshot from 2022-04-11 08-54-33](https://user-images.githubusercontent.com/93121277/162681614-094c6a21-1637-4a6b-acff-05aec02f043b.png)


# Using RMVP Package plot SNP densities per chromosome/contig

```r
library(rMVP)
sample<-"ERR4835478"
pathtosample <- "/home/michael/Desktop/Alignment/plots/vcfnewsamplename.vcf"
out<- paste0("mvp.",sample,".vcf")
memo<-paste0(sample)
dffile<-paste0("mvp.",sample,".vcf.geno.map")

message("Making MVP data S1")
MVP.Data(fileVCF=pathtosample,
         #filePhe="Phenotype.txt",
         fileKin=FALSE,
         filePC=FALSE,
         out=out
)
message("Reading MVP Data S1")
df <- read.table(file = dffile, header=TRUE)
message("Making SNP Density Plots")
MVP.Report.Density(df[,c(1:3)], bin.size = 100000, col = c("blue", "yellow", "red"), memo = memo, file.type = "jpg", dpi=300)
```
![Screenshot from 2022-04-08 15-54-00](https://user-images.githubusercontent.com/93121277/162450132-7599a588-0459-402f-94fd-dc8673e1992a.png)

# The IGV can be used to view Variants as well
# A Big Picture Overview
![Screenshot from 2022-04-11 17-33-26](https://user-images.githubusercontent.com/93121277/162776577-c02a9624-c989-41fc-85ad-ec68f7767eca.png)

# And the first two varaints
![Screenshot from 2022-04-11 14-09-00](https://user-images.githubusercontent.com/93121277/162754446-47ffb82d-8fd0-4683-96cb-39e3194b151a.png)

# Can also see particular statistics on each variant by double clicking
![Screenshot from 2022-04-11 14-14-49](https://user-images.githubusercontent.com/93121277/162754522-ad24159a-bc45-4696-b86e-19daa61b3d0a.png)

# The Reference Genome makes the Protein Asparagine from the DNA sequence AAT
# So does the SNP change the protein that is made, yes in some cases it does including this one.
# Here is the molecular structure of Asparagine

![Asparagine](https://user-images.githubusercontent.com/93121277/162773795-6e4eafec-56af-477c-93be-af054b100c2f.png)

# The SNP changes AAT to GAT which makes the protein Aspartic Acid

![AsparticAcid](https://user-images.githubusercontent.com/93121277/162775030-9a74e738-8c00-4457-aec4-708684350de9.png)

# So similar proteins but NOT THE SAME!

# A Good reference for AMino Acids
https://www.aatbio.com/data-sets/amino-acid-reference-chart-table

#We can also use Qualimap for more analysis. I made an environment for this purpose.
![qualimapenvironment](https://user-images.githubusercontent.com/93121277/164391646-d8860f04-62fa-4257-b0d9-832943fc6d29.png)

#And then I ran this command
![qualimap](https://user-images.githubusercontent.com/93121277/164391677-bed72ae6-7a7c-4dcd-9e58-779974ffeeaf.png)

#Select file drop down to New Analysis and finally BAMQC. Browse your directory for the sorted BAM file and >>>>> Start Analysis
![aag](https://user-images.githubusercontent.com/93121277/164392252-071aa607-87fc-453a-a32b-a47f348e299f.png)

![99](https://user-images.githubusercontent.com/93121277/164392943-237a8070-2e80-47c6-be8f-e341657b47cc.png)

![100](https://user-images.githubusercontent.com/93121277/164392958-970e85d8-0190-40f0-b5f6-73f85842bde5.png)

![101](https://user-images.githubusercontent.com/93121277/164392971-fff0db97-ab54-46a0-b848-f1817cf809c0.png)

![102](https://user-images.githubusercontent.com/93121277/164392981-7923627e-d58d-456e-9e3c-7b7156c8670f.png)

![103](https://user-images.githubusercontent.com/93121277/164393076-30c09c38-b7c6-421e-a594-b1832a3366bb.png)

![104](https://user-images.githubusercontent.com/93121277/164393103-a013dc04-131b-4562-9d7e-5cef11f55578.png)

![105](https://user-images.githubusercontent.com/93121277/164393126-386a3ec9-cdcf-47c5-9fd7-3c3c606a07e3.png)

![106](https://user-images.githubusercontent.com/93121277/164393147-a19c5ec6-f520-47ff-9e08-261d51ad7a60.png)

![107](https://user-images.githubusercontent.com/93121277/164393159-8984a496-79e7-4ea9-9c11-b3bd59108ef9.png)

![108](https://user-images.githubusercontent.com/93121277/164393172-8c0a6b10-d88f-4e12-b861-b4758be311c3.png)

![110](https://user-images.githubusercontent.com/93121277/164393191-653d1f51-537f-472b-8a6b-a2e111e4b7a4.png)

![111](https://user-images.githubusercontent.com/93121277/164393198-b0711c69-c521-4c37-9080-f13e8b05c0f6.png)

![112](https://user-images.githubusercontent.com/93121277/164393216-52acb8db-8930-4d9c-aacd-711fcc497bfe.png)






