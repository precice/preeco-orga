---
title: Guidelines for adapters
permalink: community-guidelines-adapters.html
keywords: contribute, develop, adapters, standardization, preECO
summary: Quality guidelines and standards for preCICE adapters and related tools
toc: true
---

v0.2, published on December 9, 2024

Are you developing a preCICE adapter or related tool? Follow these guidelines to make your adapter easier to publish, easier to integrate with the rest of the preCICE ecosystem, and more useful for the community.

We differentiate between adapters and application cases: For example, we consider the ["Nutils adapter"](https://precice.org/adapter-nutils.html) to be a collection of application cases instead of an adapter. An [adapter](https://precice.org/couple-your-code-overview.html) can be a stand-alone software project, but can also be a class, a patch, or something else with significant scholarly effort compared to the uncoupled solver. Other tools that interact with the preCICE API or configuration files can also be considered here, on a case-by-case basis.

For the guidelines, we distinguish between **metadata** and **best practices**. The best practices are split between required and optional. Adapters fulfilling all the required best practices are listed on the preCICE website as adapters conforming to the preCICE standards. Additional criteria bring further benefits and are visible individually for each adapter. Adapters not fulfilling all the required criteria can still be listed here as legacy adapters. By submitting your adapter for review, you can expect a thorough check from the preCICE team on whether these guidelines are met.

{% warning %}
We are not doing a scientific review and we cannot do a full code review. We are "only" checking best practices, not the scientific correctness of an adapter. Listing your adapter on the preCICE website does not in any way replace a traditional publication, which you can link to.
{% endwarning %}

{% tip %}
We are only in the beginning of this standardization journey. Do you have ideas that would make your life easier and integrating your adapter smoother? Comment in [this forum thread](https://precice.discourse.group/t/2125), or click "Edit" to suggest a change in this page.
{% endtip  %}

{% tip %}
Applying for research funding? Mention in your proposal that you are planning to follow best practices defined by the preCICE community.
{% endtip  %}

## Metadata

- M.1: Name of the target solver
- M.2: URL of the adapter
- M.3: License
- M.4: Contact
- M.5: How to cite (DOI or full information)
- M.6: Type of adapter (curated list: stand-alone, library, patch, integrated, ...)

## Best practices

We distinguish between required and additional, optional best practices.

The criteria follow at large the [FAIR criteria for research software](https://doi.org/10.1038/s41597-022-01710-x): Findable (documented), Accessible (working), Interoperable (standardized), and Reusable (integratable).

### Required

We consider an adapter fulfilling all of these criteria as conforming to the preCICE standards. This means that the adapter is working, documented, plays well with other adapters from the community, and feels part of the preCICE ecosystem. Others can find, build, and run the code, and they are able to understand what is does. The preCICE maintainers are, if necessary, able to maintain the adapter (e.g. update it to newer preCICE versions).

- [ ] R.1: The adapter is accompanied by one or more application cases to test it, covering an extensive part of the claimed functionality. These test cases must fulfill the required criteria of the [application case guidelines](community-guidelines-application-cases.html).
- [ ] R.2: There is a `README.md` file with at least the following information (or links to related resources):
  - [ ] application background and/or nature of coupling (e.g., surface vs. volume coupling; transient or steady-state; ...)
  - [ ] what data can be read and written for a coupling
  - [ ] which target solver versions are supported
  - [ ] list of dependencies
  - [ ] how to build
  - [ ] how to configure (including the coupling data, if available)
  - [ ] how to run the accompanying application test case
  - [ ] geometry assumptions and limitations, e.g., number of dimensions, assumptions on out-of-plane axis for lower dimensions, or support for only a single or also multiple patches.
  - [ ] which preCICE features are supported or not supported. Curated list including:
    - implicit coupling
    - mesh connectivity
    - data initialization
    - subcycling: `dt = min(dt_solver, dt_precice)`
    - multiple meshes
  - [ ] restrictions on solver features
    - e.g., cannot be run in parallel or cannot use adaptive time stepping or cannot use higher-order elements
  - [ ] references to related studies or literature necessary to understand the modeling and implementation (at least in preprint state).
- [ ] R.3: The adapter has a clear license (open is optional, but strongly encouraged).
- [ ] R.4: The adapter uses a version control system (public is optional, but strongly encouraged).
- [ ] R.5: The adapter uses a versioning scheme, such as [semantic versioning](https://semver.org/) (or other clearly defined scheme).
- [ ] R.6: There is a structured changelog, e.g., using the [keep a changelog](https://keepachangelog.com/) format.
- [ ] R.7: There is an issue tracker.
- [ ] R.8: There is a code formatting specification (e.g., clang-format specification file).
- [ ] R.9: The adapter has comments and error messages for at least its main building blocks and entry points. These comments are in English.
- [ ] R.10: The configuration follows the [preCICE Adapter and Tooling Configuration Schema](https://github.com/precice/preeco-orga/blob/main/adapter-config-schema/preatcs.json), either directly in JSON or indirectly via LLM-based auto-conversion. Using the standard name `precice-adapter-config.json` is possible (if JSON). Validating a JSON configuration against a schema can be done with the Python library [jsonschema](https://pypi.org/project/jsonschema/) or via the [JTutor GUI](https://validationproofs.oa.r.appspot.com/), for example.
- [ ] R.11: Any vertices defined through `setMeshVertex` or `setMeshVertices` need to be real locations in space and the data written to the mesh needs to be data located there, i.e., it is not allowed to decode any other information.

### Additional

These optional criteria help others to easily reuse and extend the adapter for their own needs. Maintaining the adapter could be shared among many. The preCICE maintainers can integrate the adapter and corresponding application cases into their development workflows. All tooling works seamlessly.

Aim to implement as many of these best practices as make sense for you. Each brings additional long-term benefits.

- [ ] A.1: The adapter has an open-source license.
- [ ] A.2: The adapter uses a publicly-accessible repository.
- [ ] A.3: The documentation is rendered in a user-friendly way, either:
  - on precice.org (i.e., in `docs` subfolder, see [preCICE documentation of the documentation](https://precice.org/docs-meta-overview.html))
  - on another website
- [ ] A.4: The logging is configurable, with levels at least "no logging, release logging, and debug logging".
- [ ] A.5: There is a peer-reviewed paper (at least in pre-print state) with a validation study, with all data available.
- [ ] A.6: There are contribution guidelines described in or linked from a `CONTRIBUTING.md` file.
- [ ] A.7: There is a pull request template.
- [ ] A.8: There is documentation on how to extend the adapter (i.e., documentation about the software architecture).
- [ ] A.9: There are unit tests to test components of the adapter, without running another simulation participant (and ideally, using the upcoming [general mocked interface](https://github.com/precice/preeco-orga/issues/4)).
- [ ] A.10: The repository is ready to be integrated into the [preCICE system tests](https://precice.org/dev-docs-system-tests.html): A simulation can start using an unsupervised script and there is enough information to create entries under `component-templates/` and `components.yaml`.
- [ ] A.11: The adapter is packaged either on the expected repositories of the respective solver community, or on [Spack](https://spack.io/) ([Spack packages](https://packages.spack.io/)).

## An adapter example

Some examples evaluating these guidelines:

- [OpenFOAM adapter](https://precice.org/community-guidelines-adapters-openfoam.html)

Note that these pages will be removed once the guidelines are converged and a better system is in place to render this information.
