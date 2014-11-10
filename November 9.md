# Design notebook for week ending November 9, 2014

## Description

This week was spent designing the IR and syntax, researching tools, and beginning work on the parser. The first big decision I made was to simplify the grammar in two ways. 
* First, I am removing the idea of environments and scoping for now. I don't see a reason to include this, as most non-programmers will not care about having variables inside other variable environments. This simplifies the grammar, as a variable is only a list of instructions, and not a list of variables and a list of instructions.
* Second, I have decided to use curly braces for variable instructions, instead of using tabs. I did a lot of research on the ["Off-side rule"](http://en.wikipedia.org/wiki/Off-side_rule), and found that I would probably have to write my own lexer/parser to handle INDENT/DEDENT. Curlies are much easier to handle in Scala's parser-combinator libraries, so for now, I will use braces instead of tabs.

Future ideas:
* Pass a mapping of currentColor -> newColor for a variable to change variable colors dynamically. This will help with not having to redefine variables of the same instruction set but using different colors.
* Write own lexer/parser for tabs

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

**What questions do you have for your critique partners? How can they best help
you?**

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

## Post-critique summary
Ellen liked the project, noting that since Lego Digitial Designer is no longer supported, this tool may fill a niche if designed well. She mentioned I should focus on the IR and think about what data structure I should store the results in. She also talked about having variable height blocks and non-integer dimensions. She ended by saying I shouldn't focus on the GUI and stick to extending modeling functionality.

## Post-critique reflection
I definitely have realized that I need to focus solely on the IR for now. I plan to store the IR in a 3D array, which should make the product easy to visualize as separate layers.
I didn't think much about having non-standard blocks. Initially, I plan to get this working for blocks of a single layer of height and of standard sizes. However, Ellen brings up a good point; there's lots of different odd Lego pieces out there, and I should focus on implementing those before moving onto the GUI. I also realize some bricks are taller or smaller than a single layer, so I will need to figure out how to represent that in the data structure. 

