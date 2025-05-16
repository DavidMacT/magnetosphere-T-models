## Summary

A Python wrapper for the TS05 and TA16 magnetosphere models. This code allows users to run the original F77 codes under Python and in parallel. The main files to compile the codes are in the */src* directory. These files include the magnetosphere codes, the *geopack* code for the Earth's magnetic field (the IGRF) and a F90 script to calculate quantities related to the reconnection rate (as described [here](https://link.springer.com/article/10.1007/s11207-025-02462-8)).

Instructions for compiling the code are given below. In order to run the code, please see the instructions in the */examples* directory.

## How to compile/install

To use these subroutines in Python, all the fortran codes need compiled via the numpy wrapper, [f2py](https://numpy.org/doc/stable/f2py/f2py.getting-started.html).  You will need an active Python environment with the following packages:

 - numpy
 - meson
 - ninja

You will also need a Fortran compiler.  Ensure that you python environment is active and run,
```
python -m numpy.f2py -c TS04c.for TA16_RBF.f geopack.f reconnectionMetrics.f90 magnetosphereModels.f90 TsyganenkoWrapper.pyf TsyganenkoWrapper.f90
```
within the src directory.  This should generate a module file entitled *TsyganenkoWrapper.cpython-313-x86_64-linux-gnu.so* or something similar. This module file can now be imported into Python. This code has been tested on Python v3.10.9/2023.03 from Anaconda.

**NOTE:** Do not move this file around. If you wish to call this package in another directory, use a system link to point to this file in place.  i.e., *ln -s PATH_TO_MODULE CURRENT_DIR/.*
