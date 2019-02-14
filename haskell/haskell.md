# Haskell

## GHCi

* `:reload` reload all names in scope
* `:quit`
* `:t 9` returns the type of `9`
* `:k Int` returns the kind of `Int`
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

## General syntax

### Guard syntax

[Guard Syntax](https://en.wikibooks.org/wiki/Haskell/Control_structures#if_and_guards_revisited) allows us to conditionally check a statement within a pattern matching expression.

```haskell
describeLetter :: Char -> String
describeLetter c
   | c >= 'a' && c <= 'z' = "Lower case"
   | c >= 'A' && c <= 'Z' = "Upper case"
   | otherwise            = "Not an ASCII letter"
```

## Modules

[This page](http://learnyouahaskell.com/modules) from 'Learn you a Haskell' is a good reference.

### Import hiding

```haskell
import Data.List hiding (nub)  
```

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

### Record syntax declarations

[Syntactic sugar](https://en.wikibooks.org/wiki/Haskell/More_on_datatypes#Named_Fields_%28Record_Syntax%29) providing data accessors:

```haskell
data Configuration = Configuration
    { username      :: String
    , localHost     :: String
    , remoteHost    :: String
    , isGuest       :: Bool
    , isSuperuser   :: Bool
    , currentDir    :: String
    , homeDir       :: String
    , timeConnected :: Integer
    }
```

You can pattern match against them:

```haskell
getHostData (Configuration { localHost = lh, remoteHost = rh }) = (lh, rh)
```

And create new versions with certain fields overwritten using:

```haskell
cfg { currentDir = newDir }
```

### `newtype` declarations

For the moment, I treat `newtype` as being broadly interchangable with `data` when creating a new type. There's documentation about it [here](https://wiki.haskell.org/Newtype).

### Typeclass: Semigroup

A set with an associative binary operation. Superset of Monoids.

### Typeclass: Monoids

[Monoid](https://en.wikibooks.org/wiki/Haskell/Monoids) is a typeclass with an associative `mappend` operation and an identity element.

> Integer numbers form a monoid under addition with 0 as identity element
> Integer numbers form a monoid under multiplication with 1 as identity element
> Lists form a monoid under concatenation with the empty list as identity element

`mappend` is given the infix synonym `(<>)`

### Generalised Algebraic Datatypes (GADTs)

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

## Miscellaneous

### Template Haskell

[Template Haskell](https://wiki.haskell.org/A_practical_Template_Haskell_Tutorial) is similar to Lisp macros.

```haskell
{-# LANGUAGE TemplateHaskell #-}
```

It is used e.g. by `lens` to generate the various lenses into data structures __at compile time__

### Forall Keyword

`forall` [imposes constraints on parameterising types](https://en.m.wikibooks.org/wiki/Haskell/Existentially_quantified_types) when defining new data types