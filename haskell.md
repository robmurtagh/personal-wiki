# Haskell

## Start a new stack project

In parent directory, where `simple` is the template from `stack templates` list:

```bash
stack new [project-name] simple 
```

## stack ghci

ghci session in the context of the current project:

```bash
stack ghci
```

## Install a dependency

* For a global package install, like `npm install -g package` use cabal NOT stack:

```bash
cabal update && cabal install package
```

* For a local package install restricted to only a stack project e.g. `npm install package`, use `project.cabal`:

```text
  build-depends:       base
                     , haskell-hspec
                     , hspec
                     , QuickCheck
```


## ghci helpers

`reload` does what it says on the tin and refreshes all names:

```bash
:reload
:quit
```