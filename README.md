# Dominatrix

A drop-in package for the LaTeX typesetting system that implements best-practices and fixes recommended by the community-at-large.

## Introduction

## Quick Start

Make sure you have LaTeX installed on your system and that you can compile `.tex` files to `.pdf` or `.dvi`, whichever is your poison. If you haven't done that, we recommend:

+ [MiKTeX](http://miktex.org/) for Windows
+ [MacTeX](http://tug.org/mactex/) for OS X

Thanks to contributions from a great community, both work out-of-the-box or with very little configuration on your part. We also assume that you have a functional knowledge of how LaTeX works, in which case if you don't, we recommend:

+ [LaTeX WikiBook](http://en.wikibooks.org/wiki/LaTeX)
+ [LaTeX Community](http://www.latex-community.org/forum/)

To use Dominatrix, just require the package in your preamble:

```latex
\RequirePackage{dominatrix}
\begin{document}
Your content here
\end{document}
```

That's it! You do not need to declare the document class, e.g. `\documentclass{article}` because Dominatrix does that for you.

Since you'll hopefully be using Dominatrix as a starter for all your documents, we recommend that you put Dominatrix in a directory with a globally accessible path, or in a location which is sufficiently high-up in the file-hierarchy for you to access it easily.

## Features

Package-by-package details are due to come in for this very soon. Until then, read the comments in dominatrix.sty!

### Core Functionality

Dominatrix requires LaTeX2e to work. You should be already on this version if your install is reasonably fresh (e.g. if you didn't pull the computer out of a modern day archeological dig site).

Dominatrix uses the [KOMA-script](http://www.ctex.org/documents/packages/nonstd/koma-script.pdf) package as a replacement for LaTeX's default `article` class. This introduces a number of layout fixes and generally makes everything look better.

### Parskip
We've also used KOMA-script to remove the need for you to forcibly break every line. In other words:

```latex
Lorem Ipsum Dolor Sit Amet \\

Consectetur adipiscing elit.
```

can now be written as:

```latex
Lorem Ipsum Dolor Sit Amet

Consectetur adipiscing elit.
```

to produce the same output.

#### fixltx2e and fixcm
We use the [fixltx2e and fxicm](http://texdoc.net/texmf-dist/doc/latex/base/fixltx2e.pdf) package as a polyfill for known bugs in LaTeX2e until the LaTeX Working Group releases LaTeX3. fixltx2e fixes bugs in the LaTeX kernel, while fix-cm improves the definition of the Computer Modern font families. If you'd like to know exactly what fixes they make, check out the documentation!

### Fonts and Typography

#### Font Family

Dominatrix has been configured to work with both LaTeX and XeTeX/XeLaTeX. If you'd like to roll your own truetype/opentype fonts, you'll have to use XeTeX/XeLaTeX because the old coot LaTeX doesn't support system fonts that aren't a part of its own library. The downside of using XeTeX/XeLaTeX with your own fonts is that compile time goes up by quite a bit - we're looking into an easier solution that works with native LaTeX. Suffer until then :)

If a XeTeX compiler is used, we use the [fontspec]() package to load in any fonts that we need. For example:

```latex
\usepackage{fontspec}
\setsansfont[BoldFont={* Bold}]{Miso}
```

tells the compiler to use `Miso` for the sans-serif font, and specifies that if a bold weight is to be used, `Miso Bold` is available for that purpose. The names `Miso` and `Miso Bold` are the exact names of the font that appear in your system. To check this:

+ Windows: Go to your font directory in `C:\Windows\Fonts`
+ OS X: Open Font Book and use the name of the font as it is listed

If you'd like to define an italics font or the likes thereof, you can do so in a similar fashion. Check the fontspec package documentation for more wonders of the modern world.

So that settles the XeTeX madness. If you're using LaTeX, life is a lot more straightforward. We use the [fontenc](http://www.ctan.org/pkg/fontenc) package with an option flag of `T1` to enable support for accented characters and Type 1 fonts. In simple English, this means a larger font subset and a lower chance that you'll see a weird looking 'corrupted' character, especially if you need cyrillic support.

We also use [lmodern](http://www.tug.dk/FontCatalogue/lmodern/) to call the Latin Modern font as a replacement for Computer Modern. Don't mean no disrespect, but Computer Modern was built at a time when screens weren't so pretty (or retina-ify) and there's occasions now where it doesn't work well. Latin Modern fixes those problems and provides enhanced metrics.

#### Switching Fonts

You thought we were done didn't you? Here's the thing. If you're using either a system opentype/truetype font from start to end (via XeTeX), or Latin Modern (or some LaTeX-friendly font) from start to end, you're already good to go. But if you'd like to have your header be in a system opentype/truetype font and keep your body text in Latin Modern, welcome to a whole new world of hurt.

Since we're using the KOMA-script package, we can specify different fonts for different parts of the document:

```latex
\setkomafont{title}{\fontencoding{EU1}\sffamily\bfseries}
\setkomafont{section}{\fontencoding{EU1}\sffamily\huge\centering}
\setkomafont{subsection}{\fontencoding{EU1}\sffamily\Large}
\setkomafont{subsubsection}{\fontencoding{EU1}\sffamily\large}
```

This tells XeTeX to use the EU1 font encoding and the sans-serif font family (which basically means, to use your custom font) for the title, section, subsection and subsubsection commands in your document. We've added our own recommended styles after that, like sizing, bold weights and centering accordingly. Feel free to change this, or to use the same format to further customize aspects of your document as required.

Setting your custom fonts in this way means that the rest of the document still falls back to T1 font encoding, which is your LaTeX defined font-family like Latin Modern. Savvy?

#### Font Size

We fix the font-size at 11pt by default via the document class. At and below 10pt, printers or monitors without subpixel anti-aliasing may have difficulty reproducing text for legibility. At 12pt you get text that is a bit bigger in exchange for less paper efficiency, though this may be preferred by some institutions. Change it to fit your needs!

#### Microtype

The [microtype](http://raffles.nus.edu.sg/mirror/tex-archive/macros/latex/contrib/microtype/microtype.pdf) package is used to tweak the appearance and tracking for fonts that appear at small sizes (e.g. captions or footnotes). Unless you'd like to specifically adjust a kerning pair, you don't need to call any commands for this to do its magic.

#### TextComp

[TextComp](http://home.online.no/~pjacklam/latex/textcomp.pdf) Provides support for the text companion font set, which provides additional symbols, like the copyright symbol, accents and arrow support. Check out the documentation for a full list of usable symbols.

#### SIunitX

Allows you to typeset SI units inline in equations. For example, if you wanted to write '3.8x10^3 kg', instead of using:

```latex
$3.8\times10^3\textrm{kg}\,\textrm{m}\,\textrm{s}^{-1}$
```

you can now use:

```latex
$3.8\times10^3\si{kg.m.s^{-1}}$
```

Check the [documentation](ftp://ftp.tex.ac.uk/tex-archive/macros/latex/exptl/siunitx/siunitx.pdf) for a full list of supported SI units (which is kind of everything, since this is SI after all!)

#### Ellipsis

LaTeX best practices recommend that you use the `\ldots` command to type `...`, partly to denote the semantic difference between an ellipsis and three consecutive periods, and to fix spacing issues. The [ellipsis](ftp://ftp.dante.de/tex-archive/macros/latex/contrib/ellipsis/ellipsis.pdf) package fixes up even more stuff. Unless you're trying to do something fancy (which is really unlikely, for this case), you shouldn't need to call any commands for this to work.

#### URL

If you typeset a really long URL in LaTeX, like so:

```latex
\url{http://www.a-really-really-really-really-really-really-really-really-long-url.com/long-url}
```

and it appears near the end of the line, LaTeX will not automatically break the URL over to the next line for you. You'll end up with a long URL string running off the edge of the page. The [url](http://raffles.nus.edu.sg/mirror/tex-archive/macros/latex/contrib/url/url.pdf) package corrects that behaviour so URLs break nicely and fit within the bounds of your document. You don't need to call any commands for this to work.

#### HyperRef

[hyperref](http://raffles.nus.edu.sg/mirror/tex-archive/macros/latex/contrib/hyperref/README.pdf) works if you're using PDF output. It runs through the document looking for any links inside \url{} wrappers and converts them to clickable hyperlinks in the PDF document. We call a number of option flags on the package to further customize it.

+ `ocgcolorlinks` to tell the package to make the link visible by changing its color. If this option is not set, hyperref will keep the link color unchanged (from the rest of the document body) and add a surrounding box around the link to demarcate it.
+ `hypertexnames=false` for compatibility with subfigures
+ `plainpages=false` to ensure that page number links are unique (i.e. that they work correctly)

#### Euler

Since we expect to call and use different fonts in our document (i.e. fonts that are not LaTeX's default Computer Modern), we need to tell LaTeX to type equations in the same font. [Euler](ftp://ctan.tug.org/tex-archive/fonts/eulervm/doc/latex/eulervm/eulervm.pdf) does exactly just that, and you shouldn't need to call any additional commands for it to work unless you're using something exceptionally esoteric.

#### nth

nth saves you a lot of markup by automatically superscripting text numerary counters. In other words, instead of typing:

```latex
$1^\textrm{st}$
$2^\textrm{nd}$
$3^\textrm{rd}$
$4^\textrm{th}$
```

You can now type:
```latex
$1^\st$
$2^\nd$
$3^\rd$
$4^\th$
```
for the same output. Sassy eh?

## Core Dependencies

+ [LaTeX](http://www.latex-project.org/)
+ [CTAN](http://www.ctan.org/)
+ [Miso Font](http://www.fontsquirrel.com/fonts/Miso)

## Versioning

Development will be maintained under the Semantic Versioning guidelines as much as possible in order to ensure transparency and backwards compatibility.

Releases will be numbered with the following format:

`<major>.<minor>.<patch>`

And constructed with the following guidelines:

+ Breaking backward compatibility bumps the major (and resets the minor and patch)
+ New additions without breaking backward compatibility bump the minor (and resets the patch)
+ Bug fixes and miscellaneous changes bump the patch

For more information on SemVer, visit http://semver.org/.

## Changelog

**v1.0.0**

+ Implements common fixes for LaTeX2e and community recommended packages.

## Roadmap

+ Convert Miso from a fontspec dependency to a native LaTeX font
+ Add documentation and links for/to the individual packages in Dominatrix
+ Build up logic and decision-making within the package
+ Explore precompiling static components in the package

## Bug Tracking and Feature Requests

Have a bug or a feature request? [Please open a new issue](https://github.com/openlectures/dominatrix/issues).

Before opening any issue, please search for existing issues and read the [Issue Guidelines](https://github.com/necolas/issue-guidelines), written by [Nicolas Gallagher](https://github.com/necolas/).

A bird will poo-poo on you if you, without good reason, open an issue that has already been resolved.

## Contributing

Please submit all pull requests against *-wip branches.
If your pull request contains JavaScript patches or features, you must include relevant unit tests.
All markup should conform to their respective community style guidelines:
+ [LaTeX](http://web.science.mq.edu.au/~rdale/resources/writingnotes/latexstyle.html)

## Contact

A Human: hello@openlectures.org

A Bird: [@openlecturessg](http://twitter.com/openlecturessg)

A Privacy-violating Sonuvabitch: http://facebook.com/openlectures

## Authors

This repository is maintained and developed by the **Automation and Advancement Division (AAD)**, openlectures.

**Kenneth Lim**
+ http://twitter.com/kenlimmj
+ http://github.com/kenlimmj

**Linan Qiu**
+ http://twitter.com/linanqiu
+ http://github.com/linanqiu

## Copyright and License

Licensed under the MIT License (MIT).

Copyright © 2013 openlectures LLP (http://openlectures.org/).

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
