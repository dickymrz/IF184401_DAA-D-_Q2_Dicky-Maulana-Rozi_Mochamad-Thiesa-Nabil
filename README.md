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

## Source Code

```
import string
import random
import sys
def is_solveable():
    count=0
    for x in range(8):
        if(list1[x+1] and list1[x] and list1[x] > list1[x+1]):
            count+=1
    if(count%2==0):
        return True
    else:
        print("The Puzzle is not soveable")
        sys.exit() 
```
Function for find out the numbers you've entered is can be solved or not, for the algorithm we use looping for checking do the numbers from list you've entered one by one bigger from the next number or not, then using "AND" operation also using Modulo operation ("%2"), if there were [even]s numbers reach this condition, then this puzzle may can be solved using this solver.

```
game_on = True
move = 0
goal_state = [1, 2, 3, 4, 5, 6, 7, 8, 0]
print("Insert Start State (e.g '1 2 3 4 5 6 7 8 0')")
list1 = [int(x) for x in input().split()]
is_solveable()
starting_state = list1.copy()
```
In this part, start user interaction, player must fill the numbers of puzzle by themselves.

```
matrix=[]
while list1 !=[]:
    matrix.append(list1[:3])
    list1 = list1[3:]
```
creating matrix for the list(s)

```
class Node:
	def __init__( self, state, parent, operator, depth, cost ):
		self.state = state
		self.parent = parent
		self.operator = operator
		self.depth = depth
		self.cost = cost
```
Using class for create Nodes which having those attributes

```
def display_board( state ):
	print ("-------------")
	print ("| %i | %i | %i |" % (state[0], state[1], state[2]))
	print ("-------------")
	print ("| %i | %i | %i |" % (state[3], state[4], state[5]))
	print ("-------------")
	print ("| %i | %i | %i |" % (state[6], state[7], state[8]))
	print ("-------------\n")
```

In this part of code, is the proses of arranging numbers which is player entered. (Classic UI). And also for addressing states which will be used for algorithm

```
def move_up( state ):
    new_state = state[:]
    index = new_state.index( 0 )

    if index not in [0, 1, 2]:
        temp = new_state[index - 3]
        new_state[index - 3] = new_state[index]
        new_state[index] = temp
        return new_state
    else:
        return None
```
For moving up, if the index position of zero not in index state[0], state[1], or state[2].


```
def move_down( state ):
    new_state = state[:]
    index = new_state.index( 0 )

    if index not in [6, 7, 8]:
        temp = new_state[index + 3]
        new_state[index + 3] = new_state[index]
        new_state[index] = temp
        return new_state
    else:
        return None
```
For moving down, if the index position of zero not in index state[6], state[7], or state[8].

```
def move_left( state ):
    new_state = state[:]
    index = new_state.index( 0 )

    if index not in [0, 3, 6]:
        temp = new_state[index - 1]
        new_state[index - 1] = new_state[index]
        new_state[index] = temp
        return new_state
    else:
        return None
```
For moving left, if the index position of zero not in index state[0], state[3], or state[6].

```
def move_right( state ):
    new_state = state[:]
    index = new_state.index( 0 )

    if index not in [2, 5, 8]:
        temp = new_state[index + 1]
        new_state[index + 1] = new_state[index]
        new_state[index] = temp
        return new_state
    else:
        return None
```
For moving right, if the index position of zero not in index state[2], state[5], or state[8].

```
def create_node( state, parent, operator, depth, cost ):
	return Node( state, parent, operator, depth, cost )
```
create node

