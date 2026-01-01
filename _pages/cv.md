---
permalink: /northwestern_reu/
title: "Northwestern REU"
author_profile: true
---

{% include toc %}
{% include base_path %}

This project was completed during the summer 2025 [Northwestern University](https://www.northwestern.edu) REU at the [Center for Interdisciplinary Exploration and Research in Astrophysics (CIERA)](https://ciera.northwestern.edu).

## Abstract

This study investigates the connections between the emission line spectra of galaxies and their morphological properties. We utilize recent JWST NIRSpec spectroscopic data in three bands to create emission line ratio diagrams. We examine two BPT diagrams showing the relationship between the $[OIII]\lambda 5007 / H\beta$ emission line ratio and the $[NII]\lambda 6584/H\alpha$ and $[SII]\lambda 6718 + 6731/H\alpha$ line ratios, respectively. We also examine two more emission line relationships: first, between the $[OIII]\lambda 5007/[OII]\lambda 3729$ and the $[SIII]\lambda 9531/[SII]\lambda 6717,6731$ emission line ratios, and the relationship between the $[OIII]\lambda 5007/[OII]\lambda 3729$ and the $[([OIII]\lambda 5007+[OII]\lambda 3729)/H\beta$ emission line ratios. We study the connections between these emission line ratios with several morphological properties: the effective radius $R_{eff}$, a measure of how compact/extended a galaxy we define as $\Delta log(R_{eff})$, each galaxy's S\'ersic index, and with the electron density of each galaxy. We find that there is a negative relationship between electron density and $\Delta log(R_{eff})$, along with a possible positive relationship between $\Delta log(R_{eff})$ and the S32 line ratio. 

## Introduction

A galaxy's spectrum is created by studying the galaxy's light after it has been dispersed into its component wavelengths. The emission lines present in a spectrum tell us incredible amounts of information about the physical processes within a galaxy, such as the rates of star formation within the galaxy, the galaxy's temperature and density, the amount and types of gas and dust in the galaxy, and more. Many of the strong lines we see in galaxy spectra come from HII regions, which are regions of space where hydrogen gas has been ionized by nearby stars. By taking flux ratios of emission line pairs close in wavelength, we can minimize the effects of dust extinction. 

The purpose of this study is to compare the results of these emission line diagnostics to morphological measurements of these galaxies. We examine the relationships between the aforementioned emission line ratios with several morphological properties: the effective radius $R_{eff}$, which is the radius of a galaxy that contains half of its light (M. Vika et al. 2015), a measure of how compact/extended a galaxy is, each galaxy's S\'ersic index, and with the electron density of each galaxy. 

The data used for this study was sourced from the Dawn James Webb Space Telescope (JWST) Archive, which is a repository of public JWST galaxy data  (A. de Graaff et al. 2025) (K. E. Heintz et al. 2024). The spectroscopic data was gathered by JWST's Near-Infrared Spectrograph (NIRSpec)  (P. Jakobsen et al. 2022) across three bands (G140, G235, G395).

## Methods

The morphology of each galaxy in the sample was analyzed using eight JWST images of the galaxy (A. de Graaff et al. 2025) (K. E. Heintz et al. 2024). From these images, the redshift $z$ and mass (measured in solar masses \(M_\odot\)) were measured. Profiles were then fit to galaxies using the pysersic code de (I. Pasha & T. B. Miller 2023). Throughout this process, each galaxy was assumed to follow a S\'ersic profile  (J. L. Sersic 1968). The S\'ersic index, a number representing the shape of the galaxy's light distribution, was then measured for each galaxy. Each of the eight JWST images measures slightly different $R_{eff}$ and S\'ersic index values, so these $R_{eff}$ and S\'ersic index values were then interpolated to the rest frame wavelength of $5000Å$ using SciPy's B-Spline interpolation software  (P. Virtanen et al. 2020). The observed size of galaxies correlates with both masses and redshift. This means that if we compare the galaxy size directly to the line ratio, it would be difficult to decipher whether any connections are due to differences in size or due to correlations with mass and redshift. To remove these confounding effects, a model was fit to describe the average size of a galaxy as a function of radius, mass, and redshift. 

To analyze the emission line spectra of each galaxy, each spectrum was moved into rest-frame wavelengths and had its continuum removed. An SNR-based Gaussian emission line fitting method line was utilized, and if the same emission line was detected across multiple bands, the band with the highest SNR was utilized. Several tests were performed in order to ensure the accuracy of this fitting method, including plotting the root-mean-squared of each galaxy spectra in each band and comparing the flux of the same emission line in the same galaxy across multiple bands. 

Four emission line ratio diagrams were created for this study, two of them being BPT diagrams (J. A. Baldwin et al. 1981). Although the original purpose of BPT diagrams were to find AGNs, now they are commonly used to investigate the properties of the gas within galaxies. The two BPT diagrams included in the study compared the $[OIII]\lambda 5007/H\beta$ emission line ratio to either the $[NII]\lambda 6584/H\alpha$ ratio (N2-BPT) or the $[SII]\lambda 6717 + 6731/H\alpha$ ratio (S2-BPT). The two other emission line ratio diagrams created for this study compared the $[OIII]\lambda 5007 / H\beta$ emission line ratio to each the $[SIII]\lambda 9531/[SII]\lambda 6717,6731$ and the $[([OIII]\lambda 5007+[OII]\lambda 3729)/H\beta$ emission line ratios (O32-R23). For the S32 and the O32-R23 diagrams, the emission lines in each ratio are much farther apart than in the N2-BPT and S2-BPT diagrams. This means that dust reddening effects are present in these diagrams, especially for the O32 and the S32 ratios. The PyNeb code was utilized to remove these dust reddening effects ects (V. Luridiana et al. 2015), and then these results were compared to similar plots from A. L. Strom et al. (2017) to verify their accuracy. The created N2- and S2-BPT diagrams can be seen in *Fig. 1.*, overlaid with known $[OIII]/H\beta$ relationships from A. L. Strom et al. (2017) overlaid as a comparison.

<figure style="text-align: center;">
  <img src="{{ base_path }}/images/best_combined_BPT.jpg" alt="N2 and S2 BPTs" width="500">
  <figcaption>
    <strong>Fig. 1.</strong> (left) N2-BPT diagram, (right) S2-BPT diagram. (both) 
    The red lines show known $[OIII]/H\beta$ relationships with either 
    $[NII]\lambda 6584/H\alpha$ (left) or 
    $[SII]\lambda 6718 + 6731/H\alpha$ (right), respectively. 
    These relationships come from A. L. Strom et al. (2017).
  </figcaption>
</figure>

## Results

The first relationship we explored was between a galaxy's $\Delta log(R_{eff})$, meaning how extended/compact the galaxy is, and the emission line diagnostics. We began by recreating each emission line ratio diagram, coloring the data points blue if $\Delta log(R_{eff}) > 0$ and green if $\Delta log(R_{eff}) < 0$. These plots are seen in *Figure 2*. We did not find any significant difference in scatter between the different $\Delta log(R_{eff})$ values for any of these plots. 

<figure style="text-align: center;">
  <img src="{{ base_path }}/images/2x2_delta_log_reff_BPT.jpg" alt="delta log reff BPT" width="500">
  <figcaption>
    <strong>Fig. 2.</strong> (a) N2-BPT, (b) S2-BPT, (c) S32 diagram, (d) O32-R23 diagram. (all) Blue
    points represent galaxies with $\Delta log(R_{eff}) > 0$, and green points represent galaxies with
    $\Delta log(R_{eff}) \leq 0$. We did not find any significant difference in scatter between these
    different $\Delta log(R_{eff})$ values for any of these plots.
  </figcaption>
</figure>

We then moved to compare each separate emission line ratio with its distribution of $\Delta log(r_{eff})$ values. We utilized Spearman tests to determine the significance of each relationship. These plots can be seen in *Figure 3.*, and the results of these tests are summarized in \textit{Table 1.} The majority of these tests yielded insignificant results, with p-values ranging from 0.06-0.98. However, the Spearman test comparing the relationship between the S32 emission line and $\Delta log(r_{eff})$ yielded a correlation coefficient of 0.27, representing a positive relationship, and a p-value of 0.06, which is just on the cusp of what is generally accepted to be a "significant" p-value. Further study is needed to determine whether this correlation is statistically significant.

<figure style="text-align: center;">
  <img src="{{ base_path }}/images/Screenshot 2025-08-22 at 1.04.38 AM.png" alt="delta log reff" width="400">
  <figcaption>
    <strong>Table 1.</strong> Spearman correlation coefficients and p-values for emission line ratios
    compared to morphological parameters
  </figcaption>
</figure>

<figure style="text-align: center;">
  <img src="{{ base_path }}/images/2x3_delta_log_reff_emission_ratios.jpg" alt="delta log reff" width="500">
  <figcaption>
    <strong>Fig. 3.</strong> Comparison of $\Delta log(R_{eff})$ with (top left) $log_{10}([NII]\lambda
    6584/H\alpha)$, (top middle) $log_{10}([SII]\lambda 6718 + 6731/H\alpha)$, (top right) $log_{10}
    ([OIII]\lambda 5007/H\beta)$, (bottom left) $log_{10}([SIII]\lambda 9531/[SII]\lambda 6717,6731)$, 
    (bottom middle) $[log_{10}(OIII]\lambda 5007/[OII]\lambda 3729)$, and (bottom right) $log_{10}
    ([([OIII]\lambda 5007+[OII]\lambda 3729)/H\beta)$.
  </figcaption>
</figure>

The second morphological feature we studied was each galaxy's S\'ersic index. As shown in *Figure 4.*, we plotted each individual line ratio against the distribution of each galaxy's mean optical S\'ersic index. We again utilized Spearman tests to determine the significance of each relationship, and a summary of these results can be seen in \textit{Table 1.} No relationships between the mean optical S\'ersic index and an emission line ratio were found to be significant. 

<figure style="text-align: center;">
  <img src="{{ base_path }}/images/2x3_n_opt_mean_emission_ratios.jpg" alt="n opt mean" width="500">
  <figcaption>
    <strong>Fig. 4.</strong> Comparison of mean optical S\'ersic index with (top left) $log_{10}
    ([NII]\lambda 6584/H\alpha)$, (top middle) $log_{10}([SII]\lambda 6718 + 6731/H\alpha)$, (top right) 
    $log_{10}([OIII]\lambda 5007/H\beta)$, (bottom left) $log_{10}([SIII]\lambda 9531/[SII]\lambda 
    6717,6731)$, (bottom middle) $[log_{10}(OIII]\lambda 5007/[OII]\lambda 3729)$, and (bottom right) 
    $log_{10}([([OIII]\lambda 5007+[OII]\lambda 3729)/H\beta)$.
  </figcaption>
</figure>

The final morphological feature we examined was the electron density $n_e$ of each galaxy. We utilized the PyNeb software \citep{pyneb} to calculate the electron density, inputting the $[SII]6731/[SII]6717$ emission line ratio for each galaxy and assuming a fixed electron temperature of 10,000 Kelvin. We then created plots comparing the relationship between each galaxy's electron density and other morphological features, including the galaxy's mass, $\Delta log(R_{eff})$, and S\'ersic index. The plot showing electron density's relationship with $\Delta log(R_{eff})$ is shown in *Figure 5*. A table summarizing the results of these tests s shown in \textit{Table 2.}

<figure style="text-align: center;">
  <img src="{{ base_path }}/images/pyneb_delta_log_reff_electron_density.jpg" alt="electron density" width="500">
  <figcaption>
    <strong>Fig. 5.</strong> Electron density of galaxies compared to $\Delta log(R_{eff})$. A Spearman 
    test yielded a correlation coefficient to $-0.33$ to a significance of $0.03$, showing a significant 
    negative correlation.
  </figcaption>
</figure>

<figure style="text-align: center;">
  <img src="{{ base_path }}/images/Screenshot 2025-08-22 at 1.05.13 AM.png" alt="delta log reff" width="200">
  <figcaption>
    <strong>Table 2.</strong> Spearman correlation coefficients and p-values for electron density compared
    to morphological parameters
  </figcaption>
</figure>

## Conclusion 

Throughout this study, we compared the integrated flux of six emission line ratios to measured morphological measurements. We used spectroscopic and morphological data from the Dawn JWST Archive of galaxies z=2.55-3.7. We then used an SNR-based Gaussian emission line fitting method and chose the line with the highest SNR across all bands. Then, we fit S\'ersic profiles to each galaxy, and interpolated this S\'ersic value and $R_{eff}$ values to rest frame wavelengths. We fit a model to remove the confounding effects of mass and redshift and to isolate the effects of size. Last, electron density was calculated using the PyNeb software (V. Luridiana et al. 2015), and then emission line ratio diagrams, including BPT diagrams, were created and relationships between emission line galaxies and morphology were explored. We found two significant results: first, a negative relationship between $\Delta log(R_{eff})$ and electron density, and second, a possible positive correlation from the comparison of $\Delta log(R_{eff})$ and the S32 emission line ratio.

Overall, most of the relationships we explored throughout this study did not yield significant correlations between morphology and emission line ratios. There are a few ways to interpret these results: first, it is possible that there is little correlation between the gas properties in HII regions and the overall morphology of galaxies. Another possibility is that we are simply not examining the "right" aspects of galaxies to find connections between the two. Interpreting the physical causes of emission lines is complicated because many galaxy properties contribute to these lines. Throughout this project, we took the approach of looking for morphological correlations with the observed emission line ratios, which is relatively simple to implement but can be complicated to interpret due to the aforementioned confounding effects. Future work in this project would be to use the individual emission lines measured throughout this study to do a more detailed calculation of the physical properties of the gas in these galaxies, rather than examining emission line ratios, and look for morphological correlations with these properties. 

## Acknowledgements

(Some of) The data products presented herein were retrieved from the Dawn JWST Archive (DJA). DJA is an initiative of the Cosmic Dawn Center (DAWN), which is funded by the Danish National Research Foundation under grant DNRF140.

This material is based upon work supported by the National Science Foundation (NSF) under Grant Numbers AST-2149425 and AST-2446392. Any opinions, findings, and conclusions or recommendations expressed in this material are those of the author(s) and do not necessarily reflect the views of the NSF.

## References

Baldwin, J. A., Phillips, M. M., & Terlevich, R. 1981, PASP, 93, 5, doi: [10.1086/130766](https://iopscience.iop.org/article/10.1086/130766)

de Graaff, A., Brammer, G., Weibel, A., et al. 2025, A&A, 697, A189, doi: [10.1051/0004-6361/202452186](https://www.aanda.org/articles/aa/full_html/2025/05/aa52186-24/aa52186-24.html)

Heintz, K. E., Watson, D., Brammer, G., et al. 2024, Science, 384, 890, doi: [10.1126/science.adj0343](https://www.science.org/doi/10.1126/science.adj0343)

Jakobsen, P., Herruit, P., Alves de Oliveira, C., et al. 2022, A&A, 661, A80, doi: [10.1051/0004-6361/202142663](https://www.aanda.org/articles/aa/full_html/2022/05/aa42663-21/aa42663-21.html)

Luridiana, V., Morisset, C., & Shaw, R. A. 2015, A&A, 573, A42, doi: [10.1051/0004-6361/201323152](https://www.aanda.org/articles/aa/full_html/2015/01/aa23152-13/aa23152-13.html)

Maiolino, R., & Mannucci, F. 2019, A&A Rv, 27, 3, doi: [10.1007/s00159-018-0112-2](https://link.springer.com/article/10.1007/s00159-018-0112-2)

Pasha, I., & Miller, T. B. 2023, Journal of Open Source Software, 8, 5703, doi: [10.21105/joss.05703](https://joss.theoj.org/papers/10.21105/joss.05703)

Sersic, J. L. 1968, Atlas de Galaxias Australes

Strom, A. L., Steidel, C. C., Rudie, G. C., et al. 2017, ApJ, 836, 164, doi: [10.3847/1538-4357/836/2/164](https://iopscience.iop.org/article/10.3847/1538-4357/836/2/164)

Vika, M., Vulcani, B., Bamford, S. P., Haubler, B., & Rojas, A. L. 2015, A&A, 577, A97, doi: [10.1051/0004-6361/201425174](https://www.aanda.org/10.1051/0004-6361/201425174)

Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [10.1038/s41592-019-0686-2](https://www.nature.com/articles/s41592-019-0686-2)

## Poster

<figure style="text-align: center;">
  <img src="{{ base_path }}/images/Evenson REU poster.pdf" alt="poster" width="600">
</figure>
