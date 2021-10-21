# CMPT225-Project

In this project I wrote a solver for the Rush Hour game. The input of this app will be a file containing a rush hour puzzle using Capitalized Alpabets as vehicles. To solve the puzzle, I need to get the XX car to the exit on the right, and write the solution to the output file.

My solution utilizes BFS and hash map to find a path for which the red car reaches the exit. 

## Documentation
My solution utilizes BFS and hash map to find a path for which the red car reaches the exit. For ease to storing data, I have decided to create two addition classes called Vehicles and Board. 

In Vehicle class, we store all information for a specific vehicle, for example, its coordinates on the board, the orientation of the car, the name and its size. This is all done by my search function that looks for all relevant info for a name of the car on the Board given. On the other hand, the Board class hold information such as the board in char array, it also looks for all the name of vehicles and stores it in an array list. We lastly need to store information on moves, this is an array list which keep tracks of all previous and current moves needed to reach out current state in a string array list.

My choice of storing data in both of these classes are purely for the ease of use, the heuristics I’ve used is to consider all possible moves for a vehicle to reach a different state of board and repeat after till we find a solution. This is because after considering the provided heuristics, I’ve always encountered a problem with more than 1 average blocked car. Therefore, I have decided to used BFS as I have the best understanding of this algorithm. Furthermore, if we use BFS, because we will be able to get the shortest path especially when the target is close to the starting node. Down side of using BFS, is that it is uninformed, it doesn’t have an estimate on the target’s distance.

For BFS, we start by adding the original Board into the queue. While the queue is not empty, we check if the Board is solved, if not, we make all possible moves on the Board. 

The all-possible moves function in my class is used to extend the spanning tree. It gets a Board and from its list of vehicle names, tries to make a move for the car, if after the move the Board becomes a similar board that we already have by comparing using hash code, we don’t want to extend the board anymore so continue to the next different move, but if the Board hasn’t been found yet, we append it into our hash map and add it into our queue for BFS, the moves required to get to this Board is then recorded down as well by taking its previous Board’s moves and adding the new move. Once a Board with a solution is found, we then let the print writer write out all the moves done to get to this Board.

Overall, the hardest part of this project is the solving algorithm. On paper, all I had to do is just to create every single possible states of the Board and look for a solution. Due to time complexity and the unknown of the puzzle, we have to deal with repeated states of the Board and the moving vehicle algorithm. The first assignment that we’ve done has made this a little simpler as my make move function only has to be altered a little to fit into the solver.

The biggest change that I’ve done to the project was the use of Graph and Vertex class at first, this idea was drawn on paper as I would just create every vertex and edge and use BFS and graph traversal to look for the solution. I then realized how much time this would have took and decided that we should expand the graph as we move to keep it simpler, this is where the hash map to check for duplicates came from idea came from.

Made by Jun Pin Foo (225)
