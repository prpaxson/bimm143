Class 12: Structural Bioinformatics II
================

## Prep for Docking

We want to produce a protein-only PDB file and a drug-only PDB file

``` r
library(bio3d)

# Download the PDB file
get.pdb("1hsg")
```

    ## Warning in get.pdb("1hsg"): ./1hsg.pdb exists. Skipping download

    ## [1] "./1hsg.pdb"

``` r
pdb <- read.pdb("1hsg.pdb")
protein <- atom.select(pdb, "protein", value=TRUE)
write.pdb(protein, file="1hsg_protein.pdb")
```

``` r
ligand <- atom.select(pdb, "ligand", value=TRUE)
write.pdb(ligand, file="1hsg_ligand.pdb")
```

``` r
results <- read.pdb("all.pdbqt", multi=TRUE)
write.pdb(results, file="results.pdb")
```
