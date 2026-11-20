**Research Question:** 

"Does clinical isolate SRR29021881 represent a pure, uncontaminated Niesseria meningitis genome, and what sequence type (ST), antimicrobial resistance (AMR) determinants, and virulence factors define its pathogenic potential?"


```mermaid
flowchart LR
    A[Raw FASTQ<br/>SRR29021881] --> B[fastp & Falco<br/>Adapter/Q20 Trim]
    B --> C[Kraken2 & Bracken<br/>Taxonomic Purity]
    B --> D[SPAdes --isolate<br/>De Novo Assembly]
    D --> E[QUAST<br/>Assembly QC]
    D --> F[MLST & Abricate<br/>ST, AMR & Virulence]
```
