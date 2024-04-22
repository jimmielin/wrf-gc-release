# Custom KPP mechanism folder

This folder is where you can add your own modified KPP mechanism.
The default files in this folder are based on the fullchem mechanism.

## User-modifiable configuration files

  1. **custom.kpp**: Master KPP specification file (which is a copy of
     ../fullchem/fullchem.kpp).  The **gckpp.kpp* file symbolically
     links to this file.

  2. **custom.eqn**: KPP equation file (which is a copy of
     ../fullchem/fullchem.eqn).

The following files link to files in the KPP/fullchem folder.  If you
need to modify these, consider removing the symbolic links and making
a copy of these files.  You can rename these to custom_*.F90, etc.

  3. **fullchem_HetStateFuncs.F90**: This is a symbolic link to the
     file ../fullchem/fullchem_HetStateFuncs.F90, which is the module
	 containing functions that initialize the HetChem state object.
	 This module is only needed for full-chemistry simulations.

  4. **fullchem_SulfurChemFuncs.F90**: This is a symbolic link to the
     file ../fullchem/fullchem_SulfurChemFuncs.F90.  This contains
     subroutines to compute rates for SO2 reactions in cloud,
	 and only applies to full-chemistry simulations.

  5. **fullchem_RateLawFuncs.F90**: This is a symbolic link to the
     file ../fullchem/fullchem_RateLawFuncs.F90.  This contains
     functions to compute rates for heterogenous chemistry reactions,
	 and only applies to full-chemistry simulations.

  6. **rateLawUtilFuncs.F90**: This module contains several utility
     functions for heterogeneous chemistry reactions (mostly for the
	 full-chemistry simulations).

  7. **commonIncludeVars.H**: This contains common global variables
     used by the KPP mechanisms in GEOS-Chem.  These will be inlined
     into the gckpp_Global.F90 file.

The following files link to the KPP/stubs folder.  These include stub
subroutines that are used by other chemical mechanisms.  The stubs are
needed in order to avoid compilation errors.

  1. **stub_aciduptake_DustChemFuncs.F90** Stub routines corresponding
     to the KPP/aciduptake/aciduptake_DustChemFuncs.F90 module,

  2. **stub_Hg_HetStateFuncs.F90**: Stub routines corresponding
     to the KPP/Hg/Hg_HetStateFuncs.F90 module.

## Files generated by KPP

With the exception of the symbolic link gckpp.kpp, all files starting
with the prefix "gckpp_" are generated by KPP.  These contain the
specifications of the chemical mechanism in efficient source code.

For more information, please see:

  1. KPP documentation at: https://kpp.readthedocs.io

  2. [Guide to Using KPP with GEOS-Chem](https://geos-chem.readthedocs.io/en/latest/geos-chem-shared-docs/supplemental-guides/using-kpp-with-gc.html)