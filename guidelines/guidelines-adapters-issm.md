---
title: Standardization example - ISSM adapter
permalink: community-guidelines-adapters-issm.html
keywords: contribute, develop, adapters, standardization, preECO, ISSM
summary: A review of the ISSM adapter using the contributing guidelines. This is a work-in-progress that will eventually be moved.
toc: true
---

The ISSM adapter conforms to most of the preCICE best practices.

Metadata:

- M.1: ISSM
- M.2: https://git.rwth-aachen.de/terrabyte-dnn2sim/issm-precice
- M.3: BSD-3-Clause
- M.4: Daniel Abele `<daniel.abele dlr.de>`, Angelika Humbert `<angelika.humbert awi.de>`
- M.5: https://doi.org/10.5194/egusphere-2025-3345
- M.6: stand-alone

Required best practices:

- [ ] R.1: Two application cases are available at https://doi.org/10.5281/zenodo.15849145. The cases do not follow the guidelines for application cases, mainly file/directory structure and naming conventions. Additionally, the input data for ISSM is in binary form and only compatible with ISSM version 4.24.
- [x] R.2: [`README.md`](https://git.rwth-aachen.de/terrabyte-dnn2sim/issm-precice/-/blob/main/README.md)
- [x] R.3: [`LICENSE`](https://git.rwth-aachen.de/terrabyte-dnn2sim/issm-precice/-/blob/main/LICENSE)
- [x] R.4: [GitLab project](https://git.rwth-aachen.de/terrabyte-dnn2sim/issm-precice)
- [x] R.5: The project uses semantic versioning.
- [x] R.6: [`CHANGELOG.md`](https://git.rwth-aachen.de/terrabyte-dnn2sim/issm-precice/-/blob/main/CHANGELOG.md)
- [x] R.7: [issue tracker on GitLab](https://git.rwth-aachen.de/terrabyte-dnn2sim/issm-precice/-/issues)
- [x] R.8: [`.clang-format`](https://git.rwth-aachen.de/terrabyte-dnn2sim/issm-precice/-/blob/main/.clang-format)
- [ ] R.9: Error handling is inconsistent. Many errors are checked and caught, but messages are often generic and not helpful.
- [ ] R.10: The adapter config conforms to the recommended schema, limitations are documented in ([docs](https://git.rwth-aachen.de/terrabyte-dnn2sim/issm-precice/-/blob/main/doc/configfileformat.md)). Loading from default location is currently not supported. 
- [x] R.11: The adapter uses the same vertices in 2D or 3D space as ISSM itself.
- [ ] R.12: Flux directions are currently not considered.

Additional criteria:

- [x] A.1: BSD-3-clause
- [x] A.2: [repository](https://git.rwth-aachen.de/terrabyte-dnn2sim/issm-precice) is publicly accessible
- [ ] A.3: Documentation is only available as markdown on GitLab 
- [x] A.4: Console output is configurable at run-time, but cannot be turned off entirely. The options are `errors\warnings`, `verbose` and `trace`
- [ ] A.5: A [paper](https://doi.org/10.5194/egusphere-2025-3345) is in peer-review with limited validation for real life use.
- [x] A.6: [`CONTRIBUTING.md`](https://git.rwth-aachen.de/terrabyte-dnn2sim/issm-precice/-/blob/main/CONTRIBUTING.md)
- [ ] A.7: Pull request template not available.
- [ ] A.8: No documentation specifically for extending the adapter. 
- [x] A.9: Coverage of the unit test suite is reported in the GitLab project. Input data for a small number of unit tests is currently not publicly available.  
- [ ] A.10: The adapter is not integrated into the preCICE system tests.
- [ ] A.11: Complicated dependencies and build process of ISSM make deployment with a package manager difficult.
