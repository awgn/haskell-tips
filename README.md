Haskell-Tips 
============

This is a collection of Haskell tips I've gathered reading books, blogs, twitter etc. 
I use this list predominantly as a reminder.

___

* ViewPatterns - GHC (https://ghc.haskell.org/trac/ghc/wiki/ViewPatterns)

* Use Show for debugging. Make a Pretty/ToFormat class for pretty pretting/serialization (@HaskellTips)

* If you're unsure how to create a type, see if it has a Default/Monoid instance and use def/mempty to make an arbitrary value. (@HaskellTips)

* GADTs (http://dev.stephendiehl.com/hask/)

```haskell
{-# LANGUAGE GADTs #-}

data Term a where
    Lit    :: Int -> Term Int
    Succ   :: Term Int -> Term Int
    IsZero :: Term Int -> Term Bool 
    If     :: Term Bool -> Term a -> Term a -> Term a
```

* Newtypes can prevent logic errors. To make them easier to work with, use GeneralizedNewtypeDeriving to regain the type instances. (@HaskellTips)

* Generalized deriving - GHC (http://dev.stephendiehl.com/hask/)

```haskell
{-# Language GeneralizedNewtypeDeriving #-}
{-# Language StandaloneDeriving #-}
{-# Language DeriveDataTypeable #-}
{-# Language DeriveFunctor #-}
{-# Language DeriveFoldable #-}
{-# Language DeriveTraversable #-}
```

* Smart Contructor idiom: 

```haskell
module Test (Test(), mkTest) where

data Test = Test Int

mkTest :: Int -> Test
mkTest n = if n >= 0 then Test n 
                     else error "mkTest: n < 0"
```

* Haskell performance it's all about seq, BangPatterns, unboxed types, primitive operations, and async.

* LambdaCase extension:

```haskell
    map (\case 0 -> "zero"; _ -> "not zero") [0,1,2]
```

* NamedFieldPuns can be used to make pattern matches cleaner (@HaskellTips):
```haskell
    data F = F {x :: Int, y :: Int}
    let g F { x } = x + 1 
```

* The best four things from Control.Arrow (@HaskellTips):

```haskell
    first f (x,y) = (f x,y)
    second f (x,y) = (x,f y)
    (***) f g (x,y) = (f x,g y)
    (&&&) f g x = (f x,g x)
```
