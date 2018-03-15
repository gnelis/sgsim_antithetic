# sgsim_antithetic
Implementation of antithetic random fields in sequential gaussian simulation based on gslib implementation (sgsim.f). The code is written in FORTRAN, therefore a proper compiler should be used (gcc in Windows, for example). The main code (sgsim_arf.for) calls some soubrutines located in gslib.7z, so this file must be uncompressed before use. A windows-compilated version is provided as well (sgsim_arf.exe). The main difference with the original sgsim.for implemetation is located in the random number generation, where the algorithm proposed was implemented. 

The program requires an input file, similar to every gslib program. In that file, input parameters should be provided depending on the type of simulation desired. The main change comapred to the conventional input file is the last line, where a Antithetic Random Fields parameter is requested, which is the number of simulations negatively correlated, according the proposed algorithm. The rest of the parameters work in the same way as the original implementation. More information can be found in the main page of the original code, www.gslib.com, and in the User Manual: "GSLIB: Geostatistical Software Library and User's Guide by Clayton Deutsch and Andre Journel, 1992, 340 pp."

Copyright from the original code: 
"Copyright (C) 1996, The Board of Trustees of the Leland Stanford Junior University.  All rights reserved.                            
                                                                      
 The programs in GSLIB are distributed in the hope that they will be useful, but WITHOUT ANY WARRANTY.  No author or distributor accepts responsibility to anyone for the consequences of using them or for whether they serve any particular purpose or work at all, unless he says so in writing.  Everyone is granted permission to copy, modify and redistribute the programs in GSLIB, but only under the condition that this notice and the above copyright notice remain intact."
 
