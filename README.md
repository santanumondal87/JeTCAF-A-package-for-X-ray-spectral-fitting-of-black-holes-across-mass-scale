Jet in Two Component Advective Flow (JeTCAF; 2021, ApJ, 920, 41) model is an X-ray data analysis package. The TCAF model which was proposed by Chakrabarti & Titarchuk (in 1995, arXiv preprint astro-ph/9510005) has been recently upgraded after implementing jet/mass outflows from the inner hot region, which is known as the corona, or Compton cloud or CENBOL (CENtrifugal pressure supported BOundary Layer).
The JeTCAF model description can be found in the paper by Mondal & Chakrabarti (2021, ApJ, 920, 41). In this original paper, the model is directly implemented in XSPEC as a local model and fitted the data of Black Hole Binaries, AGNs, and ULXs respectively.
To make the model available for the community, we have prepared a FITS file using a multi-dimensional parameter grid. Presently, I have prepared a FITS file for AGN only. I am preparing FITS files for BXRBS and for ULXs as well, which will be available soon.  



JeTCAF model has six parameters, namely: i) black hole mass ($M_{BH}$) in units of $M_\odot$,
ii) Keplerian rate ($`\dot{m}_d`$ in units of $`\dot{M}_{\rm Edd}`$), iii) sub-Keplerian rate ($`\dot{m}_h`$ in units of
$`\dot{M}_{\rm Edd}`$), iv) location of the shock ($X_s$ in $r_g$), v) compression ratio ($R=\rho_+ / \rho_-$, where $\rho_+$ and
$\rho_-$ are densities of post- and pre- shock matters) of the shock, and vi) jet collimation factor $`f_{\rm col}`$.

A cartoon diagram of the JeTCAF model and corresponding spectral components are shown below. 
![jetted](https://github.com/santanumondal87/JeTCAF-A-package-for-X-ray-spectral-fitting-of-black-holes-across-mass-scale/assets/34309461/a34e60aa-b22b-49bf-86a6-af605c48a384) ![jetcaf-spec-standard](https://github.com/santanumondal87/JeTCAF-A-package-for-X-ray-spectral-fitting-of-black-holes-across-mass-scale/assets/34309461/90cb5b1f-a9fa-4663-92d2-1938c1e4e32a)



After successfully making the {\it FITS} file, data can be fitted by loading the fits file in XSPEC. Here, we use the sample data of
the black hole candidate Swift~J1357.2-0933 from simultaneous ${\it NuSTAR}$ and ${\it Swift/XRT}$ observations
(Mondal \& Chakrabarti 2019). The command below shows loading the data (spectrum files from NuSTAR and Swift/XRT analysis),
\\
\colorbox{Mygray}{{XSPEC12$>$data 1:1 spec1.pha}}\\
\colorbox{Mygray}{XSPEC12$>$data 2:2 spec2.pha}\\
One can specify the energy band in which data need to be analyzed which includes good statistics by ignoring the rest.
The following command does that.\\
\colorbox{Mygray}{{\noindent XSPEC12$>$ig 1:**-0.5 70.0-**}}\\
\colorbox{Mygray}{XSPEC12$>$ig 2:**-0.5 70.0-**}\\
Once the data is loaded, it can be modeled using TCAF, by loading the {\it FITS} files as a local additive table model below.
This command prompt will ask for a guess value of the model parameters. It will be helpful, if one has some sense of
spectral state of the outburst phase, as we already discussed, TCAF model parameters vary in multidimensional space.
That will help to give the guess value, on the otherhand one can also give a blind guess and check the
evolution of the parameters. Here, TBabs is the galactic absorption model and {\it /home/Softwares/LMODELS/} is the
path of the directory where the fits file is located.\\
\colorbox{Mygray}{{\noindent XSPEC12$>$model TBabs(atable\{/home/Softwares/LMODELS/TCAF.fits\})}}\\
\colorbox{Mygray}{XSPEC12$>$fit}\\



