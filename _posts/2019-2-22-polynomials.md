---
layout: post
title: Polynomials
published: true
---
---
layout: post
title: Polynomials, Part 1
---
My goal with this post is to get you to say this as often as possible:

> No kidding, dumbass!

Ordinarily, this might not seem like a great goal. But while you're saying this to me, I'll be walking through the definition of polynomials from Jeremy Kun's book "A Programmer's Introduction To Mathematics," and by the end, you'll realize that without ever having heard a single non-obvious thing, you've heard an explanation of how to make and use polynomials.

Here's all we need to know about polynomials right now: 

- They take a number from us, and give us back a number.

Okay, that's too simple. Let's beef it up:

- They take a number from us, 
- call it "x", 
- and give us back a number.

That's a little better. Here's another step:

- They take a number from us, 
- call it "x", 
- and use math on that "x" to give us back a number.

Still pretty simple. Let's get a tiny bit more specific about the "use math" part:

- They take a number, 
- call it x, 
- and return a number that they make by 
- adding things to x 
- and sometimes multiplying x by other things 
- and sometimes multiplying x by itself. 

Nothing there that's especially hard to follow, even for me.

"Multiplying x by itself" is usually called "putting a small number to the right of x called an 'exponent'". So $$\mathrm{x}^2$$ is another way of saying "x times x", which programmers type out as "x * x" because computer keyboards don't have a good multiplication symbol. $$\mathrm{x}^2$$ has 2 for the exponent, and $$\mathrm{x}^3$$ has 3 for the exponent.

> No kidding, dumbass!

Anyway, polynomials take your x and add some number to it and then multiply it by things and sometimes use various exponents on it as well.

## Start Simpler

For me, the easiest way to think about polynomials is not to think about them at all.

Well, except for the fact that you want to give them a number and get back either a 1 or something other than 1.

(Programmer's Note: Jeremy Kun drops this conceptual bombshell in chapter 2: if you think of a polynomial as something that takes only a 0 or a 1, and returns only a 0 or a 1, then you can use polynomials to do Boolean algebra: AND, OR, and NOT. Which means you can build logic gates. And if you can build logic gates, you build a computer just by plugging the gates into each other like legos.)

Obviously in real life polynomials can take all kinds of values and can return all kinds of values, but thinking this way lets us go even *simpler.* What if we had a polynomial, or a function, or, hell, any kind of *thing* at all, that would return 1 every time I gave it the number 2? And would *never* return 1 if I gave it anything else?

I'm a programmer, so I'll make this using a function:

```
function tooSimpleToBeReal(x) {
  if (x == 2 ) {
      return 1;
  }
}
```
  
  OK, that works, but it's not using any kind of formula that gives us any flexibility. It's pretty useless.
  
  So let's do the same thing with math:

```
function tooSimpleToBeReal(x) {
  return x - 1; 
}
```

Does this work? Well, if x is 2, then x - 1 will be 2 - 1, and last time I checked, that's 1.

> No kidding, dumbass!

OK, it works with our simplest test, but what if we give it a number other than 2?

`tooSimpleToBeReal(5)`

is going to give us

$$5 - 1$$

and that isn't 1, so we've succeeded.

Let's take it a step closer to the 0 and 1 idea. What if we want it to return a 1 when we give it a 2, and we want it to give us a 0 when we give it 5?

Sure, we could do it with

```
if (x == 2 ) 
{
  return 1;
} 
  else 
{
  return 0;
}
```
  
  ...but the problem there is that it will return 0 for *everything* other than 5. This is fine, unless we kinda want to use this function as a test for both 2 and 5. 
  
Let's pretend we're playing 20 questions, so we want to get the most information we can out of every answer. "Is the number 2?" should give us 1, while "Is the number 5?" should give us a 0, and any other guess should give us a number that isn't 0 and isn't 1.
  
  `tooSimpleToBeReal(2) = 1`
  
  `tooSimpleToBeReal(5) = 0`
  
  `tooSimpleToBeReal(__) = (something that isn't 1 or 0)`

Let's go back to our math.

```
function tooSimpleToBeReal(x) {
  return x - 1; 
}
```

It turns out the key to returning a 0 or 1 is to use fractions.

What's 0/1? Hint: it's the same as 0/10, or 0/777, or 0/1337. It's always 0.

> No kidding, dumbass!

Let's put these things together, then. 

(Remember, we want 0 if x is 5, and 1 if x is 2.)

```
function tooSimpleToBeReal(x) {
  return x - 5;
}
```

Will this be 0 if x is 5? Let's see:

$$x - 5 = 5 - 5 = 0$$

Halfway there! And if x is 2, will it be 0?

$$x - 5 = 2 - 5 = -3$$

Hmm. We were so close. We need a way to turn this number from -3 to 1. What about adding 4?

```
function tooSimpleToBeReal(x) {
  return x - 5 + 4;
}
```

But wait, that's the same as 

$$x - 1$$

...which is the same thing we did earlier for turning a 2 into a 1. It undoes all the work we did to return 0 if x is 5!

What we need is a way to leave our 0 answer alone (when x is 5) but to change our -3 answer into a 1.

What about multiplication and division?

OK, we have two requirements: don't mess with zero, and turn -3 into 1.

Remember: anything divided by itself is 1.

Remember: $$\frac{0}{anything} = 0$$

So if there's something we can *divide* our stuff by that will turn -3 to 1, it will be perfect, because it won't wreck our 0. 0/anything is still 0, after all.

So let's try this:

```
function tooSimpleToBeReal(x) {
  return (x - 5) / -3;
}
```

Why? Because our problem is that we're stuck with -3 when we want 1. If we take that -3 and divide it by -3, we'll have 1. -3/-3 is 1, after all. Problem solved!

If x is 5, we'll have $$\frac{(5 - 5)}{-3}$$, which is $$\frac{(0)}{-3}$$, which is 0.

If x is 2, we'll have $$\frac{(2 - 5)}{-3}$$, which is $$\frac{-3}{-3}$$, which is 1!

## But Wait -- There's More

That -3 we're using -- where does that come from? Well, we know that's the "problem number" we got instead of the nice clean 1 we were hoping for.

$$(x - 5)$$

..when x is 2.

So here's the funny thing. Sure, we can stick with 

$$\frac{(x - 5)}{-3}$$

...and that'll work. But if $$(x - 5)$$ is another way of saying $$(2 - 5)$$, couldn't we just spell it out as $$(2 - 5)$$ on the bottom as well?

$$\frac{(x - 5)}{2 - 5}$$

Well, just looking at that, you can *tell* it's going to be 1 when x is 2. It's the same on top and bottom.

$$\frac{(x - 5)}{2 - 5}$$, when x is 2, is $$\frac{(2 - 5)}{2 - 5}$$

Obviously when we're doing the math, we'll show 2 - 5 as 3. But the huge benefit of doing things this way for *now* is that it spells out for us the two x values we care about.

$$(2 - 5)$$

There they are -- both of them in the same place.

[Part 2](https://pbalogh.github.io/Polynomials_part_2/)