```
def expand_node( node, nodes ):
	expanded_nodes = []
	expanded_nodes.append( create_node( move_up( node.state ), node, "up", node.depth + 1, 0 ) )
	expanded_nodes.append( create_node( move_down( node.state ), node, "down", node.depth + 1, 0 ) )
	expanded_nodes.append( create_node( move_left( node.state ), node, "left", node.depth + 1, 0 ) )
	expanded_nodes.append( create_node( move_right( node.state), node, "right", node.depth + 1, 0 ) )
	expanded_nodes = [node for node in expanded_nodes if node.state != None]
	return expanded_nodes
```
expanding nodes with bfs algorithm, by finding all possible movement of zero to left, right, up, or down until it find the goal state. Each node that expand will have state after it being move (wether up, down, right, or left), the node, a string to tell us where it moves, and the depth of the node.

```
def bfs( start, goal ):
    nodes = []
    nodes.append( create_node( start, None, None, 0, 0 ) )
    
    while True:
        if len( nodes ) == 0: return None
        
        node = nodes.pop(0)
        stack = []

        if node.state == goal:
            moves = []
            temp = node
            while True:
                moves.insert(0, temp.operator)
                if temp.depth == 1: break
                temp = temp.parent
                stack.append(temp.state)
            i = len(stack) - 1
            while i != -1:
                display_board(stack[i])
                i -= 1
            return moves				
  nodes.extend( expand_node( node, nodes ) )
```
BFS algorithm proccess, recursively extend the node by finding all possible movement of zero until find the goal state. And then from the goal state that has been found, the parent state is stored in a list, and print the state from the very first move after the start state to the final state (some kind of stack which is LIFO, but with list).

```
def nyerah():
    display_board(starting_state)
    result = bfs( starting_state, goal_state )
    display_board(goal_state)

    if result == None:
        print ("No solution found")
    elif result == [None]:
        print ("Start node was the goal!")
    else:
        print (result)
        print (len(result), " moves")
```
The solver main proccess, calling bfs algoritm proccess for solving the puzzle icluding the steps and moves found using the algorithm.

```
def zero(board):
    global empty_space
    for x in range (len(board)):
        for y in range(len(board[x])):
            if board[x][y] == 0:
                empty_space = (x,y)
    return empty_space
```
returning empty_space if the matrix is empty

```
def draw_board(board):
    if(board == [[1, 2, 3], [4, 5, 6], [7, 8, 0]]):
        print('you did it!\n')
        sys.exit()
    else:
        print('\n')
    print('\n\t+-------+-------+-------|')
    for x in range (len(board)):
        for y in range(len(board[x])):
            if board[x][y] == 0:
                print('\t|  0' , end='')
            else:
                 print('\t|  ' + '{:d}' .format(board[x][y]), end=' ') 
        print('\n\t+-------+-------+-------|')
```
In this part of code, is the proses of arranging numbers which is player entered. (Classic UI). And also for addressing states which will be used for algorithm If the current process already the goal state, it means the puzzle is solved and the program will exit.

```
def ask_number():
    global num , piece 
    num = input('\nplease type the number of the piece to move : (q) to give up and show the solver (bfs) : ')
    if num in ['q','Q']:
        print('\ngame over\n')
        nyerah()
        sys.exit()

    num = int(num)
    piece=()
    for i in range(len(matrix)):
        for j in range(len(matrix[i])):
            if num == matrix[i][j]:
                piece = (i,j)
    return piece , num
```
In this part of code, is the proses of entering numbers which is player entered as input.

```
zero(matrix)
while game_on:
    draw_board(matrix)      
    ask_number()         
    if num > 8:
        print('illegal move , try again  ')
    else:
        if(empty_space==(piece[0]-1,piece[1]))\
           or(empty_space==(piece[0]+1,piece[1]))\
           or(empty_space==(piece[0],piece[1]-1))\
           or(empty_space==(piece[0],piece[1]+1)):
            matrix[empty_space[0]][empty_space[1]]=num
            matrix[piece[0]][piece[1]]=0
            empty_space=(piece[0],piece[1])
            move = move +1
            print('you have made ',move , 'moves so far ')
            print('\n')
        else:
            print('illegal move , try again ')
```
The drawing proccess of the matrix, including the ask_number function start.
