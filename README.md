# :christmas_tree: Advent Of Code 2018 - Christmas puzzles

Christmas is comming and programming is always a fun way to celebrate it. From Dec 1st to Dec 25th, a puzzle consisting of two parts is released every day ([https://adventofcode.com](https://adventofcode.com)) and I'll be trying to solve them consistently, 25 days in a row, every morning, and hopefully fast enough to collect some points on the leaderboard. Let the Advent(ure) begin!

### [Day 1: Chronal Calibration](https://adventofcode.com/2018/day/1)
The answer for the first part is the sum of all the provided numbers. <br/>
For the second part, the simulation is good enough. At each step, the new frequency is added into a hash table, until a second occurence is found.

### [Day 2: Inventory Management System](https://adventofcode.com/2018/day/2)
The first subtask can be solved by computing for each box the letter frequencies, and checking if 2 and 3 are present in the frequency array. <br/>
The last subtask is straightforward, by counting the number of mismatches for each pair of boxes.

### [Day 3: No Matter How You Slice It](https://adventofcode.com/2018/day/3)
This puzzle can be approached by using a matrix, and incrementing by 1 the corresponding cells of each of the provided rectangles. The two answers are: the number of cells having the value greater than 1, and the id of the rectangle for which the sum of the cells it covers is equal to its area. <br/>
Instead of using the direct approach, I've tried to make the implementation less boring, by optimizing the operations described above, *2D range incrementation* and *2D range sum*. The core idea is to use partial sums. More information about the techniques I've used can be found here:
* [summed-area table](https://en.wikipedia.org/wiki/Summed-area_table)
* [constant time 1D range incrementation](https://www.geeksforgeeks.org/constant-time-range-add-operation-array/) (it can be extend to 2D ranges by updating 4 values)

### [Day 4: Repose Record](https://adventofcode.com/2018/day/4)
The first thing to begin with is sorting all the lines, to ensure the actions are processed in the correct order. Afterwards, it becomes a parsing problem, and computing a map like *"guard[id][m] = how many days the guard having the identifier id sleeps during the m-th minute"* will facilitate solving the two tasks.

### [Day 5: Alchemical Reduction](https://adventofcode.com/2018/day/5)
A very cute problem, that boils down to simulating efficiently the chemical reactions. By using a stack, the reactions can be executed in order, left to right, as they occur, in linear time. 

### [Day 6: Chronal Coordinates](https://adventofcode.com/2018/day/6)
I've decided tot keep the approach simple and thus I've computed the bounding box of the input points to reduce the processiong time. <br/>
For the first task, every point of the bounding box is examined to determine to which region it belongs to, and to increase the size of that region, unless  it proves to be a '.' point. The only difficulty is identifying the infinite regions. It can be observed that a region is infinite if and only if it has at least one element situated at the beginning or the end of the line or column to which the initial point belongs to. <br/>
For the second task, the searching region is derived from the original bounding box, by enlarging it as much as possible, in such a way the new corners will be still in a reach distance of 10000.

### [Day 7: The Sum of Its Parts](https://adventofcode.com/2018/day/7)
The key of the problem is the topological sorting. I've decided to use [Khan's algorithm](https://en.wikipedia.org/wiki/Topological_sorting) with slight changes to ensure the lexicographically minimal solution is computed. The second part is a generalization of the first one, where multiple workers can execute the tasks in parallel, and thus the code can be kept quite compact, by solving only the general problem.

### [Day 8: Memory Maneuver](https://adventofcode.com/2018/day/8)
Another cute problem. Since the tree layout is defined recursively, the recursive approach is self suggested. For more details, the source can be consulted.
