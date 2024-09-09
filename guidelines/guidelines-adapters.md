---
title: Guidelines for adapters
permalink: community-guidelines-adapters.html
keywords: contribute, develop, adapters
summary: A set of quality guidelines for preCICE adapters and related tools
toc: true
---

Are you developing a preCICE adapter or related tool? Follow these guidelines to make your adapter easier to publish, easier to integrate it with the rest of the preCICE ecosystem, and more useful for the community.

We distinguish between **metadata** and **best practices**, with three levels: bronze, silver, and gold. We plan to publish a list of all adapters that has achieved at least bronze level, together with the respective metadata. Higher levels bring higher visibility and further benefits.

{% tip %}
We are only in the beginning of this standardization journey. Do you have ideas that would make your life easier and integrating your adapter smoother? Comment in [this issue](https://github.com/precice/preeco-orga/issues/7), or click "Edit" to suggest a change in this page.
{% endtip  %}

{% tip %}
Applying for research funding? Mention in your proposal which level you are planning to achieve during your planned project and how.
{% endtip  %}

## Metadata

- Name of the target solver
- Available via (URL)
- License
- Original developers
- Current maintainers, including contact information
- How to cite
- Type of adapter (curated list: stand-alone, patch, integrated, ...)
- Available versions

## Best practices

We distinguish between three levels: bronze, silver, and gold.

### Bronze

We consider an adapter fulfilling all of these criteria as *Findable* and *Accessible*. This means that the adapter is working and documented. Others can find, build, and run the code, and they are able to understand what is does.

- [ ] The adapter is accompanied by at least one application case to test it, covering at least a defined minimum functionality. The test case can be provided as an independent application case or included in the adapter.
- [ ] There is a `README.md` file.
- [ ] At least the following information is contained in the `README.md` file, or in a similar place:
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
- [ ] The adapter has a clear license (open is optional, but strongly encouraged).
- [ ] The adapter uses a version control system (public is optional, but strongly encouraged).
- [ ] The adapter uses a versioning scheme, such as [semantic versioning](https://semver.org/) (or other clearly defined scheme).
- [ ] The adapter has comments and error messages for at least its main building blocks and entry points. These comments are in English.

### Silver

We consider an adapter fulfilling all of these criteria as *Interoperable* and *maintainable*. The adapter plays well with other adapters from the community and feels part of the preCICE ecosystem. The preCICE maintainers are, if necessary, able to maintain the adapter (e.g. update it to newer preCICE versions).

- [ ] The adapter is accompanied by one or more application cases to test it, covering the complete claimed functionality. These test cases must be provided as independent application cases.
- [ ] The documentation provides references to related studies or literature necessary to understand the modeling and implementation (at least in submitted or preprint state).
- [ ] The adapter has a clear open-source license.
- [ ] The adapter uses a publicly-accessible version control system.
- [ ] The adapter configuration covers the mesh name, data names, participant name, and name of the preCICE configuration file.
- [ ] In the adapter configuration, standard names are possible for the coupled data (e.g., `Displacement`).
- [ ] There is a clearly defined code style and a provided formatter (e.g., clang-format specification file).
- [ ] There is a structured changelog, e.g., using the [keep a changelog](https://keepachangelog.com/) format.
- [ ] There is an issue tracker.
- [ ] There is information on how the adapter was validated and how validation could be reproduced.
- [ ] The documentation is rendered in a user-friendly way, either:
  - on precice.org (i.e., in `docs` subfolder, see [preCICE documentation of the documentation](https://precice.org/docs-meta-overview.html))
  - on another website
- [ ] The development repository is public or at least accessible to the preCICE team.
- [ ] The logging is configurable, with levels at least "no logging, release logging, and debug logging".

### Gold

We consider an adapter fulfilling all of these criteria as *Reusable*, *community-ready*, and *integrated*. Others can easily reuse and extend the adapter for their own needs. Maintaining the adapter could be shared among many. We can integrate the adapter and corresponding application cases into our development workflows and make sure that we will not break it. All tooling works seamlessly.

- [ ] There is a peer-reviewed paper (at least in submitted or pre-print state) with a validation study, with all data available.
- [ ] There are contribution guidelines described or linked from a `CONTRIBUTING.md` file.
- [ ] There is a pull request template.
- [ ] The configuration follows a formally defined schema.
- [ ] There are unit tests (ideally, using the upcoming "fake preCICE" implementation).
- [ ] The repository is ready to be integrated into the [preCICE system tests](https://precice.org/dev-docs-system-tests.html).
- [ ] There is documentation on how to extend the adapter (i.e., documentation about the software architecture).
- [ ] The adapter is packaged either on the expected repositories of the respective solver community, or on [Spack](https://spack.io/) ([Spack packages](https://packages.spack.io/)).

## An example

TODO: Explain how, e.g., the OpenFOAM adapter conforms to these criteria.
