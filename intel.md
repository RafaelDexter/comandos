# Intel® Parallel Studio XE 2017

```
INTEL17='/opt/intel/compilers_and_libraries_2017.1.132/linux'
export INTEL17

umask 022
source $INTEL17/bin/iccvars.sh -arch intel64
source $/bin/ifortvars.sh -arch intel64
ICC_LIB=INTEL17/compiler/lib/intel64_lin
MKL_LIB=INTEL17/mkl/lib/intel64_lin
MPI_LIB=INTEL17/mpi/intel64/lib
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib:$MKL_LIB:/usr/lib:$ICC_LIB:$MPI_LIB
#PATH=$PATH:/opt/OpenMX/openmx3.8/work
#export PATH
ulimit -s unlimited

