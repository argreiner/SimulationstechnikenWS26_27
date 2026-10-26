---
layout: default
title: Installing FEniCSx
nav_order: 40
---

# Installing FEniCSx (DOLFINx) with conda

These instructions install [DOLFINx](https://github.com/FEniCS/dolfinx), the
main component of the [FEniCS Project](https://fenicsproject.org), from the
pre-built [conda-forge](https://conda-forge.org) packages. The conda-forge build
comes with PETSc and petsc4py, so `dolfinx.fem.petsc` (e.g. `LinearProblem`)
works out of the box.

> **Note:** The pip wheels (`pip install fenics-dolfinx`) are built *without*
> PETSc. Installing petsc4py separately does not help, because PETSc support has
> to be compiled into DOLFINx. Use conda for the exercises.

Official installation instructions:
<https://docs.fenicsproject.org/dolfinx/main/python/installation.html>

## Supported platforms

- **Linux, macOS:** follow the steps below.
- **Windows:** use the [Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/en-us/windows/wsl/install) 
  and follow the Linux steps inside WSL.
- **Alternative for all platforms: Docker.** If you prefer not to install
  anything into your system, use the `dolfinx/lab` image, which ships DOLFINx
  together with JupyterLab (see [Alternative: Docker](#alternative-docker) below).

## 1. Install Miniforge

[Miniforge](https://github.com/conda-forge/miniforge) is a minimal conda
installer that uses the conda-forge channel by default. If you already have
Anaconda or Miniconda installed, you can skip this step and add
`-c conda-forge` to the commands below.

Download the installer script:

```bash
curl -L -O "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh"
```

and run it (on Linux x86_64 the file is `Miniforge3-Linux-x86_64.sh`):

```bash
bash Miniforge3-$(uname)-$(uname -m).sh
```

Follow the instructions on the command line (by default it installs into
`~/miniforge3`). Then open a new terminal and run:

```bash
conda init
conda config --set auto_activate false   # don't activate the base env in every shell
```

## 2. Create an environment with DOLFINx

Install DOLFINx and everything the exercises need into a dedicated environment:

```bash
conda create -n fenicsx-env -c conda-forge fenics-dolfinx mpich pyvista matplotlib scipy jupyterlab
conda activate fenicsx-env
```

- `fenics-dolfinx` pulls in basix, ffcx, ufl, PETSc, petsc4py and mpi4py
  ([package page](https://anaconda.org/conda-forge/fenics-dolfinx)).
- `mpich` selects the MPI implementation (`openmpi` also works).
- [`pyvista`](https://docs.pyvista.org) is used for 3D plotting, `matplotlib`
  and `scipy` are used in the notebooks.

Installing everything in one `conda create` command lets conda resolve all
dependencies at once. To add packages later, use `conda install -c conda-forge <package>`.
Avoid `pip install` for packages that conda-forge provides; mixing them can
break the environment.

## 3. Check the installation

```bash
python -c "import dolfinx; print(dolfinx.__version__, 'PETSc:', dolfinx.has_petsc)"
```

This should print the installed DOLFINx version followed by `PETSc: True`:

```
0.x.y PETSc: True
```

To check that MPI works:

```bash
mpirun -n 2 python -c "from mpi4py import MPI; c = MPI.COMM_WORLD; print(f'rank {c.rank} of {c.size}')"
```

Expected output (the two lines may appear in either order):

```
rank 0 of 2
rank 1 of 2
```

## 4. Working with the environment

- **Activate the environment** in every new terminal: `conda activate fenicsx-env`.
- **Jupyter:** run `jupyter lab` in the folder you work in.
- **MPI:** Python scripts can run in parallel, e.g. on 4 processes:
  `mpirun -n 4 python my_solution.py`.
- **VS Code:** install the
  [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) and
  [Jupyter](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter)
  extensions and select `fenicsx-env` as interpreter
  (*Ctrl+Shift+P → Python: Select Interpreter*) or as notebook kernel (top right).
 
  
## Alternative: Docker

If you have (or want to install) Docker, you can skip the conda installation and
use the `dolfinx/lab` image, which contains DOLFINx, PETSc and JupyterLab.

1. Install Docker: see [Get Docker](https://docs.docker.com/get-started/get-docker/)
   (Docker Desktop for Windows/macOS, Docker Engine for Linux). If you are new
   to Docker, the [Docker getting-started guide](https://docs.docker.com/get-started/)
   explains the basics.
2. From the folder containing your exercise files, start the container:
   ```bash
   docker run --name fenicsx --init -ti -p 8888:8888 -v "$(pwd)":/root/shared -w /root/shared dolfinx/lab:stable
   ```
   The `-v` option makes the current folder available inside the container as
   `/root/shared`, so your solutions are saved on your own machine (in Windows
   PowerShell, write `${PWD}` instead of `"$(pwd)"`). Files
   stored elsewhere inside the container are lost when it is removed.
   The `-w` option makes `/root/shared` the working directory, so JupyterLab
   opens directly in your mounted folder.
3. Open the `http://127.0.0.1:8888/lab?token=...` link printed in the terminal
   in your browser.

**Managing containers with Docker Desktop:**
[Docker Desktop](https://docs.docker.com/desktop/) (available for Windows,
macOS and Linux) has a graphical interface for your containers. Under
*Containers* you can see all containers, stop and restart them, and delete ones
you no longer need. If you click a container, its *Logs* tab shows the terminal
output, including the JupyterLab link with the token. This is useful when you
have closed the terminal or restarted the container. The `docker run` command
above creates a container named `fenicsx`, which you only need to do once.
Next time, restart this container from Docker Desktop (or with
`docker start -ai fenicsx` in the terminal) instead of running `docker run`
again. Running `docker run` again fails with "name already in use" while the
old container still exists.

More details on the available images:
<https://github.com/FEniCS/dolfinx#docker-images>

## Further resources

- [FEniCSx tutorial by J. S. Dokken](https://jsdokken.com/dolfinx-tutorial/): the
  best place to start, with many worked examples
- [DOLFINx demos](https://docs.fenicsproject.org/dolfinx/main/python/demos.html)
- [DOLFINx Python API documentation](https://docs.fenicsproject.org/dolfinx/main/python/)
- [UFL documentation](https://docs.fenicsproject.org/ufl/main/) (the form language)
- [FEniCS Discourse forum](https://fenicsproject.discourse.group/) for questions
- [conda user guide](https://docs.conda.io/projects/conda/en/latest/user-guide/index.html)
