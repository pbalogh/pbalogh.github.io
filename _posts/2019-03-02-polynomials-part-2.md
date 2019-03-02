---
published: true
---
## Get to the Point

It turns out what we've been describing is a set of points. Wait, what?

The general idea of a "point" in this context is: "I'll give you an X, and you give me the right Y."

If you're making a point (2, 1) and a point (5, 0), then you're basically saying "I need a function that will take a 2 and give me a 1, and will take a 5 and give me a 0." 

(We're eventually going to add the part where numbers other than 5 or 2 give you something that isn't a 1 or a 0, just because that's useful.)

And this is where life gets truly interesting. 

We've got a function that will give you a 1 when you give it a 2, and will give you a 0 when you give it a 5. Let's call it turnTwoIntoOne.

What if our points weren't (2, 1) and 5, 0)? What if they were (2, 10) and 5, 0)?

Well, we could take our turnTwoIntoOne and figure out some way to multiply it by 10. 

Then, instead of returning 1 for 2, it would return 10 for 2.

And instead of returning 0 for 5, it would return 10 * 0, which is... still 0.

So all we need to do is come up with some function that gives us 1s when we want 1s, and 0s when we want 0s, and then we can multiply it by whatever we need to in order to get the output we want.

## Polynomials

Were you wondering when I'd get back to these? Me, too. 

Anyway, remember that a polynomial is numbers plus some amount of x values plus some kind of exponents (maybe) of x.

$$15 + 2x$$ 

is a good example of a polynomial.

$$15 + 2x + 3\mathrm{x}^2$$

is another good example, but we don't even need exponents yet.

One great thing about polynomials is that just by looking at them you can tell that if someone gave you an x, you could give them a number. It's an obvious mathematical formula to get one and only one answer. Airtight.

Another great thing about polynomials is that they're easy to add to each other.

$$15 + 2x$$

+

$$22 + 3x$$

is

$$37 + 5x$$

And they're also easy to multiply by numbers:

$$(15 + 2x) * 2  = 30 + 4x$$

...or even by other polynomials (if you remember your FOIL):

$$(15 + 2x) * (3 + 4x) = 45 + 60x + 6x + 8\mathrm{x}^2$$, or (more simply) $$45 + 66x + 8\mathrm{x}^2$$

BTW, if you've encountered polynomials before, you might be yelling at me to stop writing them backwards.

I've been doing

$$15 + 2x + 3\mathrm{x}^2$$

instead of 

$$3\mathrm{x}^2 + 2x + 15$$

...and that might be annoying. All I can say is:

1. Jeremy Kun does it, and 
2. It makes code a lot easier

Why do I say it makes code easier? I'll have to digress a minute to explain.

## One Minute Digression

$$15 + 2x + 3\mathrm{x}^2$$

is a polynomial in which the coefficients are 

15, 2, and 3

(Coefficients? Yeah, those are the actual numbers you multiply things by. In something like "3x", the coefficient of x is 3.)

and the powers of x are 

0, 1, and 2

You might be asking, what do you mean, the powers of x? 

Well, 15 is another way of saying 15 * 1. And 1 is another way of saying $$\mathrm{x}^0$$, since $$\mathrm{anything}^0$$ is 1.

> No kidding, dumbass!

Here's why that's relevant, though

2x is another way of saying $$2 * \mathrm{x}^1$$.

And $$3\mathrm{x}^2$$ is another way of saying $$3 * \mathrm{x}^3$$.

Do you see the pattern?

We took our first number, 15, and multiplied it by $$\mathrm{x}^0$$.

We took our second number, 2, and multiplied it by $$\mathrm{x}^1$$.

We took our third number, 3, and multiplied it by $$\mathrm{x}^2$$.

Any doubt in your mind what we would do if there were a fourth number in our list?

In fact, it's so self-evident what to do, we could just leave x out of our polynomial altogether:

[15, 2, 3]

...and since programmers think the first item in any list is at Position Zero, this means...

...any programmer would say "The element at position 0 is 15, so we'll multiply it by $$\mathrm{x}^0$$. The element at position 1 is 2, so we'll multiply it by $$\mathrm{x}^1$$. The element at position 2 is 2, so we'll multiply it by $$\mathrm{x}^1$$. And so on."

This is a really lean and elegant way to describe a complicated thing more simply.

## End of One Minute Digression

So, getting back to the point: if we've got a polynomial that returns a 1 when we give it 2, and returns a 0 when we give it a 5, we could say it's this:

(2, 1)
(5, 0)

If we want to change the output when we get a 2, we can multiply our polynomial by something.

Multiply it by 15, and we'll get:

(2, 15)
(5, 0)

## Welcome to the Upside Down

Now imagine a totally different polynomial. This one is:

(2, 0)
(5, 7)

That is to say, if we give it a 2, we want it to give us a 0.

And if we give it a 5, we want it to give us a 7.

Well, what we just learned is that we can *start* by coming up with a simpler polynomial:

(2, 0)
(5, 1)

...and then multiplying it by 7.

Let's use the same tricks we came up with earlier to find this polynomial:

(x - 2)

Hmm, if we give it 5, we get 3, but we want 1, so we'll do

$$(x - 2)/(5 - 2)$$

There we go. This'll give us 

(2, 0)
(5, 1)

But now we have to multiply by 7 to get the right answer (which is (5, 7)). How do we do that?

Step 1: Turn our formula into a polynomial.
Step 2: Multiply our polynomial by 7, because that's easy to do.

So how do we turn $$\frac{(x - 2)}{(5 - 2)}$$ into a polynomial?

Well, whenever we have a fraction that's

$$\frac{something - somethingelse}{somethirdthing}$$

...remember that we can split it into two fractions:


$$\frac{something}{somethirdthing}$$ - $$\frac{somethingelse}{somethirdthing}$$


So in the case of $$\frac{(x - 2)}{(5 - 2)}$$, we can turn that into

$$\frac{x}{5 - 2}$$ - $$\frac{2}{5 - 2}$$

....or, if we want to go with the polynomial pattern we set up earlier (e.g., $$15 + 2x + 3\mathrm{x}^2$$), we could do

$$\frac{-2}{5 - 2} + \frac{x}{5 - 2}$$

And yeah, that could be a whole lot simpler:

$$\frac{-2}{3} + \frac{x}{3}$$

Why is it good to have a polynomial?

Two reasons:

1. It's easy to multiply a polynomial by something
2. It's easy to combine polynomials

Remember how I earlier said you could take a function that returns a 1 or a 0 and "multiply it by 15" to get it to return a 15 or a 0? It's easy to do this if your function happens to be a polynomial, because it's easy to multiply a polynomial by a number. It's like scaling a picture up or down, so if you see something being multiplied by, say, 3, you'll sometimes hear people call that 3 a "scalar," because 3 is the kind of number you can use to scale things. 

To multiply a polynomial by a number, you just multiply all its pieces by that number.

To do #2, you just add all of the pieces together. (More on that in a minute.)

Now we've got two polynomials that are useful.

We've got one that can turn 5 into 0, and 2 into 1.

We've got another that can turn 2 into 0, and 5 into 1.

What's great about that? Let's say we want to create a polynomial that gives us these points:

(5, 11)
(2, 7)

We could take the first one (the 5 one) and multiply it by 11.

We could take the second one (the 2 one) and multiply it by 7).

