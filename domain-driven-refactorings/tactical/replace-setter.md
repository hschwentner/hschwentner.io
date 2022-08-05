---
title: Replace Setter
---

*Relative to [Rename Method](https://refactoring.com/catalog/changeFunctionDeclaration.html)*

![](../../images/domain-driven-refactorings/tactical/replace-setter.drawio.svg){: .align-center}

## Motivation

As one of the first lessons in programming we have learned that it’s good thing to protect variables and make them as less visible as possible. (A direct application of Parnas’s *information hiding*.) Instance variables or fields in classes are therefore by default declared `private`. Unfortunately, many programmers have also learned that the next thing is to write a getter and setter for that variable. Just as unfortunately, modern IDEs support this bad behavior with automatic generation of these accessor methods. If your on the JVM, the Java Beans convention enforces it.

A better (and more domain-driven) approach is to build our classes with methods that resemble domain behavior and have names that expresses this behavior. The verbs in the method names should come from the domain and *set* is a verb that is just not used in most domain.

If the setter is never used and just there because it has been generated automatically, apply [Remove Setter](replace-setter).

## Mechanics

- Identify the setter to be replaced
- Model with your domain experts the corresponding business process to find out what the right name for the new method will be
- Introduce the the new method into the to-be changed class
- Find the calls to the getter
- Step by step see how you can replace the call to the getter with a call to the domain-named method
- When all calls to the getter are replaced, remove it from the class

There are some similarities to [Rename Method](https://refactoring.com/catalog/changeFunctionDeclaration.html) here. A difference is that often the new method does not just set the field but may add some other business behavior as well.

## Example(s)
