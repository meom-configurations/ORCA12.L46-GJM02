# ORCA12.L46-GJM02
ORCA12.L46-GJM02 is a climatological run forced with repeated DFS4.4 daily climatology, for 85 years.
It was performed in the frame of GENCI Grand defis on 2012 on ADA super computer at IDRIS.

This repository hold the code, and configuration files usefull for running this configuration.


## REFERENCE CODE:
### NEMO 
   The code is based on DCM rev 1190. Reference NEMO version is 3.4 and the reference code is given in the NEMO directory.

### XIOS
  No XIOS used for this run (not ready when running this experiment). For the output, the key_dimgout was used 

## BRIEF DESCRIPTION:
### Overview
  This global configuration is a climatological simulation whose interannual equivalent is ORCA12.L46-MJM88.  It has been run for 85 years, on ada IDRIS supercomputer at the eve of 2012.
  In order to apply climatological forcing, some changes were brought to sbcblk_core in order to use wind speed climatology(|W10| )as well as pseudo stress climatology ( |W10|.u10 and |W10|.v10 ) in order to take into account the non-linearities of the main forcing terms.

### Parameterizations:
 1. use filtered free surface (key_dynspg_flt)
 2. use vector form advection scheme for dynamics, with EEN vorticity component.
 3. use TVD advection scheme for tracers.
 4. use biharmonic viscosity scaled with the cube of the mesh size.
 5. use laplacian isopycnal diffusivity for tracers.
 6. use TKE vertical mixing parameterization with enhanced vertical diffusion for deep convection. use tidal mixing parameterization.
 7. use LIM2 ice model, VP rheology.
 8. use BBL (bottom boundary layer) parameterization.
 9. use free slip lateral condition except in the Idonesian through-flow area, Mediterannean Sea, West coast of Greenland ( near cape desolation) and in the northern part of Nares Strait.
10. Use TOP with CFC passive tracers.

### Forcing:
 1. This run uses DFS4.4 daily climatology with CORE bulk formulae. For the climatological run, we use 9 atmospheric fields instead of the standard 8 fields, replacing u10 and v10 wind component by the wind speed daily climatology (|W10| ) and the pseudo stress components ( |W10|.u10, |W10|.v10 ).
 2. SSS restoring toward Levitus 98, with a piston velocity of 167 mm/day ( 60 days/10 meters).
 3. Run-off from Dai-Trenberth including climatological iceberg contribution from Da Silva


### Output data set: 
 1. 1m output  [198Gb/year] for the whole period ( 85 years )
  * **gridT** files : votemper, vosaline, sossheig, somxl010, somixhgt,sohefldo, etc...
  * **gridU** files : vozocrtx, vozotaux
  * **gridV** files : vomecrty, vometauy
  * **gridW** files : vovecrtz, voavttke
  * **flxT** files : 15 atmosperic fluxes and atmospheric variables.
  * **icemod** files : 19 ice model variables
  * **ptrcT** files : CFC11
  * **diadT** files : QTRCCFX, QINTCFC, INVCFC
 2. 5d output  3D fields [ 1.2 Tb/year ] for the years 72 to 85
  * same files as above + mld trends.
 3. 5d output 2D fields [40 Gb/year] for the whole 85-years period.
  * SST, SSU, SSV
 4. 1d output 2D fields [ 198 Gb/year] for the period 75 to 85
  * SST, SSU, SSV

### Run time files
   The run time files not  indicated in the namelist are:

 * Bathymetry : ```bathymetry_ORCA12_V3.3.nc```
 * Coordinates : ```coordinates_ORCA_R12_lbclnk_no_z.nc```
 * Ice Initialisation : ```ORCA12.L46-MAL95_y1998-2007m01_icemod_initMAL101.nc```
 * Bottom Friction enhancement : ```orca12_bfr_coef_MAL101.nc```
 * AABW damping mask : ```ORCA12.L46_dmp_mask.nc```
 * CFC atmospherique : ```cfc1112_updated4.atm```



### Bibliography:
Molines J.M., B. Barnier, T. Penduff, A.M. Treguier, J. Le Sommer. "ORCA12.L46 climatological and inter annual simulations forced with DFS4.4: GJM02 and MJM88.",  Drakkar Group Experiment report GDRI-DRAKKAR-2014-03-19 (2014)  [https://www.drakkar-ocean.eu/publications/reports/orca12_reference_experiments_2014](Technical Report)
