---
title: Guidelines for adapters
permalink: community-guidelines-adapters.html
keywords: contribute, develop, adapters, standardization, preECO
summary: Quality guidelines and standards for preCICE adapters and related tools
toc: true
---

v0.1, published on September TODO, 2024
Are you developing a preCICE adapter or related tool? Follow these guidelines to make your adapter easier to publish, easier to integrate it with the rest of the preCICE ecosystem, and more useful for the community.

We distinguish between **metadata** and **best practices**, with three levels: bronze, silver, and gold. We plan to publish a list of all adapters that has achieved at least bronze level, together with the respective metadata. Higher levels bring higher visibility and further benefits.

We also differentiate here between adapters and application cases: for example, we consider the ["Nutils adapter"](https://precice.org/adapter-nutils.html) to be a collection of application cases instead of an adapter. An [adapter](https://precice.org/couple-your-code-overview.html) can be a stand-alone software project, but can also be a class, a patch, or something else with significant scholarly effort compared to the uncoupled solver. Other tools that interact with the preCICE API or configuration files can also be considered here, on a case-by-case basis.

By submitting your adapter for review, you can expect a thorough check from the preCICE team on whether these guidelines are met. We cannot do a full code review or a scientific review, and listing your adapter here does not in any way replace a traditional publication, which you can link to.

{% tip %}
We are only in the beginning of this standardization journey. Do you have ideas that would make your life easier and integrating your adapter smoother? Comment in [this issue](https://github.com/precice/preeco-orga/issues/7), or click "Edit" to suggest a change in this page.
{% endtip  %}

{% tip %}
Applying for research funding? Mention in your proposal which level you are planning to achieve during your planned project and how.
{% endtip  %}

## Metadata

- M.1: Name of the target solver
- M.2: URL of the adapter
- M.3: License
- M.4: Original developers (**TODO:** What does "original" mean? Who do we include? Do we include the institution? Which?)
- M.5: Current maintainers, including contact information
- M.6: How to cite (DOI or full information)
- M.7: Type of adapter (curated list: stand-alone, patch, integrated, ...)
- M.8: Available versions (**TODO:** Is this supposed to be an extensive list?)

## Best practices

We distinguish between three levels: bronze, silver, and gold.

### Bronze

We consider an adapter fulfilling all of these criteria as *Findable* and *Accessible*. This means that the adapter is working and documented. Others can find, build, and run the code, and they are able to understand what is does.

- [ ] B.1: The adapter is accompanied by at least one application case to test it, covering at least a defined minimum functionality. The test case can be provided as an independent application case or included in the adapter.
- [ ] B.2: There is a `README.md` file.
- [ ] B.3: At least the following information is contained in the `README.md` file, or in a similar place:
  - [ ] application background and/or nature of coupling (e.g., surface vs. volume coupling; transient or steady-state; ...)
  - [ ] what data can be read and written for a coupling
  - [ ] which target solver versions are supported
  - [ ] list of dependencies
  - [ ] how to build
  - [ ] how to configure (including the coupling data, if available)
  - [ ] how to run the accompanying application test case
  - [ ] geometry assumptions and limitations:
    - number of dimensions
    - assumptions on out-of-plane axis for lower dimensions
    - support for only a single or also multiple patches
  - [ ] which preCICE features are supported or not supported. Curated list including:
    - implicit coupling
    - mesh connectivity
    - data initialization
    - subcycling: `dt = min(dt_solver, dt_precice)`
    - multiple meshes
  - [ ] restrictions on solver features
    - e.g., cannot be run in parallel or cannot use adaptive time stepping or cannot use higher-order elements
  - [ ] how to cite
- [ ] B.4: The adapter has a clear license (open is optional, but strongly encouraged).
- [ ] B.5: The adapter uses a version control system (public is optional, but strongly encouraged).
- [ ] B.6: The adapter uses a versioning scheme, such as [semantic versioning](https://semver.org/) (or other clearly defined scheme).
- [ ] B.7: The adapter has comments and error messages for at least its main building blocks and entry points. These comments are in English.

### Silver

We consider an adapter fulfilling all of these criteria as *Interoperable* and *maintainable*. The adapter plays well with other adapters from the community and feels part of the preCICE ecosystem. The preCICE maintainers are, if necessary, able to maintain the adapter (e.g. update it to newer preCICE versions).

- [ ] S.1: The adapter is accompanied by one or more application cases to test it, covering an extensive part of the claimed functionality. These cases must be provided as independent application cases.
- [ ] S.2: The documentation provides references to related studies or literature necessary to understand the modeling and implementation (at least in preprint state).
- [ ] S.3: The adapter has an open-source license.
- [ ] S.4: The adapter uses a publicly-accessible repository.
- [ ] S.5: The adapter configuration covers the mesh name, data names, participant name, and name of the preCICE configuration file.
- [ ] S.6: In the adapter configuration, standard names are possible for the coupled data (e.g., `Displacement`).
- [ ] S.7: There is a clearly defined code style and a provided formatter (e.g., clang-format specification file).
- [ ] S.8: There is a structured changelog, e.g., using the [keep a changelog](https://keepachangelog.com/) format.
- [ ] S.9: There is an issue tracker.
- [ ] S.10: There is information on how the adapter was validated and how validation could be reproduced.
- [ ] S.11: The documentation is rendered in a user-friendly way, either:
  - on precice.org (i.e., in `docs` subfolder, see [preCICE documentation of the documentation](https://precice.org/docs-meta-overview.html))
  - on another website
- [ ] S.12: The development repository is public or at least accessible to the preCICE team.
- [ ] S.13: The logging is configurable, with levels at least "no logging, release logging, and debug logging".

### Gold

We consider an adapter fulfilling all of these criteria as *Reusable*, *community-ready*, and *integrated*. Others can easily reuse and extend the adapter for their own needs. Maintaining the adapter could be shared among many. We can integrate the adapter and corresponding application cases into our development workflows and make sure that we will not break it. All tooling works seamlessly.

- [ ] G.1: There is a peer-reviewed paper (at least in pre-print state) with a validation study, with all data available.
- [ ] G.2: There are contribution guidelines described in or linked from a `CONTRIBUTING.md` file.
- [ ] G.3: There is a pull request template.
- [ ] G.4: The configuration follows a formally defined schema, which [will be available in the future](https://github.com/precice/preeco-orga/issues/18).
- [ ] G.5: There are unit tests to test components of the adapter, without running another simulation participant (and ideally, using the upcoming [general mocked interface](https://github.com/precice/preeco-orga/issues/4)).
- [ ] G.6: The repository is ready to be integrated into the [preCICE system tests](https://precice.org/dev-docs-system-tests.html): A simulation can start using an unsupervised script and there is enough information to create entries under `component-templates/` and `components.yaml`.
- [ ] G.7: There is documentation on how to extend the adapter (i.e., documentation about the software architecture).
- [ ] G.8: The adapter is packaged either on the expected repositories of the respective solver community, or on [Spack](https://spack.io/) ([Spack packages](https://packages.spack.io/)).

## An example

The OpenFOAM adapter currently reaches Bronze level conformity, even if it already satisfies many of the higher-level criteria.

Metadata:

- M.1: OpenFOAM
- M.2: https://precice.org/adapter-openfoam-overview.html
- M.3: GPL-3.0
- M.4: Gerasimos Chourdakis
- M.5: Gerasimos Chourdakis <gerasimos.chourdakis@ipvs.uni-stuttgart.de>, David Schneider <david.schneider@ipvs.uni-stuttgart.de>
- M.6: https://doi.org/10.51560/ofj.v3.88
- M.7: library
- M.8: v1.3.0

Bronze:

- [x] B.1: See https://precice.org/quickstart.html
- [x] B.2: See https://github.com/precice/openfoam-adapter/blob/develop/README.md
- [x] B.3: All information is available other in the `README.md` or the respective documentation
- [x] B.4: The adapter has a clear license (open is optional, but strongly encouraged).
- [x] B.5: The adapter uses a version control system (public is optional, but strongly encouraged).
- [x] B.6: The adapter uses a versioning scheme, such as [semantic versioning](https://semver.org/) (or other clearly defined scheme).
- [x] B.7: The adapter has comments and error messages for at least its main building blocks and entry points. These comments are in English.

Silver:

- [x] S.1: Several application cases are available as tutorials. The application cases list is not yet available.
- [x] S.2: https://doi.org/10.51560/ofj.v3.88
- [x] S.3: GPL-3.0
- [x] S.4: https://github.com/precice/openfoam-adapter
- [x] S.5: https://precice.org/adapter-openfoam-config.html
- [x] S.6: https://precice.org/adapter-openfoam-config.html
- [x] S.7: https://github.com/precice/openfoam-adapter/blob/develop/.clang-format
- [x] S.8: https://github.com/precice/openfoam-adapter/blob/develop/CHANGELOG.md
- [x] S.9: https://github.com/precice/openfoam-adapter/issues
- [ ] S.10: There is information on how the adapter was validated and how validation could be reproduced.
- [x] S.11: on precice.org
- [x] S.12: public
- [ ] S.13: only at compile-time

Gold:

- [x] G.1: https://doi.org/10.51560/ofj.v3.88
- [x] G.2: https://github.com/precice/openfoam-adapter/blob/develop/CONTRIBUTING.md
- [x] G.3: https://github.com/precice/openfoam-adapter/blob/develop/.github/pull_request_template.md
- [ ] G.4: (schema not available yet)
- [ ] G.5: There are no unit tests
- [x] G.6: Already integrated into the system tests
- [x] G.7: https://precice.org/adapter-openfoam-extend.html
- [x] G.8: https://packages.spack.io/package.html?name=of-precice
