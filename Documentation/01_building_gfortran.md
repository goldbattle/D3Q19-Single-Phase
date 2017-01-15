# Building Gfortran

By default the make file allows for building with the intel ifort compiler.
To make the code compatible a couple things need to be changed.
They are as follows:

## Compatibility Changes

* Update the Make file with the following
* `-r8` should become `-fdefault-real-8`
* In para.f90 line 535 update it according the comments
* With gfortran the following inquire should be uncommented
* `inquire( file=trim(DirPath)//'/.', exist=dirExist )  ! Works with gfortran`
* Finally in saveload.f90 there are two instances of the following
* Replace `dsqrt` with `sqrt`

## Building the Program

* To build the program run the Makefile
* Run `make`
* This should create a bin folder
* An executable called `main` should be placed in your directory



