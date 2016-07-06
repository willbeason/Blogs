I want to start practicing implementing existing design patterns from the Gang of Four's [*Design Patterns*](http://smile.amazon.com/dp/0201633612). Per Robert C. Martin's suggestion in [*Clean Coder*](http://smile.amazon.com/dp/0137081073), I should achieve mastery of these if I want to be a professional.

I've used design patterns in my work, but I wouldn't in any way say I've mastered them. I want to create a set of code kata, one for each design pattern from *Design Patterns*. Before I do so, I'd like to point out how design patterns and cybernetics are intertwined.

Read more...

# What Is A Design Pattern?

Design patterns are abstract, reusable patterns. They are problem independent. They are present in every field. They form everything from the tropes in fiction to the types of fallacious argument to the method of induction. I would argue none can claim to be the master in any field until they have mastered that field's design patterns. I would also argue that many design patterns have isomorphisms in other fields - they can be field-independent.

Christopher Alexander, the progenitor of design patterns, says "Each pattern describes a problem which occurs over and over in our environment, and then describes the core of the solution to that problem, in such a way that you can use this solution a million times over, without ever doing it the same way twice."

# Examples

## Chekhov's Gun

A narrative principle of keeping promises you make. ("If you say in the first chapter that there is a rifle hanging on the wall, in the second or third chapter is absolutely must go off. If it's not going to be fired, it shouldn't be hanging there." - Anton Chekhov)

Problem: There are too many distracting elements in this work. The background elements detract from the core of the story and destroy my attempts at foreshadowing.

Solution: Remove background elements which are unnecessary for the story.

## Appeal to Probability

A logical fallacy which claims that something is true because it is sufficiently likely. (The probability of the universe existing as it does is so unlikely it must have been designed with this form in mind.)

Problem: I can't prove my claim for 100% of all cases, but can do so for nearly all of them.

Solution: Assert that the claim is true for all cases.

## Interchangeability

Modularly creating machines so that individual pieces are interchangeable (the sight on an AK-47 can be removed and replaced with a different sight)

Problem: Different users of this machine will have different needs and priorities.

Solution: Design parts of the machine so they can be easily removed and replaced with a compatible part.

# Parallels in Coding

For good or ill, each one of these has parallels to design patterns in programming.

## Chekhov's Gun

Problem: There are too many variables in-scope. They distract from the meaning of this section of code.

Solution: Limit the scope of variables to where they are needed. Only declare variables which are used.

Example: Declaring an iterator in a loop's init expression instead of before the loop. This way the iterator only exists during the execution of the loop.

Each declared variable should justify its existence. If unused, it should be deleted. It should be declared as soon as possible before it is used, and pass out of scope once we are done with them. Further, the number of possible bugs in a section of code is proportional to the 2^(number of variables in scope). Each variable whose scope we limit vastly decreases the number of errors code may contain.

## Appeal to Probability

Problem: It is very unlikely that the program will encounter this state. Alternatively, I've covered all of the likely scenarios and can ignore edge cases.

Solution: Ignore that possibility.

Example: A QuickSort algorithm which takes the first element as the pivot. If the list is already sorted, the algorithm will take O(n^2) time. (Note that nothing in the code would suggest this behavior)

This pattern has been the source of many subtle bugs I've encountered. More often than not, this will be in the form of an implicit assumption as above. Bugs, even though they are not intentionally designed, are much easier to spot if we're aware of the patterns which create them.

## Interchangeability

Problem: I have similar objects with different implementation details.

Solution: Rely on interfaces, not implementation details. Decouple the logic of classes so they can be tested individually. Use inheritance or the Strategy pattern.

Example: A "Shape" abstract class with "Perimeter()" and "Area()" methods so that "Rectangle" and "Oval" concrete classes can be passed as arguments to the same functions.

Inheritance and interfaces are my favorite ways of decoupling two overly-intimate objects. In my work, I most often use this to make sections of code testable.

# Closing

Solving problems with a design pattern is a design pattern. I'll bet there's a word for that, but I can't think of it.
