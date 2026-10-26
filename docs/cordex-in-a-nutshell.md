---
title: index.md
summary: central guidance to contribute to CORDEX
authors:
    - Lluis Fita
    - CORDEX TTPI
date: 2026-09-30
some_url: https://wcrp-cordex.github.io/cordex-guidance/
---
# CORDEX in a nutshell

!!! danger "This page in under construction"

This page introduces the main steps and resources for institutions planning to contribute simulations to CORDEX.

CORDEX is a community framework for coordinating regional climate downscaling across research groups and regions.
Its shared protocols help make simulations comparable and their data easier to discover, access, and use in climate research, impact studies, and decision-making.

A CORDEX contribution generally involves three steps:

1. Run a downscaling simulation for a CORDEX domain, following the relevant experiment protocol.
2. Prepare and archive the output according to the applicable data and metadata standards.
3. Make the data available to the community, typically through the Earth System Grid Federation (ESGF).

CORDEX provides protocols and guidance for the different parts of this process, from experiment design to data publication.
This site brings those resources together and points to their current versions for both new and experienced contributors.

CORDEX data are published through the _Earth System Grid Federation_ ([ESGF](https://www.climateurope.eu/esgf-earth-system-grid-federation/)), a distributed system for publishing and discovering climate data.
To make datasets interoperable and searchable, contributors follow the conventions and metadata requirements specified for the relevant CORDEX activity and experiment.

## Before the experiment
CORDEX's _Science Advisory Team_ ([SAT](https://cordex.org/about/science-adv-team/)) provides scientific guidance and develops experiment protocols with the community.
CORDEX is organized around regional domains, each linking a defined geographic area with a community of researchers and institutions working in that region.
_Points of Contact_ ([POCs](https://cordex.org/about/points-of-contact/)) connect these regional communities with CORDEX-wide activities.
Before starting a contribution, contact the relevant POC to discuss regional priorities, ongoing activities, and how your work can align with them.

## Design of the experiment
CORDEX accommodates different methods for downscaling climate information.
The two broad categories are:

- _Regional climate models (RCMs)_: numerical models that represent physical processes and relationships among climate variables.
- _Empirical-statistical downscaling (ESD)_: methods that use statistical relationships between large-scale climate information and local or regional climate variables.

Downscaling is performed for a defined CORDEX domain and period, using a specified source of **forcing data** (the large-scale climate information used to drive or inform the downscaling method).
Depending on the experiment protocol, contributions commonly include simulations of the following types:

| Simulation | Description | Forcing (example) | Period |
|:------------:|:------------ |:------------:|:------------:|
| Evaluation | Simulation used to assess model performance, commonly driven by reanalysis data | Reanalysis | Historical or present-day climate |
| Historical | Simulation driven by a global climate model (GCM) simulation of past climate | CMIP historical experiment | Historical climate |
| Future | Simulation driven by a GCM projection under a specified future scenario | CMIP scenario experiment | Future climate |

The SAT develops experiment protocols in consultation with the CORDEX community.
Protocols evolve as climate science and the _Coupled Model Intercomparison Project_ ([CMIP](https://www.wcrp-cmip.org/)) advance, so the applicable requirements depend on the CORDEX activity and protocol you are contributing to.
Available protocol versions include:

- CORDEX-CMIP5 protocols: [RCMs](https://cordex.org/experiment-guidelines/cordex-cmip5/experiment-protocol-cordex-cmip5-rcms/) and [ESD](https://cordex.org/experiment-guidelines/cordex-cmip5/experiment-protocol-cordex-cmip5-esd/).
- CORDEX-CMIP6 protocol for RCMs: [protocol](https://zenodo.org/records/15268192).
- CORDEX-CMIP7-AFT protocol: under development.
- CORDEX-CMIP7 protocol: under development.

The protocols do not prescribe every detail of model configuration for each domain, so discuss regional setup choices with the relevant POC.
Before committing to long simulations, test the configuration selected for your model and domain, including its sensitivity to key choices where practical.
A community task is developing a skill-based assessment of GCMs for each CORDEX domain, based on how well they represent key regional climate features ([task](url)).
The CORDEX-CMIP7 activity is planned in two phases: an initial phase using the first available CMIP7 forcing data through CMIP7-AFT, followed by a phase using standard CMIP7 data.
The CMIP7-AFT data are intended to support preparation for the IPCC Seventh Assessment Report (AR7).

### CORDEX domain
A CORDEX [domain](https://cordex.org/domains/cordex-domain-description/) is both a defined geographic area for regional climate simulations and a community of researchers and institutions working in that region.
As a key organizational structure within CORDEX, each domain provides a focus for regional collaboration, discussion of priorities, and coordination of contributions.
The domain description sets out its geographic boundaries, while the relevant experiment protocol and data requirements specify the spatial coverage expected for simulations.

## Data-sharing
Sharing data among CORDEX participants is central to the initiative.
To support this, CORDEX specifies which variables to provide and how datasets should be formatted and described.

### Data request
A _Data Request_ lists the variables that contributors are asked to provide for an experiment.
Variables are assigned priorities, such as Core, Tier 1, and Tier 2, which indicate the expected contribution level.
The request also specifies details such as the required temporal frequency for each variable.
This helps make the data useful to a wide range of users while keeping production demands manageable for contributing institutions.
Data requests depend on the experiment; see the [CORDEX-CMIP6 Data Request](https://wcrp-cordex.github.io/data-request-table/dreq_default.html) for an example.
 
### Standardization
CORDEX data must follow common formatting and metadata rules so datasets from different institutions, models, and domains can be used together.
These rules build on standards such as the [CF Conventions](https://cfconventions.org/) and are described in the relevant archive specifications.
Those include a _Data Reference Syntax_ (DRS), which defines how datasets (files) are organized and named, and _Controlled Vocabularies_ (CVs), which provide approved identifiers for items such as institutions, models, and experiments.
In many cases, modellers wanting to share data under a CORDEX projet must first _register_ the identifiers of their insitution and model in the appropriate repository.

ESGF uses this metadata to index datasets and help users find available data. 
Preparing climate model output to meet a project's variable, metadata, and file-format requirements is commonly called _CMORization_ because it is often done with the [`cmor` tool](https://cmor.llnl.gov/).
Publishing through ESGF requires datasets to use the standards explained above, which is tested with a metadata compliance checker prior to publication, more on that below.

!!! info "Useful links"
    For CORDEX-CMIP6:
    - [Archive specifications](https://wcrp-cordex.github.io/archive-specifications/CORDEX-CMIP6_archiving_specifications_DD/)
    - [Controlled vocabularies](https://github.com/WCRP-CORDEX/cordex-cmip6-cv)
    - [CMOR Tables in JSON format](https://github.com/WCRP-CORDEX/cordex-cmip6-cmor-tables)
    - [An interactive view of the registered vocabularies](https://esgvoc.ipsl.fr/?projects=cordex-cmip6)

#### Example
The directory and filename patterns below illustrate the CORDEX-CMIP6 DRS; use the proper protocol and controlled vocabularies for the activity and project you are contributing to.

Directory structure is:
```
<project_id>
  <activity_id>/
    <domain_id>/
      <institution_id>/
        <driving_source_id>/
          <driving_experiment_id>/
            <driving_variant_label>/
              <source_id>/ 
                <version_realization>/
                  <frequency>/
                    <variable_id>/
                      <version>/
```

In this CORDEX-CMIP6 example, the filename combines DRS elements in the following order:
```
<variable_id>_<domain_id>_<driving_source_id>_<driving_experiment_id>_<driving_variant_label>_<institution_id>_<source_id>_<version_realization>_<frequency>_[<start_time>-<end_time>].nc"
```

The values for each element come from the experiment definition, the relevant controlled vocabularies, or the simulation output.
A full description is available in the [archive specifications](https://wcrp-cordex.github.io/archive-specifications/CORDEX-CMIP6_archiving_specifications_DD/#4-esgf-directory-structure). Given links are valid for CORDEX-CMIP6.

- `<project_id>`: "CORDEX-CMIP6", the name of the project inside ESGF.
- `<activity_id>`: the CORDEX activity, such as `DD` for dynamical downscaling or `CPM` for convection-permitting modelling.
- `<domain_id>`: the identifier of a declared CORDEX domain from the [domain tables](https://github.com/WCRP-CORDEX/domain-tables/).
- `<institution_id>`: the identifier of a registered institution from the [institution vocabulary](https://github.com/WCRP-CORDEX/cordex-cmip6-cv/blob/main/CORDEX-CMIP6_institution_id.json); contact your POC if your institution is not listed.
- `<driving_source_id>`: the identifier of the GCM providing the forcing, selected from the [GCM vocabulary](https://wcrp-cmip.github.io/CMIP6_CVs/docs/CMIP6_source_id.html).
- `<driving_experiment_id>`: the identifier of the CMIP experiment providing the forcing, selected from the [experiment vocabulary](https://wcrp-cmip.github.io/CMIP6_CVs/docs/CMIP6_experiment_id.html).
- `<driving_variant_label>`: the identifier of the GCM ensemble member, following CMIP syntax (`r?i?p?f?` for CMIP6).
- `<source_id>`: the identifier of the regional climate model, selected from the [RCM vocabulary](https://github.com/WCRP-CORDEX/cordex-cmip6-cv/blob/main/CORDEX-CMIP6_source_id.json); contact your POC if your model is not listed.
- `<version_realization>`: the identifier of the RCM ensemble member or simulation version. Following the `v?-r?` syntax.
- `<frequency>`: the output frequency, selected from the [frequency vocabulary](https://github.com/WCRP-CORDEX/cordex-cmip6-cv/blob/main/CORDEX-CMIP6_frequency.json).
- `<variable_id>`: the variable identifier, selected from the data request (see above).
- `<version>` : the date of creation of this published dataset. This only appears in the directory structure, not in the metadata. Usually, users should simply select the latest version.
- `<start_time>-<end_time>`: a date range indicating the period covered by the file (absent for fixed fields).

#### Checking before uploading
Before publication, run the checks required by the applicable protocol.
For example, the following tools support preparation and validation of CORDEX data:

- [ncrepack-cordex](https://github.com/WCRP-CORDEX/ncrepack-cordex): repacks NetCDF files to facilitate downloading and analysis.
- [esgf-qa](https://github.com/ESGF/esgf-qa): checks data against ESGF quality-assurance requirements.

#### Uploading
Uploading CORDEX-CMIP6 data to the ESGF follows the same steps as for CMIP7, and is described here : https://wcrp-cmip.github.io/cmip7-guidance/docs/CMIP7/Guidance_for_ESGF/.
The only difference in the process is specifying `CORDEX-CMIP6` as the project name instead of `CMIP7` were applicable.
