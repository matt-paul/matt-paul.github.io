---
layout: post
title: Blocks, Procs and Lambda's
---

##Procs
Procs are ways of saving blocks as re-usable objects, which can then be called in different contexts, for example as method arguments, placed in arrays or called using the .call method

```
p = Proc.new { puts 'I am a Proc'}
p.call  #=> I am a Proc
```

They keep in scope any local variables that were in scope at the time of creation. Proc is a class in Ruby.

##Lambdas
Lambda's are a certain type of Proc, and differ in two important ways.  Firstly, whereas a normal proc will assign nil to a variable for arguments that are not passed in, Lambda's will raise an argument error, much like a method would do.
Secondly, lambda' treat return in a different way to Procs. Within a lambda, return triggers an exit from the lambda to the code content immediatly surrounding the lambda.  Return from a Proc triggers a return fro the method from which the Proc is being executed.  In this regard, they act much like anonymous functions in other languages.
