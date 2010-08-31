Script to generate connected graphs
===================================

A tool to generate graphs, based on the [Barabási–Albert (BA) model](http://en.wikipedia.org/wiki/Barab%C3%A1si%E2%80%93Albert_model).  You can use this to generate test data that resembles relations on a social graph.


Usage
-----
The script takes three argumens
* -n  Number of nodes in the graph
* -m  How many edges to create for each node
* -s  The format string
* -d  If present, will at the end print the generated distribution (the distribution of node degrees)

Note that the script always generate edges in pairs,  a->b, b->a.  So a -m value of 10, will actually
create a network whose average # of edges per node is 20.

Use -s to specify your output format,  most likely some sort of CSV to import into your DB; format is the
one used for python's string formatting.

Example
-------

Runnning time is acceptable for medium-sized networks. On a modest notebook, you can expect
 
	time python ba_graph.py -m 50 -n 200000 -s "{a};{b}" -d > data.csv
	real    20m41.900s
	user    20m30.190s
	sys     0m3.980s

that is 20' to generate 200000 nodes and 20000000 (twenty million) edges.

For the above example, the resulting node degree distribution is:

![distribution](raw/master/doc/distribution.png)
(note the log10 scale)
 
Have fun!
