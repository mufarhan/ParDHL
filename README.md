# Parallel Dynamic Highway Cover Labelling (ParDHL)

This is an implementation of the paper<br/>

Muhammad Farhan, Qing Wang, **[Efficient maintenance of highway cover labelling for distance queries on large dynamic graphs](https://link.springer.com/content/pdf/10.1007/s11280-023-01146-2.pdf)**, The World Wide Web Journal.

## Sample data format
The format of the dataset file is as follows: <br/>
Line 1 : |V| |E| <br/>
Line 2 : vertex_u deg_u v1 ... vn, where v1 to vn are neighbors of u. Note that the vertex id are from 0 to (V-1), where V is the number of vertices. There are no self loops in the graph, i.e., no edge from any vertex to itself. 

To see the accepted format for graphs, updates and query pairs, you may refer to the Sample Data folder. After the test inputs are ready, please use the following commands to test ParDHL.

## 1 - Compile source files

$ g++ -O3 -std=c++11 -pthread main.cpp -o run

## 2 - Construct Labelling
./run construct_labelling @1 @2 @3<br/>
@1: name of the dataset<br/>
@2: number of landmarks<br/>
@3: file to store labelling

Example:<br/>
./run construct_labelling graph.txt 20 graph_labelling

## 3 - Update Labelling
./run update_labelling @1 @2 @3 @4 @5<br/>
@1: name of the dataset<br/>
@2: number of landmarks<br/>
@3: file to load the labelling from<br/>
@4: file containing updates<br/>
@5: method parameter (0 to test ParDHL or 1 to test ParDHL-)<br/>

Example:<br/>
./run update_labelling graph.txt 20 graph_labelling updates.txt 0

## 4 - Perform distance queries
./run query-dis @1 @2 @3 @4 @5<br/>
@1: name of the dataset<br/>
@2: number of landmarks<br/>
@3: file to load the labelling from<br/>
@4: file containing query pairs<br/>
@5: file to write query results<br/>

Example:<br/>
./run query_labelling graph.txt 20 graph_labelling query_pairs.txt query_results.txt
