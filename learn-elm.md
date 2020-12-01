# Learning Elm

One of the weak points in my current knowledge of computers 
is how to develop graphical interfaces for the web. I have
of course some knowledge of Javascript and had used it for 
some personal projects, but since 5 years mostly worked with 
system programming languages, especially Rust. The world has
moved on since then and I'm looking for a new way of
programming, which may give me the same boost when I switched
from C++ to Rust. Because of this I want to learn Elm and
write a small learning journal about it.

## Foreword

As already mentioned I have experience with imperative styled
languages and some experience with the functional style of
Rust. Haskell or other pure functional languages never
appealed to me and, while understanding monads, I never
used them explicitly. It seems therefore a bit crazy to start
writing websites in a functional language, but after glancing
through some examples of Elm, the expressiveness captivated
me and I want to give it a try. 

My goal of this document is to write a stateful editor in Elm.
I will follow the model of Vim closely with command, visual
and edit mode. Another reason for this choice is that such
a project can be very simple and arbitrary complex, depending
on the extensibility.

## Resources

If you are interested in a historic starting point, then you
may read the thesis by the author of Elm [here](https://elm-lang.org/assets/papers/concurrent-frp.pdf).

Another great resource is the [awesome](https://github.com/sporto/awesome-elm) list
of Elm. I mostly skip the exercises and read the pattern parts
with special care.

## 01/12/2020 Playing around with functions

I just started to play around with the syntax of Elm. The
[elm-live](https://github.com/wking-io/elm-live) tool helps you with
automatic reloading and I resorted therefore to my usual working flow
with one window of Vim and one window with a browser open.

Pipelines are making a lot of fun in Elm. I just created a small
function, which takes a number `n`, then creates `n` squares
of a linear sequence, joining them with a semicolon and finally
converting that into a list objects:
```elm
squares : Int -> Html msg
squares num = 
    List.range 1 num
      |> List.map (\n -> n^2)
      |> List.map String.fromInt
      |> String.join ", "
      |> \x -> li[] [ text x ]
```
The most obvious new thing here is the pipeline operator `|>`
which applies a new function in each step. Further parameters
are marked with a backslash and you are using brackets only
to separate anonymouse functions and not for arguments.
I really like the homogenous syntax of lambdas and functions
and the statement is really readable and easy to grasp on
first glance.

What I don't like right now is the syntax for comments. I mean
`-` as comment identifier is okayish for me, but `{- -}` for
multi-line comments is looking really odd. But probably that
is just personal taste.

