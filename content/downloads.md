+++
title = "Download OpenCourant"
layout = "downloads"
description = "Download pre-built OpenCourant solver packages for Linux x86-64, Linux arm64 and Windows, straight from the project's continuous delivery pipeline."
+++

## Verifying your download

Every package is published with a SHA-256 digest recorded by GitHub at upload
time. Compare it against the archive you downloaded:

```sh
sha256sum OpenCourant_linux64.zip
```

On Windows:

```bat
certutil -hashfile OpenCourant_win64.zip SHA256
```

## Getting started

Unpack the archive and point the solver at its own runtime files. The paths
differ per platform.

### Linux x86-64

```sh
export OPENCOURANT_PATH=/path/to/OpenCourant
export LD_LIBRARY_PATH=$OPENCOURANT_PATH/extlib/hm_reader/linux64:$OPENCOURANT_PATH/extlib/h3d/lib/linux64:$LD_LIBRARY_PATH
export RAD_CFG_PATH=$OPENCOURANT_PATH/hm_cfg_files
```

### Linux arm64

```sh
export OPENCOURANT_PATH=/path/to/OpenCourant
export LD_LIBRARY_PATH=$OPENCOURANT_PATH/extlib/hm_reader/linuxa64:$OPENCOURANT_PATH/extlib/h3d/lib/linuxa64:$LD_LIBRARY_PATH
export RAD_CFG_PATH=$OPENCOURANT_PATH/hm_cfg_files
```

### Windows x86-64

From `cmd.exe`:

```bat
set OPENCOURANT_PATH=C:\path\to\OpenCourant
set PATH=%OPENCOURANT_PATH%\extlib\hm_reader\win64;%OPENCOURANT_PATH%\extlib\h3d\lib\win64;%OPENCOURANT_PATH%\extlib\intelOneAPI_runtime\win64;%PATH%
set RAD_CFG_PATH=%OPENCOURANT_PATH%\hm_cfg_files
set KMP_STACKSIZE=400m
```

The required Intel runtime libraries ship inside the package, under
`extlib/intelOneAPI_runtime/win64`.

### Afterwards

The Starter and Engine executables live in `exec/`, alongside the `anim_to_vtk`
and `th_to_csv` converters. Full instructions, including the OpenMPI
requirement for the `_ompi` Engines on Linux, are in
[INSTALL.md](https://github.com/OpenCourant/OpenCourant/blob/main/INSTALL.md).

## Building from source

The solver builds on Linux with GCC and GFortran, and on Windows with the Intel
oneAPI toolchain. Clone
[the repository](https://github.com/OpenCourant/OpenCourant) and follow
[HOWTO.md](https://github.com/OpenCourant/OpenCourant/blob/main/HOWTO.md),
which covers the prerequisites, the OpenMPI setup, and the build scripts.

## Something missing?

If a package you relied on under OpenRadioss is not here, say so. It helps us
prioritise. Start a thread on
[the forum](https://github.com/orgs/OpenCourant/discussions), open an issue on
[GitHub](https://github.com/OpenCourant/OpenCourant/issues), or find us in
[the chat](https://chat.rockylinux.org/rocky-linux/channels/opencourant).