What would we get if we took the first one (the 5 one, that we multiplied by 11) and gave it 5?

Well, 11, obviously. 1 * 11.

And if we gave it 2? We'd get 0 * 11, or... 0.

What would we get if we took the second one (the 2 one, that we multiplied by 7) and gave it 2?

We'd get 7, because 1 * 7 = 7.

And if we gave it 5?

0 * 7 = 0

Here's the fun part: what happens if we add those two polynomials?

We get a combo polynomial.

Remember: **the goal of our combo polynomial is to give us (2, 7) and (5, 11).**

That is, if we give is 2, we get a 7. If we give it 5, we get 11.

If we give it 2, the first part we put in will give us 0 but the second part will give us 7, so we'd get

0 + 7 = 7

And if we give it 5, the first part will give us 11 but the second part will give us 0, so we'd get 

11 + 0 = 0

Which is exactly what we want!

So let's do these steps:

1. Spell each of our 0-or-1-returning functions out as polynomials.

2. Multiply the first one by 11.

3. Multiply the second one by 7.

4. And add them.

Here's our 5 function, that produces (5, 1) and 2, 0):

$$\frac{x - 2}{5 - 2}$$

Let's make it a polynomial:

$$\frac{-2}{3} + \frac{x}{3}$$


Now let's multiply it by 11:

