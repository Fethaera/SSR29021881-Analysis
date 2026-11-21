# Bacterial Genomics & Plasmid Screening: SRA Run `SRR29021881`

## Overview
A single-isolate microbial genomics workflow investigating **SRA accession `SRR29021881`** (organism/source: [Illumina paired-end whole genome sequencing of healthcare-associated infection isolates (SRR29021881)](https://trace.ncbi.nlm.nih.gov/Traces/index.html?view=run_browser&acc=SRR29021881&display=metadata)

The goal of this analysis is to evaluate assembly quality, identify candidate plasmid sequences, annotate genomic features, and screen for antimicrobial resistance (AMR) determinants and virulence/stress factors—interpreting what these findings imply for potential horizontal gene transfer and phenotype.

---

## Repository Structure
```text
SSR29021881-Analysis/
├── README.md                 # Project summary, findings, and limitations
├── notebooks/                # Analysis notebook(s) (e.g., Google Colab / Jupyter)
├── results/                  # Summary tables, QC metrics, AMR/plasmid outputs
└── scripts/                  # Helper scripts (if any)
```

---

## Workflow Summary
1. **Data Retrieval & Read QC:** Fetched raw reads for `SRR29021881` from NCBI SRA/ENA, assessed read quality, and trimmed adapters/low-quality bases through the use of [fastp](https://github.com/OpenGene/fastp)
2. ***De Novo* Assembly & Quality Check:** Assembled reads into contigs using [Shovill](https://github.com/tseemann/shovill) and evaluated assembly metrics through [quast](https://github.com/ablab/quast)
3. **Plasmid Identification:** Detected plasmid-associated contigs/replicons using [PlasmidFinder](https://github.com/genomicepidemiology/plasmidfinder/tree/master)
4. **Genome Annotation:** Annotated coding sequences (CDS), RNAs, and functional features through the use of [bakta](https://github.com/oschwengers/bakta) 

---

## Key Findings

### 1. Assembly & Taxonomic Check
| Metric                         | Value                | Notes                                          |
| :----------------------------- | :------------------- | :--------------------------------------------- |
| **Organism (SRA / Confirmed)** | Neisseria Meningitis | 97.80% match                                   |
| **Total Assembly Length**      | 2.2MB                | *<Compare to typical genome size for species>* |
| **Number of Contigs**          | 217                  | *<Note count of short vs. longer contigs>*     |
| **N50**                        | 44190 BP             | *<Contiguity summary>*                         |
| **GC Content (%)**             | 51.7%                | *<Expected range for taxon>*                   |

### 2. Plasmid & AMR / Virulence Highlights
* **Plasmid Contigs / Replicons:** No plasmid contigs were found which is expected of that from Neisseria Meningitis


---

## Limitations & Caveats
* **Short-read assembly constraints:** Short reads often fragment repetitive regions, insertion sequences, and plasmids across multiple contigs, meaning plasmid boundary assignment is provisional without long-read or hybrid assembly.
* **Database & threshold dependence:** Gene detection depends on reference database completeness (e.g., NCBI/CARD/VFDB) and alignment identity/coverage cutoffs; presence of a gene does not automatically prove phenotypic resistance or expression levels.
* **Execution environment:** Notebook setup steps are tailored for Google Colab and may require environment adjustments depending on package versions.

---

## Potential Next Steps (If Re-opened)
* Compare `SRR29021881` against closely related public isolates/reference genomes to place it in a broader phylogenetic or epidemiological context.
* Combine short reads with long reads (e.g., Oxford Nanopore) to resolve complete plasmid structures and flanking mobile genetic elements.
