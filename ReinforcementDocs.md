# Reinforcement Learning Algorithm Documentation (WORK IN PROGRESS)
## State
* *List* of (time t<sub>i</sub>, *list* of channels c<sub>1</sub>, (c<sub>2</sub>, ..., c<sub>n</sub>))
#### Example
* [[c1, c2, ..., cn], [c1, c2, ..., cn], ..., [c1, c2, ..., cn]]

## Time
* Discrete, arbitrary unit that increases by increments of 1.

## Channel
* [TODO] settle on representation of channel (especially interference value)
* Channel indices in the above mentioned state sublist should be static. For example, channel C is the same channel regardless if it is time 2 or time 3,000.

## Goal
* Minimize interference at any given time

## Sample Data and Pattern Generation
* Our simulated data is created with a pattern of an environment. For a given channel C at a given time T, there will be three values in its pattern. 
    * Alpha
    * Weight
    * Transmission Length
* When the data is being generated, a random number is computed and if it is lower than the alpha, then weight is *subtracted* from C's interference. Then a random transmission length is generated, and the interference is propagated into the future for the transmission length.
* The same pattern will be applied to any new data that is generated.

| Time | Channel 1 | Channel 2 | . . . | Channel N
| --- | --- | --- | --- | --- 
| t1 | c1 | c2 | ... | cN 
| t2 | 
| ... |
| t3 |



## Algorithm (based off of CSU CS 440 [lecture notes](https://nbviewer.jupyter.org/url/www.cs.colostate.edu/~anderson/cs440/notebooks/14%20Introduction%20to%20Reinforcement%20Learning.ipynb))

for round in time:
* If round < 0
   * If Q table for [round, [moves]] is empty, initialize Q table with reinforcements of 100
   * Generate either random hop or greedy hop (pick highest reinforcement) depending on epsilon
   * If hop is not the optimal hop (its interference is *not* the lowest), decay its reinforcement by the learning rate
   
