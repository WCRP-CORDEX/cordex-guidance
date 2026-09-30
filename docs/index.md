---
title: index.md
summary: central guidance to contribute to CORDEX
authors:
    - Lluis Fita
    - CORDEX TTPI 
date: 2026-09-30
some_url: https://wcrp-cordex.github.io/cordex-guidance/
---
# CORDEX guidance documents

**UNDER CONSTRUCTION**

This site provides guidance documents for CORDEX modellers and data users. 
The main objective is to orient any institution willing to contribute to CORDEX with a new experiment.

The main goal of a CORDEX experiment is to perform a downscaling of climate information in a coordinate manner with other research entities. 
In order to achieve that CORDEX provides an experimental framework designed to provide reliable climate information over an specific area through the collaboration among multiple researchers. 
Aiming to provide a landscape where data can be shared to facilitate hydroclimatic research, studies on impacts and policymaking.

A CORDEX experiment basically encompasses the following steps:
1. Execution of a numerical downscaling experiment inside a CORDEX domain
2. Archive output data following standardization protocol
3. Share the data to the community

Due to the coordination goal at the core of the CORDEX experiment, multiple documentations and guides are required in order to ensure the correct understanding among the multiple actors involved covering all the aspects of the experiment. 
This _'guidance'_ aims to providing a central unique point of access to all this documentation either for new contributions or experienced ones by giving access to the latest versions of each document. 

