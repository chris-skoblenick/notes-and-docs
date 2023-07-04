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
  * Instead, I prefer **deep** functions; ones which are worth their weight
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
