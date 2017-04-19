# extra10
Simple C++ program illustrating a graph data structure

## Graphs

### Introduction to Graphs - [YouTube Link](https://youtu.be/gXgEDyodOJU)
* A tree is a special kind of graph
* Graph definition:
	* A graph G is an ordered pair of a set V of vertices and a set E of edges
		* _G = (V,E)_
	* Ordered pair:
		* _(a,b) =/= (b,a) if a =/= b_
	* For reference, and unordered pair:
		* _{a,b} = {b,a}_
	* For a set of 8 vertices, the unordered set of vertices can be defined as:
		* _V = {v1,v2,v3,v4,v5,v6,v7,v8}_
	* Edges can be defined as
		* __directed__
			* Can refer to a tree where there one end is an origin and another end is a destination
			* Draw an arrow with a head to point to the destination
			* Can be represented as an ordered pair where the first element is the origin and the second element is the destination
			* Can have two directed edges. For example:
				* u -> v and v -> u are the ordered pairs (u,v) and (v,u)
		* __undirected__
			* The connection is two way (bidirectional)
			* Represented as an unordered pair
				* {u,v}
	* For a set of 8 vertices, the unordered set of edges can be defined as:
		* _{ {v1,v2}, {v1,v3}, {v1,v4}, {v2,v5}, {v2,v6}, {v3,v7}, {v4,v8}, {v7,v8}, {v5,v8}, {v6,v8} }_
	* Typically, graphs contain either directed or undirected edges.
	* Graphs can have both directed and undirected edges, but this program will not implement this.
	* A graph with directed edges is called a __directed graph__ or __Digraph__
	* A graph with undirected edges is called an __undirected graph__
* Many real world systems and problems can be modeled using a graph
* Graphs can be used to respresent any collection of objects having some sort of pairwise relationship. Here are a few examples:
	* A Social Network (Facebook) can be represented as an undirected graph
		* People would be modeled as nodes and a friend relationship is mutual
	* Interlinked web pages on the World Wide Web can be represented as a digraph
		* URL pages would be modeled as nodes in a graph and a link to another page would be modeled as a directed edge
			* If Page A has a link to Page B, then it is not necessary that Page B has a link to Page A
		* Web-crawling is basically __Graph Traversal__ or in simpler words, the act of visiting all nodes in a graph
* Weighted vs unweighted graphs
	* Sometimes in a graph, all connections can not be treated as equal. Some connections can be preferable to others. For example:
		* An intercity road network with cities being modeled as nodes and highways/freeways being modeled as undirected edges
		* Weights on the edges can be represented as distance in kilometers between cities
	* An unweighted graph can be seen as a weighted graph with all edges having the same weight such as _weight = 1 unit_

### Properties of Graphs - [YouTube Link](https://youtu.be/AfYqN3fGapc)
* To denote the number of elements in a set, we use cardinality of a set
	* _|V|_ -> number of vertices
	* _|E|_ -> number of edges
* Can have some special kinds of edges in a graph. They can complicate working with graphs. Need to take extra care when solving problems.
	* __Self-loop__
		* An edge is called a self-loop or a self-edge if it involves only one vertex. If both ends of the vertex are the same then it is called a self-loop.
		* Can have a self-loop in both directed and undirected graphs
		* An example would be a web page that links to itself such as when on the home page and clicking the home tab refreshes the home page
	* __Multiedge/Parallel edge__
		* An edge is called a multiedge if it occurs more than once in a graph
		* Can have a multiedge in both directed and undirected graphs
		* An example would be a graph of cities with flights as edges. There may be different flights offered from different airlines having different weights represented as costs of flights or flight numbers
* If a graph does not contain self-loop or multiedge properties then it is called a __simple graph__
* Given number of vertices in a simple graph (graph with no self-loop or multiedge), what are the miniumum number of edges?
	* 4 vertices
		* _V = {v1,v2,v3,v4}_
		* _|V| = 4_
		* It is acceptable if there a no edges. It would still be a graph
			* _E = 0_
	* So miniumum number of edges in a graph is 0
* If a simple graph is directed, what is the maximum number of edges?
	* if _|V| = n_ then, _0 <= |E| <= n(n-1)_
* If a simple graph is undirected, what is the maximum number of edges?
	* if _|V| = n_ then, _0 <= |E| <= (n(n-1))/2_
* Number of edes in a directed graph can be very large compared to the number of vertices in a graph
	* if _|V| = 10_, then _|E| <= 90_
	* if _|V| = 100_, then _|E| <= 9900_
	* Maximum number of edges would be close to squared the number of vertices
* A graph is called __dense__ if the maximum number of edges is close to the square of vertices
* A graph is called __sparse__ if the number of edges is close to the amount of vertices
* In working with graphs, many decisions are made based on whether the graph is dense or sparse
	* For a dense graph, typically use an adjacency matrix
	* For a sparse graph, typically use an adjacency list
* Paths in a graph
	* __Walk:__ -  Walk and path can be used as synonyms in different computer science materials. It is a sequence of vertices where each adjacent pair in the sequence is connected by an edge 
		* Assume there are 8 vertices labeled from A through H
		* The sequence of vertices <A,B,F,H> is a path in the graph
	* __(Simple) Path:__ - if no vertices (and thus no edges) are repeated
		* In graph theory there is some inconsistency in the use of the term __path__. Most of the time when path is referenced it is in context of a __simple path__
		* If repetition is possible then use the term __walk__
		* So a path is basically a walk in which no vertices or edges are repeated
	* __Trail:__ - vertices can be repeated, but edges can not be repeated
	* __Closed walk:__ - starts and ends at same vertex
		* Length of walk must be greater than zero
	* __Simple Cycle:__ - no repetition other than start and end vertices
		* Basically, it is a __closed walk__ with no repetition besides start and end vertices
	* __Acyclic Graph:__ - a graph with no cycle
* Strongly Connected Graphs:
	* Graph is directed (digraph)
	* if there is a path from any vertex to any other vertex

### Graph Representation: Edge List - [YouTube Link](https://youtu.be/ZdY1Fp9dKzs)
* Space Complexity
	* Vertex List is _O(|V|)_
	* Edge List is _O(|E|)_
	* So space complexity is _O(|V| + |E|)_
* Time Complexity
	* Operation:
		* Finding adjacent nodes
			* Need to perform a linear search to scan the entire list
			* _O(|E|)_
			* Very costly
		* Check if given nodes are connected
			* Need to perform a linear search to scan the entire list
			* _O(|E|)_
			* Very costly
* So in summary, the number of edges in a graph can be very large close to square the number of vertices. Need to find a way to keep time complexity down using _O(|V|)_

### Graph Representation: Adjacency Matrix - [YouTube Link](https://youtu.be/9C2cpQZVRBA)
* Store the edges in a 2 dimensional array or matrix