# CORDEX data citation service

!!! danger "This page in under construction"

CORDEX data citations will be created automatically in response to data publication on ESGF.
Data citations can be explored at [https://cmip7-citations.ceda.ac.uk](https://cmip7-citations.ceda.ac.uk) and detailed guidance is provided at [https://wcrp-cmip.github.io/cmip7-guidance/docs/CMIP7/Citation_Guidance](https://wcrp-cmip.github.io/cmip7-guidance/docs/CMIP7/Citation_Guidance/).
This document only provides CORDEX-specific instructions for the modelling teams.

## Author information

Citation entries are created automatically after data publication on ESGF.
Author information is empty, with the primary author assigned to the _Citation Support_.
At this point, representative from the modelling team can request reviewer access.
For this purpose, the **reviewer must have a GitHub account** and sign in as reviewer (at the top right corner of the [Citation service interface](https://cmip7-citations.ceda.ac.uk)).
Then they can navigate to the entry they'd like to edit and click on **Request Reviewer Access** (at the bottom of any tab).
In the dialogue, check the institutions for which you are requesting edit access.
The access is not instantaneous, as the reviewer access is moderated to make sure that not anyone can modify the entries.

Once Reviewer Access is granted, the reviewer can fill out some of the fields.
One important piece of information to fill out is the author information in the _Responsible Parties_ tab.
Here, a primary author needs to be defined for each entry along with as many other contacts as necessary.
The citation service is mainly a mean to **give credit to all authors** of a simulation, so be exhaustive in recognizing all contributors.

Affiliation information when showing an author (_Parties_ view) is automatically retrieved from their ORCID.
Please, advise all authors to have their **ORCID record updated**, so the information shown is accurate.

Reviewer access can be granted to several people in the same institution and the reviewer does not need to be the primary author.

## Citation abstract template

In the general information, citation entries show a default Abstract that can be edited.
The default abstract in CMIP7 entries is automatically created created out of the Essential Model Documentation (EMD) information.
In CORDEX, as there is no EMD for the time being, the abstract shows just some basic information retrieved from _esgvoc_ vocabularies. For example:

```
Project: project_id: CORDEX-CMIP6

activity_id: DD

CORDEX Domain: Central America

Produced by: Centre National de Recherches Meteorologiques (Using Model/Source: CNRM-ALADIN64C1 with Experiment historical)

source_id: CNRM-ALADIN64C1
```

We strongly suggest to edit this abstract and use the following common structure, in order to give CORDEX entries a homogeneous look with a similar detail in the Abstract:

```
Project: CORDEX-CMIP6
Activity: Dynamical downscaling on standard CORDEX continental domains (CORDEX-Domain) [DD]
CORDEX Domain: North America [NAM-12]
Source: Canadian Regional Climate Model version 5 [CRCM5-SN]

Produced by: Ouranos Consortium on Regional Climatology and Adaptation to Climate Change (Québec, Canada) [OURANOS]

Grid configuration : NAM-12 CORDEX North American domain at 0.11°, 695x668 grid points including a 20-point sponge (and halo) zone surrounding the domain, 5-minute time steps, 56 vertical levels and a top at 10 hPa. 17 soil levels and a bottom at 15 m.

Spectral Nudging : A spectral nudging is applied to the horizontal wind component with a half-response wavelength of 1177km and a relaxation time of 13.34 h. The nudging strength is set to zero from the surface to a height of 500 hPa and increases linearly onward to the top of the model’s simulated atmosphere.

Atmosphere:
Precipitation: large-scale condensation scheme (Sundqvist, 1998); precipitation partition diagnostic method (Bourgouin, 2000)
Shallow convection: based on transient version of Kuo (1965) scheme (Bélair et al. 2005)
Deep convection: Kain-Fritsch (1990)
Radiation: Li & Barker (2005)

Surface: CLASS3.5c (Verseghy, 1993)
Lake model: FLake (Martinov et al. 2012)
Ocean: Prescribed SST & sea ice fraction
Aerosol: Fixed

The CRCM5-SN is developed by the ESCER Centre at UQAM (Université du Québec à Montréal) with the collaboration of Environment and Climate Change Canada (ECCC), based on GEM 3.3.3.1 from ECCC.

This record was created via the CEDA Citation Service, maintained and hosted on the CEDA JASMIN Infrastructure.
```

## References

The References tab is intended for key publications further describing your model or model components, or showing their usage for various results.
References can be updated after the DOI has been minted, so there is no need to create a new version of the citation entry to include a new reference.

## Resources

 - [Citation service interface](https://cmip7-citations.ceda.ac.uk)
 - [CMIP7 Citation service guidance](https://wcrp-cmip.github.io/cmip7-guidance/docs/CMIP7/Citation_Guidance)
