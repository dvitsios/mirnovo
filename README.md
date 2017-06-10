mirnovo - Tutorial
==================


## 1. Installation
 1. Download mirnovo_pkg (.tar.gz file) from either Linux or MACOSX folder (depending on the OS on your machine). 
 2. Untar pkg: tar xvzf mirnovo_pkg_[linux|macosx].tar.gz
 3. cd mirnovo_pkg_[linux|macosx]

### Dependencies
- Python (tested with v2.7.10)
- Perl (tested with v5.24.1)
- R (tested with v3.2.2)
	required libraries: png, ROCR, randomForest 
- Unix utilities: wget, gunzip, tar, convert (pre-installed in most distributions).




## 2. Configuration
_[!] mirnovo comes with no pre-installed training models and/or genomes [!]_

You need to download at least one training model (and optionally a genome) prior to run.

For more info see details below:

	- Download / Install reference genome
	- Download Training models 




## 3. Run
_[Important Note]:_
you need to call mirnovo.pl from inside the `bin/` directory!

Output is stored under `tmp/` directory. A custom output sub-dir name may be defined using the `-o` option.

##### - Basic example run:
```
 cd bin 
 ./mirnovo.pl -i ../example_file.tallied.gz -g hsa -t hsa -o example_run 
```


##### - Example run without a reference genome (-g NA option):
```
 ./mirnovo.pl -i ../example_file.tallied.gz -g NA -t hsa -o example_run
```


##### - Example run without generating pdf files with coverage profiles and hairpins (--disable-pdf option):
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

For more info check: http://wwwdev.ebi.ac.uk/enright-dev/mirnovo-standalone-pkg/Genome-Annotation-1.0

(see _README_ file).





## 5. Download Training models
```
 cd bin
 ./download_training_model.pl [model_id]
```

e.g.: `./download_training_model.pl universal_animals`

All trained models are available here: 
http://wwwdev.ebi.ac.uk/enright-dev/mirnovo-standalone-pkg/Training-Models-1.0





### Precomplied binaries are provided with the tool, for mac os and linux platforms: 
vsearch, muscle, blastn, blastall, fasta_formatter, cdhit, bowtie2, twoBitToFa, twoBitInfo, faToTwoBit, RNAfold, RNAplot.  
