 # ✒️SRA-RNAseq


My Guthub repo include pipelines for running Pre-processing methods such as Trimming, quality control and pseudoalignment on [SRA]( https://www.ncbi.nlm.nih.gov/sra) fastq files using [Trimmomatic](https://github.com/usadellab/Trimmomatic), [fastQC](https://github.com/s-andrews/FastQC) and [Kallisto](https://github.com/pachterlab/kallisto) tools respectively .
All the pipelines are written 
using the [Workflow Description Language (WDL)](https://github.com/openwdl/wdl) and can be executed using 
[Cromwell](https://github.com/broadinstitute/cromwell) and [Docker](https://www.docker.com/). 




### ⚙️Technologies & Tools


![](https://img.shields.io/badge/OS-Linux-informational?style=flat&logo=<#FF6000>&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/Shell-Bash-informational?style=flat&logo=<#FF6000>&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/Code-JavaScript-informational?style=flat&logo=<#FF6000>&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/Tools-Docker-informational?style=flat&logo=<LOGO_NAME>&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/Tools-Cromwell-informational?style=flat&logo=<LOGO_NAME>&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/Tools-SRAtoolkit-informational?style=flat&logo=<LOGO_NAME>&logoColor=white&color=2bbc8a)


### 🔗 Quick Start

#### SRA fastq files download
* Install [SRAtoolkit](http://www.sthda.com/english/wiki/install-sra-toolkit)
* Run the following command to download SRA fastq files in parallel. The list.txt includes SRA ids. 

```bash
parallel --jobs n "fastq-dump --split-files --skip-technical -B --gzip {}" :::: list.txt
```


#### Running Trim-QC & Kallisto pipeline in WDL format
* Install [JAVA](https://www.java.com/en/download/), and [Cromwell](https://github.com/broadinstitute/cromwell) 
* Build [Docker](https://www.docker.com/) images for [Trimmomatic](https://github.com/usadellab/Trimmomatic), [fastQC](https://github.com/s-andrews/FastQC) and [Kallisto](https://github.com/pachterlab/kallisto) 
* For running Kallisto.wdl you also need to build an **index** from a FASTA formatted file of target sequences using [Kallisto](https://github.com/pachterlab/kallisto) and name it under **gencode.idx**. 
* Run the workflow directly by executing the following commands on your terminal:

```bash
java -Dconfig.file=application.conf -jar cromwell-55.jar run Trim-QC.wdl -i Trim-QC.json
```
```bash
java -Dconfig.file=application.conf -jar cromwell-55.jar run Kallisto.wdl -i Kallisto.json
```
 
 
