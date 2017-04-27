The presentation: https://www.youtube.com/watch?v=IOiZatlZtGU
The paper: http://homepages.inf.ed.ac.uk/wadler/papers/propositions-as-types/propositions-as-types.pdf

Are you ready to learn about the hilarious subject of computability theory?

> An algorithm is a sequence of instructions followed by a computer.

Now you all think of computers as machines but for an awful long time what a computer meant was a person: the person who executed the algorithm.
Algorithms go back to Euclid's elements in classical Greece and to Al Khwarizmi in 9th century persia, but a formal mathematical definition doesn't appear until the 20th century when you have proposals by Alonzo Church, Kurt Gödel and Alan Turing all appearing within a year of each other.

> It's like buses: you wait two thousand years for a definition of effective computability and then three come along at once.

Why did this happen? So at the dawn of the 20th century one of the foremost proponents of formal logic was David Hilbert in Göttingen. And what he wanted to do was put all mathematicians out of business: What he wanted was an algorithm that given a statement in formal logic would determine if that statement was true or false.

This was called the _Entscheidungsproblem_ because it sounds a lot better in German (it just means _Decision Problem_).
And what Hilbert was depending upon was the idea that logic is _complete_, meaning:

> Every provable statement is true and every true statement is provable.

Sounds reasonable, right? Except of course in nineteen thirty in Vienna Kurt Gödel published his proof of the _Incompleteness Theorem_ and this meant that Hilbert was, to use a technical term, screwed.
So what Gödel showed was that any logic powerful enough to represent arithmetic could encode the following statement:

> This statement is not provable.

The way he did this is used a clever technique called Gödel-numbering to encode statements and proofs as numbers (which is why he depended on arithmetic).

So don't worry about the details about how he did that (although it is one of the world's first functional programs) but think about this statement _this statement is not provable_ … oye!
As soon as you have this statement written down you are in trouble. Why?
It's very much like what we heard with the _Liars Paradox_, only now it's provability.

So what happens? Well if it's false then it is provable and you've proved something that's false! This is really bad news - you don't want to do that.
So the alternative is that it's true. But now you must have a statement that is true but not provable.
So that's not as bad but it's still really annoying, especially if you're Hilbert.

Now as long as people thought that there would be a solution to the Entscheidungsproblem you didn't need a formal definition of algorithm - you just write down the algorithm that was the solution and it would be like Justice Potter's definition of pornography:

> I know it when I see it.

But if your goal is to show the Entscheidungsproblem is undecidable then you need a formal definition of algorithms so you can show that no algorithm is going to work.
So the race was on. The first solution was proposed by Alonzo Church in Princeton: he came up with this thing called _Lambda-Calculus_ in 1932 and by 1936 he'd used it to show that

> Yes. If an algorithm is _what you can express in out Lambda-Calculus_, then it is the case that the Entscheidungsproblem is undecidable.

Actually he did this by means of something else that was undecidable which we now call the _Halting Problem_.

There is the complete definition of lambda calculus. Much briefer than those of you that use languages like C or Java. It's only got three constructs:

- variables
- function definition and
- function application

And it's just the world coolest programming language because it was defined a decade before one had computers.

For many years me and my colleagues have worked with functional languages (which are based on lambda calculus) and for many years people in industry and managed to pretty much ignore everything we do.
Of course these days lambdas had become very trendy: you have lambdas in C++ you have lambdas in Python and you have lambdas in Java. So there's Duke, the icon for java, looking very smog. Congratulations to cure finally caught up with where Alonso Church was in the nineteen thirties.

Here we are back to Kurt Gödel again: he came visiting in Princeton and he thought that Churches solution was thorough - His precise words were 'thoroughly unsatisfactory'.
So Church went to Gödel and he said
> Look, you come up with your own definition and I'll show that mine as good as yours.

and Gödel did: he came up with it second definition of 'effectively computable' which he called _general recursive functions_ (and this was actually written up by Churches student Kleene with attribution) and Church duly went off and he showed the two definitions are equivalent. So he went back to Gödel expecting this would resolve the matter and Gödel set

> Oh, my definition is the same as your definition. Hmm … my definition must be wrong then.

