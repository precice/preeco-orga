---
title: Standardization example - OpenFOAM adapter
permalink: community-guidelines-adapters-openfoam.html
keywords: contribute, develop, adapters, standardization, preECO, OpenFOAM
summary: A review of the OpenFOAM adapter using the contributing guidelines. This is a work-in-progress that will eventually be moved.
toc: true
---

The OpenFOAM adapter conforms to the preCICE best practices and fulfills many of the additional criteria.

Metadata:

- M.1: OpenFOAM
- M.2: https://precice.org/adapter-openfoam-overview.html
- M.3: GPL-3.0
- M.4: Gerasimos Chourdakis `<gerasimos.chourdakis ipvs.uni-stuttgart.de>`, David Schneider `<david.schneider ipvs.uni-stuttgart.de>`
- M.5: https://doi.org/10.51560/ofj.v3.88
- M.6: library

Required best practices:

- [x] R.1: Several application cases are available as tutorials. The application cases list is not yet available.
- [x] R.2: https://github.com/precice/openfoam-adapter/blob/develop/README.md
- [x] R.3: https://github.com/precice/openfoam-adapter/blob/develop/LICENSE
- [x] R.4: https://github.com/precice/openfoam-adapter (public)
- [x] R.5: https://precice.org/adapter-openfoam-get.html#what-does-the-adapter-version-mean
- [x] R.6: https://github.com/precice/openfoam-adapter/blob/develop/CHANGELOG.md
- [x] R.7: https://github.com/precice/openfoam-adapter/issues
- [x] R.8: https://github.com/precice/openfoam-adapter/blob/develop/.clang-format
- [x] R.9: See, for example, https://github.com/precice/openfoam-adapter/blob/develop/Adapter.H
- [ ] R.10: (schema not available yet)
- [x] R.11: See call to `setMeshVertices` in https://github.com/precice/openfoam-adapter/blob/develop/Interface.C

Additional criteria:

- [x] A.1: GPL-3.0
- [x] A.2: https://github.com/precice/openfoam-adapter
- [x] A.3: on precice.org
- [x] A.4: yes, but only at compile-time
- [x] A.5: https://doi.org/10.51560/ofj.v3.88
- [x] A.6: https://github.com/precice/openfoam-adapter/blob/develop/CONTRIBUTING.md
- [x] A.7: https://github.com/precice/openfoam-adapter/blob/develop/.github/pull_request_template.md
- [x] A.8: https://precice.org/adapter-openfoam-extend.html
- [ ] A.9: There are no unit tests
- [x] A.10: Already integrated into the system tests
- [x] A.11: https://packages.spack.io/package.html?name=of-precice