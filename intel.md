# Intel® Parallel Studio XE 2017

```
INTEL17='/opt/intel/compilers_and_libraries_2017.1.132/linux'
export INTEL17

umask 022
source /opt/intel/Compiler/11.1/080/bin/intel64/ifortvars_intel64.sh
source /opt/intel/Compiler/11.1/080/bin/intel64/iccvars_intel64.sh
ICC_LIB=/opt/intel/Compiler/11.1/080/lib/intel64
MKL_LIB=/opt/intel/Compiler/11.1/080/mkl/lib/em64t
MPI_LIB=/opt/mpich2/lib
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib:$MKL_LIB:/usr/lib:$ICC_LIB:$MPI_INTEL_LIB
PATH=$PATH:/opt/OpenMX/openmx3.8/work
export PATH
ulimit -s unlimited

