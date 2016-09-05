Literate Programming Examples
=============================

A literate program combines code and prose (documentation) in one file
format. The term was coined by Donald Knuth in his September 1983
paper, *Literate Programming*,
[available online](http://literateprogramming.com/knuthweb.pdf). Decades
later,
[Knuth asserts that literate programming](http://www.informit.com/articles/article.aspx?p=1193856):

1. Was the most important outcome of creating TeX.
2. Enables faster and more reliable creation of software.
3. Manages complexity better than any other methodology he's aware of.
4. Is a source of joy when programming.
5. Enables extraordinary achievements in creating software.

Can these claims be made by non-Knuth programmers who adopt literate
programming (LP) for themselves? I believe the time is ripe to find
out, as we finally have a tool that is simple (plain text), flexible,
and powerful, with mature LP capabilities:
[Emacs Org mode](http://orgmode.org).

Thus this repository is a collection of literate programming (LP)
examples, using Emacs Org mode.  These examples are intended to be
directly usable (copy and start hacking), and/or to serve as
educational literate programs.  The long-term goal is to collect and
organize a corpus of useful LP examples that point towards Knuth's
vision of programs-as-literature.


Prerequisites
=============

1. Install a recent version of Emacs, 24.3+.
2. Install both `org-mode` (older version should be included w/ Emacs
   24+) and `clojure-mode`.  Use Emacs ELPA as needed (it can also
   upgrade Emacs packages); you can invoke that from Emacs with
   `M-x package-list-packages`
   - Consider using an Emacs "starter package" that provides a good
     baseline configuration, like
     [Emacs Prelude](http://batsov.com/prelude/) or
     [Emacs Live](http://overtone.github.io/emacs-live/).  Both those
     packages choose reasonable/good default configurations, and
     support Clojure (other languages too).
3. Update your `.emacs` file to support Org's LP features for Clojure
   (and possibly other languages). 
   - The exact location and name varies, depending on whether you
     chose one of the starter packages mentioned; e.g. with Emacs
     Prelude you'd have a file like
     `~/.emacs.d/personal/yourUsername.el`
   - You'll need to add the following somewhere within the `.emacs`;
     note that the `emacs-lisp` line below is optional, it's just
     meant to show that supporting additional languages is easy:

     ```elisp
     (org-babel-do-load-languages
       'org-babel-load-languages
       '((emacs-lisp . t)
         (clojure . t)))
     ;; Show syntax highlighting per language native mode in *.org
     (setq org-src-fontify-natively t)
     ;; For languages with significant whitespace like Python:
     (setq org-src-preserve-indentation t)
     ```


The benefits of LP using Emacs + Org
====================================

1. Documentation matters, a lot.
   - For starters, do you judge a Github project by its README?
   - For all but small throwaway systems, you're likely keeping a
     separate file of development notes already; LP would integrate
     that.
   - No matter how clear the function and data names are, code itself
     rarely clarifies larger issues of architecture and design, and
     the decision histories therein.
   - With literate programming, documentation is integral to
     development, never an afterthought.
2. With one LP file, you avoid the incidental/inessential complexity
   of the filesystem, by avoiding the frequent context-switching
   overhead in moving between files.  And you sidestep your language's
   imposed filesystem structure.
3. Org rocks for prose:
   - Org's plain-text markup is lightweight, yet more powerful than
     Markdown (which lacks hierarchical structuring), and cleaner than
     rST.
   - The structural editing provided by Org documents lets you
     organize your thoughts/writing/code very quickly.  With good
     structure even major revisions are easy.
   - Org's exporter lets your write-once, express-many-times: you
     can export an Org file to HTML (e.g. for blogging) or LaTeX (for
     serious publishing) and PDF.
   - It's easy to version-control Org files; it's just plain-text.
4. Org rocks for code:
   - Each code block has flexible granularity: can be named and
     referred to; evaluated or not; have data sent in or exported;
     specify different REPL sessions; specify different target/tangled
     files (in arbitrary subdirectories).
   - Code blocks are syntax-highlighted.
   - Code blocks are ready to edit: jump to major-mode editing easily;
     edit/REPL as usual; changes will flow back to the containing Org
     file.
   - A single Org file can mix multiple languages together.
5. Meta-development, manage complexity from a coherent perspective: a
   unified, single-file approach encourages holistic software
   development and exposition, in a natural order, using structure to
   enhance understanding.  LP is not just documentation and code
   together: it's a **process and abstraction unifying the development
   lifecycle**: requirements, architecture, design, code, tests,
   deployment, and maintenance - can all be bound coherently in one
   active format.


More information
================

- Emacs: no flamebait here; I will simply say that having Org is
  sufficient reason to use the Eternal Editor.  Just be sure to
  [remap your CapsLock to Control](http://www.emacswiki.org/emacs/MovingTheCtrlKey),
  for happy hands.
- [Org documentation](http://orgmode.org/org.html), especially the
  section on
  [Working with source code](http://orgmode.org/org.html#Working-With-Source-Code)
- The excellent paper by Schulte and Davison,
  [Active Documents with Org-Mode](http://www.cs.unm.edu/~eschulte/data/CISE-13-3-SciProg.pdf)

- Pro-tip: when you want to "tangle" or export code blocks from an org
  file, =CTRL-c-v-t= is the keystroke combo to tangle all blocks.  To
  tangle only ONE block, the current one your cursor is in, just use
  the Emacs prefix code first: =CTRL-u-c-v-t= For big org files, this
  saves time, as it's essentially instantaneous to tangle/export one
  block.
