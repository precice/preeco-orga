# Checklist for the FMI runner

We consider an application case fulfilling all of these criteria as conforming to the preCICE standards. This means that the case is running and documented and that it follows a standardized structure and style. Others can easily understand what the case does and could, potentially, run it with other solvers without modifications (e.g. of the preCICE configuration). The case feels part of the preCICE ecosystem.

- [x] R.1: All coupled solvers are accessible (open or commercial)
- [ ] R.2: (no, the OpenFOAM adapter can't do that either as the adapter config files are in `system`) The case follows the following structure:

    ```bash
    - <some-application-case>/        # or <some_experiment>
      - README.md                     # see R.3
      - precice-config.xml            # preCICE configuration file, see R.4-R.7
      - run-all.sh                    # run the complete case, multiple times if necessary (optional)
      - clean.sh                      # clean the complete case (mandatory, see R.8)
      - <solver1>/
        - run.sh                      # run the solver (mandatory, see R.9)
        - clean.sh                    # individual clean script (optional)
        - precice-adapter-config.json # adapter configuration (if necessary)
        - <the-solver1-files>
      - <solver2>/
        - run.sh
        - clean.sh
        - precice-adapter-config.json
        - <the-solver2-files>
      - ...
      - <some-other-files>
    ```

    Each solver is started from its separate folder. All M2N exchange directories are thus `..`, for example:

    ```xml
    <m2n:sockets acceptor="Fluid" connector="Solid" exchange-directory=".." />
    ```

- [ ] R.3: (no, would be possible though) The README file follows the following structure:
  - Setup: the physics of the case (domain, boundary conditions, ...) including a simple sketch
  - Configuration: the preCICE configuration visualized by the [preCICE config visualizer](tooling-config-visualization.html)
  - Solvers: list of solvers, their dependencies, and potentially how to build them
  - Running the simulation: how to run the case and approximate runtimes (e.g. a few minutes on a laptop or several hours on a cluster with 128 MPI ranks). This can include information on how to run a parameter study or similar.
  - Post-processing: how to visualize and (at least) qualitatively check the results
  - Background (optional): how the case was created or any other information
  - References (optional)
- [x] R.4: The preCICE configuration is named `precice-config.xml`. Templated files (e.g. via jinja2) or symbolic links are possible and updated in an outer script (e.g. `run-all.sh`).
- [x] R.5: The preCICE configuration is formatted with [`format_precice_config.py`](https://github.com/precice/precice-pre-commit-hooks/blob/main/format_precice_config/format_precice_config.py). In the future, we will provide a more accessible solution.
- [x] R.6: The preCICE configuration passes the [offline check](tooling-builtin.html#configuration-check)
- [x] R.7: Names in the preCICE configuration follow the following conventions:
  - Participant names reflect the subdomain, not the solver, e.g. `Fluid` or `Left-Muscle`.
  - Participant, data, and mesh names start with uppercase and use `-` as separator.
  - Data names are in singular, e.g. `Stress` or `Heat-Flux`.
  - Mesh names concatenate the participant name and `-Mesh`, e.g. `Fluid-Mesh`.
    - Mesh names of participants with multiple interfaces contain the interface in the mesh name, e.g. `Fluid-Upstream-Mesh`. For meshes on which it is important to distinguish between face centers and face nodes (or similar), the modifier comes at the end, e.g. `Fluid-Upstream-Mesh-Centers`.
  - Watchpoint names should be describing the point, not be a generic name.
- [x] R.8: There is a cleaning script `clean.sh` to clean the complete case.
- [x] R.9: There is an individual run script `run.sh` for each solver. If a script takes additional options, there are default values. The scripts should be called from the individual folders.

### Additional

These optional criteria help others to easily reuse and extend the case for their own needs. The preCICE maintainers, in particular, can integrate the application case into their development workflows.

Aim to implement as many of these best practices as make sense for you. Each brings additional long-term benefits.

- [x] A.1: The case runs with released versions of preCICE and related components, without any modifications.
- [ ] A.2: (no, not yet, no metadata available) The case is ready to be integrated into the [preCICE system tests](https://precice.org/dev-docs-system-tests.html): It includes a `metadata.yaml` file, as described in the system tests documentation.
- [x] A.3: The case either includes or links to full results, including documented versions of all dependencies.
- [ ] A.4: (no, but I think the initial version was already laptop-ready) There is a "coarse" variant of the case to run on a laptop.
- [ ] A.5: (no, but would be possible) There are exports to replay each participant with [ASTE](https://precice.org/tooling-aste.html#replay-mode).
- [x] A.6: There is a related publication validating the scientific value of the case.