$$\frac{-22}{3} + \frac{11x}{3}$$

So now, when we give it a 2, we should still get 0. And when we give it a 5, we should get 11.

Let's start by giving it a 2:

$$\frac{-22}{3} + \frac{11 * 2}{3} = \frac{-22}{3} + \frac{22}{3} = 0$$

OK, that worked. Now let's give it a 5:

$$\frac{-22}{3} + \frac{11 * 5}{3} = \frac{-22}{3} + \frac{55}{3} = \frac{33}{3} = 11$$

Succcess!

OK, let's look at our 2 function, that produces (2, 1) and (5, 0):

$$\frac{x - 5}{2 - 5}$$

Let's turn it into a polynomial:

$$\frac{-5}{-3} + \frac{x}{-3}$$

Cleaned up:

$$\frac{5}{3} - \frac{x}{3}$$

...and then let's multiply it by 7:

$$\frac{35}{3} - \frac{7x}{3}$$

When we give it a 2, we should get 7:

$$\frac{35}{3} - \frac{7 * 2}{3}  =  \frac{35}{3} - \frac{14}{3} = \frac{21}{3} = 7$$

And when we give it a 5, we should get 0:

$$\frac{35}{3} - \frac{7 * 5}{3}  =  \frac{35}{3} - \frac{35}{3} = \frac{0}{3} = 0$$


So when we add them together, does it work? 

Do they affect each other? Does the 5-polynomial ruin the results of the 2-polynomial?

$$\frac{35}{3} - \frac{7x}{3} - \frac{22}{3} + \frac{11x}{3}$$

Let's group the numbers with x at the end:

$$\frac{35}{3} - \frac{22}{3} - \frac{7x}{3} + \frac{11x}{3}$$

So we'll add the numbers without x:

$$\frac{13}{3} - \frac{7x}{3} + \frac{11x}{3}$$

And add the numbers with x:

$$\frac{13}{3} + \frac{4x}{3}$$

Let's test it. What happens if we give it a 2?

$$\frac{13}{3} + \frac{4 * 2}{3} = \frac{13}{3} + \frac{8}{3} = \frac{21}{3} = 7$$

And if we give it a 5?

$$\frac{13}{3} + \frac{4 * 5}{3} = \frac{13}{3} + \frac{20}{3} = \frac{33}{3} = 11$$

It works!

## But Wait a Minute

You may have noticed that these polynomials are great at dealing with the two numbers we care about --- 2 and 5 -- and not necessarily good at handling anything else.

Also, we waited until we had turned both of them into separate polynomials before we did stuff to them. Could we have done it sooner? 

Remember, we multiplied the 2-will-give-us-1 polynomial by 7.

We multiplied the 5-will-give-us-1 polynomial by 11.

Then we added them.

Could we have done that multiplication, and addition, before we made polynomials?

Here's the heart of the 2-will-give-us-1 formula:

$$\frac{x - 5}{2 - 5}$$

Let's multiply it by 7:

$$\frac{7 * (x - 5)}{2 - 5}$$

Simplified:

$$\frac{7x - 35}{-3}$$

Here's the heart of the 5-will-give-us-1 formula:

$$\frac{x - 2}{5 - 2}$$

Let's multiply it by 11:

$$\frac{11 * (x - 2)}{5 - 2}$$

(I tend to boil things down into really basic, crude ideas. In this case, I think of the 2-will-give-us-1 as something that "loves" the number 2 and "hates" the number 5. When I think this way, the formula boils down to: "x minus the thing we hate, divided by the thing we love minus the thing we hate." That way, when x is the thing we love, we get $$\frac{something}{itself}$$, or 1. And when x is the thing we hate, we get $$\frac{0}{something}$$, which is 0.)

