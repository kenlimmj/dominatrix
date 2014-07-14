# Universal Fixes
Dominatrix implements three "universal" fixes for LaTeX. That is to say, these three packages patch known bugs and quirks at a lower level than most other mainstream packages will care to do. They require neither configuration nor interaction, and should "just work". It's likely that LaTeX3 will fix many (if not all) of the problems these packages tackle, but we've been waiting for LaTeX3 for a really. really. really. long time...

## fixltx2e
The grand-daddy of patches. This is like the Japanese Yakuza and Italian Mafia. It just works. You don't ask how, you don't ask why, you don't look at it, you don't touch it, you just leave it to do whatever it pleases. 

More realistically, it's a huge compilation of improvements to the way LaTeX renders content and how the compiler interprets the instructions we send it.

## fix-cm
This package fixes rendering issues that appear (in mostly odd cases) when a user is using the Computer Modern font-family. That means almost everyone, since LaTeX documents can be spotted from a mile away because of its distinctive font. If you're not using Computer Modern (like us), it doesn't get in your way. We're just putting it here in case someone has an epileptic fit if they don't get their daily dose of Computer Modern.

## exscale
LaTeX has a bug wherein it fudges up math operators at ridiculously large font sizes. "Ridiculously large", here, is defined as things like 300pt. Possible use cases? Posters, billboard banners, y'know, the typical things you would use LaTeX for. Either way this solves the problem, and if you're not waving large font sizes around, it won't get in your way.

# Fonts
So about that Computer Modern thing. Turns out that the wonderful TeX community created another PostScript font called Latin Modern. It has better glyphs, it has better hinting, and if you read the documentation it has all these really cool features that you need a PhD in hieroglyphics to appreciate. 

Long story short: We're using Latin Modern by default. It looks exactly the same as Computer Modern, just where Computer Modern (apparently) looks like crap, this one doesn't.

# Math
This is where things start getting a little more intense. We mainly target the way math operators and environments are handled, with a helping of secret sauce on the side.

## mathtools
This package is like that beefy Victorinox Swiss-Knife/Multi-Tool with 150 different uses. First, and most importantly, it loads ``amsmath``, without which we have no support for some symbols, a bunch of equation environments, and a bunch of math optimizations that work in the background to make our lives less miserable. 

Next, it implements starred environments for matrices. This means you can write:
```latex
\begin{vmatrix*}
1 & 2 & 3 \\
4 & 5 & 6
\end{vmatrix*}
```

## amssymb
Loads a ton of symbols. You're going to have to look through the documentation for this one, because it really loads a lot of them.

## esint
LaTeX gives you double and triple integrals, like so:
```latex
\iint\!x\,dx \qquad \iiint\!x\,dx
```
but if you're in the market for double and triple surface integrals, you're out of luck. You can get around it by defining a custom command which draws a circle around the integral, but you really don't want to go there. This package puts you back in business:
```latex
TODO
```

## mathdots
The default spacings for the vertical and diagonal ellipsis tend to be a bit odd, because LaTeX doesn't calculate spacings as well when things aren't in a straight line. This package helps it along, so you get vertical and diagonal ellipsis symbols that match the horizontal ones more closely. This comes in very useful when you're drawing sparse matrices.

## turnstile
Logicians and Computer Scientists use and abuse the sequent symbol, otherwise colloquially known as a turnstile. Again, without this package (god I sound like a desperate salesman), you'd have to draw a vertical line, find the midpoint, and draw a horizontal line. Not at all impossible, but very nasty. With this package, just write:
```latex
TODO
```

## braket
This package has its roots in Quantum Physics, where one frequently writes Bra-ket notation. If you happen to be doing a lot of that, it's here for you:
```latex
TODO
```
However, even if you don't, there's another really nifty use for this package. When trying to typeset an equation with values to be substituted for variables, we'd grapple with something like this:
```latex
\frac{x^2}{x+3} \Big\vert_{x=3}
```
Sometimes ``\Big`` is not big enough, and then you have that pesky vertical bar to deal with. Enter ``braket``:
```latex
\Set{\frac{x^2}{x+3}}_{x=3}
```
Me likey.

## relsize
The day will come (if it hasn't already), when you write an equation with parentheses inside parentheses, inside square brackets, inside curly brackets. Everything looks wonderful, except for this one slight infraction where all the brackets tend to look like they're the same size. ``relsize`` defines a new macro which can be called with ``\mathlarger``.