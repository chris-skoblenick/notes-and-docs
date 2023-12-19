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


## Chapter 6 - Objects and Data Structures
* Abstraction is not about adding layers, it's about allowing users to manipulate it without having to know its implementation.
  * Offer verbs like "throwBall" not just "setX" methods.
* Law of Demeter: "a module should not know about the innards of the objects it manipulates."
* Data Transfer Objects (DTOs) - a structure to allow modules/systems to communicate with eachother in an agreed upon structure (not that it's best suited for anything aside from the transfer)


## Chapter 7 - Error Handling
* Mental framing: try-catch-finally blocks are like transactions
  * Need to think about what happens when the unexpected happens; how should recoveries be done (if at all?) 
* Each exception you throw should provide context to allow it to actually be debugged
  * Noting it's happened is great, but that's often only the first step in debugging!
  * Especially true in minified environments!
* Generally, returning `null` is a code smell.
  * I think this is fine as a general situation, however using it as a blanket rule can assume the user isn't trying to do things like "does X exist"
* Generally, passing `null` is a code smell

## Chapter 8 - Boundaries
* As we don't own 3rd party code, there should be a very clear boundary to control how much influence they have over the structure of our application
  * Domain Driven Design as this concept taken to the extreme
  * Anti-Corruption Layer: contains breaking changes to the 3rd party library without spreading over the entire application
* Providers of 3rd party code seek to make broad tools to serve a wide range of uses. We want an implementation tailed to our specific application goals.
  * We would much prefer to have functions/objects/methods tightly suited to our purpose than have to infer what we need to do given the libraries we have chosen.
* By having a layer of indirection between the libraries we choose, and the application behaviour we want, we can change/refactor over time
* (DISAGREEMENT): adding tests on 3rd party code. If the 3rd party library changes/breaks, our tests should fail, otherwise we shouldn't be using the library to solve our needs?
* If we have our application offer functionality which isn't yet supported, we can just replace our implementation once it does exist

## Chapter 9 - Tests
* TDD is fine in principle, but does tend to lead to bloated test suites, because we're testing our code, not the product we're writing
  * BDD seems like an "evolved" way of approaching TDD, without the same maintenance issues
* (single concept per test, single assert per test)
  * this leads to very lengthy test suites to maintain over the life of the product, and acts as an inhibitor to refactoring & simplification
* F.I.R.S.T
  * Fast: should execute quickly.
  * Independent: should not depend on each other. (I feel overlapping is fine, and sometimes necessary?)
  * Repeatable: should be dependable and able to run in every environment
  * Self-Validating: should have a boolean output. Either they pass or fail.
  * Timely: should be written just before the production code that makes them pass. If you write tests after the production code, then you may find the production code to be hard to test.
 
## Chapter 10 - Classes
* Encapsulation: this one I feel really strongly about, and is vital to good software design. Only expose what must be exposed; default posture should be "it's private".
  * I disagree with "sometimes we should make it public for a test"; I feel if it's vital to the functioning of our system, it should be inherently (rather than explicitly) tested.
* (DISAGREEMENT) Size: "Classes should be small" - I disagree with this one, and much prefer the idea of depth from "A Philosophy of Software Design" - https://www.youtube.com/watch?v=bmSAYlu0NcY
  * If I'm going to take on the cognitive load of understanding a new name & it's purpose, I want to ensure it pulls it's weight.
  * Heavily fragmented classes can make a system VERY hard to understand; constantly wondering why this exists. 
* Should have one reason to change (SRP) - I largely agree with this, and the ethos behind it.
  * I am very interested in the CUPID idea, pushed by Dan North
* Cohesion: a pretty good lens to look through to decide when classes should be split/combined.
  * Classes should have a small number of instance variables. Methods should seek to change many of them, as the surface area offerings are more cohesive
* Isolation from change: things should be split/organized to prevent changes snaking all over the codebase
  * This would also improve readability, and I believe supports the concept of "deep" classes (which I also believe fights against the "small" classes)
  * Use abstracts, interfaces, etc as methods to improve isolation.
    * I strongly feel like abstracts are over used, and interfaces is a much better way to actually have isolation. (Composition over Inheritance)
   
## Chapter 11 - Systems
* metapohore: A computer solution as a city, along with specializations, overseers & sectors
  * easy for software to all ball together; with diligence we **can** keep the separation
* "construction should be kept separate from use"
  * separate startup/bootstrap from operation
* "we should implement only today's stories, then refactor and expand the system to implement new stories for tomorrow"
  * to do this, we **must** maintain proper separations of concerns (keep the specialiation alive within the city)
* enable growth by really focusing on modularity & clear boundaries

## Chapter 12 - Emergence
* Context: "Getting Clean via Emergent Design"
* (from Kent Beck) a design is "simple" if it follows these rules (in order)
  * Runs all the tests
  * Contains no duplication
  * Expresses the intent of the programmer
  * Minimizes the number of classes and methods
  * CS: I don't feel this captures it very well..
    * #1 has nothing to do with the design. I feel like tests are "table stakes" for implementation.
    * #2 can be taken way too far, and can make things really convoluted. There's a difference between coupled & coincidentally the same. We can make refactoring painful & complexity explode if the two of them are confused.
    * #3 feels wrong; it should be "the code minimimally implements the desired behaviour"; the programmer is NOT the stakeholder!
    * #4 I agree with, but could also be taken too far. Often I find it's not taken far enough though
      * I like the quote "High class and method counts are sometimes the result of pointless dogmatism" -- I find many of the Uncle Bob purists can get caught here, and may of the "best pratices" cause this.
* Expressiveness: the code should express the purpose using mechanisms inherent in the system, rather than relying on the dev fully understanding the entire codebase to make sense of it
  * Examples: choosing good names which suggest domain + pattern usage (where relevant).
* Personal thoughts; I much prefer the "A Philosophy of Software Design" or the CUPID patterns to the ones suggested here.
