---
published: true
layout: post
title: 'Polynomials, Part 2'
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

Anyway, remember that a polynomial is: numbers, plus some amount of x values, plus some kind of higher exponents (optional) of x.

$$15 + 2x$$ 

is a good example of a polynomial.

$$15 + 2x + 3\mathrm{x}^2$$

is another good example, but we don't even need exponents bigger than 1 yet.

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

### Simple Wasn't Simple Enough

Remember how I earlier gave a "simple" description of a polynomial as "numbers, plus some amount of x values, plus some kind of higher exponents (optional) of x"? Well, technically speaking, the "numbers" part is really "numbers * $$\mathrm{x}^0$$" and the "some amount of x values" is really "some number * $$\mathrm{x}^1$$". Which means a polynomial is really nothing but "number * x-raised-to-some-exponent plus number * x-raised-to-that-exponent-plus-one" and so on. Which is harder to say, maybe, but is obviously simpler -- since in a sense, you're just adding up a list of things, and everything in that list is just a number times x raised to an exponent that also happens to be that x term's position in the list!

So we never need to say what the exponent is when we write out polynomial out as a list, and the "x" part is completely taken for granted. All we need are the coefficients -- the numbers we multiply each x-term by.

[15, 2, 3]

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

Let's use the same tricks we came up with earlier to find this polynomial.

First we focus on the zero case -- the fact that we want it to give us 0 when we give it (in this case) a 2:

(x - 2)

We know that'll give us a zero when we give it 2.

But if we give it 5, we get 3, which isn't what we want. We want 1, so we'll do

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

This is the same formula, but it's expressed as a polynomial.

Why is this useful?

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

We could take the first one we made up above (the polynomial that takes a 5 and gives us a 1) and multiply it by 11.

We could take the second one (the polynomial that takes a 2 and gives us a 1) and multiply it by 7).

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

If we give it 2, the first polynomial in our combo will give us 0 but the second polynomial will give us 7, so we'd get

0 + 7 = 7

And if we give it 5, the first polynomial in our combo will give us 11 but the second part will give us 0, so we'd get 

11 + 0 = 0

Which is exactly what we want!

So let's do these steps:

1. Spell each of our 0-or-1-returning functions out as polynomials.

2. Multiply the first one by 11.

3. Multiply the second one by 7.

4. And add them.

Let's do this in [Part 3!](2019-03-03-polynomials-part-3.md)


