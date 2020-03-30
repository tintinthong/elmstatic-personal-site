Building simple shell script for git commands. to enable committing
- bash command 
- capture if errror
Project Euler using Haskell
Learn About haskell
- haskell is the girl you loved at camp but never got to cause she lived far away 

http://wadler.blogspot.com/2019/03/pinkers-thirteen-rules-for-better.html


---
title: "Types in Haskell"
tags: haskell
---

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