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
CORDEX has defined regional domains spanning land areas around the world.
_Points of Contact_ ([POCs](https://cordex.org/about/points-of-contact/)) represent CORDEX in the regions covered by these domains.
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

### Modeling tool
CORDEX aims to accommodate scientifically sound tools and methods for representing regional climate, including approaches that emerge as the field develops.
Using different methods can provide complementary evidence about climate processes and possible future changes.

### CORDEX domain
CORDEX defines a set of [domains](https://cordex.org/domains/cordex-domain-description/) that provide a shared geographic framework for regional simulations.
The experiment protocol and data requirements specify the spatial coverage expected for a contribution to each domain.

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
These rules build on standards such as the [CF Conventions](https://cfconventions.org/) and are described in the relevant [output protocol](url).
Preparing model output to meet a protocol's variable, metadata, and file-format requirements is commonly called _CMORization_.

### ESGF
Publishing through ESGF also requires datasets to use the identifiers and metadata expected by the relevant CORDEX activity.
These include a _Data Reference Syntax_ (DRS), which defines how datasets are organized and named, and _Controlled Vocabularies_ (CVs), which provide approved identifiers for items such as institutions, models, and experiments.
ESGF uses this metadata to index datasets and help users find available data.

The CORDEX vocabularies and related publication metadata are maintained in community repositories by designated maintainers.
The directory and filename patterns below illustrate the CORDEX-CMIP5 DRS; use the current protocol and controlled vocabularies for the activity you are contributing to.

In this CMIP5 example, the directory structure is:
```
<activity>/
  <product>/
    <Domain>/
      <Institution>/
        <GCMModelName>/
          <CMIP5ExperimentName>/
            <CMIP5EnsembleMember>/
              <RCMModelName>/
                <RCMVersionID>/
                  <Frequency>/
                    <VariableName>
```

In this CMIP5 example, the filename combines DRS elements in the following order:
```
<VariableName>_<Domain>_<GCMModelName>_<CMIP5ExperimentName>_<CMIP5EnsembleMember>_<RCMModelName>_<RCMVersionID>_<Frequency>[_<StartTime>-<EndTime>].nc
```

The values for each element come from the experiment definition, the relevant controlled vocabularies, or the simulation output.
A full description is available in the [output specifications](url).

- `<activity>`: the CORDEX activity, such as `DYN` for dynamical downscaling or `ESD` for empirical-statistical downscaling.
- `<product>`: the product category defined by the relevant activity's DRS.
- `<Domain>`: the identifier of a declared CORDEX domain from the [domain vocabulary](url).
- `<Institution>`: the identifier of a registered institution from the [institution vocabulary](url); contact your POC if your institution is not listed.
- `<GCMModelName>`: the name of the CMIP GCM providing the forcing, selected from the [GCM vocabulary](url).
- `<CMIP5ExperimentName>`: the name of the CMIP5 experiment providing the forcing, selected from the [experiment vocabulary](url).
- `<CMIP5EnsembleMember>`: the identifier of the GCM ensemble member, selected from the [GCM ensemble vocabulary](url).
- `<RCMModelName>`: the name of the regional climate model, selected from the [RCM vocabulary](url); contact your POC if your model is not listed.
- `<RCMVersionID>`: the registered version of the regional climate model, selected from the [RCM version vocabulary](url); contact your POC if your model version is not listed.
- `<Frequency>`: the output frequency, selected from the [frequency vocabulary](url).
- `<VariableName>`: the variable identifier, selected from the [variable vocabulary](url).
- `[_<StartTime>-<EndTime>]`: an optional date range indicating the period covered by the file.

#### Checking before uploading
Before publication, run the checks required by the applicable protocol.
For example, the following tools support preparation and validation of CORDEX data:

- [ncrepack-cordex](https://github.com/WCRP-CORDEX/ncrepack-cordex): repacks NetCDF files to facilitate downloading and analysis.
- [esgf-qa](https://github.com/ESGF/esgf-qa): checks data against ESGF quality-assurance requirements.

