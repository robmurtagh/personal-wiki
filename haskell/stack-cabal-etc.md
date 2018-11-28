# Stack, Cabal etc

[Stack](https://docs.haskellstack.org/en/stable/README/) is *a* (not the only) Haskell standard for scaffolding, building, packaging and managing dependencies for a project. It uses [Cabal](https://www.haskell.org/cabal/) under the covers. The interplay between Stack, Cabal and [HPack](https://github.com/sol/hpack) makes this area a bit of a minefield.

## Start a new stack project

In parent directory, where `simple` is the template from `stack templates` list:

```bash
stack new [project-name] simple
```

## Run ghci

GHCi session in the context of the current project:

```bash
stack ghci
```

## Build and run executable

```bash
stack build && stack exec package-name-exe
```

## Install a dependency

* For a global package install, like `npm install -g package` use cabal NOT stack:

```bash
cabal update && cabal install package
```

* For a local package install restricted to only a stack project e.g. `npm install --save package`, use `project.cabal`:

```text
  build-depends:       base
                     , haskell-hspec
                     , hspec
                     , QuickCheck
```

## List depedencies

```bash
stack list-dependencies
```

## Pass and argument to stack ghc

```bash
stack ghc -- --supported-extensions
```

## Environment setup

### What is my global ghc, why, and how do I change it?

Global ghc could have been installed in all sorts of ways, it is found by running:

```bash
ghc -v
```

But really you probably want to be using a Stack managed global setup e.g. outside of a project folder, run one of the following commands:

```bash
stack ghci -v
stack ghc -v
```

This should tell you in the logs that you are using e.g. `.stack/global-project/stack.yaml`. The `resolver` field in this file will determine which ghc version you are using.

### What is my project GHC, why, and where is it stored?

The project ghc is set via the local `stack.yaml`, again using the resolver to determine the version. ghc itself will be installed somewhere centrally by Stack.

### What are my globally installed packages, why, and where are they stored?

The following command when run globally tells you all of the packages which are installed:

```bash
ghc-pkg list
```

### What are my project installed packages, why, and where are they stored?

```bash
stack list-dependencies
```

## Useful resources

* [Problems with Cabal and how to avoid](https://wiki.haskell.org/Cabal/Survival)
* [Cabal github repo](https://github.com/haskell/cabal)
* [Why is Stack not Cabal](https://www.fpcomplete.com/blog/2015/06/why-is-stack-not-cabal)
* [Stackage is Stable Hackage and packages here have been tested to avoid dependency conflicts](https://www.stackage.org/)
* [Stack.yaml versus .Cabal](https://docs.haskellstack.org/en/stable/stack_yaml_vs_cabal_package_file/)
* [Stack FAQs](https://github.com/commercialhaskell/stack/blob/master/doc/faq.md)

## Notes

The logic for resolving dependencies without and with Stack is as follows:

* Packages GHC can use >  Are registered with "ghc-pkg register" > And (almost always) built with Cabal >  With build dependencies resolved by cabal-install > From Hackage.
* Packages GHC can use >  Are registered with "ghc-pkg register" > And (almost always) built with Cabal >  With build dependencies resolved by stack > From Stackage (if possible...) or Hackage

Stackage specifies a 'resolver'

> a GHC version, a number of packages available for installation, and various settings like build flags"

[Global Stack managed dependencies](https://docs.haskellstack.org/en/stable/yaml_configuration/):

* `/etc/stack/config.yaml` - for system global non-project default options
* `~/.stack/config.yaml` - for user non-project default options

When stack is invoked outside a stack project it will source project specific options from `~/.stack/global-project/stack.yaml`. When stack is invoked inside a stack project, only options from `<project dir>/stack.yaml` are used, and `~/.stack/global-project/stack.yaml` is ignored.
