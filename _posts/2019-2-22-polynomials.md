---
layout: post
title: Polynomials
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

function tooSimpleToBeReal(x) {
  if (x == 2 ) {
      return 1;
  }
  }
  
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

5 - 1

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

Okay, what's "0 times something else"? 0 * 1 is the same as 0 * 5 which is the same as 0 * 1337. It's zero.

No kidding, dumbass!

Let's put these things together, then. 

(Remember, we want 0 if x is 5, and 1 if x is 2.)

function tooSimpleToBeReal(x) {
  (0 if x is 5) * (1 if x is 2)
}

I'm fudging the math on this for now. But if that first thing gets a 5, it'll give us a 0, and then we're going to multiply that 0 by whatever the second part is. And we already know it doesn't *matter* what the next part is -- if you multiply it by 0, you're getting 0 back.

So giving it a 5 will give us a 0. That's a third of what we need.



Get to the Point
It turns out what we've been describing is a set of points. Wait, what?

The general idea of a "point" in this context is: "I'll give you an X, and you give me the right Y."

If you're making a point (2, 1) and a point (5, 0), then you're basically saying "I need a function that will take a 2 and give me a 1, and will take a 5 and give me a 0." 

(We're adding the part where numbers other than 5 or 2 give you something that isn't a 1 or a 0, just because that's useful.)
