---
layout: reference
title: `throw` statement
tab: documentation
author: Tom Bentley
---

# #{page.title}

## Usage 

A bare `throw` doesn't supply an exception instance:

<!-- lang: ceylon -->
    throw;

Otherwise an exception instance may be specified; commonly a new instance is 
created at the point the `throw` statement is used:

<!-- lang: ceylon -->
    throw Exception();

## Description

The `throw` statement causes the enclosing method, attribute accessor or 
initializer to return *abnormally*, signifying an exceptional circumstance 
which prevents normal completion. Insead of returning to the caller, the 
call stack is searched for the nearest [`try`](../try) statement 
with a matching `catch` clause, and execution resumes at the start of that
`catch` block (possibly after [resource cleanup](FIXME)).

An expression may be supplied with the `throw` statement. If no expression is 
given a new messageless and causeless 
[`ceylon.language.Exception`](../../ceylon.language/Exception) instance is 
created automatically. If an exression is given is must be of a type which is 
assignable to `ceylon.language.Exception`.

It is possible, though not recommended, to use `throw` to implement control 
logic.

Ceylon does not support 'checked' exceptions. Any kind of exception may be 
thrown without it having to be declared by a 
[`throws` annotation](../../ceylon.language/throws) in the relevant declaration. 
This includes Ceylon code throwing what in Java would 
be considered to be checked exceptions (such as `java.lang.Exception`). In 
other words the following is perfectly acceptable to the Ceylon compiler:

<!-- lang: ceylon -->
    import java.lang {CheckedException=Exception};
    
    void m() {
        throw CheckedException();
    }

## Grammar

    throw: THROW expression;

## See also

* [`try` statement](../try)
* [`ceylon.language.Exception`](../../ceylon.language/Exception)
* [`throw` in the language specification] (FIXME)
