# wumpus-world-genetic-algorithm
This project makes use of genetic algorithms to solve the Wumpus world problem and improve the maximal fitness of a population of agents.

To create a board, one simply needs to set a few parameters and create the board object:

```holes```: an integer representing the amount of holes on the board\
```coins```: an integer representing the amount of coins on the board\
```size```: a tuple representing the size of the board\
```path```: an array representing the path of the Wumpus. It can also be set to ```None``` to induce random movement.

The board can now be made with the command ```b = Board(size, holes, coins, path``` and visualized with
```
fig, ax = plt.subplots(1,1, figsize = (5,5))
board_plot(b.board, ax)
plt.show()
```

Now we only need to create a population:\
In our experiments we used ```p = Population(b, 1000, 500, 0.01, False)```. This creates a population with 1000 agents that each have a path with a maximal length of 500. Mutations are performed with a 0.01 chance. ```False``` indicates that mutations can happen with said chance on every step of the path. If set to ```True```, mutations can only appear on a randomly selected step. We can then perform our evolutionary algorithms on this population by calling ```x, y = p.natural_selection(1000, False)```. This performs selection for 1000 iterations. ```False``` just means that it does not plot intermediary results.

If one has installed ffmpeg (available via https://ffmpeg.org/) and provided the correct path to the .exe file in the first code block, one can create a video of the best agent moving through the Wumpus world with:
```
frames = b.check_path(path, animate = True)
boards_to_animation(frames)
```

To plot the final maximal fitness one can run the following code block:
```
plt.show()
plt.plot(range(len(y)), y, label = 'Max Fitness')

plt.xlabel('Iterations')
plt.ylabel('Fitness')
plt.legend()

plt.figure()
plt.plot(range(len(z)), z, label = 'Average Fitness')
plt.xlabel('Iterations')
plt.ylabel('Fitness')
plt.legend()
plt.show()
```

Note that all these pieces of code are already present in premade cells in the notebook.



