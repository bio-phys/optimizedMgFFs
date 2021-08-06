# Optimized Magnesium FFs parameter to be used in SPC/E, TIP3P-fb, TIP4P/2005, TIP4P-Ew, or TIP4P-D water
[Link](https://github.com/bio-phys/Magnesium-FFs) to parameters in TIP3P.

## Introduction
We have developed two sets of force field parameters each for Magnesium Mg2+, `microMg` and `nanoMg`, for use in combination with the one of the above mentioned water model.
Both optimized force field sets simultaneously reproduce thermodynamic and structural properties of aqueous solutions (hydration free energy, radius of the first hydration shell, and coordination number of the first hydration shell). 

The parameter sets `microMg` furthermore reproduce the experimental water exchange rate on the microsecond timescale, while `nanoMg` yield water exchange up to the nanosecond timescale (SPC/E). This corresponds to 10^8 exchanges per second. For TIP4P-Ew up tp 10^7 exchanges per second and for TIP3P-fb, TIP4P/2005, and TIP4P-D 10^6 exchanges per second are observed.

Upon fine tuning of the Lorentz-Berthelot combination rules, additional thermodynamic and structural properties are reproduced (activity coefficient derivative, binding affinity, and distance towards the binding sites) for the interaction towards Chloride and RNA. 

Our optimized parameters aim to precisely capture the role of Magnesium in all-atom molecular dynamics simulations of biological processes including ion specific binding and ion binding kinetics.


## Quick start guide
Our parameters are optimized for the SPC/E, TIP3P-fb, TIP4P/2005, TIP4P-Ew, or TIP4P-D water models.
The parameters are optimized for use with the Smith-Dang parametes for Cl (SPC/E) or the Cloride parameters optimized alongside the Mg2+ parameters and parmBSC0chiOL3 RNA force fields (e.g. `amber14sb.ff`).
All parameter sets here are to be used with the Lorentz-Berthelot combination rule (otherwise modifications are required).
Note that we have chosen unique names for the optimized parameters to avoid errors in overwriting atom names:
* `mMg` - MG with water exchange as in experiment
* `nMg` - MG with accellerated water exchange
* `CXY` - CL optimized for TIP3P-fb, TIP4P/2005, TIP4P-Ew, and TIP4P-D alongside Mg. For SPC/E please use the parameters by Smith and Deng.

To get started: Replace the standard ion names in your `.gro` file by our unique names.
Modify the given topology file according to your system. The topology file includes the optimized force field parameters via 
* `ffMg_spce.itp` and `Mg_spce.itp`,
* `ffMg_tip3pfb.itp` and `Mg_tip3pfb.itp`,
* `ffMg_tip4p2005.itp` and `Mg_tip4p2005.itp`,
* `ffMg_tip4pew.itp` and `Mg_tip4pew.itp`,
* `ffMg_tip4pd.itp` and `Mg_tip4pd.itp`.

# Examples

These examples are the same as for TIP3P. To test the parameters for the different water models:
* download the example files from: 
* add the new force field parameters (`ffMg_nameofwatermodel.itp` and `Mg_nameofwatermodel.itp`) to `ions.ff`
* change the names of the ions force field parameter file `.itp` in the topolology file `.top` from

`; Include optimized forcefield parameters for Magnesium and water
#include "./ions.ff/ff_Mg.itp"
#include "./ions.ff/Mg.itp"`

to the name of the selected wawter model.
## Example 1: 0.5 molar MgCl2 using microMg

Folder example_MgCl2 contains all files for an MD simulation of 0.5 molar MgCl2 solution with GROMACS.
Initial coordinates are given in `MgCl2.gro`

To create a `.tpr` file for energy minimization type: 
```
gmx grompp -f MgCl2.mdp -c MgCl2.gro -p topol_MgCl2.top -maxwarn 27
```

(`maxwarn 27` is required as in the parameter file all scaled interactions towards all RNA atomtypes are explicitly listed, this is of cause not mandatory if no RNA is simulated)

## Example 2: add A-riboswitch with nanoMg

Folder example_1y26withMg contains all files for an MD simulation of the add A-riboswitch (PDB ID:1y26) with GROMACS.
Initial coordinates are given in `1y26withMg.gro`

To create a `.tpr` file for energy minimization type: 
```
gmx grompp -f 1y26withMg.mdp -c 1y26withMg.gro -p topol_1y26withMg.top -n index.ndx -maxwarn 27
```
(`maxwarn 27` is required as in the parameter file all scaled interactions towards all RNA atomtypes are explicitly listed)

## Citation
If you use our optimized parameters for Magnesium please refer to:
K. K. Grotz, N. Schwierz (t.b.a.)


Implementation has been tested by Kara K. Grotz.
USE AT YOUR OWN RISK!!
