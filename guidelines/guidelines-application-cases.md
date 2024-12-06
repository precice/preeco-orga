---
title: Guidelines for application cases
permalink: community-guidelines-application-cases.html
keywords: contribute, develop, application cases, tutorials, standardization, preECO
summary: Quality guidelines and standards for application cases
toc: true
---

v0.2, published on December 9, 2024

Are you preparing one or several application cases for a data publication to accompany your journal article? Follow these guidelines to make your cases easier to integrate with the rest of the preCICE ecosystem and, thus, easier to reproduce, to maintain, and to build upon.

What exactly is an application case? It is everything that you need to run a coupled case: input files (configurations, meshes) of all coupled solvers, configuration files of all adapters, and the overall preCICE configuration file. Sometimes, also run scripts of the solvers, documentation, results, and postprocessing scripts are included. Application cases have many different purposes: to study application-based research questions, to study coupling methods, to test for regression during software development, or to learn preCICE. Users as well as developers of preCICE develop application cases. The preCICE tutorials are also application cases, but with specific requirements, which are collected in the [tutorials contribution guidelines](community-contribute-to-precice.html#contributing-tutorials).

A data publication can include one or more application cases. Each application case can again include several experiments or a parameter study. Some examples for such data publications:

- [Jaust and Schmidt, Replication Data for: Simulation of flow in deformable fractures using a quasi-Newton based partitioned coupling approach, DaRUS, 2021](https://doi.org/10.18419/darus-1778) including three application cases, each with mulitple experiments
- [Homs-Pons et al., Replication Data for: Partitioned Multiphysics Simulation of an Electrophysiological Three-Tendon-Biceps Model, DaRUS, 2024](https://doi.org/10.18419/darus-4228) including three application cases, each with multiple experiments
- [Chourdakis and Uekermann, OFW2019 water hammer experiments](https://gitlab.lrz.de/precice/ofw2019-experiments) including a single application case with multiple experiments

While being documented fairly well, these application cases do not yet follow all of the guidelines below, but use various structures and styles.

For the guidelines, we distinguish between **metadata** and **best practices**. The best practices are split between required and optional (or additional). Application cases fulfilling all the required best practices are listed on the preCICE website as conforming to the preCICE standards. Additional criteria bring further benefits and are visible individually for each application case. Cases not fulfilling all the required criteria can still be listed as legacy application cases. New application cases should be significantly different from existing ones. It is possible to update existing cases.

By submitting your data publication for review, you can expect a thorough check from the preCICE team on whether the application case guidelines are met and how to improve your cases. Let us know about your cases early on, then we can help from the beginning. If you submit too late, it might be that you can no longer edit your data publication or that it would simply be too much hassle to still change fundamental things.

{% warning %}
We are not doing a scientific review. We are "only" checking best practices, not the scientific correctness or value of a case. If your data publication is part of a journal article, for example, the scientific review is part of the review process of the journal instead.
{% endwarning %}

{% tip %}
We are only in the beginning of this standardization journey. Do you have ideas that would make your life easier and or do want to change the guidelines? Comment in [this forum thread](https://precice.discourse.group/t/2126), or click "Edit" to suggest a change in this page.
{% endtip %}

{% tip %}
Applying for research funding? Mention in your proposal that you are planning to follow best practices defined by the preCICE community.
{% endtip %}

## Metadata

- M.1: Title of the case
- M.2: DOI or other URL
- M.3: License
- M.4: Authors, including contact information
- M.5: Coupled solvers, including used versions
- M.6: Used preCICE version (release/branch/commit), including build config if different from default
- M.7: Short description of the case (max 300 characters)
- M.8: (Optional) URL of development repository
- M.9: (Optional) Related publication
- M.10: Used preCICE features. Curated list includes:
  - explicit coupling
  - implicit coupling
  - compositional coupling
  - multi coupling
  - quasi-Newton acceleration
  - nearest-projection mapping or linear cell interpolation
  - RBF data mapping
  - GPU computing
  - direct access
  - indirect access
  - geometric multi-scale data mapping
  - adaptive time stepping
  - waveform relaxation (order >= 2)
  - two-level initialization
  - dynamic meshes

## Best practices

We distinguish between required and additional, optional best practices.

The criteria follow at large the [FAIR criteria for research data](https://doi.org/10.1038/sdata.2016.18): *Findable* (documented), *Accessible* (working), *Interoperable* (standardized), and *Reusable* (integratable).

If an application case includes several experiments, they can be structured in individual folders. Then, each experiment should follow the guidelines individually.

```bash
- <some-application-case>/
  - README.md                # a single overall README file is enough
  - <experiment1>/
    - precice-config.xml
    - ...
  - <experiment2>/
  - <experiment3>/
  - ...
  - <some-other-files>
```

### Required

We consider an application case fulfilling all of these criteria as conforming to the preCICE standards. This means that the case is running and documented and that it follows a standardized structure and style. Others can easily understand what the case does and could, potentially, run it with other solvers without modifications (e.g. of the preCICE configuration). The case feels part of the preCICE ecosystem.

- [ ] R.1: All coupled solvers are accessible (open or commercial)
- [ ] R.2: The structure of the case should be as follows:

    ```bash
    - <some-application-case>/        # or <some_experiment>
      - README.md                     # see R.3
      - precice.config.xml            # preCICE configuration file, see R.4-R.7
      - run-all.sh                    # run the complete case, multiple times if necessary (optional)
      - clean.sh                      # clean the complete case (mandatory, see R.8)
      - <solver1>/
        - run.sh                      # run the solver (mandatory, see R.9)
        - clean.sh                    # individual clean script (optional)
        - <the-solver1-files>
      - <solver2>/
        - run.sh
        - clean.sh
        - <the-solver2-files>
      - ...
      - <some-other-files>
    ```

    Each solver is started from its separate folder. All M2N exchange directories are thus `..`, for example:

    ```xml
    <m2n:sockets acceptor="Fluid" connector="Solid" exchange-directory=".." />
    ```

- [ ] R.3: The README file follows the following structure:
  - Setup: the physics of the case (domain, boundary conditions, ...) including a simple sketch
  - Configuration: the preCICE configuration visualized by the [preCICE config visualizer](tooling-config-visualization.html)
  - Solvers: list of solvers, their dependencies, and potentially how to build them
  - Running the simulation: how to run the case and approximate runtimes (e.g. a few minutes on a laptop or several hours on a cluster with 128 MPI ranks). This can include information on how to run a parameter study or similar.
  - Post-processing: how to visualize and (at least) qualitatively check the results
  - Background (optional): how the case was created or any other information
  - References (optional)
- [ ] R.4: The preCICE configuration is named `precice-config.xml`. Templated files (e.g. via jinja2) or symbolic links are possible and updated in an outer script (e.g. `run-all.sh`).
- [ ] R.5: The preCICE configuration is formatted with [`format_precice_config.py`](https://github.com/precice/precice-pre-commit-hooks/blob/main/format_precice_config/format_precice_config.py). In the future, we will provide a more accessible solution.
- [ ] R.6: The preCICE configuration passes the [offline check](tooling-builtin.html#configuration-check)
- [ ] R.7: Names in the preCICE configuration follow the following conventions:
  - Participant names reflect the subdomain, not the solver, e.g. `Fluid` or `Left-Muscle`.
  - Participant, data, and mesh names start with uppercase and use `-` as separator.
  - Data names are in singular, e.g. `Stress` or `Heat-Flux`.
  - Mesh names concatenate the participant name and `-Mesh`, e.g. `Fluid-Mesh`.
    - Mesh names of participants with multiple interfaces contain the interface in the mesh name, e.g. `Fluid-Upstream-Mesh`. For meshes on which it is important to distinguish between face centers and face nodes (or similar), the modifier comes at the end, e.g. `Fluid-Upstream-Mesh-Centers`.
  - Watchpoint names should be describing the point, not be a generic name.
- [ ] R.8: There is a cleaning script `clean.sh` to clean the complete case.
- [ ] R.9: There is an individual run script `run.sh` for each solver.

### Additional

These optional criteria help others to easily reuse and extend the case for their own needs. The preCICE maintainers, in particular, can integrate the application case into their development workflows. 

Aim to implement as many of these best practices as make sense for you. Each brings additional long-term benefits.

- [ ] A.1: The case runs with released versions of preCICE and related components, without any modifications.
- [ ] A.2: The case is ready to be integrated into the [preCICE system tests](https://precice.org/dev-docs-system-tests.html): It includes a `metadata.yaml` file, as described in the system tests documentation.
- [ ] A.3: The case either includes or links to full results, including documented versions of all dependencies.
- [ ] A.4: There is a "coarse" variant of the case to run on a laptop.
- [ ] A.5: There are exports to replay each participant with [ASTE](https://precice.org/tooling-aste.html#replay-mode).
- [ ] A.6: There is a related publication validating the scientific value of the case.
