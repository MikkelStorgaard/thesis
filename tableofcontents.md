# Mikkels speciale
# Table of contents

0. The prelude
  1. Abstract
  2. Table of Contents
  3. Preface

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
    but instead are hand-tailored implementations uniquely crafted to exploit things like memory management in the source language.
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
    
    3. FShark itself. FShark is a compiler which, given an F# file that is written exclusively using the prelude and the limited subset, 
    , which consists of an FShark prelude
    
    
    

