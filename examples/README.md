## Summary

This directory contains:

 - *README.md* 
    - This file
 - *example_may_storm_TS05/*
     - *may_2024_storm_with_TS05_vars.dat*
        - May 2024 storm for example data.
     - *storm.py*
        - An example calculation using the Tasyganenko Fortran wrapper for TS05.  
 - *example_may_storm_TA16/*
     - *convert_TS05_data_to_TA16_data.py*
        - Generates the input parameters for the TA16 model from a TS05 input file.
    - *may_2024_storm_with_TA16_vars.dat*
        - May 2024 storm example data
    - *TA16_RBF.par*
        - Model parameters for TA16 model. Must be present in working directory from where the model is run.
    - *storm.py*
        - An example calculation using the Tasyganenko Fortran wrapper for TA16.  
 - *fortran_example_storm.py*
    - An example calculation using the original Tasyganenko codes in modern Fortran. Slower than the wrapped Python (at the moment).

When setting up a calculation, there are two main requirements. 

(1) A list of parameters for every time step you wish to process. Many of these can already be found [here](https://geo.phys.spbu.ru/~tsyganenko/empirical-models/magnetic_field/ta16/). If you need to create these data, you need to follow the format of the given model (TS05 or TA16).

(2) A script to specify the grid and and variables you wish to calculate. Please read through *storm.py* to see how this is set up. This is the script to run.

Remember that you need to soft link to the wrapper in this directory. The output files are .nc.

## Requirements

This example requires the following python packages:

 - xarray
 - multiprocess
 - pandas
 - netCDF4
 - h5netcdf - for compression when writing the magnetic field to disk.
 - The Tsyganenko_wrapper package from the modules_dir
