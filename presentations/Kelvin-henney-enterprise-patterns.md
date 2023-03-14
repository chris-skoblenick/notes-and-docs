# Author
Kevlin Henney

# Summary
* The "promised land" of Enterprise Programming Patterns do not mean your software is clean.
* Object Oriented can be taken way too far.
* Blind obedience to "best practice" doesn't mean your code is "clean".
* Clean code isn't stuff with patterns & checks, it's only what is absolutely necessary.

# Link
https://www.youtube.com/watch?v=FyCYva9DhsI

# Notes
* Taking dependencies on 3rd parties can be dangerous (example: leftpad NPM package)
  * With open source, you are at the mercy of strangers with unknown professionalism and motives
  * Ensure it's worth taking on a dependency
* (~14:00) Fizz Buzz refactoring absurdity
  * DRY can be taken way too far
    * The simple solution can be good enough
  * If you take the "gold standard, apply patterns" approach, it can make simple solutions be completely unmaintainable
    * Just because something COULD be a factory, does not mean it SHOULD be a factory.
    * When we approach simple problems thinking "this needs to be maintainable, and could be large", the patterns & architecture can overwhelm the code
  * Sometimes, repeating yourself is the better solution, in the name of maintainability.
* (~23:00) Cargo Cult Programming
  * Signal vs. Noise in code 
    * Code necessary to fulfil requirements vs. Architecture and pattern boilerplate
  * Comments in code; we always hear "good code is self documenting"
    * Incrementing a value isn't worth explaining; but perhaps WHY may require a comment.
  * Asserting "it's best practice" isn't as useful as explaining "why" something is done
    * Example: in Java, it's normal to have tons of imports. Most IDEs will just hide them, it's not a problem! (no explaination as to "why is this a good thing?". Answer: List can conflict in java.awt & java.utils.
    * Instead of focusing on "it's best practice", we should always consider "why are people saying this is a good thing?"
  * Repetition can be done even for untrue statements.
* (~39:00) Blind obedience to "follow best practice" isn't going to leave you a better coder, or lead to better code.
  * Understanding the pattern is important; understanding when (and when not) to apply it is more important.
    * Example: when should you use a Factory? When should you use a Strategy? When should you use Singleton?
    * When you have a hammer, everything looks like a nail.
    * Just because you understand a pattern, doesn't mean applying it will result in improvement.
* (~41:00) Not everything in a computer system should be a noun; (Object Oriented can be taken way too far)
  * Sometimes a `ThirstQuencherContainer` should just be called a `Glass`
  * Obvious naming can be more helpful then specific names which will never have collisions
    * We have tools like namespaces, project, modules, etc
    * Naming is important; make sure it's clear & simple
  * In general, if something has the name `Manager` in the name, it can likely be simplified.
    * Instead of `ConfigurationManager`, maybe it should just be called `Configuration`?
    * Instead of `ConditionChecker`, maybe just `Condition`? Or if you can define lambdas, why even have them to begin with as a class?
  * When naming, treat the initial name as fluid, until you understand enough about it to reduce it's name to only what is essential.
* (~50:00) Interesting (overlooked) anti-patterns
  * Mixed Levels of Abstraction
    * As a reader, I have an expected (and consistent) level of abstraction when looking at code
    * When it jumps suddenly from high level to very low, it can feel like a rollercoaster.
    * Ideally, design your code such that it's consistently stratified by abstraction level, or wade them in slowly.
* (~60:00) When he refactored the function, it wasn't by applying a bunch of enterprise patterns, it was making it read more easily by taking it down to only what was absolutely necessary (in the case of his function, nothing).
    * Instead of comments above blocks, turn them into private functions
    * Instead of declaring all your variables together, co-locate the variable declaration with the block which acts upon it
    * Question everything; instead of boilerplate and checks, find ways to avoid writing code at all.
