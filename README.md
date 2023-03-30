## Hybrid workflow for species identification and antibiotic resistance determination

### Description
A galaxy workflow for hybrid assembly, species identification and antibiotic resistance determination created by Justin Iking, Mirela Minkova, Yorick Doornbos and Lonneke Willems. As shown in the flowchart below, the workflow uses two separate input files; ONT long read data and Illumina short read data (both R1 and R2). The data then goes through a quality control step both before and after trimming, followed by an assembly of the data in Unicycler. The Unicycler output is then processed further through Busco, Prokka, StarAMR, Bandage, Quast and Kraken2. To uncover pan-genomes, the Prokka output is then loaded into Roary and visualised with Phandango.  

![alt text](https://github.com/LonnekeW/Hybrid_Galaxy_Workflow/blob/main/images/flowchart.png "Workflow Flowchart")

### Workflow Tools
| **Tool**        | **Input**                     | **Description**     |
| :---            | :---                          | :---                |
| FastQC          | Short or long read data       | Filters by quality  |
| Nanoplot        | ONT data                      | Filters by quality  |
| MultiQC         | Illumina or ONT data          | Filters by quality  |
| Unicycler       | ONT and Illumina data         | Assembles           |
| Busco           |                               |                     |
| Prokka          |                               |                     |
| Roary           |                               |                     |
| StarAMR         |                               |                     |
| Bandage         |                               |                     |
| Quast           |                               |                     |
| Kraken2         |                               |                     |
| Krona           |                               |                     | <br>

### Visualizing core and pan genomes
Roary output in phandango.net
