# Model Class Support

This page describes the types of models (e.g. single-lens or binary lens) that are supported by each package. 

## Defintions

VBM* = VBMicrolensing for model generation and RTModel for Fitting  
MM = MulensModel  
PSPL = Point Source, Point Lens (1S1L)  
PSBL = Point Source, Binary Lens (1S2L)  
BSPL = Binary Source, Point Lens (2S1L)  
BSBL = Binary Source, Binary Lens (2S2L)  

| Feature                                                | BAGLE | VBM* | MM | pyLIMA | RTModel | eesunhong  |
|--------------------------------------------------------|-------|------|----|--------|---------|------------|
| Parallax                                               | Y     | Y    | Y  | Y      |         |            |
| Static Binary Lenses and Sources                       | Y     | Y    | Y  | Y      |         |            |
| Orbital Motion Models - Binary Lens:                   |       |      |    |        |         |            |
|     Eccentric Keplerian                                | Y     | Y    | Y  | Y      |         |            |
|     Linear/Accelerated Orbital Approximations          | Y     | N    | Y  | N      |         |            |
| Orbital Motion Models - Binary Source:                 |       |      |    |        |         |            |
| Keplerian Binary Source Orbital Motion                 | Y     | N    | Y  | N      |         |            |
| Circular Binary Source Orbital Motion                  | Y     | Y    | Y  | Y      |         |            |
| Binary Source Linear/Accelerated Orbital Approximations| Y     | Y    | Y  | Y      |         |            |
| Photometry Models Available for Fitting                |       |      |    |        |         |            |
| PSPL                                                   | Y     | Y    | Y  | Y      |         |            |
| BSPL                                                   | Y     | Y    | Y  | Y      |         |            |
| PSBL                                                   | Y     | Y    | Y  | Y      |         |            |
| FSBL                                                   | N     | Y    | Y  | Y      |         |            |
| BSBL                                                   | Y     | Y    | Y  | Y      |         |            |
| Astrometry Models Available for Fitting                |       |      |    |        |         |            |
| PSPL                                                   | Y     | Y    | N  | N      |         |            |
| BSPL                                                   | Y     | Y    | N  | N      |         |            |
| PSBL                                                   | Y     | Y    | N  | N      |         |            |
| BSBL                                                   | Y     | N    | N  | N      |         |            |

