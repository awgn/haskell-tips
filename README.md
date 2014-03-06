Haskell-Tips 
============

This is a collection of Haskell tips I've gathered reading books, blogs, twitter etc. 
I use this list as a reminder predominantly.


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
```


