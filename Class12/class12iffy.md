Class 12
================
Khoi Tran
May 9, 2019

``` r
library(bio3d)
file <- get.pdb("1hsg.pdb")
```

    ## Warning in get.pdb("1hsg.pdb"): ids should be standard 4 character PDB-IDs:
    ## trying first 4 characters...

    ## Warning in get.pdb("1hsg.pdb"): ./1hsg.pdb exists. Skipping download

``` r
pdb <- read.pdb(file)
```

``` r
prot <- atom.select(pdb, "protein", value = TRUE )
lig <- atom.select(pdb, "ligand", value = TRUE)
```

``` r
#write.pdb(lig, file="1hsg_ligand.pdb")
#write.pdb(prot, file="1hsg_protein.pdb")
```

``` r
res <- read.pdb("ligand_out.pdbqt", multi = TRUE)
write.pdb(res, "results.pdb")
```

``` r
ori <- read.pdb("ligand.pdbqt")
rmsd(ori, res)
```

    ##  [1]  0.649  4.206 11.110 10.529  4.840 10.932 10.993  3.655 10.996 11.222
    ## [11] 10.567 10.372 11.019 11.338  8.390  9.063  8.254  8.978

``` r
pdb <- read.pdb("1hel")
```

    ##   Note: Accessing on-line PDB file

``` r
modes <- nma( pdb )
```

    ##  Building Hessian...     Done in 0 seconds.
    ##  Diagonalizing Hessian...    Done in 0.07 seconds.

``` r
m7 <- mktrj(modes, mode=7, file="mode_7.pdb")
```
