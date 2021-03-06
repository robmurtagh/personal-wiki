# Haskell

## GHCi

* `:reload` reload all names in scope
* `:quit`
* `:t 9` returns the type of `9`
* `:info []` returns lots of useful details about the implemented typeclasses
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

### Quick reference:

The best way to find out about these kind of constructs in ghci, e.g. `:info <*>`:

* `(.)` - Function composition
* `<*>`
* `$`

### Guard syntax

[Guard Syntax](https://en.wikibooks.org/wiki/Haskell/Control_structures#if_and_guards_revisited) allows us to conditionally check a statement within a pattern matching expression.

```haskell
describeLetter :: Char -> String
describeLetter c
   | c >= 'a' && c <= 'z' = "Lower case"
   | c >= 'A' && c <= 'Z' = "Upper case"
   | otherwise            = "Not an ASCII letter"
```

### 'where' clause

Define inline bindings (e.g. to functions or values). The [following example](http://learnyouahaskell.com/syntax-in-functions) uses guards and a where clase:

```haskell
bmiTell :: (RealFloat a) => a -> a -> String  
bmiTell weight height  
    | bmi <= 18.5 = "You're underweight, you emo, you!"  
    | bmi <= 25.0 = "You're supposedly normal. Pffft, I bet you're ugly!"  
    | bmi <= 30.0 = "You're fat! Lose some weight, fatty!"  
    | otherwise   = "You're a whale, congratulations!"  
    where bmi = weight / height ^ 2
```

### 'as' Pattern

The 'as' pattern (described [here](https://stackoverflow.com/questions/1153465/what-does-the-symbol-mean-in-reference-to-lists-in-haskell), [here](http://learnyouahaskell.com/syntax-in-functions) and [here](https://www.haskell.org/onlinereport/exps.html#sect3.17.1)), gives us a way of matching a name for the entire element being pattern matched in a list:

The following would be read `all as (x:xs)`:

```haskell
capital :: String -> String  
capital "" = "Empty string, whoops!"  
capital all@(x:xs) = "The first letter of " ++ all ++ " is " ++ [x]
```

### Modules

[This page](http://learnyouahaskell.com/modules) from 'Learn you a Haskell' is a good reference.

* Import hiding

```haskell
import Data.List hiding (nub)  
```

### Indentation

From [this page](https://en.wikibooks.org/wiki/Haskell/Indentation), the golden rule of indentation is:

> Code which is part of some expression should be indented further in than the beginning of that expression...All _grouped_ expressions must be exactly aligned

But you can avoid indentation:

> Indentation is actually optional if you instead use semicolons and curly braces

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