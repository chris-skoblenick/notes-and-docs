# Clean Code


## Chapter 1 - Clean Code
* Saying "I will go back to fix it later" rarely happens; compromise on requirements, not cleanliness
  * LeBlanc's law ("later equals never")
  * Upholding this is part of our professional responsibility; talked about a lot more in "Clean Coder"
* Clean code is something which can be read easily, and demonstrates care from the author
  * There's a lot of subjectivity built into this; who the intended audience is
  * what is "easy" varies between people
  * this needs to be the lens we evaluate everything through; don't lose track of the goal
* Boy Scout Rule: "always leave the (code) cleaner than you found it"
  * Don't limit to just refactors or large activities
  * Adding comments, cleaning up names, anything can help
  * As you learn, leave notes for the next person


## Chapter 2 - Meaningful Names
* Names should answer the big questions (units, purpose, anything *important* to understand)
* We have to be very careful about triggering the right concepts when we choose certain words, especially when they're loaded with meaning
  * Example: using `list` when it's a stack/array. Typically brings up concepts like linked lists.
* Use *real* domain names/terms
  * connects with Domain Driven Design; ensuring developers can talk with stakeholders using the same terms (to ensure we're talking about the same thing)
* Prefer pronouncable names, to make it easier to discuss them
* Use the right parts of language to frame the "thing" properly
  * Objects/Classes are nouns
  * Functions/methods are verbs
* Don't be cute or humorous; be kind to your future reader
  * They want to do their work, not appreciate what a clever person you are
* Shorter names are better, *so long as* they are clear
  * Long names are ok if that's the only way to make it clear


## Chapter 3 - Functions
* Advocates really small
  * This is a big point of common contention
  * Our code should be easy to read, and too small can cause readability/length issues
  * Naming is *very* hard. Trying to provide good quality names is that much harder when the number of functions explodes
  * Of all the things within the book, this is the one which I feel has aged the least well
  * I generally prefer the concepts raised by "A Philosophy of Software Design"
     * Prefer *deep* functions over shallow ones; something with a simple interface which hides complex details 
* Functions should only do one thing, and do it well
  * Using "And" as a code smell
* One level of abstraction per function context
* Code should be decomposed top-to-bottom, like a newspaper
  * Each functions should introduce the next
  * The file should be ordered to answer the questions shortly after they're asked ("what does X do? Ahh, it's the next function.")
* Functions should seek to take as few arguments as possible
  * When a single function needs a whole lot of inputs, it's generally doing too much
  * Flags generally signal it's multiple functions, not one!
* Keep Commands and Queries separate!
  * Prefer pure functions; answer questions OR perform mutations, not both! 


## Chapter 4 - Comments
* Old comments can propogate lies; they can be **harmful**.
* If people have difficulty expressing complex thought with code, and we're well practiced with writing code, how can we depend upon them to write intelligible comments?
* If some random set of checks is done, and it needs a comment, consider extracting a well named function instead.
  * CHALLENGE: over-use of this pattern can make your code read in a very choppy manner.
  * Where practical, function names should convey what it's doing, not comments.
* Useful: "Explanations of Intent"
  * Comments which do not explain what or how things are done, but focusing on **why** choices are made.
* Useful: "Warning of Consequence"
  * Sometimes it's really helpful to convey information not about the code itself, but about it's environment or consequence.
* Useful: "TODO Comments"
  * Can also really help future maintainers understand which patterns shouldn't be propogated, or changes we should make before further modification of the code is done
* Useful: "Amplification Comments"
  * Can call attention to things which are otherwise easy to skip over.
  * Because they introduce length (and often colouration in IDEs), it can make standard lines really jump out.
* Useful: API Comments
  * Instead of requiring external documentation, with modern IDEs, JSDoc comments are really helpful!
* Harmful: "Redundant Comments"
  * If the code already says something, and the comment says the same thing, it's just wasting their time and potentially causing confusion if it's not updated
* Harmful: "Misleading Comments"
  * As mentioned previously, sometimes comments are just plain wrong, or were correct at some point in the past.
  * This type is worse than not having a comment at all!
* Harmful: "Mandated Comments"
  * CHALLENGE: I really value a consistent code style
  * Example of mandated JSDoc - I feel it's very helfpul to have a consistent code style?
  * I can understand if some very simple or hyper-local exceptions occur?
* Harmful: "Position Markers"
  * CHALLENGE: I really value these in code bases
* Harmful: "Commented-Out Code"
  * I generally agree with this, however there are exceptions where they're used as "TODO Comments", and can offer some helpful context to maintainers during a transitionary time


## Chapter 5 - Formatting
* This is an area I really feel a great deal of passion for
* Vertical formatting
  * "Openness" between concepts is critical
    * Vertical space should allow for block "thoughts" to occur together
    * New (blank) lines denote "this thought is complete"
    * Lines with high vertical density should denote a cohesive, connected thought block
  * Variables should be declared as close to their usage as possible
  * Class instance varaibles should be at the top of the class, as they affect the understanding of the definition of the class
  * Dependent functions should be vertically close to eachother in a source file
  * The file should be designed to nicely read from top-to-bottom
* Horizontal formatting
  * Prefer to keep things horizontally compact, rather than aligned in a table
    * CHALLENGE: when dealing with very large sets of input tables for things like tests, I really do prefer doing this
    * His raise is that modern IDEs and colour coding make this less important, which I generally agree with.
  * Use consistent indentation to define your blocks
* Team rules: the whole team should be using a single style. It shouldn't be possible to tell who authored based on the style.
