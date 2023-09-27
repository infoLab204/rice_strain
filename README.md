# Rice_strain : A method of identifying false positives in the strain-specific variant calling of rice    
### Sunhee Kim and Chang-Yong Lee    
The rice_strain represents Python scripts that analyze the variants called using different variant calling models to propose a method for finding false positive variants using purebred and non-purebred samples of two strains in rice.    

We compared the performance of different variant calling models by constructing confusion matrices using the sets of variants called by different models. The constructed confusion matrices were evaluated in three different metrics: precision, recall, and F1 score. Based on the results of the performance comparison, we proposed a method to construct the dbFP, which is a collection of false positive variants. We showed that the dbFP identified the false positives from the called variants. The validity of the proposed dbFP was tested against the dbSNP and non-negligible false positives were found. We have provided the Python scripts with datasets for the readers to reproduce the results discussed in the manuscript.    

## Data sets
1.	Reference sequences of Japonica and Indica
    - Nipponbare reference genome (IRGSP 1.0) : https://www.ebi.ac.uk/ena/browser/view/GCA_001433935.1
    - Indica reference genome (ASM465v1) : https://www.ebi.ac.uk/ena/browser/view/GCA_000004655.2
2.	The dbSNP of Japonica and Indica
    - Japonica dbSNP : https://ftp.ensemblgenomes.ebi.ac.uk/pub/plants/release-57/variation/vcf/oryza_sativa/oryza_sativa.vcf.gz
    - Indica dbSNP: https://ftp.ensemblgenomes.ebi.ac.uk/pub/plants/release-57/variation/vcf/oryza_indica/oryza_indica.vcf.gz
3. 	The purebred samples of Japonica and Indica, or the non-purebred samples of Japonica and Indica
    - https://www.ebi.ac.uk/biosamples/samples/SAMEG4750728
4. Gene annotation
    - Japonica gene annotation : https://ftp.ensemblgenomes.ebi.ac.uk/pub/plants/release-57/gff3/oryza_sativa/Oryza_sativa.IRGSP-1.0.57.chr.gff3.gz
    - Indica gene annotation  : https://ftp.ensemblgenomes.ebi.ac.uk/pub/plants/release-57/gff3/oryza_indica/Oryza_indica.ASM465v1.57.chr.gff3.gz
6.	VCF files
    - The result of variants calling with the Japonica reference :
    - The result of variants calling with the Indica reference : 


## Python scripts for analyzing variant calling results
1. Python scripts for constructing the confusion matrix and evaluating performance metrics    
    ```
   rice_strain.confusion_matrix( “actual sample variants”, “predicted sample variants”)
    ```
   (eg) rice_strain.confusion_matrix(“japonica_variants.vcf”, “mixed_indica25_variants.vcf”)

2. Python scripts for constructing the dbFP and identifying false positives    
    ```
    rice_strain.dbFP( “pure samples variants”)
    ```
    (eg) rice_strain.dfFP (“pureindica_purejaponica_variants vcf”)

3. Python scripts for estimating error rates of dbSNP     
    ```
    rice_strain.error_rate( “sample_name”, “reference”, “name of database”)
    ```
    (eg) rice_strain.error_rate("RWG-006","IRGSP-1.0_genome.fasta","oryza_sativa.vcf")
