- [Description of *Nighttime lights in Mexico at units of substantive interest* repository](#orgab5a009)
- [Social science using night lights](#org7b5f756)
- [Acknowledgements](#org1b5e0c9)
- [Donate](#orgeafc33e)
- [References](#org61fe933)

---

Last revision: 2023-12-30

**News:**

-   22nov2024 Municipio series consolidated in a single file [here](./data/municipios/0all/) (by @jpfmansur Thank you!).

-   27mar2024 Possible update of the source data to 2021 [here](https://gee-community-catalog.org/projects/hntl/).

-   30may2021 Measures re-computed using INE's 2020 maps (instead of 2018 maps). Over-populated secciones are routinely split by INE, creating new units. Comments, critiques, and suggestions welcome by email.

-   5may2021 `data/municipios/` and `data/secciones/` now include luminosity measures for all 32 states. Validation detected a bug affecting smaller units (e.g. secciones in urban areas), producing large but short-lived surges/declines in luminosity measure. Bug has been fixed and data cleaned.

---


<a id="orgab5a009"></a>

# Description of *Nighttime lights in Mexico at units of substantive interest* repository

-   Author: Eric Magar
-   Location <https://github.com/emagar/luminosity>
-   Email: emagar at itam dot mx
-   Citation for the data: see 'About' on the repository landing page

The repository distributes nighttime luminosity data for Mexico, aggregated at the municipal (N approx. 2,500) and *sección electoral* levels (N approx. 67,000). Luminosity rasters are from [Li, Zhou, Zhao and Zhao](https://www.nature.com/articles/s41597-020-0510-y)'s (2020) Harmonized Global Nighttime Light Dataset 1992-2018.

The source reports annual observations geo-coded at a spatial resolution of about one square kilometer (30 arc seconds). This repository summarizes pixels within each unit's territory, reporting the mean unit luminosity, the median, and the standard deviation. While the source averages (and harmonizes) pixel luminosity in *time*, this repo averages pixels in *space*. The chosen units have analytical potential, as they can be associated with census indicators, with electoral returns, and so forth. (*Secciones electorales* are Mexico's basic units for electoral management and cartography, analogous to U.S. census tracts.)

An example from one unit clarifies the summary statistics distributed. The unit in question is electoral sección number 573 in Mexicali, the capital city of the state of Baja California. The following map shows the source's statewide data, shades of green indicating more nighttime luminosity, white less. Tijuana's brightness can be appreciated in the northwestern corner of the state, Ensenada's slightly southward, and Mexicali's eastward. The small red area is sección 573, in the city's suburbs, towards the Colorado river delta (the river is the border with neighboring state of Sonora).

![img](./pics/bc.png "Baja California's statewide nighttime lights for 2018")

The map below zooms into the unit, portraying luminosity in sección 573 and vincinity for the year 2018. (Shapefiles for secciones electorales and municipal boundaries are from [INE's cartography department](https://cartografia.ife.org.mx/sige7/?cartografia=mapas).) Mean artificial lights decreased near monotonically as one progressed towards the sección's east-southeast. I relied on `R`'s `raster` package ([Hijmans 2019](https://cran.r-project.org/web/packages/raster/index.html)) in order to summarize the unit's luminosity.

![img](./pics/bc-100-crop.png "Luminosity around the chosen sección")

The next map illustrates descriptive statistics generation (the code for this process is in script `code/export-seccion-stats.r`). `R`'s `raster::mask` operation selects pixels inside the sección's polygon, excluding the rest (which appear in white in the map). The mean luminosity, median, and standard deviation for the selected pixels are reported in annual state-by-state files in csv format inside folder `data/secciones`.

![img](./pics/bc-100-mask.png "Nighttime lights inside sección 573")

The time series can be appreciated in the final figure below. The sección's rapid urbanization is notable. Most of the area was quite dark in the mid-1990s, with mean nighttime lights of roughly 8GW per pixel, tripling by 2018. The nighttime lightning aggregated in territorial units data offers a valuable indicator of human activity in Mexico's since the 1990s in small and analytically useful geographic units.

![img](./pics/bc-100-mask-1994-2018.png)


<a id="org7b5f756"></a>

# Social science using night lights

-   Livny 2021 [Can Religiosity Be Sensed with Satellite Data?](https://academic.oup.com/poq/article/85/S1/371/6361037)
-   Bruederle and Hodler 2018 [Nighttime lights as a proxy for human development at the local level](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0202231).
-   Chen and Nordhaus 2011 [Using luminosity data as a proxy for economic statistics](https://www.pnas.org/doi/10.1073/pnas.1017031108).
-   A critical piece by Pinkowski and Sala-i-Martin [here](https://voxeu.org/article/gdp-measurement-accounts-surveys-and-lights).
-   Growth reported relative to night lights by Martínez [here](https://bfi.uchicago.edu/insight/finding/how-much-should-we-trust-the-dictators-gdp-growth-estimates/).

-   A Tweeter thread from Stanford AI Lab [here](https://twitter.com/yohaniddawela/status/1741063302988390465).
-   George and Ponattu 2018 [Like father, like son? The economic impacts of political dynasties](http://barrett.dyson.cornell.edu/NEUDC/paper_550.pdf).


<a id="org1b5e0c9"></a>

# Acknowledgements

Eric Magar is grateful for financial support from the Asociación Mexicana de Cultura A.C. He is responsible for mistakes and shortcomings in the data.


<a id="orgeafc33e"></a>

# Donate

If you find this useful, help buy a cup of coffee for the author and research assistants. [![img](https://www.paypalobjects.com/en_US/i/btn/btn_donate_LG.gif)](https://www.paypal.com/donate?business=FQDMH76GZC8WQ&currency_code=USD) with Paypal.


<a id="org61fe933"></a>

# References

-   Hijmans, Robert J. 2019. `raster`: Geographic Data Analysis and Modeling ver 3.0-2, <https://CRAN.R-project.org/package=raster>.
-   Li, Xuecao, Yuyu Zhou, Min Zhao, and Xia Zhao. 2020. A harmonized global nighttime light dataset 1992–2018. *Scientific Data* 7(1), <https://doi.org/10.1038/s41597-020-0510-y>.
