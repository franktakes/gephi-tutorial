# Gephi Tutorial for Graph/Network Visualization
Last updated Summer 2024 for Gephi version 0.10.1

## About this tutorial
This tutorial provides an introduction to [Gephi](https://gephi.org), an open source tool for visualizing graphs / networks.
It is commonly used for data analysis and research in, e.g., (social) network analysis, complex networks / network science and data science. 
The tutorial was originally written as part of the first week lab session of the [Social Network Analysis for Computer Scientists](https://liacs.leidenuniv.nl/~takesfw/SNACS/) semester course of 6 ECTS in the [MSc Computer Science](https://www.universiteitleiden.nl/en/education/study-programmes/master/computer-science) programme of [Leiden University](https://www.universiteitleiden.nl/en). 
While intended as a companion for an introductory network science lecture, the tutorial is by now likely useful for any data-savvy researcher or practitioner. 
All credit for the Gephi tool itself goes to the original authors.

Throughout the tutorial, you will see **Task**, followed by an instruction. Such an instruction corresponds to something the student is expected to conduct and practice before continuing. 

### Prior knowledge 
The tutorial assumes familiarity with [CSV files](https://en.wikipedia.org/wiki/Comma-separated_values) and their manipulation. Indeed, the tutorial is, comparatively, rather data-centered. 
Conceptually, it is assumed that at least some exposure to common network analysis concepts such as nodes, edges, degree, centrality and community structure has taken place. 
Still, without understanding these concepts in detail, it should be possible to follow the tutorial and enjoy the beauty of networks and their visualizations.

### Referencing
Do you want to reference this tutorial? Please use the following format:
* Frank W. Takes, Gephi Tutorial for Graph/Network Visualization [online], https://github.com/franktakes/gephi-tutorial, 2024.

### Index
* [Part 0: Installation](#part-0-installation)
* [Part 1: What do we see?](#part-1-what-do-we-see)
* [Part 2: A first visualization of a network](#part-2-a-first-visualization-of-a-network)
* [Part 3: Data laboratory](#part-3-data-laboratory)
* [Part 4: A real-world network visualization](#part-4-a-second-real-world-network-visualization)
* [Part 5: Exporting a network visualization](part-5-exporting-a-network-visualization)
* [Part 6: Advanced features](#part-6-advanced-features)

## Part 0: Installation

* [Download Gephi](https://gephi.org/users/download) 0.10.1 from the Gephi website.
* Install Gephi on your Windows, Linux or MacOS device; be sure to choose English as display language when asked, so that instructions match with your local installation.
* After installation, start Gephi and close the Welcome window that pops up.
* Use a [mouse](https://en.wikipedia.org/wiki/Computer_mouse) to more easily control the tool.

## Part 1: What do we see?

Gephi has 3 main "Screens", each with its own functionality: 
* Overview: network visualization, data filtering and computation of network measures.
* Data Laboratory: network data import, export, inspection and manipulation.
* Preview: to export a final version of a visualization, for example to a vector graphic PDF.

![Gephi-threetabs](https://github.com/franktakes/gephi-tutorial/blob/main/img/gephi-threetabs-annotated.png?raw=true)

_Figure: Gephi, with the three main Gephi screens highlighted._

For now, we start in the "Overview" screen, which should have several subwindows: "Appearance" and "Layout" on the left, "Graph" in the middle and "Context", "Filters" and "Statistics" on the right. 
On some installations these subwindows might not all be visible; you can use the "Window" menu option on top to make these particular subwindows visible for you, and if necessary drag them to the right location. 

**Task 1**: Install Gephi on your machine and make sure you see the correct subwindows in the "Overview" tab.

## Part 2: A first visualization of a network 

In this part of the tutorial, we will make a first network visualization.

### Part 2.1: Loading (random) data and saving a project

A first step is to make sure that there is data to visualize. 
Custom real-world data import and export will be discussed in [Part 3: Data laboratory](#part-3-data-laboratory). 
For now we generate some **random network data**. 
Press "File", "Generate", "Random Graph". By default, a network with 50 nodes in which a fraction of 0.05 of the edges are present, is generated after pressing "OK". 
The nodes are initially randomly placed, and links will be directed (notice the arrows). 
Basic statistics are presented on the top right, in the "Context" subwindow. 

First things first: similar to working in a text document, you may want to regularly save your work, and perhaps store intermediate versions under a different name as you progress. 
Save your project as a .gephi file. 
Go to "File", "Save" and choose a suitable filename and location. 

**Task 2.1**: Generate a random graph according to parameters of your choice, and save the network to a file. 
Close Gephi and load the saved network file again.

### Part 2.2: Visualizing the network 

Now that you have loaded network data, it's time to make the visualization look nice, rather than random. 
On top of the bottom left "Layout" pane, select "ForceAtlas 2" from the dropdown menu, and press "Run". 
Once the visualization has converged, press "Stop". You should see a visualization similar to the figure below. 

![Gephi-visualization](https://github.com/franktakes/gephi-tutorial/blob/main/img/gephi-random-visualization.png?raw=true)

_Figure: Visualization of a random directed graph with 50 nodes_

You can play around with parameters such as "Scaling" to disperse the nodes more. 
Notice that this entire layout process changes nothing more than the (x,y) position of the nodes. 
By choosing "Random Layout" as the visualization algoritm, nodes can be put back at a random position. 
Finally, note that you can zoom in on the visualization itself using your mouse's scroll wheel (or laptop touchpad equivalent thereof). 

**Task 2.2**: Play around with some different visualization algorithms and their parameters. 
Extra: generate larger graphs and observe how algorithm complexity of for example the Fruchterman-Reingold algorithm starts to play its parts.  

### Part 2.3: Node and edge size and color

When the layout is satisfactory, we can start to spice up the visualizaiton and move away from black-and-white dots and lines. 
Using the top left box "Appearance", almost everything about the visualization can be changed; the box looks small but offers a lot of possibilities. 
Corresponding to the four red boxes in the figure below, it is possible to change:
* A: What we are changing properties of, with the options being the nodes or the edges (2 options).
* B: What visual property we are changing, the options (in order) being: color, size, label color and label size (4 options); we discuss labels in [Part 2.4: Labels](#part-2-4-labels).
* C: How the change should be made (3 options):
	* Unique: every node/edge gets the same visual property value.
	* Partition: we set the visual property value based on some attribute of the node for which several categorical attribute values can exist.
	* Ranking: we set the visual property value propertional to some numeric (possibly continuous) attribute of the node.
* D: How we actually set the value (screen may change depending on choices made for A, B and C).
  
 It is worth noting that a total of 2 x 4 x 3 = 24 visual aspects can be changed.

![Gephi-appearance](https://github.com/franktakes/gephi-tutorial/blob/main/img/gephi-appearance-annotated.png?raw=true)

_Figure: The "Appearance" subwindow to change node and edge (label) color and size_

**Task 2.3a**: Set the node size proportional to a ranking based on degree (number of connections), and node color based on indegree (number of incoming connections). 
Your visualization may look something like the figure below.
(For now, ignore the "Partition" tab; it will be discussed in [Part 4: A real-world network visualization](#part-4-a-second-real-world-network-visualization).)

**Task 2.3b**: Node size is proportional to the size of the Layout space; experimentally confirm how a larger value for the "Scaling" parameter of the "ForceAtalas 2" algorithm will require a larger minimal and maximal value for node size. Play with different node color schemes (through the icon to the right of the colored bar in the "Ranking" tab).

![Gephi-visualization](https://github.com/franktakes/gephi-tutorial/blob/main/img/gephi-visualization.png?raw=true)

_Figure: Stylized visualization of a random directed graph with 50 nodes_

### Part 2.4: Labels

The label of a node (or edge) is a readable description of the node (or edge). In a social network it can be someone's real name, rather than numeric ID.
Label visibility can be enabled using the "Show Node Labels" button in the set of icons at the bottom of the Graph subwindow (button G in the figure below).
One or more of the data attributes of the nodes are then shown as textual label; button Q allows one to set which attributes this pertains. 
By default, the "Label" node attribute is used, which in case of the random graph is equal to the ID of the node.

![Gephi-bottom-buttons](https://github.com/franktakes/gephi-tutorial/blob/main/img/gephi-graph-bottom-buttons-annotated.png?raw=true)
_Figure: Buttons at the bottom of the Graph pane_

Icon A resets the viewport such that the entire network is visible; buttons B-D reset certain visual properties. Label G through Q adjust various meaningful aspects of the labels, such as their size, font and color, as well as provide the opportunity to adjust properties and visibility of the edges. 

**Task 2.4**: Enable node labels, and play around with the various buttons A-P and observe what happens to the visualization. 

## Part 3: Data laboratory

Next, we will learn how to modify the network data underling a Gephi visualization.

### 3.1 Modifying the network data 

We turn to Gephi's second main window, being the Data laboratory. For a random graph, it should look like the figure below.

Here, the data behind the network can be inspected. On the top left, it is possible to switch between "Nodes" and "Edges"; which brings up the node list or the edge list in the data table below. 
A node is always identified by a (typically numerical) "Id", and so is an edge, however, more importantly, an edge is defined by a "Source" and a "Target", of which the values refer to the Id of a node. 

The Data labaratory can be used to manually change the data behind the graph, adding, removing and modifying the nodes, edges and their attributes. 
Adding nodes and edges can be done by using the respective buttons on top of the data table, and modifying one particular node or edge can be done by right clicking and selecting edit-option.
Changes the the columns or column-wise modifications for all or multiple rows, can be effectuated using the buttons at the bottom of the data table.

**Task 3a** 

Create a new graph in which you represent your direct family members as nodes, and the connections between them as edges. Add a node attribute "Label" for their name, as well one for their "Age". You can also choose an edge attribute of choice (for example, a binary attribute indicating whether the two family members physically live together). When your data is complete, visualize the graph in the "Overview" tab; be sure to enable labels and choose meaningful colors for the nodes and edges. 

### 3.2 Importing data 




## Part 4: A second real-world network visualization

## Part 5: Exporting a network visualization

## Part 6: Advanced features


Based on the tutorial above, you will likely develop your own iterative process in which you import data, and then play with layout algorithms, filters and statistics, before exporting a finalized network visualization. 

Many more things are possible with Gephi, often implemented through [Gephi Plugins](https://gephi.org/plugins/#/). 

- [GeoLayout](https://gephi.org/plugins/#/plugin/geolayout-plugin) to visualize nodes at particular coordinates on the world map often used together with [MapsOfCountries](https://gephi.org/plugins/#/plugin/mapofcountries) to show the outline of the world, a country or region. 

- [MultimodeNetworksTransformationPlugin](https://gephi.org/plugins/#/plugin/multimode): a plugin for network projection, i.e., for modifying a network with multiple types of nodes (as defined by particular categorical node attributes), i.e., multipartitie networks, to unipartitate networks that can be meaningfully analyzed using Gephi. 

- The [BoundingDiameters](https://gephi.org/plugins/#/plugin/boundingdiametersssuite) algorithm for quickly computing the exact diameter (longest shortest path length) of a network. 

- The [Leiden Algorithm](https://gephi.org/plugins/#/plugin/leiden-algorithm-gephi-plugin), a community detection algorithm similar to "Modularity" discussed above, but solving a number of bugs and generally attaining higher quality partitionings of the network. 

Thank you for walking through this tutorial! I hope you enjoyed it.

See details on top on how to [reference](#referencing) this tutorial. 
Feedback and suggestions are welcome (via Github "Issues"); also (and especially!) from students.

------------------------------------------------------------------------------------

OLD:


## Part 3: Data laboratory

## Part 4: A second real-world network visualization

filtering 

advanced algo's, statistics (such as degree give results but it's about data) 
communities 



## Part 5: Exporting a network visualization

preview
create some export 
