# SQSLorene
Repository contains code used to calculate configuration of strange quark stars using LORENE library. Library consist of 
## Code to calculate EOS of magnetized SQS - EOS.cpp
dependencies:
* boost library

## Code to calculate configurations of SQS using LORENE library with MPI based paralellism -mag_eos_star.C
dependencies:
* MPI library

in order to use code one need to create file local_settings_mpi using the same template as local_setting 
replacing normal compilers with mpi wrappers for them and place it in LORENE_HOME where normal local_setting file can be found.
There is also wrapper around file com that can be used to calculate series of configurations with changing central enthalpy value (decrese be 0.01). 
In order to calculate n configurations with p mpi-threads we can use:
```sh
./com p n
```
Code produces two tables: results.txt and psurface.txt. One contains parameters of stars and second points of surface of the star and is used by energy.py to calcualte 
energy outside star.

## Code to calculate external energy of SQS contained in magnetic field outside star. Typicaly when we do calculations with previosly mentioned code we get results.txt and psurface.txt.
Then in order to calculate external energy we can simply invoke energy.py with
```sh
python energy.py arg
```
where arg is name of the file we want to save external energy combined with rest of results. 