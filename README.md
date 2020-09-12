# mpi4jax
![Tests](https://github.com/PhilipVinc/mpi4jax/workflows/Tests/badge.svg) [![Conda Recipe](https://img.shields.io/badge/recipe-mpi4jax-green.svg)](https://anaconda.org/conda-forge/mpi4jax)

MPI plugin for JAX, allowing MPI operations to be inserted in jitted blocks and be traced through by AD.

# Installation
You can Install `mpi4jax` through pip (see below) or conda (click on the badge)
```python
pip install mpi4jax # Pip
```

# Supported operations

- Allreduce

# Usage
```python
import MPI from mpi4py
import jax
import mpi4jax

comm = MPI.COMM_WORLD
a = jax.numpy.ones(5,4)
b = mpi4jax.Allreduce(a, op=MPI.SUM, comm=comm) 
b_jit = jax.jit(lambda x: mpi4jax.Allreduce(x, op=MPI.SUM, comm=comm))(a)

```

# Contributors
- Filippo Vicentini @PhilipVinc
- Dion Häfner @dionhaefner 
