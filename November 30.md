# Design notebook for week ending November 30, 2014

## Description

This week, I named my project! Titled "Progettare," Italian for "To plan" or "To design," I believe this embodies my goals for the project. I also worked on the evaluation, and am continuing work on the interpreter. I am implementing "above" and "below," working on dynamic grids for variables, and working on error checking. Once I finish these, I will be polishing the project.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

During my discussion with Tyler, we realized I have an edge case I didn't consider. Say I design a variable, with 6 1x1 bricks in a row. Additionally, I have some 2x2 tower on the board. Currently, if I placed the 6 1x1's in the grid on the tower, without having a dynamic grid and intersecting these, 4 of the bricks would fall. If I created a grid, they would be placed above the tower. But this is incorrect, as 1x1 bricks need to stick to something, or else they are floating. I'm not sure how I will deal with this.

**What questions do you have for your critique partners? How can they best help
you?**

Any comments over the entire project would be useful!

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

I worked for 2 hours during class this week, and 2-3 hours over the weekend, working on the evaluation. I hope to work more on the code tomorrow.

## Post-critique summary and reflection

My partner did not submit this for this week.
