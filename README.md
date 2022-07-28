Singularity container for GFLow, Software for modeling circuit theory-based connectivity
================
Cysearch
May 2, 2022

**GFlow, and dependencies**

Repository based on public template
[`gsalzet/singularity-template`](https://github.com/gsalzet/singularity-r-TROLL)

This container includes:

-   `GFlow` v0.1.7-alpha
-   `openmpi-bin` 0.0
-   `libhypre-dev` 0.0
-   `petsc-dev` 0.0

Singularity container based on the recipe:
[`Singularity`](https://github.com/gsalzet/singularity-r-TROLL/blob/main/Singularity)

Initial bootstrap :
[`docker://ubuntu:16:10`](https://hub.docker.com/layers/ubuntu/library/ubuntu/16.10/images/sha256-7d3f705d307c7c225398e04d4c4f8512f64eb8a65959a1fb4514dfde18a047e7?context=explore)

**build**:

``` bash
singularity build --fakeroot image.sif ubuntu-gflow.def
```

**pull**:

``` bash
singularity pull https://github.com/cysearch/singularity-GFlow/releases/download/0.1/singularity-GFlow.latest.sif
```

**snakemake**:

``` python
singularity:
    "https://github.com/gsalzet/singularity-GFlow/releases/download/0.1/singularity-GFlow.latest.sif"
```