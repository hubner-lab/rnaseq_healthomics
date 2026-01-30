# SNP‑Calling Pipeline 


## How to run the pipeline

```bash
# minimum setup to run with default parameters
nextflow run main.nf \
    --reference path/to/ref.fa \
    --sample_list path/to/samples.csv \
    --outdir result \
    -profile docker
````


```bash
# if all parameters set in nextflow.config
nextflow run main.nf \
    -profile docker
````

`samples.csv` **must** have a header with three columns:

```csv
name,path1,path2
SampleA,/data/ANY_NAME_A_R1.fastq.gz,/data/ANY_NAME_A_R2.fastq.gz
SampleB,/data/ANY_NAME_B_R1.fastq.gz,/data/ANY_NAME_B_R2.fastq.gz
```

## Tuning resources

All parameters (with defaults) live in [`nextflow.config`](nextflow.config):

| Parameter          | Default      | Description                                        |
| ------------------ | ------------ | -------------------------------------------------- |
| `reference`        | *none*       | Reference genome **FASTA**                         |
| `sample_list`      | *none*       | CSV table of samples                               |
| `outdir`           | `result`     | Output directory root                              |
| `output_prefix`    | `Test`       | Prefix for output files                            |
| `threads`          | `16`         | Threads for BWA‑MEM2, SAMtools, Tabix              |
| `threads_gatk`     | `1`          | Threads for GATK Java processes                    |
| `memory_low`       | `15G`        | RAM for light SAMtools/BWA tasks                   |
| `memory`           | `100G`       | RAM for most GATK tasks                            |
| `haplotype_memory` | `20G`        | RAM for **HaplotypeCaller**                        |
| `combine_memory`   | `200G`       | RAM for **CombineGVCFs**                           |
| `genotype_memory`  | `15G`        | RAM for **GenotypeGVCFs**                          |
| `intervals`        | `scaffold_1` | Optional interval(s) for GenotypeGVCFs (comma‑sep) |

