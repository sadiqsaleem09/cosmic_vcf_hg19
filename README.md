cosmic_vcf_hg19
===============

Simple commandline scripts to create MuTect compatible cosmic vcf

While using MuTect I ran into this issue of finding a comaptible COSMIC vcf file particularly for hg19.

I was able to download the file from Sanger's website : http://cancer.sanger.ac.uk/files/cosmic/current_release/VCF/CosmicCodingMuts.vcf.gz
However the file didn't have 'chr' before each chromosome number which was required by the hg19 format.

Based on searches on various forums I was able to put together two simple statements to produce a cosmic vcf compatible with hg19 and MuTect

Requirements:

1. Linux commandline
2. VCFtools (http://sourceforge.net/projects/vcftools/files/)
