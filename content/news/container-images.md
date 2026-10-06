+++
title = "Container images are here"
date = 2026-10-06T03:30:00Z
summary = "Multi-arch solver containers for x86-64 and arm64 are now published to Docker Hub and GHCR with every stable release, OpenMPI included, QA-gated like everything else."
+++

OpenCourant now ships as a container. Every stable release publishes multi-arch
images — one tag covers both x86-64 and arm64 — to two registries:

```text
docker.io/opencourant/opencourant
ghcr.io/opencourant/opencourant
```

The images are built from the same release packages you can download, include
the OpenMPI runtime so the `_ompi` Engines work immediately, and are
smoke-tested on both architectures before publication. Like the packages
themselves, they only publish after the full regression suite passes.

Running a model is one command:

```sh
docker run --rm -v $PWD:/work -e OMP_NUM_THREADS=4 \
    opencourant/opencourant starter -i MODEL_0000.rad -np 1
```

HPC users can pull the same image with Apptainer:

```sh
apptainer pull opencourant.sif docker://ghcr.io/opencourant/opencourant:latest
```

Use `latest`, or pin a release with its dated tag such as `latest-20261006`.
Full instructions are on [the downloads page](/downloads/#containers).

Containerized OpenRadioss used to be a community affair — and a vital one: one
of the recovered reader libraries that keeps this project running was salvaged
from exactly such a community image after the upstream deletion. Making
containers a first-class, officially published artifact is partly a thank-you
to that tradition.
