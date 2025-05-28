Ex. No: 12E - KRUSKAL’S ALGORITHM FOR MINIMUM SPANNING TREE (MST) IN PYTHON

AIM:

To write a Python program using Kruskal’s Algorithm to find the Minimum Spanning Tree (MST) of a given connected, undirected, and weighted graph.

ALGORITHM:

Input the number of vertices and edges of the graph.

Create a list of edges, where each edge is represented as a tuple: (u, v, weight).

Sort all edges in non-decreasing order based on their weights.

Initialize the parent and rank arrays for union-find operations:

parent[i] = i for each vertex.

rank[i] = 0 initially.

Iterate over the sorted edges and for each edge:

Use the find() function to check the root parents of the two vertices.

If they belong to different sets, include the edge in MST and perform union operation to merge the sets.

Repeat the above step until the MST has V - 1 edges (where V is the number of vertices).

Display the edges in the MST and calculate the total weight (cost) of the MST.

PYTHON PROGRAM
```
from collections import defaultdict

# Class to represent a graph


class Graph:

	def __init__(self, vertices):
		self.V = vertices # No. of vertices
		self.graph = [] # default dictionary
		# to store graph

	# function to add an edge to graph
	def addEdge(self, u, v, w):
		self.graph.append([u, v, w])

	# A utility function to find set of an element i
	# (uses path compression technique)
	def find(self, parent, i):
		if parent[i] == i:
			return i
		return self.find(parent, parent[i])

	# A function that does union of two sets of x and y
	# (uses union by rank)
	def union(self, parent, rank, x, y):
		xroot = self.find(parent, x)
		yroot = self.find(parent, y)

		# Attach smaller rank tree under root of
		# high rank tree (Union by Rank)
		if rank[xroot] < rank[yroot]:
			parent[xroot] = yroot
		elif rank[xroot] > rank[yroot]:
			parent[yroot] = xroot

		# If ranks are same, then make one as root
		# and increment its rank by one
		else:
			parent[yroot] = xroot
			rank[xroot] += 1

	# The main function to construct MST using Kruskal's
		# algorithm
	def KruskalMST(self):

		result = [] # This will store the resultant MST
		
		# An index variable, used for sorted edges
		i = 0
		
		# An index variable, used for result[]
		e = 0

		# Step 1: Sort all the edges in
		# non-decreasing order of their
		# weight. If we are not allowed to change the
		# given graph, we can create a copy of graph
		self.graph = sorted(self.graph,
							key=lambda item: item[2])

		parent = []
		rank = []

		# Create V subsets with single elements
		for node in range(self.V):
		    parent.append(node)
		    rank.append(0)
		     #---Code Here----
		
		# Number of edges to be taken is equal to V-1
		while e<self.V-1:
		    u,v,w=self.graph[i]
		    i+=1
		    x=self.find(parent,u)
		    y=self.find(parent,v)
		    if x!=y:
		        e+=1
		        result.append([u,v,w])
		        self.union(parent,rank,x,y)
		minimumCost=0
		print("Edges in the constructed MST")
		for u,v,weight in result:
		    minimumCost+=weight
		    print("%d -- %d == %d"%(u,v,weight))
		print("Minimum Spanning Tree",minimumCost)
		    

			# Step 2: Pick the smallest edge and increment
			# the index for next iteration
			        
			        #---Code Here----

			# If including this edge doesn't
			# cause cycle, include it in result
			# and increment the indexof result
			# for next edge
			            
			            
			            #---Code Here----

		

# Driver code
g = Graph(4)
g.addEdge(0, 1, 10)
g.addEdge(0, 2, 6)
g.addEdge(0, 3, 5)
g.addEdge(1, 3, 15)
g.addEdge(2, 3, 4)

# Function call
g.KruskalMST()
```

OUTPUT
![image](https://github.com/user-attachments/assets/c9466c6b-9f9e-429f-b6c4-f4574a44bf56)


RESULT

Thus the python program was initialised and executed successfully.
Thus the python program was initialised and executed successfully.
