# Running Local Development

This was tested on a machine with the following specifications:
`Intel(R) Xeon(R) CPU E3-1240 V2 @ 3.40GHz`.
This should allow anybody to run the code on their local system.
On this machine it took 13 minutes to run 1000 iterations.


## Codebase Changes

* Change the following to correct the file output in para.f90
```
dircntdflow0 = trim('/glade/scratch/ngeneva/D3Q19_Channel/')
dircntdpart0 = trim('/glade/scratch/ngeneva/D3Q19_Channel/')
dirgenr = '/glade/scratch/ngeneva/D3Q19_Channel/'
```
* Change the above to the following to export to your local directory
```
dircntdflow0 = trim('data/')
dircntdpart0 = trim('data/')
dirgenr = 'data/'
```
* Next the amount of nodes the system can use should be selected (para.f90)
```
nprocY = 20 !MPI topology width
```
* In this case, we are on a 8 core machine, so 8 will be selected
```
nprocY = 8 !MPI topology width
```



## Running the Program

* First compile the program with `make`
* Next lets run it with 8 MPI cores
* `mpiexec -n 8 ./main`
* This should use all CPU cores on the current system
* To see nice stats the following can be done
    * `sudo apt-get install sysstat`
    * `watch -n 1 mpstat -P ALL 1`
* Note that we specify 8 core, which should match the `nprocY`