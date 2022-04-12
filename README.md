# DIFFaX-openmp-patches
DIFFaX was created by M.M.J. Treacy, et al, and is available from https://www.public.asu.edu/~mtreacy/DIFFaX.html . The patches in this repository enable effective simulation of larger structures, and were created for simulation of stacks of metal-organic frameworks (MOFs). The patches can be applied as follows (for Linux, adjust as appropriate for other OSs):

1. `curl https://www.public.asu.edu/~mtreacy/DIFFaX_v1813.tar.gz > DIFFaX_v1813.tar.gz`
1. `tar -zxvf DIFFaX_v1813.tar.gz`
1. `cd DIFFaX_1813`
1. Download the two patch files from this repo
1. `patch -p0 < DIFFaX-moreatoms.patch`
1. `patch -p0 < DIFFaX-openmp-1813-1815TMM.patch`
1. edit makefile to specify your fortran compiler and to enable openMP compilation. For example: `FC = gfortran` and `FCFLAGS = -O2 -fopenmp`
1. Run `make` to build DIFFaX
1. Execute the examples in the manual, and ensure that all three test cases give identical (precisely the same) outputs:
   1. DIFFaX 1.813 without these patches
   1. DIFFaX with these patches and `OMP_NUM_THREADS=1`
   1. DIFFaX with these patches and `OMP_NUM_THREADS=16`
