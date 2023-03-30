## Hybrid workflow for species identification and antibiotic resistance determination

### Description
A galaxy workflow for hybrid assembly, species identification and antibiotic resistance determination.

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
| Krona           |                               |                     |

### Visualizing core and pan genomes
Roary output in phandango.net
