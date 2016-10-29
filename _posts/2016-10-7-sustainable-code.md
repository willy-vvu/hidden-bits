---
title:  "Sustainable Code"
date:   2016-10-07 21:11
---

This semester, I'm taking an introductory AI course. I already had Python
experience, so I challenged myself to reduce the amount of time I spent on
homework while still producing quality, workable solutions.

Thus, I began with a "code-golf" mindset, trying to reduce the amount of code
I needed to write. To keep things on one line, I resorted to a functional
programming style. I dove right in with Assignment 0:

```python
def compute_string_properties(string):
    """Given a string of lowercase letters, returns a tuple containing the
    following three elements:
        0. The length of the string
        1. A list of all the characters in the string (including duplicates, if
           any), sorted in REVERSE alphabetical order
        2. The number of distinct characters in the string (hint: use a set)
    """
    return (len(string), list(reversed(sorted(list(string)))), len(set(string)))
```

Not bad! But unlike real code-golf, I avoided obfuscating or minifying my
code: in addition to making code less readable, it'd probably be a headache to
debug. But a one thing began to stick out to me:

In an effort to follow the relatively descriptive docstring comment, the order
of operations had to be reversed. "A `list` of characters, `sorted`, and in
`reverse` alphabetical order" became `reverse(sorted(list(...)))`. This
functional style, although standard practice in Mathematics, I could foresee
being harder to read and follow than the prose equivalent, especially as
problems grew larger, more involved, and stopped fitting on one line. Here's
an excerpt from Assignment 1:

```python
def backchain_to_goal_tree(rules, hypothesis):
    # The output should be simplified as in the previous problem (you can
    # use the simplify function). This way, you can create the goal trees
    # using an unnecessary number of OR nodes, and they will be
    # conglomerated together nicely in the end.
    return simplify(

      # Given a hypothesis, you want to see what rules can produce it, by
      # matching the consequents of those rules against your hypothesis. All
      # the consequents that match are possible options, so you'll collect
      # their results together in an OR node. If there are no matches, this
      # hypothesis is a leaf, so output it as a leaf of the goal tree.
      OR(sum(map(

        (lambda rule: (lambda matched: [
              # If a consequent matches, keep track of the variables that are
              # bound.

              # The antecedent may have AND or OR expressions. This means that
              # the goal tree for the antecedent is already partially formed.

              # The branches of the goal tree should be in order: the goal trees
              # for earlier rules should appear before (to the left of) the goal
              # trees for later rules.
              # Intermediate nodes should appear before their expansions.

              # If two different rules tell you to check the same hypothesis,
              # the goal tree for that hypothesis should be included both times,
              # even though it seems a bit redundant.
              deepmap(lambda leaf:

                # Look up the antecedent of that rule, and instantiate those
                # same variables in the antecedent (that is, replace the variables
                # with their values). This instantiated antecedent is a new
                # hypothesis.
                backchain_to_goal_tree(rules, populate(leaf, matched))
              )(rule.antecedent())

            ] if matched != None else []

          )(match(rule.consequent()[0], hypothesis))
        ),rules),

      # If there are no matches, this hypothesis is a leaf, so output it as a
      # leaf of the goal tree.
      # (Add hypothesis to the OR tree as a default case where no rules match.)
      [hypothesis])
    ))
```

Unfortunately, the functional syntax didn't help my coding process. As with
`simplify(`, last-called functions would be syntactically stuck at the
beginning, fragmenting and reordering the comments. Also, for `),rules),` and
`[hypothesis])`, operands ended up drifting far apart from their operators,
which led to the shuffling of parenthesis, dangling commas, strange
indentation, and ultimately, less readable code.

As I embraced adding whitespace and empty lines, I found that lifting and
interspersing comments straight from the problem descriptions helped my own
thought processes. This is similar to "Literate Programming", where code and
comments support each other, and are written tightly in tandem.

And then I realized: In order to spend less time coding, I would need to write
not just to run, but also to read, understand, and debug. To reduce the amount
of wasted time and rewritten code, I would need to be mindful, reconsidering
many decisions as to how and what I write. Instead of producing single-use,
"disposable code", I would need to code sustainably.

I pay particular attention to the importance of writing to debug. To many
novice programmers, the arcane symbols and structures of code can be
alienating. Like any language, programming is learned, mistakes expected.
Ultimately, the heart of debugging is the question, "what went wrong?". The
answer to this seemingly innocuous question can cost hours of time. Not to
mention frustration, stress, and confusion.

Effective debugging requires a thorough understanding of multiple
perspectives/representations and how they differ: intended behavior, source
code, and runtime results. Sometimes, even a slight, easily overlooked
difference between intention and source can cause huge or misleading behaviors
in runtime. Especally for a novice programmer or by using someone else's code,
the presence or absence of explanation by means of documentation or comments
can make the world of difference.

But I believe that much of this lost time can be reclaimed. Source code can be
written in a way conducive to understanding, for intent as well as structure.
This does not stop at comments and documentation; consistent formatting,
sugared syntaxes, and literate programming can all can impact readability,
depending on how they are used. There is one important distinction to note:
much of what contributes to code readability comes from the optional features
- even stylistic choices - not required language features. As such, I feel
there is much to explore in this space, even for existing programming
languages.

And thus I began the quest for sustainable code.
