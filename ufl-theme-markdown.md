---
title: Beamer themes for the University of Florida
author: Jason Cory Brunson
date: \today
aspectratio: 169
institute: |
  Laboratory for Systems Medicine, University of Florida
section-titles: false
header-includes: |
  \usepackage[utf8]{inputenc}
  \usepackage[T1]{fontenc}
theme: ufl
---

## Markdown + Pandoc

The `ufl` **Beamer theme** will be described in more detail in `ufl-theme-example.pdf`, generated from `ufl-theme-example.tex` using all four themes. (Currently, only the color and font themes are drafted.) This slideshow is generated instead from the **Markdown** file `ufl-theme-markdown.md` using the document conversion program [**Pandoc**](https://pandoc.org/).

Note that Markdown syntax is not standardized, so much so that i decided not to link to any specific introduction or guide in the previous paragraph. Features may differ between the **Pandoc Beamer** converter and other engines, so beware that the syntax used here will not necessarily work in, say, GitHub.

# Pandoc Beamer

## Markdown to \LaTeX\ in Pandoc

Render this document directly into a PDF using Pandoc from the command line:

    pandoc ufl-theme-markdown.md \
      -t beamer \
      --include-in-header=environment-shortcuts.tex \
      --toc \
      -o ufl-theme-markdown.pdf

Change the output format to \TeX\ by substituting the final option:

      -o ufl-theme-markdown.tex \
      -s

(This will produce an intermediary standalone **\LaTeX\ source file**.)

## Metadata

The **[YAML](https://yaml.org/) front matter** at the top of `ufl-theme-markdown.md` contains several metadata, including the title, author, institution, and date. This document also sets the following variables:

```yaml
aspectratio: 169
section-titles: false
theme: ufl
```

The `theme` variable calls the `ufl` Beamer theme. The `themeoptions` variable receives options that are passed to the theme.

Find a list of Beamer-specific variables that can be set in the front matter at the Pandoc User's Guide:

    https://pandoc.org/MANUAL.html#variables-for-beamer-slides

## Environment shortcuts

The Pandoc command above included one atypical option:

      --include-in-header=environment-shortcuts.tex

This adds the contents of `environment-shortcuts.tex` to the \LaTeX\ preamble when rendering. The file contains several definitions like this:

```tex
\newcommand{\blockbegin}[1]{\begin{block}{#1}}
\newcommand{\blockend}{\end{block}}
```

These allow to use \LaTeX\ environments without the use of `\begin{}` and `\end{}`, thereby enabling Pandoc to render Markdown syntax within these environments.

# Formatting text

## Blocks

\blockbegin{Text Block}

This text block is rendered using \verb|\blockbegin{Block Title}| and \verb|\blockend|.
Since Pandoc interprets single carriage returns as spaces, two are required to separate these commands from the text they contain.

Block titles are rendered in \primarytype{Cantarell extra bold}, a free alternative to the Gothic bold used for campus, college, and school woodmarks.

\blockend

\theorembegin

Likewise, a theorem can include **bold**, \emph{emphatic}, and `fixed-width` font rendered from Markdown syntax.
Note that \verb|\emph{}| is required for emphatic text when _italics_ are ignored in a theorem block, and notice the difference between `fixed-width` and \verb|inline verbatim code|, which can still be rendered using \verb|\verb|.

\theoremend

## Lists

Enumerated, itemized, and nested lists can be intuitively typed:

```markdown
1. This is a first item.
2. This is a second, but it has
    - not one,
    - not two, but
    - three sub-items.
```

The code above renders as follows:

1. This is a first item.
2. This is a second, but it has
    - not one,
    - not two, but
    - three sub-items.

## Code blocks

The code blocks on the preceding slides use either 4-space indentation (for command line code) or triple–back ticks with syntax highlighting specific to the language on display (`yaml`, `tex`, and `markdown`).

These and many other shorthands are documented in the [Pandoc User's Guide](https://pandoc.org/MANUAL.html).

# Thanks

## Acknowledgments

Since i didn't recognize them in previous documents, i'll thank here the designers of \TeX\ and \LaTeX, as well as those of Markdown and Pandoc, for making this exceedingly easy, while necessarily limited, plain text–to–PDF workflow possible.

As in the other example documents, suggestions are very welcome! Email Cory ([jason.brunson@medicine.ufl.edu](mailto:jason.brunson@medicine.ufl.edu)), raise an issue, or submit a pull request (on a new branch).

<!--
pandoc ufl-theme-markdown.md \
  -t beamer \
  --include-in-header=environment-shortcuts.tex \
  --toc \
  -o ufl-theme-markdown.pdf

  -o ufl-theme-markdown.tex \
  -s
-->
