# microsynphylo

Perform phylogenetic analysis of genes in microsyntenic blocks using a user-friendly graphical interface.

## Installation

```bash
# Create and enter a new conda environment
conda create -n microsynphylo python=3.10 -c conda-forge -y
conda activate microsynphylo

#install the package
pip install microsynphylo

#install dependencies
conda install -c conda-forge -c bioconda mafft fasttree raxml-ng -y
```

## Launch the App

After installation, start the graphical interface by running:

```bash
microsynphylo
```

---

## Inputs

The app requires two inputs:

### 1. **Gene Block CSV File**

A CSV file where:
- **Each row** represents a **species**.
- **Each column** represents a **gene position** within a microsyntenic block.
- **Column headers** must indicate block and species identity using the format:
  - `"B0-GeneName"` — for **outgroup** species.
  - `"B1-GeneName"`, `"B2-GeneName"` etc. — for **ingroup** species.

Example headers:
```
B0-GeneX, B1-GeneA, B2-GeneB, B3-GeneC
```

### 2. **Orthologous Group Definitions**

Manually input orthology groups in the GUI:

- **Each line** defines one group.
- Format:
  ```
  GroupName: B1-GeneID, B2-GeneID, B3-GeneID
  ```

Example:
```
NK3_Family: B0-NK3, B1-Nkx3.1, B2-Nkx3.2, B3-Nkx3.3
```

---

## Features

- Fetches and aligns sequences using the Ensembl or GenBank databases.
- Supports both **FastTree** and **RAxML** inference.
- Automatically generates rooted and unrooted trees per orthogroup.
- Builds a consensus tree of block-level relationships.
- Switch between rooted and unrooted views with a checkbox toggle.

---

## Outputs

Results are saved to your selected output folder and include:
- Per-group rooted and unrooted trees (PNG format).
- A consensus block tree based on shared subtree topologies.
- Aligned FASTA files and support trees (e.g., `.support` files).
