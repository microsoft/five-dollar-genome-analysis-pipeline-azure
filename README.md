# Germline alignment and variant calling pipeline on Azure
**This repository has been deprecated in favor of https://github.com/microsoft/gatk4-genome-processing-pipeline-azure**

This repository is an example of running the germline alignment and variant calling pipeline, based on [Best Practices Genome Analysis Pipeline by Broad Institute of MIT and Harvard](https://software.broadinstitute.org/gatk/best-practices/workflow?id=11165), on Cromwell on Azure.<br/> 

Learn more about using Azure for your Cromwell WDL workflows on our GitHub repo! - [Cromwell on Azure](https://github.com/microsoft/CromwellOnAzure).<br/>

This repository is a fork from [the original](https://github.com/gatk-workflows/five-dollar-genome-analysis-pipeline) and has all the required changes to run the WDL workflow on Cromwell on Azure.<br/>

Here, you can find the WDL file and an example inputs JSON file with links to data hosted on a public Azure Storage account. You can use the "datasettestinputs" storage account directly as a relative path, like in the inputs JSON file. 

The `WholeGenomeGermlineSingleSample.hg38.trigger.json` trigger file is ready to use. You can start the workflow on your instance of Cromwell on Azure, using [these instructions](https://github.com/microsoft/CromwellOnAzure/blob/master/docs/managing-your-workflow.md/#Start-your-workflow).

## five-dollar-genome-analysis-pipeline
Workflows used for germline short variant discovery in WGS data

### germline_single_sample_workflow :
This WDL pipeline implements data pre-processing and initial variant calling (GVCF
generation) according to the GATK Best Practices (June 2016) for germline SNP and
Indel discovery in human whole-genome sequencing data.

#### Requirements/expectations
- Human whole-genome paired-end sequencing data in unmapped BAM (uBAM) format
- One or more read groups, one per uBAM file, all belonging to a single sample (SM)
- Input uBAM files must additionally comply with the following requirements:
    * filenames all have the same suffix (we use ".unmapped.bam")
    * files must pass validation by ValidateSamFile
    * reads are provided in query-sorted order
    * all reads must have an RG tag
- Reference genome must be Hg38 with ALT contigs

#### Outputs 
- Cram, cram index, and cram md5 
- GVCF and its gvcf index 
- BQSR Report
- Several Summary Metrics 

### Software version requirements :
- GATK 4.0.10.1
- Picard 2.16.0-SNAPSHOT
- Samtools 1.3.1
- Python 2.7
- Cromwell version support 
  - Successfully tested on v37
  - Does not work on versions < v23 due to output syntax

### Important Note :
- The provided JSON is meant to be a ready to use example JSON template of the workflow. It is the user’s responsibility to correctly set the reference and resource input variables using the [GATK Tool and Tutorial Documentations](https://software.broadinstitute.org/gatk/documentation/).
- Please visit the [User Guide](https://software.broadinstitute.org/gatk/documentation/) site for further documentation on our workflows and tools.

### LICENSING :
Copyright Broad Institute, 2019 | BSD-3
This script is released under the WDL open source code license (BSD-3) (full license text at https://github.com/openwdl/wdl/blob/master/LICENSE). Note however that the programs it calls may be subject to different licenses. Users are responsible for checking that they are authorized to run all programs before running this script.
- [GATK](https://software.broadinstitute.org/gatk/download/licensing.php)
- [BWA](http://bio-bwa.sourceforge.net/bwa.shtml#13)
- [Picard](https://broadinstitute.github.io/picard/)
- [Samtools](http://www.htslib.org/terms/)
