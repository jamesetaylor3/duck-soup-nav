# duck-soup-nav

duck-soup-nav is a project that finds the shortest path between two points of longitude and latitude using data for road networks. It uses the A* searching algorithm to find the special route and a RTree to find the nearest node to a pair of coordinates. I'll explain the algorithmic decisions I made more in depth as the project progresses. Eventually, I hope to make this an api where duck-soup-nav takes https post requests and returns the path.

### Build

duck-soup-nav has no dependencies, so you can either compile all of the files together or use the makefile. To use the makefile, run the following command to build. It will create the target binary in `build/bin/ducksoup`

`$ make all`

Run `$ make help` to check out the other things to do with the Makefile!

### Run

To be able to run this, you must provide the road network data as .txt files. For my development so far, I am using Calfornia roads. Essentially, the nodes text file must have a new line for each node where the node id, longitude and latitude are separated by a space. The node is must start at 0 and increment by one each line. [This](https://www.cs.utah.edu/~lifeifei/research/tpq/cal.cnode) is that particular file I am using for nodes right now. [Here](https://www.cs.utah.edu/~lifeifei/research/tpq/cal.cedge) is the file for edges.

Currently, duck-soup-nav only runs a test between two random points I chose. I'll make it more usable soon, so bear with me! To run the test, run the following make goal, or execute the binary with the nodes and edges files in main directory as `cal_node.txt` and `cal_edge.txt`.

`$ make run`

Also, unfortunately, things are a bit slow right now if they points to compute the route between are far away! Computing A* is not easy, and I have not experimented with finding a good heuristic yet or possibly using a different algorithm than A* search. Optimizations will come soon! :)

### Credit

Special thanks to the [researchers](https://www.cs.utah.edu/~lifeifei/SpatialDataset.htm) at University of Utah that provided the database for the road networks. Their creation is awesome!