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
