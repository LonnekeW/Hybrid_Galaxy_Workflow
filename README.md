## Hybrid workflow for species identification and antibiotic resistance determination

### Description
A galaxy workflow for hybrid assembly, species identification and antibiotic resistance determination. As shown in the flowchart below, the workflow uses two separate input files: ONT long read data and Illumina short read data (both R1 and R2). The data then goes through a quality control step both before and after trimming, followed by an assembly of the data in Unicycler. The Unicycler output is processed further through Busco, Prokka, Staramr, Bandage, Quast and Kraken2. To uncover the pan-genomes and infer phylogeny, the Prokka output is loaded into Roary and RAxML; the results of which can be visualized in Phandango. 

![alt text](https://github.com/LonnekeW/Hybrid_Galaxy_Workflow/blob/main/assets/flowchart.png "Workflow Flowchart")

### Installation
Retrieve the .ga directly from this GitHub, the file can then be imported into galaxy. Make sure to seperate out your short R1, R2 and long read data according to the instructions in the workflow before starting a run with new data.<br>

### Workflow Tools
| **Tool**        | **Input**                              | **Description**                                                           |
| :---            | :---                                   | :---                                                                      |
| FastQC          | Short read data                        | Filters paired-end short read data by quality. Note: In order to compare the short read to the long read data in the workflow, both files will be entered in FastQC before the files are transferred to MultiQC.                                |
| Nanoplot        | Long read data                         | Filters long read data by quality.                                        |
| MultiQC         | Output of FastQC                       | Summarizes the output of FastQC in a single report.                       |
| Trimmomatic     | Short read data                        | Trims both paired-end and single ended illumina short read data.          |
| Flitlong        | Long read data                         | Trims long read data by quality.                                          |
| Unicycler       | Output of Trimmomatic and Flitlong     | Assembles bacterial genomes. For best results in the hybrid assembly, both the short and long read data will be loaded into the tool simultaneously.                                                                                           |
| Busco           | FASTA output of Unicycler              | Evaluates the accuracy of the genome assembly and annotation.             |
| Staramr         | FASTA output of Unicycler              | Scans contigs against the antimicrobial resistance databases ResFinder, PlasmidFinder and Pointfinder.                                                                                                                                            |
| Bandage         | Final assembly graph of Unicycler      | Displays connections not available in contigs file.                       |
| Quast           | FASTA output of Unicycler              | Evaluates genome assembly.                                                |
| Prokka          | FASTA output of Unicyler               | Annotates prokaryotic genomes.                                            |
| Roary           | GFF output of Prokka                   | Creates list of core and pan genomes from Prokka output. Note: Roary needs multiple input files. The Roary input data is separated in the galaxy workflow, allowing for the tool to be run separately once Prokka annotation is complete.          |
| RAxML           | Output of Roary                        | Infers phylogeny using core gene SNPs.                                    |
| Kraken2         | FASTA output of Prokka                 | Assigns taxonomic labels to short DNA sequences.                          |
| Krona           | Taxonomy output of Kraken2             | Visualizes the results of Kraken2 in an interactive chart.                | <br>

### Visualising with Phandango
In order to visualise the phylogeneitc reconstruction, a few additional steps need to be taken:
1. Download the `gene_presence_absence.csv` output from Roary.
2. Download the `result.nhx` file from RAxML.
3. Rename the result's file extension to .tree.
4. Upload both files to http://phandango.net to visualise the results.
