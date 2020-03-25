## Problem 8-Puzzle using Breadth-First Search (BFS)

  The 8-puzzle is a puzzle invented and popularized by Noyes Palmer Chapman in the 1870s. It is played on a 3-by-3 grid with 8 square blocks labeled 1 through 8 and a blank square. Your goal is to rearrange the blocks so that they are in order. You are permitted to slide blocks horizontally or vertically into the blank square. The following shows a sequence of legal moves from an initial board position (left) to the goal position (right).

  Breadth-first search (BFS) is an algorithm for traversing or searching trees or graph data structures. It starts at the root tree (or some arbitrary node of a graph, sometimes referred to as a 'search key'), and explores all of the neighbor's nodes at the present depth prior to moving on to the nodes at the next depth level.

  It uses the opposite strategy as depth-first search, which instead explores the node branch as far as possible before being forced to backtrack and expand other nodes. Objective of this work is to find the complete solution of eight puzzle problem i.e. examining all the permutations for solvability. Using Breadth First search (BFS) graph traversal we can reach the solution for a definite goal.

## How to play 8-puzzle using Breadth-First Search (BFS) in python

1.  Run the python file and will show "Insert Start State (e.g '1 2 3 4 5 6 7 8 0')"

2.  Enter 8 digit different numbers Range = {0,1,2,3,4,5,6,7,8}
    Example : 7 5 4 0 3 2 8 1 6
    
3.  If the puzzle showed up then its time to start to play, and if the puzzle not showed up means you entered the wrong number. 
    Example : 
    7,5,4
    0,3,2
    8,1,6
    
4.  Solve the puzzle until the numbers arranged into :
    1,2,3
    4,5,6
    7,8,0
    
5.  Type a number you want to move and hit enter
    Example : 7
    0,5,4
    7,3,2
    8,1,6
    if you input an 7, then it will move the zero to the down, which is the number of 7. If you input a 5, then the zero will move         right, and etc.
    
6.  If you have given up, type 'Q' / 'q' and hit enter

7.  Try moving as little as possible and solve it
