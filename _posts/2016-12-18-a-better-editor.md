---
title:  "A Better Editor"
date:   2016-12-18
author: willy-vvu
---

<img alt="Animated tree manipulation in the editor" src="/hidden-bits/assets/16-12-17-anim1.gif" width="275">

Over the past few days, I've been working on a prototype editor for [Scheme](http://www.paulgraham.com/avg.html). Except, this editor doesn't edit text - it edits the underlying tree structures of the code itself.

(I've been thinking about [creating](https://pcmonk.wordpress.com/2014/04/01/why-dont-we-have-a-general-purpose-tree-editor/) [such](http://www.lamdu.org/) [an](https://www.facebook.com/notes/kent-beck/prune-a-code-editor-that-is-not-a-text-editor/1012061842160013/) [editor](http://lighttable.com/) for a while, and I chose Scheme for it's relatively minimal syntax and code structure.)

Besides making it impossible to [forget parethesis](http://blog.interfacevision.com/design/design-visual-progarmming-languages-snapshots/) and [mis-indent your code](https://shaunlebron.github.io/parinfer/), this new breed of tree-based, or structure editors are loaded with unforeseen advantages.

Because when programmers actually edit their code, they're not just typing and deleting characters. They're trying to match up a rich, hierarchical, interconnected, underlying model in their head with an intermediate text form in front of them, which eventually gets translated back into something akin to the cognitive model. Unfortunately, the use of text is a vestige of typewriters and punchcards. Higher order structures suddenly become delicate, fragile, and brittle, when converted to and from text -- as any novice programmer will recount how many errors they've received from a compiler about a forgotten semicolon or bracket.

Instead of working with text as an immediate form, a structure editor operates directly on the tree form of code, mitigating if not completely bypassing the notion of "syntax errors". However this requires learning a new set of editing commands and operations, at the expense of leaving the comfortable textual model behind.

I'm currently experimenting with testing out different types of structural operations. I'd like to eventually conduct a study where I record programmers writing code, to find common code transformations from patterns of editing. But until I conduct the study, I'll be dogfooding a variety of atomic operations that I rapidly prototype, in hopes I'll find useful ones. Here are the ones that I've tested:

*Split* `(a b c d)` → `(a b) (c d)`
and
*Join* `(a b) (c d)` → `(a b c d)`

*Wrap* `a b c d` → `a (b c) d`
and
*Unwrap* `a (b c) d` → `a b c d`

*Push* `(a b c) d` → `(a b c d)`
and
*Pop* `(a b c d)` → `(a b c) d`

Take note that these specific operations are purely for rearranging the structure of the code while keeping order intact -- a highly constrained subset of all operations. I've come to realize that for LISP in particular, some of the above operations are more/less useful than others due to the constraints that LISP imposes; for example, because function names come first in each parenthesis grouping, Split and Join can unintentionally put names where they do not belong. And to that, I'll continue trying out new operations as I think them up.

Stay tuned for a [follow-up post](/hidden-bits/2016/12/26/a-better-editor-2.html).
