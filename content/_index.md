+++
title = "OpenCourant"
+++

## What happened to OpenRadioss?

On October 1, 2026, Siemens discontinued the OpenRadioss project. The website
was retired and the GitHub repository — home to four years of community-driven
development on the open-source version of the Radioss finite element solver,
originally published by Altair in 2022 — was removed without an archive.

The code, however, was released under the GNU AGPL v3, and free software
doesn't disappear just because a repository does. **OpenCourant** continues
from the last available open-source code base — so that this work remains
open, permanently, for everyone.

## Why "Courant"?

The name honors Richard Courant and the **Courant–Friedrichs–Lewy (CFL)
condition** — the stability criterion at the heart of every explicit
time-integration solver, including this one. It's a nod to the numerical
foundations this community builds on.

## Where things stand

The solver builds, runs, and ships. Continuous integration has been rebuilt on
OpenCourant's own infrastructure, replacing the vendor-internal pipeline it
inherited; the regression suite gates every release; and stable Linux and
Windows packages are published automatically.
**[Get the latest build →](/downloads/)**

The full commit history came across intact, so the work of everyone who
contributed to OpenRadioss is preserved and attributed. Linux arm64 builds run
natively in an experimental pipeline and aren't packaged here yet, and a few
proprietary build-time pieces still need open replacements. All of it is
tracked in the open.

## We're looking for the OpenRadioss community

The code is safe and the builds are flowing. What this project still needs is
its people. If you were a user, contributor, researcher, or maintainer of
OpenRadioss — or you're simply interested in open-source crash and impact
simulation — we want to hear from you.

<ul class="contact-grid">
  <li>
    <strong>Code</strong>
    The solver lives at <a href="https://github.com/OpenCourant/OpenCourant">github.com/OpenCourant/OpenCourant</a>.
    Issues and pull requests are open.
  </li>
  <li>
    <strong>Forum</strong>
    Ask questions, propose changes, and follow release threads in
    <a href="https://github.com/orgs/OpenCourant/discussions">GitHub Discussions</a>.
  </li>
  <li>
    <strong>Chat</strong>
    For realtime conversation, join the
    <a href="https://chat.rockylinux.org/rocky-linux/channels/opencourant">#opencourant channel</a>
    on the Rocky Linux Mattermost.
  </li>
  <li>
    <strong>Email</strong>
    Email the project directly at <a href="mailto:hello@opencourant.org">hello@opencourant.org</a>.
  </li>
</ul>

This is not an abstraction: when we asked whether anyone had archived a build
dependency that vanished with the upstream repository, someone did. That
contribution improved every Linux build published since.

Former OpenRadioss maintainers and community leaders: please get in touch. We
want governance and direction for this project to be set by the people who
built it.
