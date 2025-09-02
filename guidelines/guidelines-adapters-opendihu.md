---
title: Standardization example - OpenDiHu adapter
permalink: community-guidelines-adapters-opendihu.html
keywords: contribute, develop, adapters, standardization, preECO, OpenDiHu
summary: A review of the OpenDiHu adapter using the contributing guidelines. This is a work-in-progress that will eventually be moved.
toc: true
---

The OpenDiHu adapter conforms to TODO: of the preCICE best practices and fulfills a few of the additional criteria. 

Metadata:

- M.1: OpenDiHu
- M.2: https://opendihu.readthedocs.io/en/latest/settings/precice_adapter.html
- M.3: MIT license
- M.4: Carme Homs-Pons `<carme.homs-pons ipvs.uni-stuttgart.de>`
- M.5: TODO:
- M.6: integrated

Required best practices:

- [ ] R.1: TODO:
- [x] R.2: Since this is an integrated adapter, there is a [solver documentation page](https://opendihu.readthedocs.io/en/latest/settings/precice_adapter.html) about the adapter.
- [x] R.3: [`MIT license`](https://github.com/opendihu/opendihu/blob/develop/LICENSE)
- [x] R.4: The adapter is hosted on [GitHub](https://github.com/opendihu/opendihu/tree/develop/core/src/control/precice), as part of the [OpenDiHu repository](https://github.com/opendihu/opendihu/tree/develop)(public)
- [x] R.5: It follows the OpenDiHu versioning scheme, e.g., v1.5
- [ ] R.6: There is no dedicated `CHANGELOG.md` file. Only [release notes](https://github.com/opendihu/opendihu/releases/tag/v1.5) are available. 
- [x] R.7: See label `precice-adapter` on [GitHub issues](https://github.com/opendihu/opendihu/issues)
- [x] R.8: [`.clang-format`](https://github.com/opendihu/opendihu/blob/develop/.clang-format)
- [x] R.9: See, for example, https://github.com/opendihu/opendihu/blob/develop/core/src/control/precice/checkpoint.tpp
- [ ] R.10: The adapter is configured directly inside the solver configuration files, see `"PreciceAdapter"` in https://github.com/opendihu/opendihu/blob/develop/examples/electrophysiology/fibers/fibers_contraction/with_tendons_precice/dirichlet_neumann/settings_muscle_dirichlet_neumann.py
- [ ] R.11: See call to `setMeshVertices` in https://github.com/opendihu/opendihu/blob/develop/core/src/control/precice/initialize.tpp

Additional criteria:

- [x] A.1: MIT license
- [x] A.2: [repository](https://github.com/opendihu/opendihu/tree/develop/core/src/control/precice) is publicly accessible
- [x] A.3: yes, on [readthedocs](https://opendihu.readthedocs.io/en/latest/settings/precice_adapter.html)
- [ ] A.4: "release" or "debug" logging can be selected at compile time
- [ ] A.5: TODO: no?
- [x] A.6: Some guidelines are specified in the [OpenDiHu documentation](https://opendihu.readthedocs.io/en/latest/developer/conventions.html)
- [x] A.7: [`pull_request_template.md`](https://github.com/opendihu/opendihu/blob/develop/.github/pull_request_template.md)
- [ ] A.8: There are no explicit guidelines for the adapter. Some useful information is given in the [OpenDiHu documentation](https://opendihu.readthedocs.io/en/latest/developer/conventions.html)
- [ ] A.9: There are no unit tests
- [ ] A.10: TODO:
- [ ] A.11: No package of the adapter is currently available
