# OpenFOAM (com) {#sec-openfoam-com}

Unlike other distributions, you don't have to source `$OPENFOAM_DIR/etc/bashrc` via `bash`
before running OpenFOAM executables.

Most OpenFOAM binaries are also able to run in parallel via `mpi`: to make
invocations easier, each binary has an additional wrapper, such as `simpleFoam-mpi`.

## How to compile and use OpenFOAM extensions {#how-to-compile-and-use-openfoam-com-extensions}

The derivation exposes a function to compile extensions:

```nix
fooExt = openfoam.mkExtension {
  name = "foo";
  src = ./test-ext;
};
```

These extensions can then be merged together with OpenFOAM to produce a new derivation:

```nix
openfoam' = openfoam.withExtensions [fooExt];
```
