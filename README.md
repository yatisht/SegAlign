# SegAlign 

A Scalable GPU System for Pairwise Whole Genome Alignments

## Table of Contents

- [Overview](#overview)
- [Dependencies](#dependencies)
- [How to run SegAlign](#run)
    - [Running a test](#test)

## <a name="overview"></a> Overview

The system has been tested on all the AWS G3 and P3 GPU instances with AMI Ubuntu Server 18.04 LTS (HVM), SSD Volume Type (ami-0fc20dd1da406780b (64-bit x86))

* Clone SegAlign repository (https://github.com/gsneha26/SegAlign)

```
    $ git clone https://github.com/gsneha26/SegAlign.git
    $ export PROJECT_DIR=$PWD/SegAlign
```

## <a name="dependencies"></a> Dependencies
The following dependencies are required by SegAlign:
  * zlib1g-dev
  * libboost-all-dev
  * CMake 3.8
  * parallel
  * NVIDIA CUDA 10.2 toolkit
  * LASTZ 1.04.03
  * faToTwoBit, twoBitToFa (from kentUtils)
  * Intel TBB library

The dependencies can be installed with the given script as follows (this might take a while): 

```
    $ cd $PROJECT_DIR
    $ ./scripts/installUbuntu.sh
```

## <a name="run"></a> How to run SegAlign
* Run SegAlign

```
    $ run_segalign target query [options]
```

* For a list of options 

```
    $ run_segalign --help
```

### <a name="test"></a> Running a test

```
    $ cd $PROJECT_DIR
    $ mkdir test
    $ cd test
    $ wget https://hgdownload.soe.ucsc.edu/goldenPath/ce11/bigZips/ce11.2bit
    $ wget https://hgdownload-test.gi.ucsc.edu/goldenPath/cb4/bigZips/cb4.2bit 
    $ twoBitToFa ce11.2bit ce11.fa
    $ twoBitToFa cb4.2bit cb4.fa
    $ run_segalign ce11.fa cb4.fa > ce11.cb4.maf
```
