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


## Ensure Local Process Limit

* We are going to want to run a lot of MPI process on a single machine to simulate a server
* Normally the amount of processes that one user can launch is limited
* Change the following
* `sudo nano /etc/security/limits.conf`
* Append the following to the file (replace <username> with your username)
* `<username> soft nproc 1000`
* Restart all terminals so that this takes effect


## Running the Program

* First compile the program with `make`
* Next lets run it with 100 MPI process
* `mpiexec -n 100 ./main`
* This should use all CPU cores on the current system
* To see nice stats the following can be done
    * `sudo apt-get install sysstat`
    * `watch -n 1 mpstat -P ALL 1`
* Note that we specify 8 core, which should match the `nprocY`