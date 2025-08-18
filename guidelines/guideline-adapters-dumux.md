---
title: Standardization example - DuMuX adapter
permalink: community-guidelines-adapters-dumux.html
keywords: contribute, develop, adapters, standardization, preECO, DuMuX
summary: A review of the DuMuX adapter using the contributing guidelines. This is a work-in-progress that will eventually be moved.
toc: true
---

The DuMuX adapter conforms to some of the preCICE best practices and fulfills a few of the additional criteria.

Metadata:

- M.1: DuMuX
- M.2: https://precice.org/adapter-dumux.html
- M.3: GPL-3.0
- M.4: Ishaan Desai `<ishaan.desai ipvs.uni-stuttgart.de>`, Jun Chen `<jun.chen ipvs.uni-stuttgart.de>`
- M.5: (There is no code-specific publication related to the DuMuX adapter available yet.)
- M.6: integrated

Required best practices:

- [x] R.1: Several application cases are available as tutorials. The application cases list is not yet available.
- [x] R.2: [`README.md`](https://github.com/precice/dumux-adapter/blob/develop/README.md)
  - [ ] application background and/or nature of coupling (e.g., surface vs. volume coupling; transient or steady-state; ...)
  - [ ] what data can be read and written for a coupling
  - [x] which target solver versions are supported
  - [x] list of dependencies
  - [x] how to build
  - [ ] how to configure (including the coupling data, if available)
  - [x] how to run the accompanying application test case
  - [ ] geometry assumptions and limitations, e.g., number of dimensions, assumptions on out-of-plane axis for lower dimensions, or support for only a single or also multiple patches.
  - [ ] which preCICE features are supported or not supported. Curated list including:
    - implicit coupling
    - mesh connectivity
    - data initialization
    - subcycling: `dt = min(dt_solver, dt_precice)`
    - multiple meshes
  - [ ] restrictions on solver features
  - [ ] references to related studies or literature necessary to understand the modeling and implementation (at least in preprint state).
- [x] R.3: [`LICENSE`](https://github.com/precice/dumux-adapter/blob/develop/LICENSE)
- [x] R.4: [GitHub project](https://github.com/precice/dumux-adapter) (public)
- [ ] R.5: no versioning scheme is defined
- [x] R.6: [`CHANGELOG.md`](https://github.com/precice/dumux-adapter/blob/develop/CHANGELOG.md)
- [x] R.7: [issue tracker on GitHub](https://github.com/precice/dumux-adapter/issues)
- [x] R.8: [`.clang-format`](https://github.com/precice/dumux-adapter/blob/develop/.clang-format)
- [x] R.9: See, for example, https://github.com/precice/dumux-adapter/blob/develop/dumux-precice/couplingadapter.hh
- [ ] R.10: The adapter is configured directly inside the solvers, such as https://github.com/precice/dumux-adapter/blob/develop/examples/ff-pm/flow-over-cube-3d/main_pm-reversed.cc
- [x] R.11: See call to `setMeshVertices` in https://github.com/precice/dumux-adapter/blob/develop/dumux-precice/couplingadapter.cc

Additional criteria:

- [x] A.1: GPL-3.0
- [x] A.2: [repository](https://github.com/precice/dumux-adapter) is publicly accessible
- [x] A.3: on precice.org
- [x] A.4: yes, but only at compile-time
- [ ] A.5: no peer-reviewed paper with a validation study
- [ ] A.6: no existing contribution guidelines
- [x] A.7: [`pull_request_template.md`](https://github.com/precice/dumux-adapter/blob/develop/.github/pull_request_template.md)
- [ ] A.8: no documentation on how to extend the adapter
- [ ] A.9: no unit tests
- [ ] A.10: TODO
- [ ] A.11: The adapter is not packaged on the expected repositories of the respective solver community or on Spack.
