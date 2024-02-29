# 2.2 ASSESSMENT - Heat Maps

An extension of the `random walk` (see 2.2 challenge) is a [heat map](https://en.wikipedia.org/wiki/Heat_map). Essentially every time a location (or data point) is touched, increase the value by 1. This represents how "hot" that data item is. (More info available [here](https://chartio.com/learn/charts/heatmap-complete-guide/))

You will create some functions that provide heat maps for a 2-dimensional grid. _You **are** permitted to use any of your own previous code._

### Print_2d
Copy over your `print_2d` function (and any other helper functions) from the `2.2 - 2D Arrays` task so that you can easily see results.

### Ver. 1 - Completely Random
Create the function `heat_map(width, height)` that starts at location (0, 0) and randomly moves in any direction - including diagonally. The goal is to reach the bottom-right corner (`width`-1, `height`-1).
**Some details:**

- Your starting location of (0, 0) begins with a value of 1.
- You could move in one of eight possible directions: N, NE, E, SW, S, SW, W, NW.
- You must not exit the grid.
  - For example, a movement of "N" as the first move is not permitted, pick a new direction
- Every direction should always have the same probability of being selected.
  - If an invalid direction is chosen, do not increase any data points and pick a new direction.
- The bottom-right corner is the final destination.
  - It should have a value of 1 as the progam has reached the goal.
  - The program ends and _returns_ the final grid.

### Ver. 2 - Controlled Random
Create the function `controlled_map(width, height, start, end)` that starts at location `start` (a 2D array of [x, y]) and finishes when it reaches `end` (a 2D array of [x, y]). 
**Ver. 2 details:**
- The values of `start` and `end` should never be equal.
  - If they are, the program should exit (return) and the _only_ data point with any value should be `start` with a value of 1.
- In this version, the map will never backtrack one step.
  - Example: if the movement is [3, 4] -> [4, 4], it will not immediately go back to [3, 4]
  - It _can_ revisit locations, just not immediately
- All other rules of Ver. 1 apply, except the start and end locations.

### Ver. 3 - Given Data (challenging)
Create the function `prescribed_map(data)`. Read this description carefully.
**Ver. 3 details:**
- You are given a one-dimensional array of movements (integers) from 1 to 8
```
NW N NE         8  1  2
  \|/             \|/
W - - E   <=>   7 - - 3
  /|\             /|\
SW S SE         6  5  4
```
- You do not know where the starting position is. That is to say, it is _not necessarily_ (0, 0).
- Any direction is valid, at any time.
- The function ends (returns the grid) when the given `data` has run out.
**Important final data points:**
- Any non-visited locations in the grid (not outside the grid) are marked with `0`
- The starting location is marked with "*"
- The final location is marked with "X"

**Ver. 3 Examples will follow**

Plan your work carefully for this. It is highly recommended that you _pseudocode_ or create a plan before starting to code.


<br><br><br><br>
