# minesweeper
Implementation of Minesweeper in python

## Introduction

The purpose of this project is to re-create the Minesweeper game in Python, running on Linux devices.
The game gives you a grid, where each position has the possibility of hiding a mine. At the start of the game, the nature of each button is hidden (if it contains a bomb, or it is a safe space). If the player clicks a safe space, a number is revealed, and it represents the number of bombs connected to that space. Knowing the number of bombs connected to each position, we can deduce the location of the bombs, without clicking on them.
The player wins when they tick all the safe spaces.
Using right click, the player can mark where they think a bomb might be.

For simplicity, we will consider that the grid can only be a squared matrix.

## Solution

The solution is to randomly generate the grid, and use a GUI interface to represent it. We create the interface using the Tkinter library for Python. The interface itself is quite simple. Each element of the grid is represented by a button. Once we click a button, there are two possibilities: If the player clicks on a safe space, the number of adjacent bombs is revealed. If the player clicks on the bomb, it’s game over. Once the player clicks on all the safe spaces, the game is won. 
Using the Numpy library, we can easily generate and randomize the playing grid. We feed in the size of the grid and the number of the bombs. The grid starts of as a one dimensional array, and the first n elements are 1, and the rest are 0. Where n is the number of bombs. We then shuffle the array, and re-arrange to a matrix.
For each of the non-bomb element, we count the neighboring bombs.

![Picture1](https://user-images.githubusercontent.com/89041216/214024414-f327219b-ae8d-4efb-b544-5517a68893e8.png)

The adjacency matrix that is generated. -9 represents a bomb. We need to represent this in an interface.

![Picture2](https://user-images.githubusercontent.com/89041216/214024572-6fb02467-7e08-449a-aaa2-b33e185f5f64.png)

The start of the game, all elements are hidden. Bad luck if you hit a bomb the first time. (Of course this can be addressed by moving the bomb somewhere else and regenerating the adjacency matrix) 

![Picture3](https://user-images.githubusercontent.com/89041216/214024951-c3e27f5b-e530-40f6-b4d6-c0060a81775c.png)

As more of the grid gets revealed, we can deduce the location of the bombs.

![Picture4](https://user-images.githubusercontent.com/89041216/214025034-951f42c5-b67d-41a3-abbc-430ebd518781.png)

We hit a mine, and it is game over. All buttons are disabled

![Picture5](https://user-images.githubusercontent.com/89041216/214025124-ea103092-c799-484a-a9be-7ca5314d8e62.png)

You win the game when you click all safe spaces. F means that a space is flagged by the player.

## Conclusion

In conclusion, I have created a version of Minesweeper that runs on Linux, and it’s almost fully functional. 
In the future, this could be improved with

* Restart button
* Fail-safe in case user clicks on the bomb at the start
* Better looking interface
* Settings menu to change the parameters of the game (Currently hardcoded)