Simplified:

$$\frac{11x - 22}{3}$$

## Put Them Together First

So now that we've done the multiplication, can we add them, and *then* turn them into a polynomial?

$$\frac{7x - 35}{-3} + \frac{11x - 22}{3}$$

Well, the denominators are different (-3 and 3) but we could multiply one of those fractions by $$\frac{-1)}{-1}$$ and solve that. 

(Remember that you can multiply any number by 1 without changing it, and that another way of saying "1" is any fraction that has $$\frac{something}{itself}$$.

So let's switch our fractions around:

$$\frac{11x - 22}{3} + \frac{7x - 35}{-3}$$

...and multiply the second one by -1/-1:

$$\frac{11x - 22}{3} + \frac{-7x + 35}{3}$$

Now we're just doing some addition and subtraction on the top half of our fraction:

$$\frac{11x - 22 -7x + 35}{3}$$

Simplified:

$$\frac{4x - 22 + 35}{3}$$

And more:

$$\frac{4x + 13}{3}$$

So we can turn this into a polynomial by splitting this one fraction into two fractions: a numbers-only fraction and a-fraction-that-has-x:

$$\frac{4x}{3} + \frac{13}{3}$$

Now switch the order because that's the way we like our polynomials:

$$\frac{13}{3} + \frac{4x}{3}$$

What happens when we give it 2?

$$\frac{13}{3} + \frac{4 * 2}{3} = \frac{13}{3} + \frac{8}{3} = \frac{21}{3} = 7$$

Good! And 5?

$$\frac{13}{3} + \frac{4 * 5}{3} = \frac{13}{3} + \frac{20}{3} = \frac{33}{3} = 11$$

Good! It worked.

## Mind the Pattern

In general, when we're making our fractions for the something-will-give-us-1 formula, you can see this taking shape:

$$\frac{x - some X value we hate}{the X value we love - that X value we hated up above}$$

Note that since we're using actual x values on the bottom, like 2 and 5, and we never subtract anything from itself, there's no way we'll wind up with a 0 on the bottom -- which would definitely be a risk if we left X in there as a variable. (x - 5 can very definitely be 0 if someone sneaks a 5 in for X.)

A fun thought that will pay off: remember that 0 * anything is 0. So if you want the top of your fraction to turn to 0 for more than one X, just make sure you have (X - that thing you hate) on the top of your fraction, being multiplied by the rest of the things up there.

For example, let's say you want to make sure you return a 0 for 13 as well as for 5. No problem! Just do

$$\frac{(x - 5)(x - 13)}{(5 - 2)(13 - 2)}$$

The interesting thing is, multiplying (x - 5) by (x - 13) isn't just simple arithmetic anymore -- you need to use FOIL to do it, and your answer is going to wind up with $$\mathrm{x}^2$$ in there. But we're okay with that! We're already working with polynomials. So far our polynomials have just been "degree one" polynomials" (meaning that they contain x but not $$\mathrm{x}^2$$ or $$\mathrm{x}^3$$). Now we're expanding a tiny bit.

Also, we've moved a little bit ahead of where we started. Remember that we used to have functions that returned 1s or 0s. 

Really, under the hood, they were just fractions that put an x - something up top in the numerator.

Now we're multiplying the numerator by some constant -- some number like 7 or 11 -- so that instead of returning 1s and 0s, it'll return some-number-we-like or 0.

This pattern is important for a few reasons. One is that it's so clean and simple conceptually, and the other is that it can easily be expanded to have more numbers we love or hate.

myFunction(x) = 7 * (fraction that will be 1 or 0) + 11 * (fraction that will be 1 or 0) + ....

You can keep adding "+ some Y we want for a particular number * (fraction that will be 1 or 0)", and as long as that fraction is 1 when it's supposed to be, and 0 for the other X's we care about, we'll get that Y back from our function. 

So if someone told us that (6, 8) should be a point in our graph, or is part of our data set (and that data set can be basically anything, because numbers can represent basically anything in the world now that everything is being digitized), we can add it easily.

myFunction = 7 * (firstFraction) + 11 * (otherFraction) + 8 * (newFraction)

newFraction should be 1 when X is 6, so that we'll get 8 * 1. And we just have to make sure that firstFraction and otherFraction are 0 when X is 6, because we don't want to pollute our nice 8 with any of that 7 and 11 stuff. 

Which is easy, because as long as the numerators of firstFraction and otherFraction are being multiplied by (X - 6) we can guarantee that those fractions will be 0 when X is 6. 

We just have to make sure the denominators also contain 2 - 6 (for firstFraction) and 5 - 6 (for otherFraction) so that they'll be the same on the top and bottom when X is 2 (for firstFraction) and 5 (for otherFraction).

## Chinese Remainders

There's a formula that we're getting really, really close to, and it's very similar to an old math puzzle that has one of the most simple-once-you-know-it-but-impossible-otherwise answers imaginable. It's really satisfying to learn -- sort of like the ancient Babylonian square-root-finding formula that Newton apparently loved.

The puzzle is something like this...

We're looking for a number. If you divide this number by 5, you'll get a remainder of 3.

If you divide it by 7, you'll get a remainder of 4.

So something like 8 would work well for the first part (8 / 5 is 1 with a remainder of 3) but lousy for the second part (because 8 / 7 is 1 with a remainder of 1).

How do we find a number that gives us the remainders we want?

## We Sorta Did This Already

Let's say you want a get-remainder-of-1 function. Like our earliest functions above, this one should have some number of things being added, but all of them should be 0 except for one of them which is 1.

So when we give it a 5, we'll get

(fraction that will be 1) + (fraction that will be 0)

And when we give it a 7, we'll get

(fraction that will be 0) + (fraction that will be 1)

And just like before, when we don't want just a 1, we multiply our formula by, well, whatever we actually want to get out of it.

For 5, we wanted a remainder of 3, so:

Formula for 5 = 3 * (remainderAfterDividingBy5 + remainderAfterDividingBy7)

...in which remainderAfterDividingBy5 is 1 and remainderAfterDividingBy7 is 0.

Just like above: take any number that has a remainderAfterDividingBy7 of 0 (say, 14). Multiply it by any integer and it'll still have a remainder of 0 after dividing by 7. Try it: 14 * 2 = 28. Why? Because the "remainder of 0" part means "it's made of sevens." 

## Bad Metaphor Alert

If the only Lego blocks you have are the ones with 6 nubbins, and you start lining them up, you can't made anything smaller than 6 nubbins, and you can't make anything *between* sizes of 6, 12, 18, etc. 

The number 14 has a remainder of 0 after you divide it by 7 because it's *made* of sevens. Multiply 14 by something else and you're just making a longer row of sevens, but you're not putting anything in there smaller than 7 (since as far as remainders are concerned, 14 is just a pair of sevens).

## Back to the Formula

So any number that has a remainder of 0 after dividing it by 7 is going to stay that way if you multiply it by 3. 

What's nice is that any number with a remainder of *1* after dividing it by 5 is going to have a remainder of *3* after you multiply it by 3. 

Try it: 6 has a remainder of 1 after dividing it by 5. 6 * 3 = 18. 18 divided by 5 has a remainder of 3.

So if we found a number with a remainder of 1 after dividing it by 5, and a remainder of 0 after dividing it by 7, we could multiply that number by 3 and we'd be all set.

## Finding Zero-Remainder Numbers

A number that has a remainder of 0 when you divide it by 7 is a number that's made of sevens. (Think of the Lego blocks.) 7 * 1, maybe, or 7 * 2, or, well, 7 * anything. They'll all work.

Call this number 7x.

What we need is a case where 7x has a remainder of 1 when divided by 5.

7 * 1 (or 7) has a remainder of 2 as far as 5 is concerned. 

7 * 2 (or 14) has a remainder of 4 as far as 5 is concerned. 

Wanna bet 7 * 3 has a remainder of 6 as far as 5 is concerned?

7 * 3 = 21, which after dividing by 5 has a remainder of... 1.

Well, it turns out it *does* have a remainder of 6, but 6 is actually bigger than 5, so your remainder has gotten bigger than the Lego blocks it's supposed to be the remainder of! And that's fine. Just add another 5-block. For 7 * 2 (or 14) we used 2 of our 5-blocks to get 10, with a remainder of 4. For 7 * 3, we thought we were going to be able to just add another 5-block (to get 15), but it turns out that the "21 has a remainder of 6 when dividing by 5" part means your remainder is too big, which means 15 isn't big enough, so you need to add another 5-block. Which gets you to 20, and then you can see the remainder is 1.

Remainder of 6 really means remainder of 1, when you're dividing by 5.

It's kinda like... we know the remainder will be 1 (after dividing by 5) if the remainder is 1, 6, 11, etc. Or... *any number that itself has a remainder of 1 after dividing by 5.*

## Build the Formula

So 7 * 3 has a remainder of 0 after dividing by 7...

> No kidding, dumbass!

...and a remainder of 1 after dividing by 5. Perfect! Multiply it by 3 and we're halfway there!

7 * 3 * 3 = 63

It checks out: remainder of 0 for 7, remainder of 3 for 5.

Our answer = 3 * (numberThatHasRemainder1for5and0For7) + 

...in which the first part, the "1", is "the remainder after you divide our number by 5" and the second part, the "0", 

For 7, we wanted a remainder of 3, so:

Formula for 7 = 3 * ((fraction that will be 0) + (fraction that will be 1))

## How to Make a Zero Remainder

For our 5 formula, we need something that gives a remainder of zero

## We Already Have the Answer

...or at least the tools that will find the answer.

Let's focus on the "when you divide by 5, you'll get a remainder of 2" part.

If someone came to you and said "I have a number that solves this! It's a 7 (or 12, or some other valid answer). But I'm being told I have to add something to it, and I don't want to break the remainder-of-2 part. What can I add that won't affect the remainder when I divide by 5?"

Well, you could always just add 5, right? That won't affect the remainder, will it?

7 + 5 = 12, which is still remainder 2. 

12 + 5 = 17, which is still remainder 2.

And now this starts to feel like common sense. If what you're adding is 5 * 1 or 5 * 2 or 5 * (any integer), you can't possibly be messing with the remainder.

> No kidding, dumbass!



Answer = something * 5 + 2

So what's that something?

Well, it can be anything (as long as it's an integer).

The fact that we're multiplying it by 5 means it can't possibly affect our answer in terms of 5.

## Flashback

The same way that up above, we were "deactivating" our fractions by multiplying our numerators by 0 (when X was something we hated). That way, we could multiply our "deactivated" fractions by anything at all, because that 0 was going to guarantee our being immune from any effects. 

function = (the Y we want from 2) * (a fraction that is zero for any X other than 2)

+

(the Y we want from 5) * (a fraction that is zero for any X other than 5)

+
...

See how that's similar to the Chinese Remainder puzzle? 

answer = (some multiple of 5) + (something that will give us the remainder we want for 5)

So that's very similar to what we're doing when we were setting up our functions to return 1 for the "good" x and 0 for every "bad" x. And it's even *more* similar when we multiply the stuff inside those functions so that instead of returning 1 they return something like 7 or 11.

The question is: what changes when you have exponents like $$\mathrm{x}^2$$ in your polynomial?

## Lines vs curves

1 point -- a lot of different lines can pass through it. A line is a polynomial of degree 1, which is a fancy way of saying there's an x in it but nothing above that -- no x^2, no x^3, etc.

In fact, you probably were taught the formula for a line: $$y = mx + b$$

...which is a polynomial, in which the coefficient for x is "m" and the coefficient for $$\mathrm{x}^0$$ is b. Remember, $$\mathrm{x}^0$$ is just another way of saying 1, and b is basically the non-x term -- the equivalent of "the number in the ones place."

2 points -- you get a line. 

3rd point -- you need a curve. Unless you're so lucky that the 3rd point happens to be on the line, but let's assume that's like winning the lottery.

Show JKun's picture of the two points and the curves passing through them. There's only one line that can pass through them, but there's an infinite number of curves. Curves happen when you have a polynomial that goes above somenumber + somecoefficient * x and get exponents bigger than 1 on your x terms.

Also -- it's all about adding curves, to an extent. 

Like Fourier synthesis!
