# Design notebook for week ending November 2, 2014

## Description

When first deciding on a project, I knew I wanted to work with Legos in some way. However, I wasn't sure what I wanted to do with them. The project had a few different possible directions. The first was a tool for constructing Legos. Input to the program would be instructions on how to build a creation, and output would be a visualized model. The second was using Legos as the output of the program, inspired by [Beat Bricks](https://github.com/superquadratic/beat-bricks), where Legos were used to specify a melody. I was thinking about having input to the DSL being game instructions which were then passed to a program that interpreted the instructions. A Lego matrix, on a MxN board, could be read via OpenCV, letting the game be played on a Lego board and having the DSL use the instructions of the game to generate moves as an AI.

I chose the first option, as I wanted a tool to assist in building custom Lego constructions. The project will take as input a list of instructions that will be translated to an IR containing Bricks with Size and Color, along with variable constructions for ease of design. The output will be either a 3D matrix, possibly serialized to JSON, to be interpreted by another program to generate layer-by-layer visualizations. Alternatively, the IR could be used to generate step-by-step instructions, much like a standard Lego model.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

What needs to be in the IR in order to fully represent my language? If I want to translate the IR to serialized JSON, what choices must be made to simplify this? Also, how should I represent variables, which is just a subset of instructions? What errors may arise when using variables?

To answer the second to last, I suspect I will use dynamic scoping to evaluate instructions in the environment that they're called from. However, maybe I should have static scoping, or possibly I won't need to worry about scope and each instruction will be relatively separate from one another.

**What questions do you have for your critique partners? How can they best help
you?**

Are there any features you would like to see implemented that would simplify creating Lego constructions? How can I simplify the language to minimize verbosity? What possible errors could occur with using variables besides having ones that aren't defined?

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

I had about 1.5 hours of discussions to develop my ideas for this project. I have worked for 2 hours on description documentation for the project, and 1.5 hours for planning.

## Post-critique summary
Ellen liked the project, noting that since Lego Digitial Designer is no longer supported, this tool may fill a niche if designed well. She mentioned I should focus on the IR and think about what data structure I should store the results in. She also talked about having variable height blocks and non-integer dimensions. She ended by saying I shouldn't focus on the GUI and stick to extending modeling functionality.

## Post-critique reflection
I definitely have realized that I need to focus solely on the IR for now. I plan to store the IR in a 3D array, which should make the product easy to visualize as separate layers.
I didn't think much about having non-standard blocks. Initially, I plan to get this working for blocks of a single layer of height and of standard sizes. However, Ellen brings up a good point; there's lots of different odd Lego pieces out there, and I should focus on implementing those before moving onto the GUI. I also realize some bricks are taller or smaller than a single layer, so I will need to figure out how to represent that in the data structure. 