The impasse was resolved by this man: Alan Turing at Cambridge who of course came up with what we now call _Turing Machines_ and again he showed for a Turing machine with your definition of algorithm that the Entscheidungsproblem was undecidable. And Turing proved his definition was equivalent to Churches and hence to Gödels.

What Turing did that was different was not the mathematics. It was the philosophy: he gave an argument that anything that a computer could do could be done by a Turing machine (where again 'computer' means a 'person following a sequence of instructions') and Gödel was finally convinced that all three equivalent definitions did capture effective computability.

Philosophers often argue:

> Is mathematics invented or is it discovered?

Three times guys. Three different independent definitions all turn out to be equivalent. That's powerful evidence that you have not invented something, you've _discovered_ something.
It's not just sports fans were impressed by a hat-trick.

Kurt Gödel was 28 when he undermined the work of David Hilbert. Alan Turing was 23 (still an undergraduate) when he undermined the work of Alonzo Church who was 33 and Kurt Gödel who was then an ancient 30.
So to all you young people in the audience: please keep explaining to your elders when we are wrong!

Ok so now you've got the background and we can start talking about the brilliant idea of _propositions as types_.

Here is Gerhard Gentzen. He was trying to carry out what was called _Hilbert's Program_ and he came up with a new way of writing down logic.
This is called _natural deduction_: Gentzen in his PhD thesis came up with natural deduction which is the main form of logic we use today.
He came up with _sequence calculus_ which is the second most used formalism in logic today.
And he also came up with using the upside down ∀ to mean for all. So there's a little goal for all you PhD students.

This is actually from Gentzens paper and we're just going to look at a fraction of this.
So the fractions having to do with implication and conjunction: implication is that funny backward `⊃` it really is a backward `C` - its _consequence backwards_ and ampersand `&` which means _and_.
And you can see it's exactly the same except that a Genzten wrote his letters in German.

So what do we have here?

> The rules come in pairs.

This is the important thing. On the Left we have rules with I meaning _introduction rules_ and you have the connective implication `⊃` or ampersand `&` below the line.
The rules on the right are called _elimination rules_ and there you have a connective above the line.

what does the one on the right say, the elimination rule? it says

> If you know A implies B and you know A (those are the two hypotheses above the line) and then below the line we have the conclusion - what do you know if you know A implies B and you know A? Hey, you know B!

So that's how you make use of an implication. How do you create or introduce an implication? Well it says

