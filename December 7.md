# Design notebook for week ending December 7, 2014

## Description

This week's goals were and are adding final functionality to the base product, implementing 
basic error checking, and adding a test suite. Currently, the first two have been 
accomplished, and the rest of this week will be spent on cleaning up error checking, adding 
tests, and writing my final documentation. Features will be implemented as time permits, but 
since I plan on continuing working on this project, I am not worried about this.

First, for errors, I added my own error to catch throughout the code. I currently catch files 
that do not exist in the input; interestingly, if I make this a web app, the code is 
currently vulnerable to a path traversal attack, but this is not important for now since 
they're only accessing their own files. I also catch undefined variables and out-of-bounds 
piece/variable placement. I will need to catch if a piece/variable cannot be placed "below" 
something, as there is the possibility I will exhaust my search "below" a certain spot.

Next, I implemented the ability to place variables "below" and "above" a certain spot. Now, 
there are three functionalities for variables, and three for pieces. An available spot is 
defined as an empty cell or no intersections pieces.

First, for pieces:
* At: Search from the base up for the first available spot
* Above: Place above the highest spot underneath the entire piece
* Below: Search from the maximum height downwards for the first available spot

Then, for variables:
* At: Search from the base up for the first non-intersecting spot
* Above: Place above the highest spot, where the highest spot would touch the bottom of the 
dynamic grid (variable)
* Below: Find the highest spot, then move the search spot (1 + maxHeight(variable)) 
downwards, which will align the top of the dynamic grid with right below the highest spot in 
the matrix

For edge cases, Philip and I discussed at length how to handle issues of connectedness, one 
of my major edge cases. Since I now place the entire variable in the matrix at once, not 
placing everything line-by-line (which would have caused more issues), we run into this 
problem:
```
BreakingVar {
	1x1 Red Brick at 1,1
	1x1 Yellow Brick at 1,2
	1x1 Blue Brick at 1,3
	1x1 Green Brick at 1,4
}
2x2 Black Brick at 2,2
2x2 Black Brick at 2,2
2x2 Black Birck at 2,2
BreakingVar at 1,1
```
This would look something like a T, with a colorful top. However, we notice that the red and 
green bricks are floating. Therefore, Philip helped me to come up with a way of accounting 
for connectedness between bricks. For each index in the matrix, I will have an object 
tracking the color and connectedness of the brick. A cell connects in the x and y direction 
if the cells are one single piece. A cell connects in the z direction if it has a brick on 
top of or below it. With this, I can track what is connected and determine if I have any 
floating pieces.

As an aside, Prof. Ben and I discussed using Matrix traits to combine matrices of different 
types together. I plan to do this later on, along with making many functions traits that I 
can mix in.

I also discussed with my friend Alex about searching for connections that are floating. I can 
do a breadth first search, consuming all slots in the grid that are connected to the base. I 
can then do one more pass, and anything not consumed must be floating.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

The most pressing issue is getting tests up and running. I mentioned I will polish for the 
next two weeks, but probably not add features, unless they're small. I would also love to 
have some sort of basic visualization tool for the demo.

**What questions do you have for your critique partners? How can they best help
you?**

I don't really have questions at this point. Any useful testing tools I should be using?

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

I spent 2.5 hours in class this week working and discussing, and spent 2 hours outside of 
class implementing, and spent about an hour designing this week's notebook. I worked less 
this week since I had three other projects (Semantics, Cog Sci, and CS121) which 
unfortunately all consumed my time, and took away from working more on each project.

## Post-critique summary

Philip summarized our discussion on connectedness in the graph, as I discussed above. For 
style, he talked about using traits like he did, which would make my code more modular. I 
plan to do this in the code cleanup in the next two weeks. He also gave a stylistic way of 
working with nested for loops.

## Post-critique reflection

I changed my for loops! :) We learned that the style Philip mentioned is for list 
comprehensions that yield results. Otherwise, you should do
```
for (x <- 0..10; 
	 y <- 0..10) {
	code()	 
}
```
I also reviewed his code and plan to make my code less messy and more modular through traits.
