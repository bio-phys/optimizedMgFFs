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
* `ff_Mg_spce.itp` and `Mg_spce.itp`,
* `ff_Mg_tip3pfb.itp` and `Mg_tip3pfb.itp`,
* `ff_Mg_tip4p2005.itp` and `Mg_tip4p2005.itp`,
* `ff_Mg_tip4pew.itp` and `Mg_tip4pew.itp`,
* `ff_Mg_tip4pd.itp` and `Mg_tip4pd.itp`.

# Examples

Examples can be used similar as for TIP3P water. To test the parameters for the selected water model (here spce as an example, works the same for the other parameters):

* download the example files from: [Link](https://github.com/bio-phys/Magnesium-FFs)
* add the new force field parameters (`ff_Mg_spce.itp` and `Mg_spce.itp`) to `ions.ff`
* change the names of the ions force field parameter file `.itp` in the topolology file `.top` from `ff_Mg.itp` to `ff_Mg_spce.itp` and from `Mg.itp` to `Mg_spce.itp`
* follow the description for TIP3P.

## Citation
If you use our optimized parameters for Magnesium please refer to:
K. K. Grotz, N. Schwierz (t.b.a.)


Implementation has been tested by Kara K. Grotz.
USE AT YOUR OWN RISK!!
