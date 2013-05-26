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
\end{document}
```

That's it! You do not need to declare the document class, e.g. `\documentclass{article}` because Dominatrix does that for you.

**Since you'll hopefully be using Dominatrix as a starter for all your documents, we recommend that you put Dominatrix in a directory with a globally accessible path, or in a location which is sufficiently high-up in the file-hierarchy for you to access it easily.**

## Features

Package-by-package details are due to come in for this very soon. Until then, read the comments in dominatrix.sty!

### Core Functionality

Dominatrix requires LaTeX2e to work. You should be already on this version if your install is reasonably fresh (e.g. if you didn't pull the computer out of a modern day archeological dig site).

Dominatrix uses the [KOMA-script](http://www.ctex.org/documents/packages/nonstd/koma-script.pdf) package as a replacement for LaTeX's default `article` class. This introduces a number of layout fixes and generally makes everything look better. KOMA-script also removes the need for you to forcibly break every line. In other words:

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

We use the [fixltx2e](http://texdoc.net/texmf-dist/doc/latex/base/fixltx2e.pdf) package as a polyfill for known bugs in LaTeX2e until the LaTeX Working Group releases LaTeX3.

### Fonts

*Font Size*
We fix the font-size at 11pt by default. At and below 10pt, printers or monitors without subpixel anti-aliasing may have difficulty reproducing text for legibility. At 12pt you get text that is a bit bigger in exchange for less paper efficiency, though this may be preferred by some institutions. Change it to fit your needs!

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
