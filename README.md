# FiLTR
[![GitHub](https://img.shields.io/badge/python-3-blue)](https://www.python.org/)
[![GitHub](https://img.shields.io/badge/license-GPL--3.0-green)](https://github.com/CSU-KangHu/FiLTR/blob/master/LICENSE)
[![Conda](https://img.shields.io/badge/Conda-support-yellow)](https://docs.conda.io/en/latest/)

## Table of Contents
- [Installation](#install)
- [Demo data](#demo)
- [Experiment reproduction](#reproduction)
- [Usage](#cmd)

## <a name="install"></a>Installation
### System Requirements
Recommended Hardware requirements: 40 CPU processors, 128 GB RAM.

Recommended OS: (Ubuntu 16.04, CentOS 7, etc.)

### <a name="install_conda"></a>Option 1. Run with Conda
```sh 
git clone https://github.com/CSU-KangHu/FiLTR.git ## Alternatively, you can download the zip file directly from the repository.

# compile and make LtrDetector
cd FiLTR/bin/LtrDetector/src && rm -rf ../bin && make bin && make tr -j


cd FiLTR
chmod +x tools/*

conda install mamba -c conda-forge
# Find the **yml** file in the project directory and run
mamba env create --name FiLTR -f environment.yml
conda activate FiLTR
```

## <a name="demo"></a>Demo data

Please refer to [demo](/demo) for the demo data to play with:
* _genome.fa_: demo sequences of the genome assembly.
```sh
# Inputs: 
#       --genome: The input genome assembly.
#       --outdir: The output directory.
#       --thread: The thread number used in FiLTR.
# Outputs: 
#       confident_ltr.fa: The LTR library.
python ${pathTo}/FiLTR/main.py \
 --genome ${pathTo}/FiLTR/demo/genome.fa \
 --out_dir ${outdir} \
 --thread ${threads_num}
 # e.g., my command: 
 # python /home/hukang/FiLTR/main.py \
 # --genome /home/hukang/FiLTR/demo/genome.fa \
 # --out_dir /home/hukang/FiLTR/demo/test \
 # --thread 40
```
Add `> log.txt 2>&1 &` at the end of the command to run it in the background.

## <a name="reproduction"></a>Experiment reproduction

All experimental results in the manuscript of FiLTR can be reproduced step by step through [Experiment reproduction](https://github.com/CSU-KangHu/FiLTR/wiki/Experiment-reproduction).

## <a name="cmd"></a>Usage
```shell
usage: main.py [-h] --genome genome --out_dir output_dir [--thread thread_num] [--miu miu] [--skip_detect skip_detect] [--debug is_debug] [--recover is_recover] [--BM_RM2 BM_RM2] [--BM_EDTA BM_EDTA]
               [--BM_HiTE BM_HiTE] [--EDTA_home EDTA_home] [--species species]

########################## FiLTR, version 0.0.1 ##########################

optional arguments:
  -h, --help            show this help message and exit
  --genome genome       Input genome assembly path
  --out_dir output_dir  The path of output directory; It is recommended to use a new directory to avoid automatic deletion of important files.
  --thread thread_num   Input thread num, default = [ 40 ]
  --miu miu             The neutral mutation rate (per bp per ya), default = [ 1.3e-08 ]
  --skip_detect skip_detect
                        Whether to skip_HybridLTR, 1: true, 0: false. default = [ 0 ]
  --debug is_debug      Open debug mode, and temporary files will be kept, 1: true, 0: false. default = [ 0 ]
  --recover is_recover  Whether to enable recovery mode to avoid starting from the beginning, 1: true, 0: false. default = [ 0 ]
  --BM_RM2 BM_RM2       Whether to conduct benchmarking of RepeatModeler2, 1: true, 0: false. default = [ 0 ]
  --BM_EDTA BM_EDTA     Whether to conduct benchmarking of EDTA, 1: true, 0: false. default = [ 0 ]
  --BM_HiTE BM_HiTE     Whether to conduct benchmarking of HiTE, 1: true, 0: false. default = [ 0 ]
  --EDTA_home EDTA_home
                        When conducting benchmarking of EDTA, you will be asked to input EDTA home path.
  --species species     Which species you want to conduct benchmarking.
```

## Citations
Please cite our paper if you find `FiLTR` useful:

Hu, K., Xu, M., Gao, X. & Wang, J.✉ (2024). FiLTR: An accurate tool for identification of long terminal repeat retrotransposons using deep learning and boundary detection on flanking matrix. <!-- [bioRxiv](https://doi.org/10.1101/2024.01.21.576519). -->
