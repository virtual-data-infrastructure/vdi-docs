---
layout: default
title: VDI Client for Users
---

# VDI Client for Users

The VDI client provides tools for interacting with the virtual data
infrastructure (VDI). It includes:

- the `vdi` command-line client
- the shared library `libvdi.so`, which records file-I/O activity and can
  transparently download files from remote resources while a program runs
- utilities for managing views on a VDI server and inspecting generated logs

## Requirements

- An initialized EESSI environment. Published wheels support several documented
  EESSI versions.

  ```bash
  source /cvmfs/software.eessi.io/versions/2025.06/init/lmod/bash
  ```

- A virtual environment created with the Python provided by the active EESSI
  compatibility layer.

See the [EESSI access documentation](https://www.eessi.io/docs/getting_access/is_eessi_accessible/)
for mounting and initialization options.

## Installation

Create a virtual environment with EESSI's Python and install the published
client from PyPI:

```bash
"${EESSI_EPREFIX}/usr/bin/python" -m venv ~/.venvs/vdi-client
source ~/.venvs/vdi-client/bin/activate
pip install --upgrade pip
python -m pip install vdi-client
```

## Quick start

Preview a wrapped command without executing it:

```bash
vdi run --dry-run python -c 'print("Hello, VDI")'
```

Store the address of your VDI server in `~/.vdi/config`:

```bash
mkdir -p ~/.vdi
echo 'BASE_URL=https://vdi.example.org' > ~/.vdi/config
```

Then list the views available on that server:

```bash
vdi view list
```

Run a program with VDI instrumentation enabled:

```bash
vdi run python examples/map_plot.py data/no.json --out outputs
```

The wrapper prints the path to the generated log file. List and inspect it with:

```bash
vdi log list
vdi log show <pid>
```

## Topics

- [Configuration](configuration.md)
- [Command-line usage](cli.md)
- [Examples](examples.md)
- [Managing VDI logs](logging.md)
