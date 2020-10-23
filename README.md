# Search Search and more Search

Page created by Kelly Dyer for CMSC 421 Fall 2020 Professor: William Regli
Worked in a group with: 

Purpose: Conduct a science-y like expierement on graph traversal methods relating back to the traveling salesman problem(TSP). The TSP is given a graph, in this case fully connected, what is the shortest path from a starting city to all other cities in the given graph.

# Introduction

This page is all about searching symmetric, full connected graphs to find optimal solutions for the traveling salesman problem.
  
### Code Used

I mostly used the python search code given in the Russel and Norvig AI:MA textbook. This consisted of a few classes:
  * Graph Class: Used along with Node Class to constuct graphs with a given adjancy matrix. 
  * Priority Queue: Implemented priority queue.
  * Problem Class: Abstract class to define problem subclasses.
  * Graph Problem Class: Subclass of Problem where most of the handwritten code is located. The actions and path cost are used to get neighbors in the graph at a node. Also contains all the huristics needed for A* search:
     * cheapest_edges
     * random_edges
     * primm_mst
     * kruskal_mst
   * Search Algorithms: All the search algorithms, except for MST, came from the AI:MA textbook. They are:
        * A Star
        * best_first
        * uniform_cost
        * hill_climbing
        * simulated_anneling
        * genetic
        
Outside sources of code that I used were: 
  * GeeksforGeeks website: Kruskal and Primm minmum spanning tree implementation (link in code)
  * Python-Graph-Gallery website: The shell for the graphs used in analysis section (link in code)
 
# Goal

The goal of using all this code is to randomly generate graphs with different number of nodes, 5, 8, 10, 15, and run all kinds of search algorithms on the generated graphs. Then I can analyse the path costs and time it takes for algorithms to run to determine the differences in search approach. Each search is done in batches of 30 graphs, then we can take the average of the batches to get a pretty good aproximation of the search preformance. 
    

Once all the searches are ran and the data is collected, I uploaded a csv file with all the data into a Pandas dataframe which looks like below.
  
