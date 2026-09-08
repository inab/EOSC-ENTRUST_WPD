# EOSC-ENTRUST WP19-20-21 Workflow Processing Demonstrator

This repository describes a demonstration scenario to reproduce, using WfExS, the execution both of a test workflow execution and a whole variant calling analysis using Sarek within a TES job submitted to a properly deployed funnel TES service.

It also includes both the TES jobs used, as well as almost intact funnel configuration files.

All the needed contents are available online:

* Workflow Run RO-Crate of the test hello workflow => https://doi.org/10.5281/zenodo.22640966

* Workflow Run RO-Crate of the Sarek nf-core workflow => https://doi.org/10.5281/zenodo.21134855

* Pre-populated WfExS caches with the shared datasets needed by the workflow, as well as the configuration files => https://doi.org/10.5281/zenodo.22641326
  * The minimal configuration files needed for the demonstration deployment within a containerised environment ([wfexs_min_config.tar.gz](https://zenodo.org/records/22641326/files/wfexs_min_config-20260831.tar.gz?download=1)).

  * The pre-populated side caches needed for the demonstration deployment within an isolated environment ([wfexs_side_caches.tar.gz](https://zenodo.org/records/22641326/files/wfexs_side_caches-20260831.tar.gz?download=1)).

  * The pre-populated dataset caches needed for the demonstration deployment within an isolated environment when either https://zenodo.org/records/21134855 or https://zenodo.org/records/22640966 WRROCs are used as the starting point ([wfexs_prepopulated_cache.tar.gz](https://zenodo.org/records/22641326/files/wfexs_prepopulated_cache-20260907.tar.gz?download=1)).

* Test input files (paired-end normal and tumour samples):
  * [s3://ngi-igenomes/test-data/sarek/SRR7890919_WES_HCC1395BL-EA_normal_1.fastq.gz](https://ngi-igenomes.s3.amazonaws.com/test-data/sarek/SRR7890919_WES_HCC1395BL-EA_normal_1.fastq.gz)
  * [s3://ngi-igenomes/test-data/sarek/SRR7890919_WES_HCC1395BL-EA_normal_2.fastq.gz](https://ngi-igenomes.s3.amazonaws.com/test-data/sarek/SRR7890919_WES_HCC1395BL-EA_normal_2.fastq.gz)
  * [s3://ngi-igenomes/test-data/sarek/SRR7890918_WES_HCC1395-EA_tumor_1.fastq.gz](https://ngi-igenomes.s3.amazonaws.com/test-data/sarek/SRR7890918_WES_HCC1395-EA_tumor_1.fastq.gz)
  * [s3://ngi-igenomes/test-data/sarek/SRR7890918_WES_HCC1395-EA_tumor_2.fastq.gz](https://ngi-igenomes.s3.amazonaws.com/test-data/sarek/SRR7890918_WES_HCC1395-EA_tumor_2.fastq.gz)

## Scenario: isolated TES service with no shared WfExS cache directories:

This scenario is one of the most secured ones, but it requires to include as input both the workflow RO-Crate and each of the prepared WfExS cache and configuration archives.

The used funnel configuration file is [funnel_wfexs-docker-privileged_v4_rw_cache.yaml](setup_scenarios/default_config/funnel-configs/funnel_wfexs-docker-privileged_v4_rw_cache.yaml) for a singularity within docker approach.

## Scenario: hidden shared WfExS cache directories within the TES service:

This scenario internally hardcodes both the WfExS configuration files and cache directories, as well as the parent working directories.

The used funnel configuration file is [funnel_wfexs-docker-privileged_v3_rw_cache.yaml](setup_scenarios/hidden_shared_config/funnel-configs/funnel_wfexs-docker-privileged_v3_rw_cache.yaml) for a singularity within docker approach.
