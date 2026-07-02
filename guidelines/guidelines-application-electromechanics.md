# Application: electromechanics simulation of a fusiform muscle

In this application, we simulate the contraction of an artificial fusiform muscle. We use a partitioned approach to couple the electrophysiology (simulated in OpenDiHu) with the mechanics (simulated either in OpenDiHu or in FEBio). 

## Metadata

- M.1: Electromechanics simulation of a fusiform muscle
- M.2: The case is included in the dataset with DOI [10.18419/DARUS-6125](https://darus.uni-stuttgart.de/dataset.xhtml?persistentId=doi:10.18419/DARUS-6125)
- M.3: LGPL 3.0 License
- M.4: Carme Homs-Pons, homspons at gmail.com
- M.5: We couple OpenDiHu's *FastMonodomainSolver* with either OpenDiHu's *MuscleContractionSolver* or FEBio. We use [OpenDiHu v1.6](https://github.com/opendihu/opendihu) and [FEBioStudio v2.10](https://github.com/febiosoftware/FEBioStudio) with the [febio-adapter v1.0.0](https://github.com/carme-hp/FEBio-adapter).
- M.6: preCICE v3.0.0
- M.7: Short description of the case (max 300 characters)
- M.8: The case is developed on [GitHub](https://github.com/carme-hp/FEBio_cases/tree/main/partitioned-fusiform-muscle)
- M.9: A partitioned coupling approach for electromechanics simulations of skeletal muscles using FEBio, Proceedings in Applied Mathematics and Mechanics (submitted).
- M.10: Used preCICE features. Curated list includes:
  - explicit coupling
  - ~~implicit coupling~~
  - ~~compositional coupling~~
  - ~~multi coupling~~
  - ~~quasi-Newton acceleration~~
  - ~~nearest-projection mapping or linear cell interpolation~~
  - RBF data mapping
  - ~~GPU computing~~
  - ~~direct access~~
  - ~~just-in-time data mapping~~
  - ~~geometric multi-scale data mapping~~
  - ~~adaptive time stepping~~ but i do have a participant that sub-cycles!
  - ~~waveform relaxation (order >= 2)~~
  - ~~two-level initialization~~
  - dynamic meshes

## Checklist

### Required

We consider an application case fulfilling all of these criteria as conforming to the preCICE standards. This means that the case is running and documented and that it follows a standardized structure and style. Others can easily understand what the case does and could, potentially, run it with other solvers without modifications (e.g. of the preCICE configuration). The case feels part of the preCICE ecosystem.

- [x] R.1: All coupled solvers are accessible (open or commercial)
- [x] R.2: The case has the following structure

    ```bash
    - <partitioned-fusiform-muscle>/        
      - README.md                     
      - precice-config.xml            
      - run-opendihu-opendihu.sh      # 
      - run-opendihu-febio.sh         # 
      - clean.sh                      # clean the complete case (mandatory, see R.8)
      - <fibers-opendihu>/
        - run.sh                      # run the solver (mandatory, see R.9)
        - clean.sh                    # individual clean script (optional)
        - <the-fibers-opendihu-files>
      - <mechanics-opendihu>/
        - run.sh                      # 
        - clean.sh                    # 
        - <the-mechanics-opendihu-files>
      - <mechanics-febio>/
        - run.sh                      # 
        - clean.sh                    # 
        - <the-mechanices-febio-files>
      - <meshes>/
      - <some-other-files>
    ```
  > We have two alternative for the mechanics participant and one for the fibers participant, thus in total we have three solver folders and two options for the `run-all.sh`. 

- [x] R.3: There is a README file that includes at least the following elements:
  - Setup: the physics of the case (domain, boundary conditions, ...) including a simple sketch 
  - Configuration: the preCICE configuration visualized by the [preCICE config visualizer](tooling-config-visualization.html)
  - Solvers: list of solvers, their dependencies, and potentially how to build them
  - Running the simulation: how to run the case and approximate runtimes (e.g. a few minutes on a laptop or several hours on a cluster with 128 MPI ranks). This can include information on how to run a parameter study or similar. 
  - Post-processing: how to visualize and (at least) qualitatively check the results
  - Background (optional): how the case was created or any other information
  - References (optional)
  > Since most elements are there I've marked as complete, yet there is no sketch
- [x] R.4: The preCICE configuration is named `precice-config.xml`. Templatization is not supported.
- [x] R.5: The preCICE configuration is formatted using the [preCICE CLI](https://github.com/precice/cli).
- [ ] R.6: The preCICE configuration passes the [offline check](tooling-builtin.html#configuration-check)
- [ ] R.7: Names in the preCICE configuration follow the following conventions:
 
  - Participant names reflect the subdomain, not the solver, e.g. `Fluid` or `Left-Muscle`.
  - Participant, data, and mesh names start with uppercase and use `-` as separator.
  - Data names are in singular, e.g. `Stress` or `Heat-Flux`.
  - Mesh names concatenate the participant name and `-Mesh`, e.g. `Fluid-Mesh`.
    - Mesh names of participants with multiple interfaces contain the interface in the mesh name, e.g. `Fluid-Upstream-Mesh`. For meshes on which it is important to distinguish between face centers and face nodes (or similar), the modifier comes at the end, e.g. `Fluid-Upstream-Mesh-Centers`.
  - Watchpoint names should be describing the point, not be a generic name.
  > No: participant names are Muscle and Fibers, while meshes are called MuscleMesh and FibersMesh. The febio-adapter hard-codes the names of the participant, mesh and data, and hence adhering to the naming convention (using Muscle-Mesh instead of MuscleMesh) can be done but requires modifying the adapter.
- [ ] R.8: There is a cleaning script `clean.sh` to clean the complete case.
- [x] R.9: There is an individual run script `run.sh` for each solver. If a script takes additional options, there are default values. The scripts should be called from the individual folders.

### Additional

These optional criteria help others to easily reuse and extend the case for their own needs. The preCICE maintainers, in particular, can integrate the application case into their development workflows. 

Aim to implement as many of these best practices as make sense for you. Each brings additional long-term benefits.

- [x] A.1: The case runs with released versions of preCICE and related components, without any modifications.
- [ ] A.2: The case is ready to be integrated into the [preCICE system tests](https://precice.org/dev-docs-system-tests.html): It includes a `metadata.yaml` file, as described in the system tests documentation.
    > No, because the adapters are not integrated to the preCICE CI
- [x] A.3: The case either includes or links to full results, including documented versions of all dependencies.
    > Yes, see M2
- [x] A.4: There is a "coarse" variant of the case to run on a laptop.
    > The default case is already small enough for a laptop
- [ ] A.5: There are exports to replay each participant with [ASTE](https://precice.org/tooling-aste.html#replay-mode).
- [x] A.6: There is a related publication validating the scientific value of the case.
    > Yes, see M9
- [x] A.7: The `run.sh` script follows the following guidelines:
  - It uses `/usr/bin/env` for setting the shell and sets `bash` or simple `sh`: `#!/usr/bin/env bash`.
  - It defines `set -e -u` for fault tolerance.
  - It captures the output in log files.
- [ ] A.8: Any provided Python codes define a `requirements.txt`.
  - This also defines version restrictions.
  - The respective `run.sh` script automatically installs any Python in a new Python virtual environment and logs the installed packages with their versions in a file.
    > Not planned
