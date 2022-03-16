
LFNS Documentation
====================

General
----------
  * Author: Jan Mikelson <jan.mikelson@bsse.ethz.ch>

This toolbox provides the functions lfns_seq, lfns_mpi and simulate. The lfns commands lfns_seq and lfns_mpi are the
sequential and parallel version of the LF-NS algorithm which performs likelihood-free nested samplinga as described
in 

Mikelson, Jan, and Mustafa Khammash. "Likelihood-free nested sampling for parameter inference of biochemical reaction networks." PLoS computational biology 16.10 (2020): e1008264.

the command "simulate" performs ODE simulation.
This version is a trimmed version of the full LF-NS toolbox that was used for the inference runs for the paper in the
preprint

Dessauges, Coralie, et al. "Optogenetic actuator/biosensor circuits for large-scale interrogation of ERK dynamics identify sources of MAPK signaling robustness." bioRxiv (2021).


The general use of the lfns commands are (we exemplify it on the lfns_seq command)
"lfns_seq [path/to/config/file] -O [path/to/output/file] [options]"
where a list of options can be obtained by calling "lfns_seq --help". Examples of confg files can be found in the folder
"models/egf_endo_light/config.xml".


Dependencies
--------------------
  * [Boost](http://www.boost.org): minimal version: 1.53
  * [Eigen3](http://eigen.tuxfamily.org/index.php) matrix library
  * [DP-GMM](https://github.com/Mijan/DPGMM) density estimation library
  * [muParser](https://beltoforion.de/article.php?a=muparser) parsing library
  * [cvode](https://computing.llnl.gov/projects/sundials/cvode) Ode library


INSTALLATION
--------------------
Preparation
--------------------

Before attempting to compile, you must ensure that the required dependencies can be found by CMake.
If you have everything installed in standard locations, the CMake find scripts should locate everything.
If not, you can specify the environment variables `EIGEN3_ROOT`, `BOOST_ROOT`, `MUPARSER_ROOT` and `SUNDIALS_ROOT`.

For example, assuming '/usr/local/include` contains a folder `Eigen` and the file
`signature_of_eigen3_matrix_library`,you can write

    export EIGEN3_ROOT=/usr/local/include

Installation
--------------------
To install the program you need to run the cmake script followed by a make.
	
	mkdir build
	cd build
	cmake -DCMAKE_INSTALL_PREFIX:PATH=/usr/local/ ../
	make
	make install

The above commands would create the the libraries of the LF-NS toolbox in the folder build and install them along with the
necessary header files and the executables "lfns_seq", "lfns_mpi" and "simulate" into the folder "/usr/local/lib", "/usr/local/include" and "/usr/local/bin" respectively.


