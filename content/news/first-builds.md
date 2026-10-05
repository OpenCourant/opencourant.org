+++
title = "The first OpenCourant builds are here"
date = 2026-10-05T02:45:00Z
summary = "Stable Linux packages are now published automatically from OpenCourant's own continuous integration. Here's what it took to rebuild the delivery pipeline, what the community already fixed, and what is still missing."
+++

When we [announced OpenCourant](/news/announcing-opencourant/) on October 1, the
honest summary was that the code was safe and the lights were on. That was about
all we could claim. It is no longer all we can claim.

**OpenCourant now publishes automated builds.** Stable Linux x86-64 packages are
available from the new [downloads page](/downloads/) — compiled from source,
gated on the regression suite, and released straight from continuous
integration.

## What it took

The delivery pipeline we inherited did not survive the shutdown. It depended on
an internal container registry, self-hosted runners, a private binary
repository, and a second private source repository — none of which came with the
code. Every one of those had to be replaced before a single package could ship.

It has been rebuilt on OpenCourant's own infrastructure, using our own CI
images. The regression suite now runs as a gate *before* packaging, so a build
that fails QA is never published. The `anim_to_vtk` and `th_to_csv` converters,
which used to arrive as prebuilt binaries from a repository we no longer have,
are compiled from source in [OpenCourant/Tools](https://github.com/OpenCourant/Tools)
as part of the same pipeline.

## The community already fixed something

OpenRadioss relied on a proprietary input-reader library that was never kept in
git. When the upstream repositories went down, it went with them, and the newest
copies we could recover from public sources were months older than the rest of
the code base expected.

So we asked whether anyone still had one. Someone did. A community member had
archived the original package, we verified it against an independently recovered
binary of the same build, and it is now the reader in every Linux build we
publish. The starter uses the solver's native part API again instead of a
compatibility fallback.

One request, one answer, and every download since is better for it. That is the
entire premise of this project working as intended, inside a week.

## What is still missing

We would rather be specific than optimistic:

- **Windows and Linux arm64 packages.** Windows needs runners, a compiler
  toolchain, and open replacements for several vendor-internal build
  dependencies. arm64 is blocked on a reader binary that may not exist in public
  hands at all. Both already have placeholders on the downloads page and will
  appear there automatically as soon as the builds do.
- **A second reader fallback is still active.** Listing include files still goes
  through a compatibility path, because the function that replaces it only
  exists in a newer reader than anyone has recovered so far.
- **`/ALE/STRUCTURED_MESH` remains unsupported** and is rejected explicitly
  rather than silently producing bad meshes.
- **The open reader is the durable fix.** The AGPL-licensed reader already in
  the repository is a handful of functions short of replacing the proprietary
  one on every platform, ARM included. Finishing it removes this entire class of
  problem permanently.

## Still looking for people

The infrastructure is the easy part. The harder and more important work is
reassembling the community, and settling how this project is governed, with the
people who built it.

If you worked with OpenRadioss in any capacity — contributor, maintainer,
researcher, industrial user, student — please reconnect:

- **Forum:** [GitHub Discussions](https://github.com/orgs/OpenCourant/discussions) —
  questions, proposals, and release threads
- **Chat:** the [#opencourant channel](https://chat.rockylinux.org/rocky-linux/channels/opencourant)
  on the Rocky Linux Mattermost
- **Email:** [hello@opencourant.org](mailto:hello@opencourant.org)
- **Code:** [github.com/OpenCourant/OpenCourant](https://github.com/OpenCourant/OpenCourant)

And if you have old OpenRadioss release files or build directories sitting in a
downloads folder somewhere, check them. We are still looking.