In recent years, CORDEX related data has been made accessible throughout the _'Earth System Grid Federation'_ ([ESGF](https://www.climateurope.eu/esgf-earth-system-grid-federation/)). 
In order to achieve that, CORDEX data has to follow precise ESGF standards which are trying to mimic the CMIP standard.

## Before the experiment
CORDEX has a _'Science Advisory Team'_ ([SAT](https://cordex.org/about/science-adv-team/)) which coordinates the experiment. 

CORDEX defined a series of domains which cover the entire land masses. 
For each land mass, there are representatives of CORDEX known as _'Points of Contact'_ ([POC](https://cordex.org/about/points-of-contact/)). 
Is highly recommended to contact the local POC in order to insert any new experiment within the on-going activities in the specific domain.

## Design of the experiment
Any CORDEX experiment will use in its core a modeling tool which should follow a given scientific methodology. 
CORDEX defines 2 main categories:
- _Regional Climate Model (RCM)_: models that solve the physical equations and relationships among climate variables
- _Empirical­-Statistical Downscaling (ESD)_: models based on mathematical or statistical relationships among climate variables

This models are applied over a given CORDEX domain over a given period of time. 
A CORDEX experiment requires the selection of a **forcing** (data provided for an external source) a given **period** of time over which the downscaling will be produced. In general the experiment is based in 3 main simulations:

| Name     | Description | Forcing (example) | Period |
|:------------:|:------------ |:------------:|:------------:|
| evaluation | Simulation under controlled forcing to understand systematic model errors | re-analysis | current climate |
| historical | Simulation using a forcing from an external source | CMIP | current climate |
| future | Simulation using same forcing source as 'historical' | CMIP | future climate |

In consultancy with the entire community, SAT provides an experiment protocol to be followed. There are different versions of the protocol which inherit the state-of-the-art at each certain period mostly related to the _'Coupled Model Intercomparison Project'_ [CMIP](https://www.wcrp-cmip.org/) cycle at the moment of its inception. Therefore it can be found:
- CORDEX CMIP5 protocol: [RCM](https://cordex.org/experiment-guidelines/cordex-cmip5/experiment-protocol-cordex-cmip5-rcms/), [ESD](https://cordex.org/experiment-guidelines/cordex-cmip5/experiment-protocol-cordex-cmip5-esd/)
- CORDEX CMIP6 protocol: [RCM](https://zenodo.org/records/15268192)
- CORDEX CMIP7-AFT protocol (under elaboration)
- CORDEX CMIP7 protocol (under elaboration)

Fine scale details in how to configure modeling tools over an specific CORDEX domain are not imposed, but a coordination with the respective POC is recommended. 
Also is recommended to perform some sensitivity tests of the _most suited_ configuration of the model at the given domain before performing the long simulations.

### Modeling tool
CORDEX aims to accommodate any numerical tool or methodology designed to provide a scientifically-based numerical representation of the climate system. 
Since climate modeling science is a continuously evolving topic, new concepts tend to arise. 
CORDEX aims to incorporate also the new ones aiming to enrich the lines of evidence for study of the climate and the potential uses of the produced data.

### CORDEX domain
CORDEX defines a series of [domains](https://cordex.org/domains/cordex-domain-description/). 
These domains provide the minimal spatial extent in which any experiment has to contribute with data.

## Data-sharing
Sharing of the data among CORDEX participants it is at the core of the initiative. 
In order to achieve that, CORDEX establishes 2 main protocols: list of variables and standardization.

### Data request
A list of required variables is provided known as _Data Request_. 
These variables are grouped in different priorities: Core, Tier1, Tier2. 
Each group contains a different variables and/or frequencies at which the variable has to be provided. 
The main objective is to provide enough data to maximize the usability of the produced data without overwhelming the institutions that produce the data. 
They depend on the design experiment see the [CORDEX-CMIP6](https://wcrp-cordex.github.io/data-request-table/dreq_default.html) as the last available one.
 
### Standardization
Any data to be incorporated into CORDEX has to follow a series of rules in order to guarantee the interoperability of data-sets produced from different institutions, models and domains. 
These rules are based (but not limited) on the [CF-conventions](https://cfconventions.org/).

### ESGF
Since the possibility to upload CORDEX data into ESGF nodes, a new series of protocols and standards have to be followed. 
ESGF introduces a series of _'Data Reference Syntax'_ (DRS), _'Controlled Vocabulary'_ (CV) among others. 
These elements consists in a series of tables used by the ESGF nodes to directly consult which data is available.

These ESGF-derived standardization encompasses all the metadata of any file archived in the ESGF. From the register of institutions, models, activities to the name of the archive itself. 
All this register infrastructure is controlled via GIT repository and managed by researchers designated by CORDEX SAT.

The CORDEX DRS path follows the directory structure:
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

For file names, the DRS elements are joined by underscores and organized in the following order (example from CMIP5):
```
<VariableName>_<Domain>_<GCMModelName>_<CMIP5ExperimentName>_<CMIP5EnsembleMember>_<RCMModelName_RCMVersionID<_<Frequency>[_StartTime-EndTime].nc 
```

Each entry has different sources. A full description can be found in this output specifications [OutputFile](url)

- `<activity>`: activity of the experiment (by now only `DYN`: dynamic downscaling, `ESD`: Empirical­-Statistical Downscaling)
- `<product>`:
- `<Domain>`: one of the declared domains from this [CV-domains](url)
- `<Institution>`: one of the declared institutions from this [CV-institutions](url). **NOTE**: contact your POC in case your institution is not listed
- `<GCMModelName>`: one of the declared CMIP GCMs from this [CV-GCMS](url) used as forcing
- `<CMIP5ExperimentName>`: one of the declared CMIP experiments of the GCM from this [CV-ExpName](url) used as forcing
- `<CMIP5EnsembleMember>`: one of the declared CMIP members of the runs of the GCM from this [CV-GCMEns](url)
- `<RCMModelName>`: one of the declared RCMs from this [CV-RCMs](url). **NOTE**: contact your POC in case your RCM is not listed
- `<RCMVersionID>`: one of the declared versions of the RCM from this [CV-RCMversion](url). **NOTE**: contact your POC in case your RCM is not listed
- `<Frequency>`: one of the declared output freqeuncies from this [CV-Frequency](url)
- `<VariableName>`: one of the declared name of variables from this [CV-variables](url)
- `[_StartTime-EndTime]`: format of the period covered by the file

#### Checking before uploading
Before data can be upload 2 steps are necessary:
- [ncrepack-coredex](https://github.com/WCRP-CORDEX/ncrepack-cordex): tool to repack the data inside the files in order to facilitate downloading and analysis
- [esgf-qa](https://github.com/ESGF/esgf-qa): tool to check ESGF compilance of the data

