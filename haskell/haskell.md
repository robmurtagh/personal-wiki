# Haskell

## Helpful GHCi commands

* `:reload` reload all names in scope
* `:quit`
* `:set prompt  "\x03BB > "` would change the command prompt to `λ >`
* `:set -XExistentialQuantification` sets up the language extension

You can give [multiline input](https://en.wikibooks.org/wiki/Haskell/Using_GHCi_effectively) to GHCi as follows:

```text
   *Main> :{
   *Main| let askname = do
   *Main|               putStrLn "What is your name?"
   *Main|               name <- getLine
   *Main|               putStrLn $ "Hello " ++ name
   *Main| :}
   *Main>
```

## Template Haskell

[Template Haskell](https://wiki.haskell.org/A_practical_Template_Haskell_Tutorial) is similar to Lisp macros.

```haskell
{-# LANGUAGE TemplateHaskell #-}
```

It is used e.g. by `lens` to generate the various lenses into data structures __at compile time__

## Forall Keyword

`forall` [imposes constraints on parameterising types](https://en.m.wikibooks.org/wiki/Haskell/Existentially_quantified_types) when defining new data types

## Types and Typeclasses

In the following snippet ([reference](https://wiki.haskell.org/Constructor)):

* `data` means we're declaring a new type
* `Expr` is the type constructor
* `I ...`, `Add ...`, `Mul ...` are the value constructors

```haskell
data Expr = I Int         -- integer constants
          | Add Expr Expr -- add two expressions
          | Mul Expr Expr -- multiply two expressions
```

* Adding `deriving (Show)` at the end of a data declaration automatically makes that type part of the Show typeclass ([reference](http://learnyouahaskell.com/making-our-own-types-and-typeclasses)):

```haskell
data Expr = I Int         -- integer constants
          | Add Expr Expr -- add two expressions
          | Mul Expr Expr -- multiply two expressions
          deriving (Show)
```

## Generalised Algebraic Datatypes (GADTs)

The crux of [GADTs](https://en.wikibooks.org/wiki/Haskell/GADT) is that the provide a way to explicitly declare the type signature of each constructor.

The following language option is required:

```haskell
{-#LANGUAGE GADTs #-}
```

And then an example would be:

```haskell
data Maybe a where
   Nothing  :: Maybe a
   Just :: a -> Maybe a
```