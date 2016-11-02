---
title:  "Recipes (Appendix)"
date:   2016-11-2
---

I was fooling around to see how other languages fare in terms of a recipe-like syntax.

[Elm](elm-lang.org) has a practically ready-made implementation.

```haskell
4
|> flip (^) 3
|> sqrt
```

[Haskell](https://www.haskell.org/) can get to Elm by setting `(|>) = flip ($)`.

```haskell
4
|> flip (**) 3
|> sqrt
```

[Mathematica](https://www.wolfram.com/mathematica/) require some tricks and piecing together, but all the parts are provided natively.

```haskell
(
  (4&)
  /*(#^3&)
  /*(Sqrt)
)[]
```

[Scheme](https://en.wikipedia.org/wiki/Scheme_(programming_language)) requires some [helper macros](https://gist.github.com/willy-vvu/a388e632130b0919edf29fa11f38ccdd), but afterwards it's syntax becomes quite slick!

```scheme
(_
  4
  (expt _ 3)
  (sqrt)
)
```

[JavaScript](https://en.wikipedia.org/wiki/JavaScript) also requires some [helper code](https://gist.github.com/willy-vvu/7ee6d94341df56fe6a8bf3be4194d2ea)*.

```javascript
_(4)
._(Math.pow).ThatWith(3)
._(Math.sqrt)
()
```

<sup>*It's actually just a reimplementation of the Python library in the [previous post](/hidden-bits/2016/10/28/recipes.html).</sup>

It gets interesting with JavaScript, as with Ruby, because another syntactical method kicks in: method chaining by calling object methods.

```javascript
["World", "Hello"]
.sort()
.map(word => word.toLowerCase())
.join(" ")
```

Ruby takes this kind of syntax to the next level by making most parenthesis optional.

```ruby
["World", "Hello"]
.sort
.map{ |word| word.downcase }
.join " "
```
