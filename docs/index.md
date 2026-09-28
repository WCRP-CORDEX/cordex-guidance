# CORDEX guidance documents

** UNDER CONSTRUCTION **

This site provides guidance documents for CORDEX modellers and data users. The main objective is to orient any institution willing to contribute to CORDEX with a new experiment.

The main goal of a CORDEX experiment is to perform a downscaling of climate information in a coordinate manner with other research entities. In order to achieve that CORDEX provides an experimental framework designed to provide reliable climate information over an specific area through the collaboration among multiple researchers. Aiming to provide a landscape where data can be shared to facilitate hydroclimatic research, studies on impacts and policymaking.

A CORDEX experiment basically encompasses the following steps:
1. Execution of a numerical downscaling experiment inside a CORDEX domain
2. Archive output data following standardization protocol
3. Share the data to the community

Due to the coordination goal at the core of the CORDEX experiment, multiple documentations and guides are required in order to ensure the correct understanding among the multiple actors involved covering all the aspects of the experiment. This 'guidance' aims to providing a central unique point of access to all this documentation either for new contributions or experienced ones by giving access to the latest versions of each document. 

In recent years, CORDEX related data has been made accessible throughout the _'Earth System Grid Federation'_ ([ESGF](https://www.climateurope.eu/esgf-earth-system-grid-federation/)). In order to achieve that, CORDEX data has to follow precise ESGF standards which are trying to mimic the CMIP standard.

## Before the experiment
CORDEX has a _'Science Advisory Team'_ ([SAT](https://cordex.org/about/science-adv-team/)) which coordinates the experiment. 

CORDEX defined a series of domains which cover the entire land masses. For each land mass, there are representatives of CORDEX known as _'Points of Contact'_ ([POC](https://cordex.org/about/points-of-contact/)). Is highly recommended to contact the local POC in order to insert any new experiment within the on-going activities in the specific domain.

## Design of the experiment
Any CORDEX experiment will use in its core a modeling tool which should follow a given scientific methodology. CORDEX defines 2 main categories:
- _Regional Climate Model (RCM)_: models that solve the physical equations and relationships among climate variables
- _Empirical­-Statistical Downscaling (ESD)_: models based on mathematical or statistical relationships among climate variables

This models are applied over a given CORDEX domain over a given period of time. A CORDEX experiment requires the selection of a **forcing** (data provided for an external source) a given **period** of time over which the downscaling will be produced. In general the experiment is based in 3 main simulations:
| Name     | Description | Forcing (example) | Period |
| ---      | ---       | ---       | ---       |
| evaluation | Simulation under controlled forcing to understand systematic model errors | re-analysis | current climate |
| historical | Simulation using a forcing from an external source | CMIP | current climate |
| future | Simulation using same forcing as 'historical' | CMIP | future climate |

In consultancy with the entire community, SAT provides an experiment protocol to be followed. There are different versions of the protocol which inherit the state-of-the-art at each certain period mostly related to the _'Coupled Model Intercomparison Project'_ [CMIP](https://www.wcrp-cmip.org/) cycle at the moment of its inception. Therefore it can be found:
- CORDEX CMIP5 protocol: [RCM](https://cordex.org/experiment-guidelines/cordex-cmip5/experiment-protocol-cordex-cmip5-rcms/), [ESD](https://cordex.org/experiment-guidelines/cordex-cmip5/experiment-protocol-cordex-cmip5-esd/)
- CORDEX CMIP6 protocol: [RCM](https://zenodo.org/records/15268192)
- CORDEX CMIP7-AFT protocol (under elaboration)
- CORDEX CMIP7 protocol (under elaboration)

Fine scale details in how to configure modeling tools over an specific CORDEX domain are not imposed, but a coordination with the respective POC is recommended.

### Modeling tool
CORDEX aims to accommodate any numerical tool or methodology designed to provide a scientifically-based numerical representation of the climate system. Since climate modeling science is a continuously evolving topic, new concepts tend to arise. CORDEX aims to incorporate also the new ones aiming to enrich the lines of evidence for study of the climate and the potential uses of the produced data.

### CORDEX domain
CORDEX defines a series of [domains](https://cordex.org/domains/cordex-domain-description/). These domains provide the minimal spatial extent in which any experiment has to contribute with data.
