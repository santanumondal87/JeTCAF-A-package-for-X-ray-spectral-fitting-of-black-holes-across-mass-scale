# JeTCAF Model and how to use it for spectral fitting


Jet in Two Component Advective Flow (`JeTCAF`; 2021, ApJ, 920, 41) model is an X-ray data analysis package. The `TCAF` model which was proposed by `Chakrabarti & Titarchuk` (in 1995, arXiv preprint astro-ph/9510005, ApJ, 455, 623) 
has been recently upgraded after implementing jet/mass outflows from the inner hot region, which is known as the corona, or Compton cloud or CENBOL (CENtrifugal pressure supported BOundary Layer).
The JeTCAF model description can be found in the paper by `Mondal & Chakrabarti (2021, ApJ, 920, 41)`. In this original paper, the model is directly implemented in `XSPEC` as a local model using `initpackage` command and fitted the data of `Black Hole X-ray Binaries (BHXRBs)`. Later, following the same method the model was applied to fit the data of `AGNs (Mondal et al. 2022, A&A, 662, 77)`, and `ULXs (Palit & Mondal, 2023, PASP, 135, 054101)` respectively.
To make the model available for the community, we have prepared a `FITS` file using a multi-dimensional parameter grid. Presently, I have prepared a `FITS` file for `AGN` only. I am preparing `FITS` files for `BXRBS` and `ULXs` as well, which will be available soon.  


## JeTCAF model parameters

`JeTCAF` model has six parameters, namely: i) black hole mass ($M_{BH}$) in units of $M_\odot$,
ii) Keplerian rate ($`\dot{m}_d`$ in units of $`\dot{M}_{\rm Edd}`$), iii) sub-Keplerian rate ($`\dot{m}_h`$ in units of
$`\dot{M}_{\rm Edd}`$), iv) location of the shock ($X_s$ in $r_g$), v) compression ratio ($R=\rho_+ / \rho_-$, where $\rho_+$ and
$\rho_-$ are densities of post- and pre- shock matters) of the shock, and vi) jet collimation factor $`f_{\rm col}`$. 


According to `TCAF` or `JeTCAF`, spectra become soft with increasing disk mass accretion rate, when all other parameters are fixed and hard 
with the increase in halo accretion rate. Increase in dynamic corona size or $X_s$, spectra become hard, however,
after a certain value of $X_s$ the scenario may change as the optical depth of the corona depends on $X_s$. Therefore, the above description is to get a
zeroth order idea about the dependence of spectral shape with model parameters, however, when we fit data, parameters change in multidimensional space where things are highly non-linear. 
Therefore, I suggest searching for parameters that seem physical and follow theoretical understanding.


A cartoon diagram of the `JeTCAF` model and corresponding spectral components are shown below. 



![jetted](https://github.com/santanumondal87/JeTCAF-A-package-for-X-ray-spectral-fitting-of-black-holes-across-mass-scale/assets/34309461/a34e60aa-b22b-49bf-86a6-af605c48a384) ![jetcaf-spec-standard](https://github.com/santanumondal87/JeTCAF-A-package-for-X-ray-spectral-fitting-of-black-holes-across-mass-scale/assets/34309461/90cb5b1f-a9fa-4663-92d2-1938c1e4e32a)


## Spectral Components

The emergent spectrum from `JeTCAF` has four components; `(1)` a multicolor black-body spectrum coming from the disk (green), `(2)` hard radiation from the upscattering of the soft photons from
the disk by the hot corona (red), `(3)` a second hard component at the shoulder of the black-body bump is due to scattering of soft photons from the disc by the base of the jet (blue), and 
`(4)` down-scattering of hard radiation from the corona by the bulk motion of the jet produces excess above 10 keV (indigo). This component also fits the Compton humps that are observed in reflection models.
In this model, the same corona, which is producing hard radiation, is also launching a jet at its base. The jet/mass outflow rate is obtained after solving a series of coupled hydrodynamic equations; 
thus, it naturally connects the disk and jet.




## Loading the fits file in XSPEC and command for fitting data

After successfully making the `FITS` file, data can be fitted by loading the fits file in `XSPEC`. Here, I put the commands that can be used to load both data and the model in `XSPEC`.



XSPEC12>data 1:1 spec1.pha



XSPEC12>data 2:2 spec2.pha



One can specify the energy band in which data needs to be analyzed which includes good statistics by ignoring the rest using `ig` command.


Once the data is loaded, it can be modeled using `JeTCAF`, by loading the `FITS` files as a local additive table model below.
This command prompt will ask for a guess value of the model parameters. It will be helpful if one has some idea of the spectral state of the outburst phase.
That will help to give the guess value, on the other hand, one can also give a blind guess and check the
evolution of the parameters. Here, I used a multiplicative model `TBabs`, which is a galactic absorption model, and `/home/Softwares/LMODELS/` is the
path of the directory where the fits file is located. Commands for loading the model and fitting the data are:



`XSPEC12>model TBabs*(atable{/home/Softwares/LMODELS/JeTCAF.fits})`


XSPEC12>fit

One can use `steppar` command to generate confidence contour among parameters as was done in `S. Mondal, T. P. Adhikari, K. Hryniewicz, C. S. Stalin, and A. Pandey, 2022, A&A, 662, 77`

## helpdesk

For any queries regarding data fitting, fits file updates, or fits file with any specific sweet spot of parameters, please contact me here: `santanuicsp@gmail.com`

## Citation

If you are publishing anything using the model fits file, please cite the paper: `Mondal & Chakrabarti, 2021, ApJ, 920, 41`

