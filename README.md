# Extract
## 1. Install bcftools 
Clarification: Summaized from source: https://raw.githubusercontent.com/samtools/bcftools/develop/INSTALL

Use Git to clone the bcftools repository from GitHub:
```
git clone https://github.com/samtools/bcftools.git
```

If you don't have git function in your window or macOS, you do need to install it

Then navigate to the bcftools folder
```
cd bcftools
```
Build and Install Bcftools using 'make'
```
make
```
Verify the installation of bcftools
```
bcftools --version
```
Make sure your bcftools is in the path that can be execute in any directory

First make sure you are in the directory where bcftools.exe is located, then copy it to the path by using
```
#MacOs

sudo cp bcftools /usr/local/bin/bcftools/

#Window

export BCFTOOLS_PLUGINS=/path/to/bcftools/plugins
```

## 2. Extract variant of interest

For this section if the words is inside of <  > means that are the parameter that can be changed based on your data

Before extract the variant, first you can make a new directory to ensure your files are more organised. Make sure your vcf files also inside of that directory. 
```
#make directory
mkdir <Put a name for your folder>
cd <name of your folder>
```

To view your vcf file you can use
```
#See what is in header only
bcftools view --header-only <name of your vcf file> | -tail -n1

#See the whole files (sometimes is too big and not informative)
bcftools view <name of your vcf file>
```

Usually vcf file will have a standard format, for more info can look at https://samtools.github.io/hts-specs/VCFv4.1.pdf

It is very important to identify what is in the header of vcf file to ensure we extract the correct columns

To extract the variant, please ensure your vcf file is in .gz format and there are .csi file accompany inside the folder. If not can try:
```
#To compress your vcf file into .gz (zip file)
bgzip <name of your vcf file>
#To make .csi file (index file)
bcftools index <Name of your vcf file in .gz>
```

Before you extract out make a header of your files first according to the arrangement you saw in the header above and depend on what you want to extract
```
#I want my header to be CHROM,POS,REF,ALT,SAMPLE_ID_GENO and it will be saved in file named output.csv
echo "CHROM,POS,REF,ALT,SAMPLE_ID_GENO" > output.csv
```

Now the main business which is to extract the variant, at here i am extracting the CHROM,POS,REF,ALT and genotyping of all samples

To know more what info is present in vcf file can go to the pdf link I attached just now.
```
bcftools query -r <chromosome_number>:<starting_position>-<end_position> -f '%CHROM,%POS,%REF,%ALT[%GT]\n' <Name of your vcf file in .gz> >> output.csv
```

# Extract variants for SMPD1



