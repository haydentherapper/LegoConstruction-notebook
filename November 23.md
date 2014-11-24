# Design notebook for week ending November 23, 2014

## Description

This week was spent figuring out the internal set up of the 3D matrix. I talked for a bit with Prof Ben about the best ways to hold the individual pieces in a structure. For now, I use a 3D matrix to hold the colors of the pieces. From there, I would like two other matrices, or metadata, one which will hold the type of the piece and one which will hold an identifer to the unique part. In other words, given the three matrices, we can construct cubes of color, and then refine the cubes with lines signifying unique pieces in the 3D space. 

My language now will parse variables and instructions, but will interpret them a list of instructions one by one. Therefore, it is not possible to create some structures, as I've discussed in the past post. Therefore, the next two things that need to be implemented are:
* The ability to place pieces above and below relative to the current pieces there. Therefore, I will have "at", which will by default search from the base level up for a spot in the grid, "below" which will start at the highest placed block in the grid and look down, and "above," which will find the highest and place above it. 
* Creating variables within a dynamic grid and then placing that structure in the grid. This proved harder than I thought, so I'm still working on this.

From there, I plan to add coordinate variables, dynamic grid sizes, and special variable additions, like having a mapping of Color -> Color and rotations.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

As I have mentioned above, the most pressing thing is the variable creations and at/below/above. This would allow me to create all possible structures. Additionally, I need to figure out the best way to output the matrix.

**What questions do you have for your critique partners? How can they best help
you?**

I don't really have any right now. I only wish to make my code more functional, so if you see any places where I could, that would help!

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

I spent two hours over Monday and Wednesday, and spent 4 hours later on in the week.

## Post-critique summary

Johnathan discussed my example in the previous notebook entry and commented on what I'd like to add. He answered my question on the z-axis, mentioning something similar to what I'll do where I find a position where the variable fits by moving the whole grid up or down. He also said I should focus on the core product.

## Post-critique reflection

I agree, I need to make sure I don't have feature creep. As for the x's in the previous notebook, that was simply a sketch of what the Lego structure would look like if it was actually designed; it wasn't output from the program.
