# Design notebook for week ending November 16, 2014

## Description

This week, I built the parser and added AST wrappers for all non-terminals in my grammar. I also wrote the design and implementation document. 

I spoke with my roommate about my current syntax additionally, and he suggested I modify the current input to simplify the coordinate system. When building Legos, one never thinks about placing a Pawn at 6,2, a specific place in a grid. It'd be much easier to refer to a grid's left, or middle, or right, or a specified position, B1. Therefore, I would like to add some default relative positions and allow for the designer to add coordinate positions within the grid. Additionally, I'd like some way to add a piece or variable relative to another piece or variable relative to the grid, but that will be a feature I plan to add later.

While writing the design document, I realized a lot of details and edge cases I hadn't considered. For one, I have no way to place pieces beneath other pieces with my current system, since I always build upwards. This isn't a major concern, since I could build a variable that started with the lowest pieces, and built upwards, but it would be a nice feature to add. 

Additionally, a bigger issue is that I had planned to dynamically run the instructions of a variable each time one was referenced. However, I realized this will produce wrong results. Imagine the following:
```
Var {
  1x1 Red Brick at 1,1
  1x1 Red Brick at 6,1
  6x1 Red Brick at 1,1
}
2x2 Red Brick at 3,1
2x2 Red Brick at 3,1
2x2 Red Brick at 3,1
```
Output:
```
XXXXXX
X xx X
  xx  
  xx
```
However, this is not the output that would be produced. Since I run each instruction one-by-one, I would first place the 1x1 bricks at the lowest level, since nothing is blocking their placement, then place the 6x1 brick above all. Therefore, the solution is to build a variable in its own dynamic grid then place it at the first level that does not intersect with any parts in the variable.

The final issue was dealing with placing a non-1x1 brick in the grid. For example, I now choose to place a 2x2 brick across four spots in the 3D matrix. This is lossy, since we lose that the bricks are connected, but I could build a dictionary mapping these positions to a specific brick. However, more importantly, now when I go to add another 2x2 brick that only is on top of half the first brick, I cannot naively place four 1x1 bricks in the grid, since it naively places the bricks in each place that it fits. Therefore, I'll need find the maximum height of the current pieces that would be underneath the whole new piece, and then put some empty place holders beneath this in the grid. 

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

Right now, it's balancing these details with getting a basic prototype out. I can ignore a lot of these details for now though, and focus on the core product.

**What questions do you have for your critique partners? How can they best help
you?**

Everything I wrote above might sound confusing. Does this generally make sense? Is there another way to deal with handling empty space in the Z-direction in a grid? 

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

I spent 2 hours in class over Monday and Wednesday discussing the project and designing the parser. I worked for 5 hours on Thursday writing up the design document and discussing the details I ran into. I spent an hour Friday continuing to flesh out the implementation to these details.

## Post-critique summary

Andrew commented on the syntax changes along with comments about using this tool as a non-programmer. He mentioned that I should try to get a perspective from a non-programmer to see if everything makes sense.

## Post-critique reflection

One of the most important design choices for me is structuring the input in such a way that is easy to learn and simple to non-programmers. I feel I've been able to do this. The most "programming" they will need to understand is a grid system and what variables are. I will find a way to write out good documentation that makes easy to understand analogies regarding this.
