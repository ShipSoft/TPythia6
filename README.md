# Pythia6 interface to ROOT

This is a copy of the $ROOTSYS/montecarlo/pythia6 folder, which is not supported by ROOT from 6.32 onward.

The only difference is the CMakeList.txt, which builds with

ROOT_GENERATE_DICTIONARY

instead of

ROOT_STANDARD_LIBRARY_PACKAGE

## Requisites

The CMAKE build requires

* ROOT (which is looked for automatically by find_package(ROOT))

* pythia6 (which is provided as cmake -DPythia6_ROOT=/your/path/pythia6/)

