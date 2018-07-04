# sgsim_antithetic

## Description
Implementation of antithetic random fields in sequential gaussian simulation based on gslib implementation (sgsim.f). The code is written in FORTRAN, therefore a proper compiler should be used (gcc in Windows, for example). The main code (sgsim_arf.for) calls some soubrutines located in gslib.7z, so this file must be uncompressed before use. A windows-compilated version is provided as well (sgsim_arf.exe). 

## Usage
The program requires an input file, similar to every gslib program. In that file, input parameters should be provided depending on the type of simulation desired. The main change compared to the conventional input file is the last line, where a Antithetic Random Fields parameter is requested, which is the number of simulations negatively correlated, according the proposed algorithm. The rest of the parameters work in the same way as the original implementation. More information can be found in the main page of the original code, www.gslib.com, and in the User Manual: "GSLIB: Geostatistical Software Library and User's Guide by Clayton Deutsch and Andre Journel, 1992, 340 pp."

## Documentation
The main difference with the original sgsim.for implemetation is located in the random number generation, where the algorithm proposed was implemented. The changes are detailed next:

1. Correlation Matrix (line 1176 - 1187): The correlation matrix, based on parameter ARF is generated and stored in matrix 'cor'. A Cholesky decomposition is performed to obtain the lower triangular matrix, stored in matrix 'inf'
2. Fixed random path (line 1230): A new random path is drawed only for the first element of the ARF-tuple, and it is fixed for the rest of the realizations of such tuple. The indicator variable counts the simulations performed in each tuple in order to draw a new random path when the tuple is complete.
3. Random Numbers matrix (line 1237): For each node and realization, a gaussian random number is drawed using the acorni function and calling gauinv. To obtain the correlated random numbers, each tuple is multiplied with matrix 'inf'. The resulting vector of correlated random numbers is stored sequentially in variable 'rmatrix'.
4. Simulated Value (line 1413): When the value of each node is simulated, the acorni function was replaced with matrix 'rmatrix' where the corresponding random number for each node and realization is obtained.


## License
Copyright from the original code: 
"Copyright (C) 1996, The Board of Trustees of the Leland Stanford Junior University.  All rights reserved.                            
                                                                      
 The programs in GSLIB are distributed in the hope that they will be useful, but WITHOUT ANY WARRANTY.  No author or distributor accepts responsibility to anyone for the consequences of using them or for whether they serve any particular purpose or work at all, unless he says so in writing.  Everyone is granted permission to copy, modify and redistribute the programs in GSLIB, but only under the condition that this notice and the above copyright notice remain intact."
 
 Everyone is granted permission to copy, modify and redistribute our sgsim_arf.for implementation, but under the condition that the original sgsim.for copyright is preserved.
