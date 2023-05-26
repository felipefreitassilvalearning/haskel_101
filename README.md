<center>
  <a href="https://www.haskell.org/documentation/"><img src="./haskell_logo.png" alt="Haskell Docs" width="200" /></a>
</center>

- [About this repository](#about-this-repository)
- [About Haskell](#about-haskell)
  - [Characteristics](#characteristics)
    - [Imutability](#imutability)
    - [Pure functions](#pure-functions)
    - [Syntax](#syntax)
    - [Reserved words](#reserved-words)
  - [Installation](#installation)
  - [Playground](#playground)
  - [Project management (Stack)](#project-management-stack)
- [In practice](#in-practice)
  - [Functions](#functions)
  - [Lists](#lists)
  - [Types](#types)
  - [Tuples](#tuples)

## About this repository

This repository contains many projects built in Haskell, varying in difficulty. This is my first experience with the functional paradigm.
It was based on the [Programação Funcional em Haskell - Curso Completo - UFABC](https://www.youtube.com/playlist?list=PLYItvall0TqJ25sVTLcMhxsE0Hci58mpQ) playlist from [ufabc_hal](https://www.youtube.com/@ufabchal) channel.

## About Haskell

Haskell is a functional programming language, which means that it is based on the lambda calculus. It is a purely functional language, which means that in Haskell, functions are first-class citizens. This means that functions can be passed as arguments to other functions, returned as values from other functions, and stored in data structures. Haskell is also a lazy language, which means that expressions are not evaluated until their results are needed.

### Characteristics

- Haskell is a language that is
  - lazy
    - expressions are not evaluated until their results are needed
    - infinite data structures are possible
      - as they are not evaluated until their results are needed
      - for example, [1..] is a list from 1 to infinity
      - but it is not evaluated until its results are needed
      - so it is possible to get the first 10 elements of this list
      - but it is not possible to get the last element of this list
        - as it is infinite
  - strongly typed
    - types are checked at compile time
  - compiled
    - it is compiled to machine code (not interpreted)
  - general-purpose
  - high-level
  - garbage-collected
    - so it is memory-safe
  - Turing-complete
    - meaning that it can do any computation that any other programming language can do
  - declarative
    - meaning that it describes what to do, not how to do it

#### Imutability

- There are no variables, only constants
- Once a value is assigned to a name, it cannot be changed
- Similar to math, where
  - if x = 2,
  - then x cannot be changed to 3 (x = 3)
- Loops are replaced by recursion
  - as variables cannot be changed, there is no way to change the value of a variable in a loop (counter, for example)

#### Pure functions

- Functions are pure
  - they always return the same result for the same arguments
  - they do not have side effects
    - they do not change anything outside of their scope

#### Syntax

- Haskell is case-sensitive
- Haskell uses indentation to delimit blocks of code
  - similar to Python

#### Reserved words
  - `case`
  - `class`
  - `data`
  - `default`
  - `deriving`
  - `do`
  - `else`
  - `foreign`
  - `if`
  - `import`
  - `in`
  - `infix`
  - `infixl`
  - `infixr`
  - `instance`
  - `let`
  - `module`
  - `newtype`
  - `of`
  - `then`
  - `type`
  - `where`

### Installation

To install Haskell, you can use the [Haskell Platform](https://www.haskell.org/platform/). It includes GHC, the de facto standard compiler for Haskell and Stack, a tool to manage Haskell projects.

### Playground

- `ghci`: starts the interactive Haskell interpreter.
- `Ctrl + D`: exits the interactive Haskell interpreter.

### Project management (Stack)

- `stack new <project-name>`: creates a new project.
- `stack new <project-name> simple`: creates a new project with a simple template.
  - Observations:
    - project-names must be in lowercase and use hyphens instead of spaces.
      - underscores are also not allowed
      - numbers are allowed, but not at the beginning of the name (or word, which starts every hyphen)
- `stack build`: builds the project.
- `stack run`: runs the project.

## In practice


### Functions

- Function naming starts with a lowercase letter
  - and uses camelCaseLikeThis
- Functions are called by writing the function name followed by the arguments
  - separated by spaces
  - for example, `f x y` calls the function `f` with the arguments `x` and `y`
    - this is equivalent to `f(x, y)`
- Parentheses are used to group expressions only
  - for example, `f (x + y)` calls the function `f` with the result of the sum of `x` and `y`
    - this is equivalent to `f(x + y)`
  - However, parentheses are not used to call functions
    - for example, `f(x, y)` is not valid
  - Parentheses are also not used to call functions with a single argument
    - for example, `f(x)` is not valid
    - instead, `f x` should be used
  - Parentheses are also not used to call functions with no arguments
    - for example, `f()` is not valid
    - instead, `f` should be used
  - Composite functions are also not called with parentheses
    - for example, `f(g(x))` is not valid
    - instead, `f (g x)` should be used
      - that is, the function `g` is called with the argument `x`, and the result of this call is passed as an argument to the function `f`
  - More examples
    - `f a b` is equivalent to `f(a, b)`
    - `f a b + c*d` is equivalent to `f(a, b) + c*d`
    - functions have higher precedence than operators
      - so `f a + b` is equivalent to `f(a) + b`
      - and `f a * b` is equivalent to `f(a) * b`
- Typing functions
  - Separate arguments via the `->` simbol
    - For example sum(a:number,b:number):number would be
    - sum :: number -> number -> number
    - sum a b = a + b

### Lists

- Lists are homogeneous.
  - This means that all elements of a list must be of the same type.
- Lists are defined by square brackets (`[]`).
- And its elements are separated by commas (`,`).
- A list of T is of type `[T]`.
- A list of lists of T is of type `[[T]]`.
- Conventions
  - lists are named by using the plural form of the element type
    - for example, `ints` is a list of integers
    - and `css` is a list of strings (a list of a (list of characters; string))
    - A String is equivalent to a `[Char]`.
      - And, of course, a sentence is a `[String]`.
        - Which is equivalent to `[[Char]]`.

- To create a list
- `[x]` creates a list with one element, x
- `[x..]` creates a list from x to infinity
- `[x..y]` creates a list from x to y
- `[x,y..]` creates a list from x to y, with a step of (y - x)
- `[x,y..z]` creates a list from x to z, with a step of (y - x)

### Types

- Types always start with an uppercase letter.
- Things are typed via the `::` notation.
  - So `v :: T` means that `v` is of type `T`.
- `:t <expression>`: shows the type of the expression.

- Int
- Integer
- Float
- Double
- Bool
  - True e False
  - && (and)
  - || (or)
  - not
- Char
  - Any unicode character
  - 'a'
  - '5'
- String
  - A list of characters
  - "abc"
  - "abc" == ['a', 'b', 'c']
- Num
  - A numeric type
  - Int, Integer, Float, Double
  - Floating || Fractional
    - Float, Double

### Tuples

- Tuples are finite sequences of elements, having 0 or more different types.
- They are heterogeneous.
  - This means that the elements of a tuple can be of different types.
- Tuples are defined by parentheses (`()`).
- And its elements are also separated by commas (`,`).
- Examples
  - (True, False) :: (Bool, Bool)
  - (1.0, "Sim", False) :: (Double, String, Bool)
- A Tuple with 1 element is simply the element
  - (1) :: Int == 1 :: Int
  - ([1,2,3]) :: [Int] == [1,2,3] :: [Int]
- It is however possible to create a tuple with 0 elements
  - It is called a unit
  - () :: ()