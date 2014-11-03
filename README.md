cosmic_vcf_hg19
===============

Simple commandline statements to create MuTect compatible cosmic vcf

While using MuTect for my exome sequencing analysis I ran into this issue of finding a comaptible COSMIC vcf file particularly for hg19 with all the coding mutations.

I was able to download the file from Sanger's website : http://cancer.sanger.ac.uk/files/cosmic/current_release/VCF/CosmicCodingMuts.vcf.gz
However the file didn't have 'chr' before each chromosome number which was required by the hg19 format.

Based on searches on various forums I was able to put together two simple statements to produce a cosmic vcf compatible with hg19 and MuTect

##Requirements:

1. Linux commandline
2. VCFtools (http://sourceforge.net/projects/vcftools/files/)

##Code:

First step is to add chr to non-chr contigs containing vcf
```
awk '{if($0 !~ /^#/) print "chr"$0; else print $0}' no_chr_cosmic.vcf > with_chr_cosmic.vcf
```

Second step is to sort the file
```
# -c, --chromosomal-order option for the natural order of chromosomes (1,2,10,MT,X)
cat with_chr_cosmic.vcf | vcf-sort -c > sorted_cosmic_hg19.vcf
```
