# MNS_CD
This is the Cluster Dynamics code for evolution of Mn-Ni-Si in low-Cu RPV steels. 

Information regarding the thoery of this model is published at: H. Ke, P. Wells, P. D. Edmondson, N. Almirall, L. Barnard, G. R. Odette, D. Morgan, Thermodynamic and kinetic modeling of Mn-Ni-Si precipitates in low-Cu reactor pressure vessel steels, *Acta Materialia*, **138**(2017), pp10-26. 

********
**Please note this code is a research tool under development and still contains significant discrepancies in predictions compared to experiments. Please use with caution.
For more information please contact Huibin Ke <hke@wisc.edu> or Dane Morgan <ddmorgan@wisc.edu>.**
********

This readme file will include information for 1)solver information; 2)input parameters to run code; 3)explanation of output from code.
1) Solver information.

   The solver used in this code is SUNDIALS (SUite of Nonlinearand DIfferential/ALgebraic Equation Solvers), which can be downloaded from website: https://computation.llnl.gov/projects/sundials. And more detail information about SUNDIALS can also be found from the website above. The module we used here is cvode.
2) Input parameters to run code.

   Two kinds of parameters are needed:
   
   One is the all physical parameters needed for the evolution of precipitates, including temperature, irradiation flux, precipitate phase and matrix information et al. All of these paramters are defined in Input.cpp.
   
   The other is the parameters affecting the numerical stability of the code and output file, including the maximum cluster size, cutoff size, method to calculate mean radius, running time et al. All of these parameters are defined in Constants.h. Two parameters that we would like to explain more here is **runs** and **RadiusCalc**.
   
   **runs**: Total output times, the corresponding irradiation time for each value of runs is given at the end of this file
   **RadiusCalc**: According to different needs, two ways of calculating mean radius are provided. If *r<sub>i* is the radius of each cluster with size *i*, *N<sub>i* is the number density of each cluster with size *i*, **radM1** means the mean radius is calculated via function *MeanRadius*= sum(*r<sub>i*x*N<sub>i*)/sum(*N<sub>i*). And **radM2** means the mean size of each phase is calculated first with equation *MeanSize*=sum(*i*x*N<sub>i*)/sum(*N<sub>i*), then the mean radius is radius corresponding to a cluster with size *MeanSize*.
3) Explanation of output from code

   There will be a total of five output files generated by the code, namely **Output**, **Profile_0**, **Profile_1**, **Profile_2**, **Profile_3**
   
   **Output** contains information of mean radius, number density of each phase (both homogeneous and heterogeneous nucleated) at different irradiation fluences.
   
   **Profile_0** contains particle size distribution of homogeneous nucleated T3 phase
   
   **Profile_1** contains particle size distribution of homogeneous nucleated T6 phase
   
   **Profile_2** contains particle size distribution of heterogeneous nucleated T3 phase 
   
   **Profile_3** contains particle size distribution of heterogeneous nucleated T6 phase 

Relationship between parameter **runs** and irradiation time mentioned in list **2**:


runs | Irradiation time (s) | 
--- | --- |
1| 1 |
2 | 2 |
3 | 3 |
4 | 4 |
5 | 5 |
6 | 6 |
7 | 7 |
8 | 8 |
9 | 9 |
10 | 10 |
11 | 20 |
12 | 30 |
13 | 40 |
14 | 50 |
15 | 60 |
16 | 70 |
17 | 80 |
18 | 90 |
19 | 100 |
20 | 200 |
21 | 300 |
22 | 400 |
23 | 500 |
24 | 600 |
25 | 700 |
26 | 800 |
27 | 900 |
28 | 1x10<sup>3 |
29 | 2x10<sup>3 |
30 | 3x10<sup>3 |
31 | 4x10<sup>3 |
32 | 5x10<sup>3 |
33 | 6x10<sup>3 |
34 | 7x10<sup>3 |
35 | 8x10<sup>3 |
36 | 9x10<sup>3 |
37 | 1x10<sup>4 |
38 | 2x10<sup>4 |
39 | 3x10<sup>4 |
40 | 4x10<sup>4 |
...| ...|
