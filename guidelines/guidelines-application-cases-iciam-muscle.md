---
title: Standardization example - electrophysiological three-tendon-biceps model
permalink: community-guidelines-application-cases-iciam-muscle.html
keywords: contribute, develop, application cases, standardization, preECO, OpenDiHu, muscles
summary: A review of a multi-physics muscle application case using the contributing guidelines. This is a work-in-progress that will eventually be moved.
toc: true
---

The data set "electrophysiological three-tendon-biceps model" does not conform to all of the preCICE best practices, but most could be implemented for a similar case in the future.

Metadata:

- M.1: Electrophysiological three-tendon-biceps model
- M.2: https://doi.org/10.18419/DARUS-4228
- M.3: Various, see DOI
- M.4: Carme Homs-Pons, David Schneider `<david.schneider ipvs.uni-stuttgart.de>`, Frédéric Simonis, Miriam Schulte, Benjamin Uekermann
- M.5: OpenDiHu (archive included, no reference to release/commit TODO really?), deal.II (TODO), ASTE (TODO)
- M.6: v3.1.2
- M.7: The data set contains software, setup files, and instructions to reproduce the three experiments of the paper "Partitioned Multiphysics Simulation of an Electrophysiological Three-Tendon-Biceps Model": "Volume coupling of muscle fiber and muscle mechanics", "multi coupling of muscle mechanics and three tendons", and "compositional coupling".
- M.8: (Optional) TODO private?
- M.9: (Optional) Related publication: TODO
- M.10: Used preCICE features. Curated list includes:
  - [x] explicit coupling
  - [x] implicit coupling
  - [x] compositional coupling
  - [x] multi coupling
  - [x] quasi-Newton acceleration
  - [x] nearest-projection mapping or linear cell interpolation
  - [x] RBF data mapping
  - [ ] GPU computing
  - [ ] direct access
  - [ ] just-in-time data mapping
  - [ ] geometric multi-scale data mapping
  - [ ] adaptive time stepping
  - [ ] waveform relaxation (order >= 2)
  - [ ] two-level initialization
  - [ ] dynamic meshes

Required best practices:

- [x] R.1: Included in data set
- [ ] R.2: The participants are not started from different folders. Running and cleaning scripts are not provided. The structure could be fixed, but tedious for such an existing case. It would, however, imply some code duplication for participants that use the same solver (tendon-top-a and tendon-top-b) (TODO: really?).
- [ ] R.3: A description of the physics, a visualization of the preCICE configuration, and instructions for post-processing are missing. Building and running instructions are there.
- [ ] R.4: The configuration file is either named `precice_config.xml` or in case of several files, it has a descriptive name such as `precice_config_IQN_ILS_mui_50_twr_100.xml`.
- [ ] R.5: Not formatted
- [ ] R.6: Not checked 
- [ ] R.7: Names don't use a `-` as separator, e.g., `TendonTopBMesh`. Some mesh names don't follow the pattern of concatenating the participant name and `-Mesh`. This was actually a conscious choice to indicate a subsection of the participant: `MuscleMeshBottom`, `MuscleMeshTopB` and `MuscleMeshTopA` (TODO: `Muscle-Top-A-Mesh`?). Participant names reflect the subdomain, e.g. `MuscleMechanics` and `MuscleFibers`.
- [ ] R.8: Not included
- [ ] R.9: Not included

Additional criteria:

- [x] A.1: TODO: True for OpenDiHu?
- [ ] A.2: Not included
- [x] A.3: Full results are included
- [ ] A.4: Not included
- [ ] A.5: Not included
- [x] A.6: TODO
