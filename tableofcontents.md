Mikkels speciale


0. The prelude
  1. Abstract
  2. Table of Contents
  3. Preface
  4. Vocabulary

1. Introduction
  1. Sequential vs. parallel computin
    1. What is sequential computing good at
    2. What is parallel computing good for? (list a couple of use cases for parallel computing, i.e. physics simulations and large scale data processing.)
    3. Parallel 

  2. The Futhark Language
    1. Shortly describe the Futhark programming language,
    the way that it's design nudges the user towards designing programs 
    that are inherently parallelizeable (because of how Futhark focused on maps, reduces, and partly folds and loops.)
    
    3. The optimizing compiler generates standalone modules that can be 
    used as either libraries or stand-alone programs.
    
    4. Benchmarks ported from other languages to Futhark shows in most cases, that 
    the Futhark versions are (much) faster than their source language counterparts.
    The only exceptions are source benchmarks which are not written as "obvious" implementations of an algorithm
    but instead are hand-tailored implementations uniquely crafted to exploit things like memory management i\chapter{The \LO{} language}
\label{chap:l0language}
n the source language.
    (lets call back to this point when we compare FShark to similar solutions)
    
    5. Conclusion: Futhark creates huge performance boosts wherever it goes. 
    However, this entails writing actual Futhark programs, which has a certain learning curve.
    This thesis seeks to let normal F# developers develop Futhark programs without writing any actual Futhark code. 

    Instead of writing Futhark code directly, F# developers are given a subset of the F# language, and an FShark prelude library, which can be used in combination to write
    F# programs, that are guaranteed* to translate to equivalent Futhark programs.
    
    As a nice bonus, FShark code can be debugged directly within IDEs like Rider and VSCode.
    
  3. The contributions of this thesis.
    1. The FShark prelude: A library of second order array combinators and array helper functions, 
    which all map 1-to-1 to equivalent Futhark functions. 

    2. A limited and Futhark translated subset of the F# language.
    
    3. FShark itself. FShark is a compiler/wrapper pipeline which, given an F# file that is written exclusively using the prelude and the limited subset, 
    compiles, imports and invokes Futhark programs at runtime, from within a regular F# program. 
    Although setting up FShark does require a bit of configuration, the final result is a wrapper that enables F# programs to leverage Futhark speeds whilst demanding minimal changes 
    to the original code.
    
    4. A C# backend for Futhark. As F# has "painless" F#/C# interoperability, and C# has a library with "optimal" OpenCL bindings, Futhark-csharp modules were 
    the most obvious way to generate Futhark code (via FShark), and invoke the resulting program in the original F# program.
    Futharks intermediate language itself is imperative, it has been relatively easy to generate valid C# code from Futharks ImpCode.
    The C# backend is useful not only for FShark purposes, but does also add C- and F# to the list of languages that can employ Futhark in their projects.
    
  4. Roadmap
    
2. Background
  1. What is Futhark?
    1. a short description of the language
    2. a short description of how compiled futhark libs are used in C or Python projects
  2. What is F#?
    1. a short description of the syntax
    2. description of the benefits of F# being .NET and lib-sharing with C#

Part One: The FShark Language
3a. Write the complete FShark grammar
    (include supported statements in grammar)
3b. List the supported F# Operators 

3. The FShark Prelude
  1. Introduction
  2. Description of the chosen library functions, their F# implementations and corresponding Futhark function.
  3. Arguing their correctness (also from testing) based on equivalence testing between F# and FShark

4. The F# Subset
  1. Introduction
  2. Arguing for the selected subset (i.e. why specifically operators and built-in math functions)
  3. Description of the chosen library functions and their F# implementations.
  4. Describe and defend specific subset handlings (i.e. log10 which doesn't have a futhark equivalent, 
  and therefore have been implemented as an inlined log identity)
  5. Arguing their correctness (also from testing) based on equivalence testing between F# and FShark
  
Part Two: The FShark Compiler and Wrapper
5. The FShark Compiler
  1. Parsing an FSharp program using the FSharp compiler
    1. A short description of the FSharp Compiler Services package
    2. An example of a well-formed FShark program
    3. Running the FSharp Compiler Service on a well-formed FShark program
    
  2. Building an FShark program from the parsed ImplementationFileDecl list
    1. Getting the root entity from the parsed program
    2. Writing up the complete conversion rules from FSharpVals and -Exprs to FSharkDecls and -Code
    3. Talk about retrieving function types from FSharpVals
    4. Writing up the complete conversion rules from FSharkDecls and -Code to Futhark
  
  3. Pretty-printing, compiling and invoking the resulting Futhark program in the FShark-using F# program.
  
  4. Invoking FShark
    1. Types that are usable in the invokation
    2. flattening F# arrays into flat arrays, and back again
Part Three: The Futhark C# Generator
6. The Futhark C# Generator
  1. Writing OpenCL-enabled C# code
    1. Choosing an OpenCL library fit for the task
    2. Alternatives to Cloo, and why they weren't chosen

  2. Designing the standalone Futhark C# class/library class.
    1. Global size-things for opencl.
    2. The class itself (initial fields, futhark functions, entry functions and the entry itself)
    
  3. The Futhark ImpCode intermediate language
    1. Convertion rules from ImpCode to C#
    2. Convertion rules from ImpCode to C# (with OpenCL)
    
  4. (maybe describe the free list)

Part Four: Results and the rest
7. Evaluation
  1. An example of a finished FShark-using F# program
  2. Benchmark comparisons between FShark running native in F#, and through the FShark compiler (both CL and non-CL)
  3. Benchmark comparisons between FShark and other OpenCL implementations for F#
  
  4. Explain where the speed differences comes from.
8. Limitations

9. Method

10. Related work

11. Future work 

12. Conclusion

  
