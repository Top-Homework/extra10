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
		* directed
			* Can refer to a tree where there one end is an origin and another end is a destination
			* Draw an arrow with a head to point to the destination
			* Can be represented as an ordered pair where the first element is the origin and the second element is the destination
			* Can have two directed edges. For example:
				* u -> v and v -> u are the ordered pairs (u,v) and (v,u)
		*undirected
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
* 