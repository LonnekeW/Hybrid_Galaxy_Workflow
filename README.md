## Hybrid workflow for species identification and antibiotic resistance determination

### Description
A galaxy workflow for hybrid assembly, species identification and antibiotic resistance determination created by Justin Iking, Mirela Minkova, Yorick Doornbos and Lonneke Willems. As shown in the flowchart below, the workflow uses two separate input files; ONT long read data and Illumina short read data (both R1 and R2). The data then goes through a quality control step both before and after trimming, followed by an assembly of the data in Unicycler. The Unicycler output is then processed further through Busco, Prokka, StarAMR, Bandage, Quast and Kraken2. To uncover pan-genomes, the Prokka output is then loaded into Roary and visualised with Phandango.  

![alt text](https://github.com/LonnekeW/Hybrid_Galaxy_Workflow/blob/main/images/flowchart.png "Workflow Flowchart")

### Workflow Tools
| **Tool**        | **Input**                              | **Description**                                                           |
| :---            | :---                                   | :---                                                                      |
| FastQC          | Short read data                        | Filters paired-end short read data by quality. Note: In order to compare the short read to the long read data in the workflow, both files will be entered in FastQC before the files are transferred to MultiQC.                  |
| Nanoplot        | Long read data                         | Filters long read data by quality.                                        |
| MultiQC         | Output of FastQC                       | Summarizes the output of FastQC in a single report.                       |
| Trimmomatic     | Short read data                        | Trims both paired-end and single ended illumina short read data.          |
| Flitlong        | Long read data                         | Tims long read data by quality.                                           |
| Unicycler       | Output of Trimmomatic and Flitlong     | Assembles bacterial genomes. For best results in the hybrid assembly, both the short and long read data will be loaded into the tool simultaneously.                                                                                 |
| Busco           |                               |                     |
| Prokka          |                               |                     |
| StarAMR         |                               |                     |
| Bandage         |                               |                     |
| Quast           |                               |                     |
| Kraken2         |                               |                     |
| Krona           |                               |                     | <br>

### Visualising core and pan genomes
Roary output in phandango.net
