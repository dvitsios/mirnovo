mirnovo - Standalone version Tutorial
==================
### (Web version is available here): [http://wwwdev.ebi.ac.uk/enright-dev/mirnovo/index.php](http://wwwdev.ebi.ac.uk/enright-dev/mirnovo/index.php)


## 1. Installation
 1. Download mirnovo_pkg (.tar.gz file) from either Linux or MACOSX folder (depending on the OS on your machine). 
 2. Untar pkg: tar xvzf mirnovo_pkg_[linux|macosx].tar.gz
 3. cd mirnovo_pkg_[linux|macosx]

#### Dependencies
- Python (tested with v2.7.10)
- Perl (tested with v5.24.1)
- R (tested with v3.2.2)
	required libraries: png, ROCR, randomForest 
- Unix utilities: wget, gunzip, tar, convert (pre-installed in most distributions).




## 2. Configuration
**_[Important Note]:_** mirnovo comes with no pre-installed training models and/or genomes.

You need to download at least one training model (and optionally a genome) prior to run.

For more info see details below:

	4. Download / Install reference genome
	5. Download Training models 




## 3. Run
**_[Important Note - 1]:_**
you need to call mirnovo.pl from inside the `bin/` directory.

**_[Important Note - 2]:_**
You should not merge multiple files together prior to mirnovo's analysis. **Each file should be analysed separately!** 

This is due to the fact that clustering steps' efficiency (which are part of the mirnovo pipeline) may decrease as the sequence complexity of a sample becomes higher (i.e. when the number of unique sequence variants grows significantly). 
Please refer to the **Parameter specification** section of [mirnovo’s paper](https://academic.oup.com/nar/article/4210935/Mirnovo-genome-free-prediction-of-microRNAs-from) for more information.


Output is stored under `tmp/` directory. A custom output sub-dir name may be defined using the `-o` option.

##### - Basic example run:
```
 cd bin 
 ./mirnovo.pl -i ../example_file.tallied.gz -g hsa -t hsa -o example_run 
```


##### - Example run without a reference genome (`-g NA` option):
```
 ./mirnovo.pl -i ../example_file.tallied.gz -g NA -t hsa -o example_run
```


##### - Example run without generating pdf files with coverage profiles and hairpins (`--disable-pdf` option):
(allows for faster execution time, especially for large files):
```
 ./mirnovo.pl -i ../example_file.tallied.gz -g hsa -t hsa -o example_run --disable-pdf
``` 





## 4. Download / Install reference genome
```
 cd bin
 ./download_genome.pl [genome_id]
```

e.g.: `./download_genome.pl dme`

For more info see: http://wwwdev.ebi.ac.uk/enright-dev/mirnovo-standalone-pkg/Genome-Annotation-1.0

(see _README_ file).





## 5. Download Training models
```
 cd bin
 ./download_training_model.pl [model_id]
```

e.g.: `./download_training_model.pl universal_animals`

All trained models are available here: 
http://wwwdev.ebi.ac.uk/enright-dev/mirnovo-standalone-pkg/Training-Models-1.0





## 6. miRNA quantification (known/novel) with [Chimira](http://wwwdev.ebi.ac.uk/enright-dev/chimira/).

[Mirnovo](http://wwwdev.ebi.ac.uk/enright-dev/mirnovo/) is able to predict both hairpins and mature miRNAs, providing count data in the latter case. 

However, inherent sequence clustering steps (initial and refined) of the mirnovo pipeline may be imperfect in some cases and thus affect, even at a low level, the yielded expression data. 

Thus, in order to extract even more accurate expression data we have expanded [chimira](http://wwwdev.ebi.ac.uk/enright-dev/chimira/), a method that was previously published in our lab ([Vitsios & Enright, Bioinformatics, 2015](https://academic.oup.com/bioinformatics/article-lookup/doi/10.1093/bioinformatics/btv380)). 

In that case, [chimira](http://wwwdev.ebi.ac.uk/enright-dev/chimira/) serves as a mirnovo extension, allowing the user to upload a custom set of hairpin sequences (e.g. known and/or novel hairpins predicted by mirnovo) and then align their input files against this reference set to get mature miRNA expression counts. 

All uploaded reference files are merged and sequences with an alignment identity over 0.90 are collapsed. As an additional functionality, [chimira](http://wwwdev.ebi.ac.uk/enright-dev/chimira/) is able to generate coverage profiles of each identified mature miRNA and the secondary structure of the corresponding hairpin reference hit.






### Precomplied binaries (_from third parties_) are provided with the tool, for mac os and linux platforms: 
```vsearch, muscle, blastn, blastall, fasta_formatter, cdhit, bowtie2, twoBitToFa, twoBitInfo, faToTwoBit, RNAfold, RNAplot.```  


---
If you use mirnovo for your research, please kindly cite the following paper: 

["Mirnovo: genome-free prediction of microRNAs from small RNA sequencing data and single-cells using decision forests"](https://academic.oup.com/nar/article/4210935/Mirnovo-genome-free-prediction-of-microRNAs-from)

DM Vitsios, E Kentepozidou, L Quintais, E Benito-Gutiérrez, S van Dongen, MP Davis and AJ Enright. 

**Nucleic Acids Research** (2017), doi: [https://doi.org/10.1093/nar/gkx836](https://doi.org/10.1093/nar/gkx836)
