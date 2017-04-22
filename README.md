# Artificial Intelligence Nanodegree
## Introductory Project: Diagonal Sudoku Solver

# Question 1 (Naked Twins)
Q: How do we use constraint propagation to solve the naked twins problem?

A: Sudoku has 29 units in total, which are 9 row units, 9 comlumn units,
9 square units and 2 diagonal units. So the constraints will be
propagated into every 29 units using loop. And keep in mind that every
unit has 9 boxes (or numbers). First, in every loop for 29 units, we
don't care the numbers with a length of 1 in a box. We're just going to
take the box of 1-length values as solved boxes. Because, we don't need
to unnecessary computation for the solved ones in 9 boxes.

Next, we should investigate which one has the naked twins in 9 boxes. In every
units, all the values whose length is 2 could be considered as a candidate for
the naked twins. But to be the naked twins between the boxes with two-length values,
their values must duplicated in boxes.

To find out which boxes are duplicated, we're going to introduce a dictionary,
its keys is going to be each numbers in a box and its values is going to
be a list with the name of boxes (ex. D4, E6) that has every duplicated numbers.

If, the length of the list is greater than 1, it means there are duplicated
boxes at where that value is. Therefore, we can take all the boxes which is
greater than 1 in a list into the naked twins.

So far, we could find out what the unsolved boxes and the naked twin boxes are.
Now, we invastigate 9 boxes in a unit again with these boxes. We're going to
choose only the unsolved boxes from 9 boxes, and also exclude the naked twin
boxes itself from 9 boxes. Then, replace the value of the unsolved box with
the value of the naked twin box


# Question 2 (Diagonal Sudoku)
Q: How do we use constraint propagation to shouolve the diagonal sudoku problem?
A: It is simple. Add two diagonal units into the exsiting entire unit. Then, we have 29 units to propagate the constraint. As well as the existing `eliminate ()` and `only_choice ()` algorithms, apply the `naked_twins()` algorithms to the strategies to solve all of the units which has included the diagonal units.

### Install

This project requires **Python 3**.

We recommend students install [Anaconda](https://www.continuum.io/downloads), a pre-packaged Python distribution that contains all of the necessary libraries and software for this project.
Please try using the environment we provided in the Anaconda lesson of the Nanodegree.

##### Optional: Pygame

Optionally, you can also install pygame if you want to see your visualization. If you've followed our instructions for setting up our conda environment, you should be all set.

If not, please see how to download pygame [here](http://www.pygame.org/download.shtml).

### Code

* `solution.py` - You'll fill this in as part of your solution.
* `solution_test.py` - Do not modify this. You can test your solution by running `python solution_test.py`.
* `PySudoku.py` - Do not modify this. This is code for visualizing your solution.
* `visualize.py` - Do not modify this. This is code for visualizing your solution.

### Visualizing

To visualize your solution, please only assign values to the values_dict using the ```assign_values``` function provided in solution.py

### Submission
Before submitting your solution to a reviewer, you are required to submit your project to Udacity's Project Assistant, which will provide some initial feedback.

The setup is simple.  If you have not installed the client tool already, then you may do so with the command `pip install udacity-pa`.

To submit your code to the project assistant, run `udacity submit` from within the top-level directory of this project.  You will be prompted for a username and password.  If you login using google or facebook, visit [this link](https://project-assistant.udacity.com/auth_tokens/jwt_login for alternate login instructions.

This process will create a zipfile in your top-level directory named sudoku-<id>.zip.  This is the file that you should submit to the Udacity reviews system.

