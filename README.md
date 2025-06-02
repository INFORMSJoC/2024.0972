[![INFORMS Journal on Computing Logo](https://INFORMSJoC.github.io/logos/INFORMS_Journal_on_Computing_Header.jpg)](https://pubsonline.informs.org/journal/ijoc)

# ILP models for the Bin Packing Problem with Minimum Color Fragmentation

This archive is distributed in association with the [INFORMS Journal on
Computing](https://pubsonline.informs.org/journal/ijoc) under the [GNU GENERAL PUBLIC LICENSE](LICENSE).

The software and data in this repository are a snapshot of the software and data
that were used in the research reported on in the paper 
[Pseudo-Polynomial Formulations for the Bin Packing Problem with Minimum Color Fragmentation](https://doi.org/10.1287/ijoc.2024.0972) by Mathijs Barkel, Maxence Delorme, Enrico Malaguti and Michele Monaci.

**Important: This code is being developed on an on-going basis at 
https://github.com/MathijsBarkel/BPPMCF2. Please go there if you would like to
get a more recent version or would like support.**

## Cite

To cite the contents of this repository, please cite both the paper and this repo, using their respective DOIs.

https://doi.org/10.1287/ijoc.2024.0972

https://doi.org/10.1287/ijoc.2024.0972.cd

Below is the BibTex for citing this snapshot of the repository.

```
@misc{CodeBPPMCF,
  author =        {Mathijs Barkel and Maxence Delorme and Enrico Malaguti and Michele Monaci},
  publisher =     {INFORMS Journal on Computing},
  title =         {Pseudo-Polynomial Formulations for the Bin Packing Problem with Minimum Color Fragmentation},
  year =          {2025},
  doi =           {10.1287/ijoc.2024.0972.cd},
  url =           {https://github.com/INFORMSJoC/2024.0972},
  note =          {Available for download at https://github.com/INFORMSJoC/2024.0972},
}  
```

## Description

The goal of this software is to evaluate different ILP models for solving the Bin Packing Problem with Minimum Color Fragmentation (BPPMCF), 
and also to investigate the effect of changing the number of bins on the optimal solution value.

## Details of code

All algorithms are coded in C++ and part of our methods require the commercial solver Gurobi (we used version 11.0.2). The files have the following contents:

| Name  | Description |
| ------------- | ------------- |
| main.h/cpp  | example of front-end code for calling our methods to solve a given instance  |
| BPPLB.h/cpp | code required for the algorithm BPP-LB (introduced by Barkel et al. (2025))  |
| BPPUB.h/cpp | code required for the algorithms BPP-UB (introduced by Barkel et al. (2025))  |
| TS.h/cpp | code required for the algorithm TS (introduced by Barkel et al. (2025))  |
| AFCSP.h/cpp | code required for the arcflow formulation (which is used by our algorithms)  |
| IP2RE.h/cpp | code required for our re-implementation of method IP2 by Mehrani et al. (2022)  |
| RM2GIFFRE.h/cpp | code required for our re-implementation of method RM2-GIFF by Mehrani et al. (2022)  |
| LF.h/cpp | code required for method LayerFlow.  |
| HF.h/cpp | code required for method HierarchyFlow |
| MFMB.h/cpp | code required for method MonoFlow-MultiBin |
| helper_functions.h/cpp | code containing miscellaneous simple/supportive functions |

The repository also contains the file CMakeLists.txt, which can be used to create a Makefile after running "cmake .. -DCMAKE_BUILD_TYPE=Release; make -j".
When using a different version of Gurobi, make sure to update the relevant lines in CMakeLists.txt.

## Details of instances
Moreover, "InstancesBPPMCF.zip" contains a txt-file for each of our test instances. These are spread over 5 folders, each corresponding to a different data set: "Dataset 1", "Dataset 2", "Dataset 3" and "Dataset 4" correspond to datasets D1, D2, D3 and D4 as introduced by Mehrani et al. (2022) (see https://github.com/saharnazmehrani/BPPMCF-IJOC), and "Triplets" corresponds to D5*. Instances D1*, D2*, D3* and D4* (introduced by Barkel et al. (2025) are obtained by setting the number of bins to the minimum number of required bins (see main.cpp), where the minimum number of required bins per instance is saved in the file "minNumberOfBinsPerInstance.txt".

Each instance file is structured as follows: 

For Datasets 1,2,3 and 4:
- The first line is always a 1.
- The second line contains the number of bins (B).
- The third line contains the bin capacity (W).
- Then a blank line, followed by a 0-matrix of size BxW, followed by three more blank lines.
- The next line contains the number of colors (C).
- The next line contains the number of items (I).
- Then follows a blank line.
- Finally there is a matrix of size Ix2, where each row i gives the color c and the weight w of item i.

For Dataset 5 (Triplets):
- The first line contains the number of items I.
- The remaining lines contain a matrix of size Ix2, where each row i gives the color c and the weight w of item i.

## References

Barkel, M., Delorme, M., Malaguti, E., and Monaci, M. (2025). Bounds and heuristic algorithms for the bin packing problem with minimum color fragmentation. European Journal of Operational Research, 320(1):57–68.

Mehrani, S., Cardonha, C., and Bergman, D. (2022). Models and algorithms for the bin-packing problem with minimum color fragmentation. INFORMS Journal on Computing, 34:1070–1085.

## Ongoing Development

This code is being developed on an on-going basis at the author's
[GitHub site](https://github.com/MathijsBarkel/BPPMCF2).

## Support

For support in using this software, submit an
[issue](https://github.com/MathijsBarkel/BPPMCF2/issues/new).
