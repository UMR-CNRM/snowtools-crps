# Snowtools-crps

`snowtools-crps` is a module for calculating the CRPS (continuous ranked probability score)
between two ensembles coded in Fortran90 and installed as a python package.
This package is a dependency of the `snowtools` package.

`snowtools-crps` is freely distributed under CeCILL-C licence. See [LICENCE](LICENCE.txt) for details

# Install 

run 
```commandline
pip install . 
```
in your virtual environment.

or temporary create one...

 install script for local machines with access to PyPI.
 The pypi access is needed to install build dependencies (meson, meson-python, ninja)
 not installed system wide.
```commandline
python3 -m venv venv_test --system-site-packages
source ./venv_test/bin/activate
pip install meson meson-python ninja
python3 -m numpy.f2py -c crps.f90 -m crps --lower # --build-dir bla
deactivate
rm -rf venv_test
```