> (so those brackets around the A mean assume A. Don't prove A, just assume A is true.)
If you assume a is true and from assuming it is true you can get a proof of B then you know A implies B .

and the second one says

> well if you've got a proof of A and you've got a proof of B, you've proved A and B.

And what can you do with that? You can do two different things: the middle rule on the bottom says

> If you have proved A and B you may conclude A.

And the other rule says

> If you've proved A and B you may conclude B.

(Okay are there any questions? All right. I will zip on but do ask a question. If there's something that's confusing you, I'm sure, will be confusing other people as well.)

Here's a little proof: it's a proof that

> if you know B and A then you can conclude A and B.

Now this seems funny obvious, right? Of course if I know `B and A` I can conclude `A and B`. But it would be nice to actually have a formal proof. So here's the formal proof: it says

> okay let's assume B and A

and on the left we say

> if we can assume B and A we certainly know A.

and on the right we say

> well if we assume B and A we can certainly conclude B.

That's using the two different elimination rules. Now we've proved `A and B` so we know `A and B` and now we can _discharge our assumption_. So with no assumptions now we know that `B and A` implies `A and B`.

The key thing that Gentzen did that was amazing is he had the insight that _the rules come in pairs and that pair's cancel out_.
And he used this to prove what's called the _sub formula property_ which says that

> If you have a proof you can always normalize it by applying these rules so that the only formulas that appear in it (so the formulas are propositions here) are going to be
> - the conclusion
> - the hypotheses and
> - parts of those (what are called sub formulas)
no other formulas.

I'll give you an example of that in a minute but let's look at the simplification rules: the top one says

> Okay, I assumed A, I proved B, so I know A implies B. And I've also got a proof of A so I can conclude B.

But there's a simpler way of doing this, right? We don't need to assume `A`, we were just given a proof of `A` so everywhere in that proof on the left that you have an assumption that `A is true` just replace it by the proof you were given on the right that `A is true`. And now we've got another direct proof of B that doesn't use the formula `A implies B` so we've got rid of a formula that doesn't appear in the conclusion or the hypothesis.

Similarly if from `A and B` we conclude `A & B` and then from that you conclude `A` … well there's a much simpler way of doing that, right? You've got a proof of `A` just use that. So proofs can be simplified.

Let's do an example of that: here's a roundabout way of proving `A & B`. Let's say that somewhere I've got a proof of `B and A`. But we we've just proved right that `B & A implies A and B` so by modus ponens I can conclude `A and B`

So we've got a roundabout proof and notice this proof has formulas in it like `B and A implies A and B` that don't appear in the [conclusion].
We've got two undischarged hypothesis here: `B and A` on the right, and some discharged hypothesis the `B & A` (which has a little z on it) have discharged by the rule arrow implication which has the z, saying

> right, this is the rule that discharges those hypotheses

You've got two undischarged hypothesis `B & A` and a conclusion `A & B` and a bunch of other stuff including stuff like `B & A implies A & B` that doesn't appear as a hypothesis or a conclusion. Can we get rid of it? Well yes because our second to last rule is an introduction and our last rule is an elimination so we can just do what I said and take those two places where we assumed `B&A` and replace them by the proof of `B&A` on the right.

So it simplifies down to this. And once we've taken that proof on the right and moved it on the top then we've now got two places here where `&-I` is on top of `&-E` so we can simplify again and now we've got a direct proof. This is a much simpler proof of the same thing. Now notice that when you substitute something in to a proof it might actually have more nodes in it but it will always be simpler in the sense that you've gotten rid of the sub formula and you keep doing that until you have gotten rid of all the sub formulas. And that always works.

Why did Gentzen care about this? Because it says

> Okay, well just doing the proof could always be done in a direct way that there were no round about.

That's kind of cool. But in particular you can do the following: one of the formulas you have is `false` and a logic is consistent if you
cannot prove `false`. You really don't have any proofs of `false` sitting around. If you did have a proof of `false` then what the sub formula property tells you is

> The proof would look like `false` and only consisting of sub formulas of that.

Well there are no sub formulas of `false`, right? It's like

> What part of _no_ don't you understand?

So it's very easy to look at the proof rules and say

> Ah, ok. There's no proof rule that ends in `false` and therefore you couldn't get it in any other way.

So it gives a simple proof of consistency among other things.

Now at pretty much the exact same time that Gentzen was coming up with this new way of formulating logic this was when Church was coming up with lambda calculus.
Church originally used lambda calculus as a kind of macro language for a logic. And it turned out

> lambda calculus is really powerful!

In fact it's so powerful it let you write down the equivalent of infinite formulas and with those you had an inconsistent logic: one that could prove anything.
So that was kind of bad. But he did write in his original paper

> It may have uses other than its uses logic.

In particular turned out to be good for defining algorithms. But also he wanted a consistent system and to do that he used the same way of getting rid of paradoxes that Russell used: he used a _type theory_.
So in 1940 Church wrote down the simply typed lambda calculus. Here I've got terms of the lambda calculus in red and conclusions in blue and as well as functions I'm now dealing with pairs. You could also deal with things like record variance and pretty much every data type you name - you can build up out of these ideas. But I'm just going to show you functions and pairs.

So `λx.N` and where `x` is a term `λx.N` is a term, it's a function. It's a function that given a value of type `A` returns a value of type `B`. Is is a function from `A` to `B`. And what does this mean? we'll `x` must be a variable of type `A` and it must appear in some term `N` whose type is `B`. So `λx.N` would be a function from `A` to `B` and then if `L` is a function from `A` to `B` and `M` is an argument of type `A`: well of course if you apply `L` to `M` the result has type `B`. And a pair is built from two terms of types `A` and `B` and gives you an `A&B`-pair and of course first and second extract if you've gotten a `A&B`-pair first would be an `A` and second would be a `B`. This is a very simple definition of a small fragment of simply typed lambda calculus.

So here's an example of a program: `λz return the pair second of z, first of z` so what does this do? It swaps the elements of a pair and so it's type is going to be

take a `B&A`-pair and return an `A&B` pair

So at this point I'd like you to all reach under your seats you should find their some rose colored glasses. Please put on those rose-colored glasses you will then only see the blue bits and off the red bits and that should look kind of familiar: the blue bit of what Church did is exactly what Gentzen did.

You know it actually took a long time to see this. Because the proof I showed you that of Gentzens result - Gentzen didn't prove it that way. He had to invent sequent calculus to prove it. It's kind of ironic: Gentzen needed a round about proof to show the absence of roundabout proofs.

But [profits?] a little later came up with the form of proof that I showed you. And then Church came up with this and there are rules for _evaluating_ lambda expressions. They're very simple: the first one says

> if you've got `λx` and apply it to `M` what does that mean? Well, take the actual parameter `M` and substitute it everywhere for the formal parameter `x`.

And what does it mean given an (M,N)-pair to take the first component? Of course it just means return an M and again if you put on your rose-colored glasses you see that _evaluation corresponds exactly to simplification of proofs_.

The one thing you need to know is that this process _terminates_ that was actually first proofed by Turing of all people. So remember the hard thing about the halting problem is you can never solve it - it is undecidable. There's no algorithm to tell you if a given algorithm halts or not.

But if it's in simply typed lambda calculus - if you've typed it and you're not using what's called the fixed point operator (that is unlimited general recursion - yeah, that's the idea that Gödel came up with) - then you're _guaranteed that it terminates_.

So we have functional programming languages where we include the fixed point operator and you can write every general recursive programs do everything a Turing machine can do but we have other ones which are simply typed like this and examples of such languages are things like Agda or the proof system in Coq and those are guaranteed to always terminate. So the halting problem which you think of it as a very hard problem is actually completely solved by this idea of types.

Here's an example: here's the program that swaps two elements of a pair applied to a particular pair and of course we just substitute-in the argument `(y,x)` for the formal `z` and we get that and then we simplify again and we get that. So notice what these rules are telling us is that

> As we evaluate a program it stays well typed.

So what have we seen? Propositions in logic correspond to types in a programming language, proofs in the logic correspond to terms programs in the programming language and simplification of proof corresponds to evaluation of programs.

It's not a shallow idea, it's a deep idea with a lot of structures:
- propositions as types
- proofs as programs
- simplification of proof as evaluation of programs

This is sometimes called the curry Howard isomorphism. This is a drawing due to Luca Cardelli illustrating the correspondence between types on the top and formulas of logic on the bottom.

Hmm … you say _that's really cool!_ But hey you know it's just kind of an accident that happens once like that, right? Well no it's not an accident. The idea showed up many times in the 20th century. You can find it in the work of
Brouwer, Heyting and Kolmogorov, the intuitionists, but it was also noted by Haskell Curry and then the form that i'm showing you really was clarified by William Howard who then went on to say

> Well wait a minute! If implication and … correspond to these things, what do for all and there exists correspond to?

And that came up with a new kind of type that hadn't existed before called _dependent types_. And these are the bases today of many proof systems. So it's often called the _Curry-Howard-Isomorphism_, it's often called the _BHK-Interpretation_, it's sometimes called _propositions as types_. Anything that's really important will of course have lots of names.

So there's Howards original paper which was in fact published in a festive dedicated to Curry.

There's what I showed you:
- propositions as types
- proofs as programs and
- normalization or simplification of proofs as evaluation of programs

As I said

> well, fine but you know it's just for this one particular logic in fact I showed you only works for something called intuitionistic logic. It's just kind of an accident, right?

Well no. It works for everything!

So here just a couple of ways in which it works and the interesting thing to note here is for instance: the logician Hindley came up with type schemes and the computer scientist Robin Miler came up with the _type system Standard-ML which is the basis for the type systems used in all functional languages now_ like F# and Haskell. And notice that it's still called the Hindley-Miler-System, right?

But a logician and a computer scientist independently discovered the same thing. There's something called _polymorphic lambda calculus_ which is actually the basic for generics in Java and it was discovered once by the logician Girard who called it System-F and once by the computer scientist Reynolds who called polymorphic lambda calculus.

Curry-Howard is a double-barreled name that predicts there will be other double-barrelled names. Every good idea will be discovered twice: once by a logician and once by a computer scientist.

Pretty much every functional language you can name has as its core the lambda calculus. That's pretty much the definition of a functional language and interestingly _pretty much every proof assistant you can name such as Coq or Agda or what have you, has at it's core dependent types and using lambda terms to represent proofs_ in exactly the way that we were discussing.

That goes back to the Automath system of de Bruijn in the nineteen seventies. Some people actually don't call it Curry-Howard they call it Curry-Howard-de-Bruijn: it's a very powerful idea and of course just like any programming language there are bits in all of these things that are completely arbitrary. But their core is not arbitrary. Their core is something that was written down once by a logician and once by a computer scientist that is it was not invented but discovered.

Most of you use programming languages that are invented - and you can tell, can you? So this is my invitation to you to use programming languages that are discovered.

… Questions:

_Q: I claim that industry has ignored lambda calculus for many years. Why is this the case?_
A: Not just lambda calculus, they've ignored lots of things. If you look at good ideas like garbage collection - garbage collection came around in the late fifties, early sixties it finally became prevalent in the mainstream community with the advent of java and even then many people fought against it. So it's like 25-30 years maybe 35 years before garbage collection got into widespread use. I even though we think of it as a very rapidly moving field. Fundamental good ideas often take a very long time - 25 or 30 years - to be adopted.

Which I will rant now for a minute: in the UK we're supposed to do impact studies to show the impact of our research and impact must be an idea that was published 20 years ago and used within the last 20 years. So I want to use

> Oh, ok: Java makes use of generics which comes among other things from the work of Robin Miler on the Hindley-Miler type system and I helped contribute to generics in Java so that's clearly an impact story.

Well no because the original work by Robin Milner was too old to count: it was more than 20 years old.

If you look at what happens in the development of logic: rule comes along in the mid eighteen hundreds, Frege and Hilbert around 1900 all the stuff I showed you around nineteen thirty-five and it was nineteen thirty-five that Genzten and Church came up independently with natural deduction and simply typed lambda calculus - it wasn't until 1969 that Howard wrote this down it was just circulated as a Xerox note. It wasn't published until nineteen eighty. That's like 45 years. It takes a long time for good ideas to get out and so it's worth having a long perspective if you want to have the best and most interesting ideas - If you want things that are discovered and not invented.

_Q: In Currry-Howard we have a correspondence between logic and lambda calculus. Are there any others?_
A: Of course. But we saw a few others. So on the left here we have lots of different varieties of logic and on the right we have lots of different features of programming languages. By the way there's one thing that's emitted from here which is the most important one which is _distribution and concurrency_. And of course there are many, many different solutions to distribution and concurrency. What is the right one? Wouldn't it be great if there was some logic that corresponded to the distribution and concurrency that might give us a hint as to an idea that is discovered rather than invented? And indeed _linear logic_ on the left seems to correspond to things called _session types_ on the right and in fact that's a major focus of my current research.

So there's a possibility that we will be able to discover an approach to concurrency and distribution again that is discovered rather than invented but that's still ongoing work of course. Once we're done it will then take another 25 years before people adopt it.

_Q: Is there a third column or fourth?_
A: So many people say that category theory is the third column and that corresponds to both of these things. So yes, this actually goes deeper. There's some very nice paper by physicists talking about these correspondence because they get exploited in quantum physics. So yes, it extends through even to things like quantum physics.

_Q: What does this say about the impact of computer science on knowledge in general?_
A: Right, a lot of what we do day to day has arbitrary bits to it. This I've tried to explain to you is deep and not arbitrary: we are discovering things rather than inventing things. Clearly that has to have implications everywhere and there's a growing movement that says

> look, the ways of thought applied in computing - the things that you guys are all good at - give us new insights into how information is structured.

And structuring of information is not going to just be important for understanding how computers should be designed. It can also be important for understanding how the universe works. So this idea of using ideas of how information is structured to examine many many different field goes by the name of _Informatics_. Some people work in departments of computer science and I actually work in a department of a school of Informatics and I think Informatics is a much better word to use. By computer science the only two things wrong with it: the word _computer_ and the word _science_. Because it's not about just the computer, it's about patterns of information; and you don't put _science_ in your name if you're real science.