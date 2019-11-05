# Introducing DSE Graph Frames
This repository serves as an accompaniment to the Introducing DSE Graph Frames which discusses the basic functionality available in DSE Graph Frames. 

Contributors: Artem Aliev originally copied from [here](https://github.com/datastax/graph-examples/tree/master/dse-graph-frame)

## Objectives

* To demonstrate the basic usage of DSE Graph Frames as discussed in the accompanying blog post
  
## Project Layout

* [friends-graph.groovy](friends-graph.groovy) - The schema and data that needs to be added to the graph for the following examples
* [Spark-shell-notes](Spark-shell-notes.scala) - A file that contains commands to copy and paste into Spark Shell
* [com.datastax.bdp.graphframes.example](/src/main/scala/com/datastax/bdp/graphframe/example) - The directory that contains the two Scala files needed for the Streaming example

## How this Sample Works
A detailed description of how this code works is available at the accompanying blog post [Introducing DSE Graph Frames](https://www.datastax.com/blog/2017/05/introducing-dse-graph-frames).

## Setup and Running

### Prerequisites
The prerequisites required for this application are:

* Scala 2.11
* A DSE Cluster with Graph and Analytics enabled

### Running
To begin working with this sample you first need to create a graph and add some data so that we have something to work against.  
The easiest way to accomplish this is to run the [friends-graph.groovy](friends-graph.groovy) script from Gremlin Console.
In order to run this script you can run the following command from one of the nodes in the cluster:

`dse gremlin-console -e friends-graph.groovy`

By running this script the following will happen:

* A graph with the name of `test` will be created
* A schema will be created for the `test` graph
* Three vertices and four edges will be added to the graph

Once this script has completed we now have a populated graph to use for the remaining queries.

#### Spark Shell
For the majority of the blog post you will need to be running Spark Shell to copy and paste the commands.  To
launch Spark Shell use the following command from one of the nodes in the cluster:

`dse spark`

To paste multi-line statements into Spark Shell use the command below:

`scala> :paste`

This will allow you to copy and paste multi lines into the shell.  To exit this mode and execute the commands you use Ctrl-D.

#### Streaming Example
One of the examples discussed in the blog post is on how to use Spark Streaming with DseGraphFrames.  To try this we need
to build the code under the `/src` directory using the following command:

`sbt package`

Once this has successfully built we submit it to Spark using the command from one of the nodes in the cluster:

`dse spark-submit target/scala-2.11/dse-graph-frame\_2.11-0.1.jar`




