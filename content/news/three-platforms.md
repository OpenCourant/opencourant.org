+++
title = "All three platforms now ship"
date = 2026-10-06T01:00:00Z
summary = "Linux x86-64, Linux arm64 and Windows packages are all published from the same pipeline, each gated on the same regression suite. ARM was unblocked by a community donation of a lost reader package."
+++

OpenCourant now publishes packages for **Linux x86-64, Linux arm64, and
Windows x86-64**. All three come out of the same delivery pipeline, and none of
them ships unless the regression suite passes first.

[Get them from the downloads page →](/downloads/)

We first shipped a single platform, the other two now exist because people sent
us files. Thank you!

## Mission success

OpenRadioss depended on an input-reader library that was never kept
in git. When the upstream repositories were deleted, it went with them. We
[asked whether anyone had archived a copy](https://github.com/orgs/OpenCourant/discussions/10),
and someone had. That donation fixed the x86 reader and improved every Linux
build we publish.

ARM was harder. The only arm64 reader that survived anywhere was a February
2026 build, old enough that it could not parse the configuration files the
current code ships. ARM regression runs scored **0 out of 81**. The file we
needed had never been published, so there was nowhere to get it.

Another community member then turned up the official `latest-20260728` ARM
package.

We could verify it without trusting anyone's word for it. The package travels
with siblings: a Windows reader whose hash we already knew, and a Linux reader
we could compare byte-for-byte against the copy we had. Both matched. That
authenticated the ARM reader inside it as the genuine July **v70** build,
`20260710_d899773e`, the same build x86 and Windows already use.

ARM regression results went from **0/81 to 81/81**. The arm64 reader's list of
missing functions collapsed to exactly one, the same single function x86 has
been missing all along. The compatibility shims we had added specifically for
ARM were deleted, because ARM no longer needs special treatment.

## What you get

| Package | Contents |
| --- | --- |
| `OpenCourant_linux64.zip` | Starter and Engine, single and double precision, SMP and OpenMPI |
| `OpenCourant_linuxa64.zip` | Identical set, built natively for arm64 |
| `OpenCourant_win64.zip` | Starter and Engine, single and double precision, SMP and Intel MPI |

All three include the `anim_to_vtk` and `th_to_csv` converters and the launcher
GUI. The Linux `_ompi` Engines need OpenMPI 4.1.2; the SMP Engines run
standalone. The Windows package bundles the Intel MPI runtime, so single-node
`mpiexec` runs work with no extra setup.

Per-platform setup is on the [downloads page](/downloads/).

## Still open

- **One reader function is still missing on every platform.** Listing include
  files goes through a compatibility path, because the function that replaces
  it only exists in a reader newer than anything recovered so far. If you have
  an OpenRadioss package from **August or September 2026**, please check it.
- **`/ALE/STRUCTURED_MESH` is still rejected**, explicitly, rather than
  silently producing bad meshes.
- **The open reader is the durable fix.** The AGPL-licensed reader already in
  the repository is a handful of functions from replacing the closed one
  outright, on every platform. Finishing it ends this entire category of
  problem. No more hoping the right zip file is in someone's downloads folder.

## Thank you

People who went looking through old archives unblocked platforms we could not
have fixed ourselves. If you have old OpenRadioss release files, build
directories, or container images sitting around, please look.

Say hello on [the forum](https://github.com/orgs/OpenCourant/discussions) or in
[the chat](https://chat.rockylinux.org/rocky-linux/channels/opencourant).
