<h1>8 Queens Problem </h1>

This is a sample readme file for our 8 queens problem.

The code demonstrates the queens placement on the board so no queens can remove each other.




<code>
import numpy as np
import matplotlib.pyplot as plt
from matplotlib import colors

# Initialize the chessboard
class ChessBoard:
    def __init__(self, n):
        self.size = n
        self.grid = np.zeros((n, n), dtype=int)

        self.cmap = colors.ListedColormap(['black', 'white'])
        self.bounds = [0, 0.5, 1]
        self.norm = colors.BoundaryNorm(self.bounds, self.cmap.N)

    def reset(self):
        self.grid = np.zeros((n, n), dtype=int)

    #place the queen on the chessboard with the validation of no queens can attack each other
    #in row, column or diagonally
    def placeQueens(self, start_row=0, j=0):
        i = start_row
        while (i < self.size):
            while (j < self.size):
                if self.checkValid(i, j):
                    self.grid[i, j] = 1
                    if i+1 >= self.size or self.placeQueens(i+1):
                        return True
                    else:
                        self.grid[i, j] = 0
                j += 1
            return False
        
    def placeMultipQueens(self, all=True):
        if all:
            pltSize = int(self.size**0.5)
            ctr = 1
            ctrMax = pltSize**2
            _ = plt.figure(figsize=(10, 8))
            explored = []
            for j in range(self.size):
                self.reset()
                if (self.placeQueens(0, j)) and (ctr <= ctrMax) and (j not in explored):
                    mat = np.array(board.grid)
                    plt.subplot(pltSize, pltSize, ctr)
                    plt.xticks(np.arange(-0.5, self.size), range(0, self.size+1))
                    plt.yticks(np.arange(-0.5, self.size), range(0, self.size+1))
                    plt.imshow(mat, cmap=self.cmap, norm=self.norm)
                    plt.grid(which='major', axis='both', linestyle='-', color='w', linewidth=2)
                    ctr += 1
                    explored.append(np.argmax(self.grid[0]))
                    
        else:
            self.placeQueens()
            mat = np.array(board.grid)
            print(mat)
            plt.imshow(mat)
            plt.show()
            print("tf")
            
            
    #Checking whether the positon of the queen is valid or not. 
    #The condition is two queens does not meet with each other in row, column or diagonally. 
    #The queens positions are placed in the way where they can't attack each other
    #backtracking method
    def checkValid(self, row, col):
        if any([self.grid[row, x] for x in range(self.size)]) or any([self.grid[x, col] for x in range(self.size)]):
            # print("hori/vert")
            return False
        for x in range(self.size):
            if ((0 <= row-x < self.size) and (0 <= col-x < self.size) and self.grid[row-x, col-x]):
                # print((row-x, col-x))
                return False
            if ((0 <= row+x < self.size) and (0 <= col+x < self.size) and self.grid[row+x, col+x]):
                # print((row+x, col+x))
                return False
            if ((0 <= row-x < self.size) and (0 <= col+x < self.size) and self.grid[row-x, col+x]):
                # print((row-x, col+x))
                return False
            if ((0 <= row+x < self.size) and (0 <= col-x < self.size) and self.grid[row+x, col-x]):
                # print((row+x, col-x))
                return False
        return True


if __name__ == "__main__":
    # user will determine the number of the queens(n) on the nxn chessboard
    n = int(input("Enter the number of the queens on the chessboard(N > 3): "))

    board = ChessBoard(n)
    board.placeMultipQueens()

    #show the result using matplotlib
    plt.show()
</code>


<h2>Explanation and how to implement</h2>

<em> Initially, we chose to create a N x N grid chessboard since the user will enter the value for n when the program is launched.
The placement of the white chessboard pieces is understood to represent the queens' positions, while the black chessboard pieces are understood to represent the board's empty spaces. </em>

<h4><code>    
 def __init__(self, n):
        self.size = n
        self.grid = np.zeros((n, n), dtype=int)

        self.cmap = colors.ListedColormap(['black', 'white'])
        self.bounds = [0, 0.5, 1]
        self.norm = colors.BoundaryNorm(self.bounds, self.cmap.N)

    def reset(self):
        self.grid = np.zeros((n, n), dtype=int)

 </code></h4>

<hr>

<em> To ensure that no queens can attack one another at a point in a row, column, or diagonally, we must validate the position of the queen.
The programme will verify the queen's placement on the chessboard each time a queen is added.  </em>

<h4><code>

def checkValid(self, row, col):
        if any([self.grid[row, x] for x in range(self.size)]) or any([self.grid[x, col] for x in range(self.size)]):
            # print("hori/vert")
            return False
        for x in range(self.size):
            if ((0 <= row-x < self.size) and (0 <= col-x < self.size) and self.grid[row-x, col-x]):
                # print((row-x, col-x))
                return False
            if ((0 <= row+x < self.size) and (0 <= col+x < self.size) and self.grid[row+x, col+x]):
                # print((row+x, col+x))
                return False
            if ((0 <= row-x < self.size) and (0 <= col+x < self.size) and self.grid[row-x, col+x]):
                # print((row-x, col+x))
                return False
            if ((0 <= row+x < self.size) and (0 <= col-x < self.size) and self.grid[row+x, col-x]):
                # print((row+x, col-x))
                return False
        return True

</code> </h4>
<hr>

<em> This is a user input so that the user could choose the grid and the quantity of queens on the chessboard.  </em>  
<h4><code>

 n = int(input("Enter the number of the queens on the chessboard(N > 3): "))

    </code></h4>
<hr>    

<em> The queen will always start at position (0, 0) as a result of this validating their positions. It moves the queen to an open area on the board and circles the entire thing to look for openings. By using this function, the queen is placed in a suitable location where other queens cannot occupy it.</em>
<h4><code>

   def placeQueens(self, start_row=0, j=0):
        i = start_row
        while (i < self.size):
            while (j < self.size):
                if self.checkValid(i, j):
                    self.grid[i, j] = 1
                    if i+1 >= self.size or self.placeQueens(i+1):
                        return True
                    else:
                        self.grid[i, j] = 0
                j += 1
            return False

    </code></h4>
<hr>

<em> This function demonstrates the various outcomes when the first-row queen is positioned in various columns. This is done to demonstrate the various options that can be found based on user input and plot the queen in the output.</em>

 <h4><code>

 def placeMultipQueens(self, all=True):
        if all:
            pltSize = int(self.size**0.5)
            ctr = 1
            ctrMax = pltSize**2
            _ = plt.figure(figsize=(10, 8))
            explored = []
            for j in range(self.size):
                self.reset()
                if (self.placeQueens(0, j)) and (ctr <= ctrMax) and (j not in explored):
                    mat = np.array(board.grid)
                    plt.subplot(pltSize, pltSize, ctr)
                    plt.xticks(np.arange(-0.5, self.size), range(0, self.size+1))
                    plt.yticks(np.arange(-0.5, self.size), range(0, self.size+1))
                    plt.imshow(mat, cmap=self.cmap, norm=self.norm)
                    plt.grid(which='major', axis='both', linestyle='-', color='w', linewidth=2)
                    ctr += 1
                    explored.append(np.argmax(self.grid[0]))
                    
        else:
            self.placeQueens()
            mat = np.array(board.grid)
            print(mat)
            plt.imshow(mat)
            plt.show()
            print("tf")
     
 </code></h4>
 
<hr>
<hr>
