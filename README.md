Jet in Two Component Advective Flow (`JeTCAF`; 2021, ApJ, 920, 41) model is an X-ray data analysis package. The `TCAF` model which was proposed by `Chakrabarti & Titarchuk` (in 1995, arXiv preprint astro-ph/9510005) has been recently upgraded after implementing jet/mass outflows from the inner hot region, which is known as the corona, or Compton cloud or CENBOL (CENtrifugal pressure supported BOundary Layer).
The JeTCAF model description can be found in the paper by `Mondal & Chakrabarti (2021, ApJ, 920, 41)`. In this original paper, the model is directly implemented in `XSPEC` as a local model using `initpackage` command and fitted the data of `Black Hole X-ray Binaries`, `AGNs`, and `ULXs` respectively.
To make the model available for the community, we have prepared a `FITS` file using a multi-dimensional parameter grid. Presently, I have prepared a `FITS` file for `AGN` only. I am preparing `FITS` files for `BXRBS` and `ULXs` as well, which will be available soon.  



`JeTCAF` model has six parameters, namely: i) black hole mass ($M_{BH}$) in units of $M_\odot$,
ii) Keplerian rate ($`\dot{m}_d`$ in units of $`\dot{M}_{\rm Edd}`$), iii) sub-Keplerian rate ($`\dot{m}_h`$ in units of
$`\dot{M}_{\rm Edd}`$), iv) location of the shock ($X_s$ in $r_g$), v) compression ratio ($R=\rho_+ / \rho_-$, where $\rho_+$ and
$\rho_-$ are densities of post- and pre- shock matters) of the shock, and vi) jet collimation factor $`f_{\rm col}`$.

A cartoon diagram of the `JeTCAF` model and corresponding spectral components are shown below. 



![jetted](https://github.com/santanumondal87/JeTCAF-A-package-for-X-ray-spectral-fitting-of-black-holes-across-mass-scale/assets/34309461/a34e60aa-b22b-49bf-86a6-af605c48a384) ![jetcaf-spec-standard](https://github.com/santanumondal87/JeTCAF-A-package-for-X-ray-spectral-fitting-of-black-holes-across-mass-scale/assets/34309461/90cb5b1f-a9fa-4663-92d2-1938c1e4e32a)



After successfully making the `FITS` file, data can be fitted by loading the fits file in `XSPEC`. Here, I show the command that can be used to load the model in `XSPEC`.



XSPEC12>data 1:1 spec1.pha



XSPEC12>data 2:2 spec2.pha



One can specify the energy band in which data need to be analyzed which includes good statistics by ignoring the rest.
The following command does that.


XSPEC12>ig 1:$**$-0.5 70.0-$**$


XSPEC12>ig 2:$**$-0.5 70.0-$**$


Once the data is loaded, it can be modeled using `JeTCAF`, by loading the `FITS` files as a local additive table model below.
This command prompt will ask for a guess value of the model parameters. It will be helpful if one has some idea of the spectral state of the outburst phase.
That will help to give the guess value, on the other hand, one can also give a blind guess and check the
evolution of the parameters. Here, I used a multiplicative model `TBabs`, which is a galactic absorption model, and `/home/Softwares/LMODELS/` is the
path of the directory where the fits file is located. Commands for loading the model and fitting the data are:



`XSPEC12>model TBabs*(atable{/home/Softwares/LMODELS/JeTCAF.fits})`


XSPEC12>fit



