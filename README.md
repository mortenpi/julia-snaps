# Snap packages for Julia

This repository contains the [snapcraft](https://snapcraft.io/) build files
to build a snap package for [Julia](https://julialang.org/) and its [Atom-base IDE Juno](http://junolab.org/).

* The Julia distribution simple repackages the official generic Linux binaries.
* The Juno snap includes a wrapper script that starts Atom in `$HOME/.juno`
  and sets up a `.desktop` file, making it look like a separate IDE.

## Building

To build the snaps, `cd` into either `julia/` or `juno/` and call `snapcraft`, e.g.:

```
$ cd julia/
$ snapcraft
```

To install the snaps:

```
$ snap install <snap-file>.snap --classic --dangerous
```

The snaps use classic confinement. `--dangerous` is necessary because the local builds are not signed.


## Using the Atom snap distribution for Juno.
There appears to be a bug in either Snappy or Node.js that makes it problematic to
run a snap binary from Node.js that is distributed as a snap
(see [nodesource/distributions#663](https://github.com/nodesource/distributions/issues/663) for more information).
For Juno/Julia this means that Atom (which uses Node.js) can not start snap-packages
`julia` binary packaged properly.

You have two options:

1. Do not use the Atom snap distribution.
2. Change the Julia path to the full binary path `/snap/julia/current/bin/julia`
   in the `julia-client` package settings in Atom.
