---
layout: post
title: Polynomials
published: true
---
My goal with this post is to get you to say "No kidding, dumbass!" as often as possible.

Ordinarily, this might not seem like a great goal. But while you're saying this to me, I'll be walking through the definition of polynomials from Jeremy Kun's book "A Programmer's Introduction To Mathematics," and by the end, you'll realize that without ever having heard a single non-obvious thing, you've heard an explanation of how to make and use polynomials.

Here's all we need to know about polynomials right now: 

They take a number from us, and give us back a number.

Okay, that's too simple. Let's beef it up:

They take a number from us, call it "x", and give us back a number.

That's a little better. Here's another step:

They take a number from us, call it "x", and use math on that "x" to give us back a number.

Still pretty simple. Let's get a tiny bit more specific about the "use math" part:

They take a number, call it x, and return a number that they make by adding things to x and multiplying x by other things and sometimes multiplying x by itself. 

Nothing there that's especially hard to follow, even for me.

"Multiplying x by itself" is usually called "putting a small number to the right of x called an 'exponent'". So x^2 is another way of saying "x times x", which as a programmer I like to show as "x * x" because my computer keyboard doesn't have a good multiplication symbol. x^2 has 2 for the exponent, and x^3 has 3 for the exponent.

No kidding, dumbass!

Anyway, polynomials take your x and add some number to it and then multiply it by things and sometimes use various exponents on it as well.

Start Simpler

For me, the easiest way to think about polynomials is not to think about them at all.

Well, except for the fact that you want to give them a number and get back either a 1 or something other than 1.

