# Search Search and more Search

Page created by Kelly Dyer for CMSC 421 Fall 2020 Professor: William Regli
Worked in a group with: 

Purpose: Conduct a science-y like expierement on graph traversal methods relating back to the traveling salesman problem(TSP). The TSP is given a graph, in this case fully connected, what is the shortest path from a starting city to all other cities in the given graph.

# Introduction

  This page is all about searching symmetric, full connected graphs to find optimal solutions for the traveling salesman problem.
  
### Code Used

  I mostly used the python search code given in the Russel and Norvig AI:MA textbook. This consisted of a few classes:\n
    Graph Class: Used along with Node Class to constuct graphs with a given adjancy matrix. 
    Priority Queue: Implemented priority queue.
    Problem Class: Abstract class to define problem subclasses.
    Graph Problem Class: Subclass of Problem where most of the handwritten code is located. The actions and path cost are                 used to get neighbors in the graph at a node. Also contains all the huristics needed for A* search. The heuristics are cheapest_edges, random_edges, primm_mst, and kruskal_mst.
    Search Algorithms: All the search algorithms, except for MST, came from the AI:MA textbook. They are A Star, best_first, uniform_cost, hill_climbing, simulated_anneling, and genetic. 
    
  Outside sources of code that I used were: 
    GeeksforGeeks website: Kruskal and Primm minmum spanning tree implementation (link in code)
    Python-Graph-Gallery website: The shell for the graphs used in analysis section.
    
    
  
![globe](https://user-images.githubusercontent.com/66328517/88014096-13b5de00-caec-11ea-8ce0-b342623ddbee.png)

My dataframe is filled with everything needed and looks as follows:
![image](https://user-images.githubusercontent.com/66328517/88014651-7491e600-caed-11ea-89d6-baf3462519bc.png)

### Data Tidying
  As you can see in my dataframe, the year variable contains a decimal point that represents when the measurement was made. The decimal is not easy on the eyes and hard to understand when beginning to look at the data. So, I decided to seperate out the year into quarters based on this decimal point. This seperates the year into quarters similar to the fiscal year, [0,.25)=Q1 [.25,.5)=Q2 [.5,.75)=Q3 [.75,1)=Q4. Creating a new variable made grouping and understanding the year eaiser. Other than the year, the data was relatively clean and easy to understand. Below you can see the code I used to create the quarters variable and the final dataframe after tidying. 
```markdown
  code goes here
```


