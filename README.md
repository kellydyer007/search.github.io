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
 
### Goal

The goal of using all this code is to randomly generate graphs with different number of nodes, 5, 8, 10, 15, and run all kinds of search algorithms on the generated graphs. Then I can analyse the path costs and time it takes for algorithms to run to determine the differences in search approach. Each search is done in batches of 30 graphs, then we can take the average of the batches to get a pretty good aproximation of the search preformance. 
    

Once all the searches are ran and the data is collected, I uploaded a csv file with all the data into a Pandas dataframe which looks like below.
  
![image](https://user-images.githubusercontent.com/66328517/96971557-49030b00-14e3-11eb-82cf-1184dbab9da7.png)

This dataframe is then grouped by search technique and how many nodes are in the graph. The analysis of the graphs presented next are grouped this way. 

## Part 1 Graphs 

For part 1 we were asked to implement A* on random TSP problem using three heuristic:
  * h(n)=0 which is just uniform cost serch
  * Random Edges which grabs edge lengths connected to the node, adds them together and used for h(n)
  * Cheapest Remaining Edges which uses cheapset remaining edges for h(n)

My results from running the A* heuristic look like the following graphs:

### Graph 1

Compares the nodes exppanded along with the average cost of the path found for each different search algorithm.

![image](https://user-images.githubusercontent.com/66328517/97049910-746d1080-154a-11eb-9744-65b09bd41abd.png)

### Graph 2

Compares CPU time and wall time for each of the search algorithms

![image](https://user-images.githubusercontent.com/66328517/97050026-a67e7280-154a-11eb-93a9-8b59a739b5eb.png)



```markdown


  code goes here
```


