---
title: A nice LaTeX manuscript style
tags: ['latex','typewriter',]
original_date: 2015-08-02
revised_date:
---
Sometimes I just want a nice typewriter-like manuscript.
Save it as `preamble.tex`.

```latex
\chapterstyle{dash}
\usepackage{ulem}
\usepackage{xcolor}

% All font size must be normal size 
\renewcommand{\large}{\normalsize}
\renewcommand{\Large}{\normalsize}
\renewcommand{\huge}{\normalsize}
\renewcommand{\Huge}{\normalsize}
% more sizes as necessary

\renewcommand{\LARGE}{\normalsize} % changes the title size
\usepackage{titling}
\setlength{\droptitle}{-0.5in} % move the now small title up

% define red text
\newcommand{\red}[1]{\textcolor{red!50!black}{#1}}
\newcommand{\RED}[1]{\textcolor{red!50!black}{\MakeUppercase{#1}}}

% font hyphenation 
\usepackage{everysel}
\EverySelectfont{ %
\fontdimen2\font=0.6em % interword space
%
% for justified text
%\fontdimen3\font=0.2em % interword stretch
%\fontdimen4\font=0.1em % interword shrink
%\fontdimen7\font=0.9em % extra space
%
% for ragged text with hyphenation
\fontdimen3\font=0em % interword stretch
\fontdimen4\font=0em % interword shrink
\fontdimen7\font=0em % extra space
\hyphenchar\font=`\-% to allow hyphenation
}

\renewcommand{\baselinestretch}{1}

% skip line paragraphs
\setlength{\parindent}{0pt}
\nonzeroparskip

% header
\makepagestyle{plain}
\makerunningwidth{plain}{\headwidth}
\makeevenhead{plain}{}{\RED{CONFIDENTIAL}}{} 
\makeoddhead{plain}{}{\RED{CONFIDENTIAL}}{} 
\makeevenfoot{plain}{}{-\thepage-}{}
\makeoddfoot{plain}{}{-\thepage-}

% typewriters don't have thick dots
\def\labelitemi{-}

% math fonts to typewriter
\usepackage[defaultmathsizes]{mathastext}
\MTfamily{\ttdefault}\Mathastext

\frenchspacing

% smaller uniform margins
\setulmarginsandblock{2.5cm}{2.5cm}{*}
\setlrmarginsandblock{2.5cm}{2.5cm}{*}
\checkandfixthelayout
```

A sample document would look like this:

```latex
\documentclass[ms,letterpaper,12pt]{memoir}
\include{preamble} % the stuff above
\title{\RED{My Title}}
\author{My Name}
\date{\today}
\begin{document}
\maketitle
Some text.
\end{document}
```

Here are sample files: [preamble](/files/preamble.tex),
[manuscript](/files/manuscript.tex) and [output](/files/manuscript.pdf).

[This stackexchange answer](http://tex.stackexchange.com/a/95793)
was helpful.