(Programmer's Note: Jeremy Kun drops this conceptual bombshell in chapter 2: if you think of a polynomial as something that takes only a 0 or a 1, and returns only a 0 or a 1, then you can use polynomials to do Boolean algebra: AND, OR, and NOT. Which means you can build logic gates. And if you can build logic gates, you build a computer just by plugging the gates into each other like legos.)

Obviously in real life polynomials can take all kinds of values and can return all kinds of values, but thinking this way lets us go even *simpler.* What if we had a polynomial, or a function, or, hell, any kind of *thing* at all, that would return 1 every time I gave it the number 2? And would *never* return 1 if I gave it anything else?

I'm a programmer, so I'll make this using a function:

`function tooSimpleToBeReal(x) {
  if (x == 2 ) {
      return 1;
  }
  }`
  
  OK, that works, but it's not using any kind of formula that gives us any flexibility. It's pretty useless.
  
  So let's do the same thing with math:

function tooSimpleToBeReal(x) {
  return x - 1; 
}

Does this work? Well, if x is 2, then x - 1 will be 2 - 1, and last time I checked, that's 1.

No kidding, dumbass!

OK, it works with our simplest test, but what if we give it a number other than 2?

tooSimpleToBeReal(5)

is going to give us

$$5 - 1$$

and that isn't 1, so we've succeeded.

Let's take it a step closer to the 0 and 1 idea. What if we want it to return a 1 when we give it a 2, and we want it to give us a 0 when we give it 5?

Sure, we could do it with

if (x == 2 ) {
      return 1;
  } else {
  return 0;
  }
  
  ...but the problem there is that it will return 0 for *everything* other than 5. This is fine, unless we kinda want to use this function as a test for both 2 and 5. 
  
Let's pretend we're playing 20 questions, so we want to get the most information we can out of every answer. "Is the number 2?" should give us 1, while "Is the number 5?" should give us a 0, and any other guess should give us a number that isn't 0 and isn't 1.
  
  tooSimpleToBeReal(2) = 1
  
  tooSimpleToBeReal(5) = 0
  
  tooSimpleToBeReal(__) = (something that isn't 1 or 0)

Let's go back to our math.

function tooSimpleToBeReal(x) {
  return x - 1; 
}

It turns out the key to returning a 0 or 1 is to use fractions.

What's 0/1? Hint: it's the same as 0/10, or 0/777, or 0/1337. It's always 0.

No kidding, dumbass!

Let's put these things together, then. 

(Remember, we want 0 if x is 5, and 1 if x is 2.)

function tooSimpleToBeReal(x) {
  return x - 5;
}

Will this be 0 if x is 5? Let's see:

x - 5 = 5 - 5 = 0

Halfway there! And if x is 2, will it be 0?

x - 5 = 2 - 5 = -3

Hmm. We were so close. We need a way to turn this number from -3 to 1. What about adding 4?

function tooSimpleToBeReal(x) {
  return x - 5 + 4;
}

But wait, that's the same as 

x - 1

...which is the same thing we did earlier for turning a 2 into a 1. It undoes all the work we did to return 0 if x is 5!

What we need is a way to leave our 0 answer alone (when x is 5) but to change our -3 answer into a 1.

What about multiplication and division?

OK, we have two requirements: don't mess with zero, and turn -3 into 1.

Remember: anything divided by itself is 1.

Remember: 0 / anything = 0

So if there's something we can *divide* our stuff by that will turn -3 to 1, it will be perfect, because it won't wreck our 0. 0/anything is still 0, after all.

So let's try this:

function tooSimpleToBeReal(x) {
  return (x - 5) / -3;
}

Why? Because our problem is that we're stuck with -3 when we want 1. If we take that -3 and divide it by -3, we'll have 1. -3/-3 is 1, after all. Problem solved!

If x is 5, we'll have (5 - 5)/ -3, which is 0/-3, which is 0.

If x is 2, we'll have (2 - 5)/ -3, which is -3/-3, which is 1!

But Wait -- There's More

That -3 we're using -- where does that come from? Well, we know that's the "problem number" we got instead of the nice clean 1 we were hoping for.

(x - 5)

..when x is 2.

So here's the funny thing. Sure, we can stick with 

(x - 5)/-3

...and that'll work. But if (x - 5) is another way of saying (2 - 5), couldn't we spell it out as (2 - 5) on the bottom as well?

(x - 5) / (2 - 5)

Well, just looking at that, you can *tell* it's going to be 1 when x is 2. It's the same on top and bottom.

(x - 5) / (2 - 5), when x is 2, is (2 - 5)/(2 - 5)

The huge benefit of doing things this way, instead of (x - 5)/-3, is that it'll work even when x isn't 2. I know, I know, I made it plain that we didn't care about any value of x other than 2 or 5, but this is a twofer: it's obviously gonna give us 1 when we want 1, and it's obviously gonna work whenever we have an x that isn't 5.

It also spells out -- and this isn't a coincidence -- the two x values we care about.

(2 - 5)

There they are -- both of them in the same place.


Get to the Point

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

So all we need to do is come up with an function that gives us 1s when we want 1s, and 0s when we want 0s, and then we can multiply it by whatever we need to in order to get the output we want.

Polynomials

Were you wondering when I'd get back to these? Me, too. 

Anyway, remember that a polynomial is numbers plus some amount of x values plus some kind of exponents (maybe) of x.

15 + 2x 

is a good example of a polynomial.

15 + 2x + 3x^2

is another good example, but we don't even need exponents yet.

One great thing about polynomials is that just by looking at them you can tell that if someone gave you an x, you could give them a number. It's an obvious mathematical formula to get one and only one answer. Airtight.

Another great thing about polynomials is that they're easy to add to each other.

15 + 2x

+

22 + 3x

is

37 + 5x

And they're also easy to multiply by numbers:

(15 + 2x) * 2  = 30 + 4x

...or even by other polynomials (if you remember your FOIL):

(15 + 2x) * (3 + 4x) = 45 + 60x + 6x + 8x^2, or (more simply) 45 + 66x + 8x^2

BTW, if you've encountered polynomials before, you might be yelling at me to stop writing them backwards.

I've been doing

15 + 2x + 3x^2

instead of 

3x^2 + 2x + 15

...and that might be annoying. All I can say is:

1. Jeremy Kun does it, and 
2. It makes code a lot easier

Why do I say it makes code easier? I'll have to digress a minute to explain.

One Minute Digression

15 + 2x + 3x^2

is a polynomial in which the coefficients are 

15, 2, and 3

and the powers of x are 

0, 1, and 2

You might be asking, what do you mean, the powers of x? 

Well, 15 is another way of saying 15 * 1. And 1 is another way of saying x^0, since anything^0 is 1.

No kidding, dumbass!

Here's why that's relevant, though

2x is another way of saying 2 * x^1.

And 3x^2 is another way of saying 3 * x^3.

Do you see the pattern?

We took our first number -- 15 -- and multiplied it by x^0.

We took our second number -- 2 -- and multiplied it by x^1.

We took our third number -- 3 -- and multiplied it by x^2.

Any doubt in your mind what we would do if there were a fourth number in our list?

In fact, it's so self-evident what to do, we could just leave x out of our polynomial altogether:

[15, 2, 3]

...and since programmers think the first item in any list is at Position Zero, this means...

...any programmer would say "The element at position 0 is 15, so we'll multiply it by x^0. The element at position 1 is 2, so we'll multiply it by x^1. The element at position 2 is 2, so we'll multiply it by x^1. And so on."

This is a really lean and elegant way to describe a complicated thing more simply.

End of One Minute Digression

So, getting back to the point: if we've got a polynomial that returns a 1 when we give it 2, and returns a 0 when we give it a 5, we could say it's this:

(2, 1)
(5, 0)

If we want to change the output when we get a 2, we can multiply our polynomial by something.

Multiply it by 15, and we'll get:

(2, 15)
(5, 0)

Welcome to the Upside Down

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

(x - 2)/(5 - 2)

There we go. This'll give us 

(2, 0)
(5, 1)

But now we have to multiply by 7 to get the right answer (which is (5, 7)). How do we do that?

Step 1: Turn our formula into a polynomial.
Step 2: Multiply our polynomial by 7, because that's easy to do.

So how do we turn (x - 2)/(5 - 2) into a polynomial?

Well, whenever we have a fraction that's

something - somethingelse
------------------
somethirdthing

...remember that we can split it into two fractions:

something                 somethingelse
---------           -     -----------
somethirdthing            somethirdthing


So in the case of (x - 2)/(5 - 2), we can turn that into

x                 2
--         -     ---
5 - 2            5 - 2

....or, if we want to go with the polynomial pattern we set up earlier (e.g., 15 + 2x + 3x^2), we could do

-2            x
---     +    ---
5 - 2        5 - 2

And yeah, that could be a whole lot simpler:

-2/3  + x/3

Why is it good to have a polynomial?

Two reasons:

1. We can multiply this by anything, to turn that 1 (the current output) into anything we want
2. We can combine it easily with any other polynomial

Now we've got two polynomials that are useful.

We've got one that can turn 5 into 0, and 2 into 1.

We've got another that can turn 2 into 0, and 5 into 1.

What's great about that? Let's say we want to create a polynomial that gives us these points:

(2, 7)
(5, 11)

We could take the first one (the 5 one) and multiply it by 11.

We could take the second one (the 2 one) and multiply it by 7).

What would we get if we took the first one (the 5 one, that we multiplied by 11) and gave it 5?

Well, 11, obviously. 1 * 11.

And if we gave it 2? We'd get 0 * 11, or... 0.

What would we get if we took the second one (the 2 one, that we multiplied by 7) and gave it 2?

We'd get 7. 1 * 7 = 7.

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

So let's spell each of our formulae out as polynomials.

Multiply the first one by 11.

Multiply the second one by 7.

And add them.

Here's our 5 function, that produces (5, 1) and 2, 0):

(x - 2)
-------
(5 - 2)

Let's make it a polynomial:

-2		  x
--    +  ---
3         3


Now let's multiply it by 11:

-22/3 + 11x/3

So now, when we give it a 2, we should still get 0. And when we give it a 5, we should get 11.

-22/3 + 11 * 2/3 = -22/3 + 22/3 = 0

-22/3 + 11 * 5/3 = -22/3 + 55/3 = 33/3 = 3

Succcess!

OK, let's look at our 2 function, that produces (2, 1) and (5, 0):

(x - 5)
-------
(2 - 5)

Let's turn it into a polynomial:

-5/3 + x/3

...and then let's multiply it by 7:

-35/3 + 7x/3

When we give it a 2, we should get 7:

-35/3 + 7*2/3 = -35/3 + 14/3 = 21/3 = 7

And when we give it a 5, we should get 0:


-35/3 + 7*5/3 = -35/3 + 35/3 = 0


So when we add them together, does it work? 

Do they affect each other? Does the 5-polynomial ruin the results of the 2-polynomial?

-35/3 + 7x/3 + -22/3 + 11x/3




But Wait a Minute

You may have noticed that these polynomials are great at dealing with the two numbers we care about --- 2 and 5 -- and not necessarily good at handling anything else.
