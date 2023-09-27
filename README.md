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




