+++
title = "Download OpenCourant"
layout = "downloads"
description = "Download pre-built OpenCourant solver packages for Linux and Windows, straight from the project's continuous delivery pipeline."
+++

## Verifying your download

Every package is published with a SHA-256 digest recorded by GitHub at upload
time. Compare it against the archive you downloaded:

```sh
sha256sum OpenCourant_linux64.zip
```

## Getting started

Unpack the archive and point the solver at its own runtime files:

```sh
export OPENCOURANT_PATH=/path/to/OpenCourant
export LD_LIBRARY_PATH=$OPENCOURANT_PATH/extlib/hm_reader/linux64:$OPENCOURANT_PATH/extlib/h3d/lib/linux64:$LD_LIBRARY_PATH
export RAD_CFG_PATH=$OPENCOURANT_PATH/hm_cfg_files
```

The Starter and Engine executables live in `exec/`, alongside the `anim_to_vtk`
and `th_to_csv` converters. Full instructions, including the OpenMPI
requirement for the `_ompi` Engine, are in
[INSTALL.md](https://github.com/OpenCourant/OpenCourant/blob/main/INSTALL.md).

## Building from source

The solver builds on Linux with GCC and GFortran. Clone
[the repository](https://github.com/OpenCourant/OpenCourant) and follow
[HOWTO.md](https://github.com/OpenCourant/OpenCourant/blob/main/HOWTO.md),
which covers the prerequisites, the OpenMPI setup, and `build_linux.sh`.
Building from source is currently the only route to platforms that have no
published package yet.

## Something missing?

If a package you relied on under OpenRadioss is not here, say so — it helps us
prioritise. Open an issue on
[GitHub](https://github.com/OpenCourant/OpenCourant/issues), or find us in
[the chat](https://chat.rockylinux.org/rocky-linux/channels/opencourant).
