# ASSESSMENT - 2D Arrays

##### ICS4U - Mr. Brash 🐿️

#### This assessment is out of 40 points - 10 per function. _Heat Map Version 3 is an optional extension worth bonus marks._

You will create some functions that create or utilize 2-dimensional grids in some way. _You **are** permitted to use any of your previous code from 2D array work or similar._ You are **not** permitted to use code generators, online assistance or code-sharing sites.

## 1 - Modify `print_2d()`

Copy over your `print_2d()` function (and any other helper functions you made) from the [2D Arrays classroom practice](https://www.brash.ca/ics4uc/lessons/9). The original `print_2d()` function only took an array and printed it with **_tabs_** as the separator.  

_Modify_ your `print_2d()` function with the parameter `separator` so that each element can be separated by a specific character or string.

```JS
function print_2d(arr, separator = "\t") {
  // Your code
}
```

That is called a default parameter value. If the parameter is ommitted, it defaults to the `tab` character. BUT, you could use any character you wanted:

```JS
print_2d(my_array, " ");    // separate by spaces
print_2d(my_array, "*");    // separate by stars
print_2d(my_array, "🐿️");  // separate by squirrels (actually, it's a chipmunk...)
```

**TEST YOUR CODE THOROUGHLY**

## 2 - String to 2D

Mr. Brash has some 1-dimensional arrays (actually, they're Strings!) that are supposed to be 2D arrays for an art project. All he knows is how tall each art piece should be.

Your job is to create the function `ascii_art(str, height)` that does _three_ things:
1. Convert the `str` to a 2D array of individual characters that is `height` rows tall.
2. Print the new 2D array to the screen using your `print_2d()` function _with no separator_. That is - the separator is an empty string `""`.
3. _Return_ the 2D array version of the artwork.

**Examples:**
```BASH
ascii_art("───▄▀▀▀▄▄▄▄▄▄▄▀▀▀▄──────█▒▒░░░░░░░░░▒▒█───────█░░█░░░░░█░░█─────▄▄──█░░░▀█▀░░░█──▄▄─█░░█─▀▄░░░░░░░▄▀─█░░█", 5);

───▄▀▀▀▄▄▄▄▄▄▄▀▀▀▄───
───█▒▒░░░░░░░░░▒▒█───
────█░░█░░░░░█░░█────
─▄▄──█░░░▀█▀░░░█──▄▄─
█░░█─▀▄░░░░░░░▄▀─█░░█

## AND RETURNS THE 2D ARRAY BUT NOT SHOWING THAT HERE ##

ascii_art("   ▀▄ ▀▄     ▄▀ ▄▀     █▀▀▀▀▀█▄   █░░░░░█ █  ▀▄▄▄▄▄▀▀  ░░░░░░░░░░░", 6);

   ▀▄ ▀▄   
  ▄▀ ▄▀    
 █▀▀▀▀▀█▄  
 █░░░░░█ █ 
 ▀▄▄▄▄▄▀▀  
░░░░░░░░░░░

## AND RETURNS THE 2D ARRAY BUT NOT SHOWING THAT HERE ##
```

**TEST YOUR CODE THOROUGHLY**

## 3 - Heat Map
An extension of a `random walk` (from the 2D arrays challenge) is a [heat map](https://en.wikipedia.org/wiki/Heat_map). Essentially every time a location (or data point) is touched, increase the value by 1. This represents how "hot" that data item is. (More info available [here](https://chartio.com/learn/charts/heatmap-complete-guide/))

**You will be creating two version of a heat map with an _optional_ third version (extension).**

### Ver. 1 - Completely Random

Create the function `heat_map(width, height)` that starts at location (0, 0) and randomly moves in any direction - including diagonally. The goal is to reach the bottom-right corner (`width`-1, `height`-1).  

**Some details:**

- Note the format of the function - it is defined with `width` and then `height`
- Your starting location of (0, 0) begins with a value of 1.
- You could move in one of eight possible directions: N, NE, E, SE, S, SW, W, NW.
- You must not exit the grid and no wrapping.
  - For example, a movement of "N" as the first move does nothing, pick a new direction
  - If an _invalid_ direction is chosen, do not increase any data points and pick a new direction.
- Every direction should always have the same probability of being selected.
- The bottom-right corner is the final destination!
  - It should have a value of 1 as the progam has reached the goal.
  - The program ends and _returns_ the final grid.

**A heat map is best printed with `tabs` as a separator. TEST YOUR CODE THOROUGHLY **

### Ver. 2 - Controlled Random (somewhat challenging)

This version starts at location `start` (an array of [x, y]) and finishes when it reaches `end` (an array of [x, y]).  

**Ver. 2 details:**
- The function is called `controlled_map(width, height, start, end)`
- If the values of `start` and `end` are equal, the program should end and the _only_ data point with any value in the returned map should be `start` with a value of 1.
- **In this version, the map will never backtrack one step.**
  - Example: if the movement is [3, 4] -> [4, 4], it cannot immediately go back to [3, 4]
  - It _can_ revisit locations, just not immediately
- All other rules of Ver. 1 apply, except the start and end locations.

### Ver. 3 - EXTENSION A Heat Map with Given Data (challenging)

Create the function `data_map(data)`. _Read this description carefully_.

**Ver. 3 details:**
- You are given a one-dimensional array of _movements_ (integers) from 1 to 8
```TXT
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

Plan your work carefully for this. It is highly recommended that you _pseudocode_ or create a plan before starting to code.

**Ver. 3 Examples:**

```
Given: [ 5, 6, 8, 2, 5, 6, 1, 2, 4, 5, 5, 3, 6, 3, 2, 6, 2, 6, 7, 6, 6, 2,
         7, 7, 1, 2, 5, 2, 8, 2, 1, 3, 8, 5, 8, 5, 6, 8, 5, 8, 7, 5, 4, 4,
         4, 2, 4, 8, 6, 4 ]

Heat Map:
0	0	0	0	1	1	0	0	0	
1	1	1	0	1	4	*	0	0	
1	0	1	1	2	2	2	0	0	
0	1	0	0	2	1	1	0	0	
0	0	1	0	3	1	1	1	2	
0	0	0	3	1	1	2	3	0	
0	0	0	1	X	2	0	0	0	
0	0	0	0	1	0	0	0	0
```

```
Given: [ 5, 2, 8, 2, 8, 8, 3, 1, 7, 1, 6, 3, 2, 8, 6, 6, 5, 4, 5, 6, 1, 5,
         5, 8, 6, 1, 5, 1, 4, 1, 1, 5, 7, 3, 6, 7, 5, 7, 6, 4, 6, 1, 4, 6,
         4, 8, 7, 5, 7, 7 ]

Heat Map:
0	0	0	0	0	0	0	0	0	0	1	0	0	
0	0	0	0	0	0	0	0	0	1	1	1	0	
0	0	0	0	0	0	0	0	1	1	2	1	0	
0	0	0	0	0	0	0	0	1	0	1	1	0	
0	0	0	0	0	0	0	0	0	1	0	1	0	
0	0	0	0	0	0	0	1	1	1	0	0	1	
0	0	0	0	0	0	3	4	2	0	0	1	0	
0	0	0	0	0	1	3	1	1	0	0	*	1	
0	0	0	0	1	1	0	0	0	0	0	1	0	
0	0	0	1	0	0	0	0	0	0	0	0	0	
0	0	0	1	1	0	0	0	0	0	0	0	0	
0	0	0	1	1	0	0	0	0	0	0	0	0	
0	0	1	2	0	0	0	0	0	0	0	0	0	
X	1	1	0	1	0	0	0	0	0	0	0	0
```

<br><br><br><br>
