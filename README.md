Jet in Two Component Advective Flow (JeTCAF) model is an X-ray data analysis package. The TCAF model which was proposed by Chakrabarti & Titarchuk (in 1995, arXiv preprint astro-ph/9510005) has been recently upgraded after implementing jet/mass outflows from the inner hot region, which is known as the corona, or Compton cloud or CENBOL (CENtrifugal pressure supported BOundary Layer).
The JeTCAF model description can be found in the paper by Mondal & Chakrabarti (2021, ApJ, 920, 41). In this original paper, the model is directly implemented in XSPEC as a local model and fitted the data of Black Hole Binaries, AGNs, and ULXs respectively.
To make the model available for the community, we have prepared a FITS file using a multi-dimensional parameter grid. Presently, I have prepared a FITS file for AGN only. I am preparing FITS files for BXRBS and for ULXs as well, which will be available soon. 

JeTCAF model has six parameters, namely: i) black hole mass ($M_{BH}$) in units of $M_\odot$,
ii) Keplerian rate ($\dot{m_d}$ in units of $\dot{M_Edd}$), iii) sub-Keplerian rate ($\dot{m_h}$ in units of
$\dot{M}_{Edd}$), iv) location of the shock ($X_s$ in $r_g$), v) compression ratio ($R=\rho_+ / \rho_-$, where $\rho_+$ and
$\rho_-$ are densities of post- and pre- shock matters) of the shock, and vi) jet collimation factor f$_{\rm col}$.