![image](https://user-images.githubusercontent.com/66328517/96971557-49030b00-14e3-11eb-82cf-1184dbab9da7.png)

This dataframe is then grouped by search technique and how many nodes are in the graph. The analysis of the graphs presented next are grouped this way. 

## Part 1 Graphs 

For part 1 we were asked to implement A* on random TSP problem using three heuristic:
  * h(n)=0 which is just uniform cost serch
  * Random Edges which grabs edge lengths connected to the node, adds them together and used for h(n)
  * Cheapest Remaining Edges which uses cheapset remaining edges for h(n)

For this part I was only about to run graphs of size 5, 7, and 8. Larger graphs exponentially increase the time it takes for uniform cost search and could not be run. I tried to run size 9 and 10 overnight, because I used Google CoLab for this project, it timed out after 3 hours and had to be restarted. Even after restarting at 7:30 AM, the 6 hours I was asleep the code did not finish for size 9 or 10. I got it to finish once for size 9, but this was in the testing phase and I did not gather the data for the graphs at this time. There is a huge leap in computing time for any sizes above size 8 as you can see from the orange bars in the graphs.

My results from running the A* heuristic look like the following graphs:

### Graph 1

Compares the nodes exppanded along with the average cost of the path found for each different search algorithm.

![image](https://user-images.githubusercontent.com/66328517/97049910-746d1080-154a-11eb-9744-65b09bd41abd.png)

You can see the huge exponential leap for the number of nodes expanded between just 7 and 8 nodes in the bar graph. The line graph represents the average cost of the path found. Most of the algorithms find a path with similar cost, but hill climbing cost is more due to the nature of how hill climbing takes many steps and may not be optimal. 

### Graph 2

Compares CPU time and wall time for each of the search algorithms

![image](https://user-images.githubusercontent.com/66328517/97050026-a67e7280-154a-11eb-93a9-8b59a739b5eb.png)

We can tell by this second graph that the difference in CPU and Wall time is not significant. The alorithms are not interrupted when they start, they just finish all the way through in one sitting so the times are almost equivlent. Simmulated anneling, random edges, and genetic algorithms all take very very small amounts of time and run very fast. UCS and MST has been the algorithm that keep my code from running larger size graphs. Even on size 10 I could not let it run long enough to complete. 

## Part 2 Graph

Part 2 deals with solving the TSP problem with A* search and a minimum spanning tree heuristic. The goal of this part is to compare the path costs of MST A* and cheapest edges A*. For all of my graphs that I ran, the difference in path cost between the two searches was virtually non existent. Both of these searches are optimal and find the same path.

![image](https://user-images.githubusercontent.com/66328517/97051573-653b9200-154d-11eb-9702-e3c4a3f6b0c7.png)

As you can see, the bar heights of MST A* and cheapest edges A* are the same. This means that the difference in path cost is the same between the searches.

## Part 3 Graphs

Part 3 involves running only local search algorithms With the local searches being so fast, I was able to run genetic, simmulated annealing, and hill climbing on graphs of a larger size than the last two sections. I ran the searches on graphs of size 25, 27, and 30. It was nice to finally be able to run bigger graphs in a reasonable time because UCS and MST was not run.

### Graph 1

Compare CPU time of local search algorithms on large graphs (finally some large graphs run!)

![image](https://user-images.githubusercontent.com/66328517/97052043-45f13480-154e-11eb-881e-032c1f7ddab6.png)

As you can see, simmulated anneling does not have an bars. This is because it is so fast, the scale of the y axis is too large for a bar to appear at y=.002 which is how fast simulated anneal was on larger graphs. This is kinda cool and incredible it runs so fast while theres no chance I could run MST on large sizes like 25,27, and 30. 

The time increase it takes between these three sizes of graphs is not nearly as exponential as the other A* searches. It looks like you could run local searches on larger size graphs if you update the node names to include names of nodes for larger graphs. I used the alphabet to name the nodes and there are only 26 letters in the alphabet, so for anything more than 26 nodes, I added node names "AA", "BB", "CC", and "DD' to be able to get a 30 node labeled graph. This technique could continue for more nodes, but the code would have to be edited to include "EE","FF", ect.

### Graph 2

The idea of this final graph is to compare the difference in total cost for MST A* and the local search algorithms. Because I could not get MST A* to run on larger graphs of size 25,27, and 30, we have to go back to comparing graphs of size 5,7, and 8. :( 

![image](https://user-images.githubusercontent.com/66328517/97054932-bfd7ec80-1553-11eb-9094-d24cc0abc221.png)

In this graph you can see that genetic and simmulated anneling algorithm come pretty clost to the optimal MST A* path cost. Hill climbing seems to not do very well in estimating the path cost, perhaps bcause it is not optimal every time. You may be able to get the cost closer to MST A* by doing more random restarts. Simarlly with genetic algorithm, you may still be able to lower the delta by running more iterations. Simmulated anneling does very well at estimating path cost, but like the other two algorithms, as the node size goes up, the difference in path cost also increases.

# Conculsion

This project was actually very intersting to run and look at the time and path cost results. Using the AI:MA code took awhile to understand, but after some tinkering, I think it works pretty well. It is dissapiointing not to be able to get MST A*, or any A* search, to run on larger graphs, even after letting it run overnight. Perhaps if I were to attempt this project again, I wouldnt use Google CoLab and would set up an enviroment on my PC. Using Google CoLab runs my code on the Google virtual machines, which was problematic because they time you out occationally for no understood reason, so my size 10 graphs never completed even after 6 hours of runtime. 

Even though I couldnt get the larger graphs to complete, you can see the incredible logistic increase in the number of nodes expanded between graphs of size 5,7, and 8. With the large jump between sizes 7 and 8, one could understand why size 10 takes so long to run just due to the incredible amount of nodes being expanded. 

### Video Running of Code

Here is a link to a youtube video I uploaded for the requirement of showing I can run my code on my PC.

# Code 

I have included all the code I needed for this project in the repo. It includes:
  * search.ipynb   
    * Has all of the functions and code needed to run the search algorithms
  * graph.ipynb
    * Has all the graph creation using pandas and matplotlib
  * .json files 
    * Comma delimited fies wit all the data I generated from running the search code. 
  

