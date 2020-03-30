---
title: "Type you a Haskell"
tags: haskell
---

A lot of beginners visit Haskell and perceive it to be a truly difficult language to learn. Most describe the frustration comes from the alternative way of thinking "functionally". From my experience, this is opposite from the truth. Thinking functionally is not difficult. In fact, those concepts already manifest in other programming languages; For example, you can find first-order functions in javascript. 

I believe the harder concept is in digesting the type terminology. In order to feel progress in Haskell, you just needs to get really good in types and how they are used. They are the fundamental building blocks of Haskell and will be a powerful toolkit when solving complex problems (especially if you want to do it elegantly). 

I would like to disclaim that I directly copied the examples from (learnyouahaskell)[http://learnyouahaskell.com/]. It is a fantastic book; till this day I still use it as my book of Haskell fundamentals.  

### Why are Haskell types so important? 

There are two main reasons: 
1. Type-Safety: These exists in most low-level languages. The existence of a type system block unexpected behaviour of code.  
2. Parametric Polymorphism: In haskell, the type system do not have to take-on specific types rather a class of types. This is known as parametric polymorphism; it introduces more expression to the code while maintaining type-safety. 

### What is a type?

The most basic types in Haskell is 

- Char
- Bool
- String
- Int
- Integer
- Float 
- Double

These are known as the native/primitive types. Any newer custom types will be built upon these using constructors.   

```
addThree :: Int -> Int -> Int -> Int  -- function signature
addThree x y z = x + y + z  -- function declaration  
```

The function above is a simple function that adds three numbers. As you can see, it's type signature contains `Int` types as arguments to a function.  

In the above, 


### What is a typeclass? 

A general version of a type is a typeclass. A typeclass is a collection of types that behave similarly. 

- Eq
- Ord 
- Show
- Read 
- Enum
- Bounded 
- Num 
- Integral
- Floating

Each of the types in the previous chapter are contained in one or more typeclassess. Why bother with typeclasses anyway? The simplest answer: greater generalisation. 

```
addThree :: (Num a) => a -> a -> a -> a
```

As you can see, without restricing ourselves to types, we can create a function declaration that applies to more than one type. 

### What is an algebraic data type?

A type is synonymous with an algebraic data type. Let's not forget this. `Int`, `Char`, `Double` are all algebraic data types. 

```
data Bool = True | False 
     ----   ----   -----
     type   value constructors
```

The thing on the LHS is a type(or type constructor) and everything on the RHS is a value constructor. In this case, Bool is a type and, True and False are value constructors (simply functions). Let's see a few examples here:

```
data Shape = Circle Float Float Float | Rectangle Float Float Float Float   
```
Shape as the type and Circle and Rectangle are value constructors. What about Float? Is Float a type or is Float a value constructor? No. Float is indeed a type. 

```
data Tree a = Tip | Node a (Tree a) (Tree a)
```
Tree is a type constructor with single argument. Tip and Node are value constructors. The (Tree a) on the RHS however are types. 

```
data Point = Point Float Float 
```
Point is a type constructor. Point on the RHS is a value constructor. The two instances of Point are not the same. The simplest way to put it is that the former exists in type signatures whereas the latter exists in type declarations. 

```
:t Point  --refers to the value constructor
Point :: Float -> Float --> Point 
data Coordinates = Coordinates Point -- refers to Point type
:t Coordinates 
Coordinates :: Point -> Coordinates -- refers to Point type 
```

Notice that if I wrote. I would obtain a new value constructor for Point. This means that we should be careful to always make new value constructors for different types. If we wanted to use Point again, we should use it as an argument (a type ) inside a new constructor. 

```
data Coordinates' = Point 
:t Point 
Point :: Coordinates'  
```

### What is a type constructor? 

Type constructors are the basis of Haskell's type system. You can make functions deal with types which are not yet constructed. That's amazing.   

```
data Mayba a = Nothing | Just a
```

Let's apply what we just learnt just now. We have two value constructors Nothing and Just. Just will take a type of that received by the argument a. You can think of Maybe like a container that contains values of a certain type. 

This is important because Functors, Applicatives and Monads are types which deal with non-deterministic types like Maybe.

Remember. Just is a value constructor; much like a function. We can inspect this via `:t Just`. Whereas, Maybe is a type; not a function. It follows that we can't inspect this.














Rule of Thumb: 

never add typeclass constraints in data declarations

Because if we wrote it in the data declaration, we would need to write it inside all our keys. 






- Expressions: Expression is simply something that returns a value (??)
https://wiki.haskell.org/Declaration_vs._expression_style
- Functions
- Value Constructors
- Type Values: Predefined type values inside Prelude library are Booleans, Characters, Strings, Lists, Tuples, Unit, IO 
- User-defined Types: Anything beginning with data
- Type Constructors: Maybe, List 
- Type Constraint / Type Classes: 
        - Eq, Num, Ord, Enum, RealFrac, Integral, Float
        - Show, Read, Monad, Functor
- Type Synonym: 
- Type Signature:
- Polymorphic Types: A family of types, e.g. [a]
- Polymorphic Functions: A function that can be applied to and evaluate to values of different types
- Caset Syntax
- Fixity: Fixes how tightly operator binds(precedence) and (left associative or right associative)
### This is an example of a post


```
view : Header v m -> List (Element PageStyles v m) -> Html.Html m
view header contentElems =
    viewport stylesheet <|
        column Main
            [ center, width (percent 100) ]
            [ header
            , column Main
                [ width <| px 800, spacingXY 0 10, alignLeft ]
                contentElems
            , footer
            ]
```

https://www.haskell.org/onlinereport/haskell2010/haskellch6.html

https://www.haskell.org/tutorial/goodies.html

http://learnyouahaskell.com/making-our-own-types-and-typeclasses#type-parameters

Syntactical sugars about haskell:
Cons is the same as : 
: and ++ are different 