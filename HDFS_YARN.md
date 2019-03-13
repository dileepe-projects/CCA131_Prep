Hadoop - HDFS & YARN

HDFS - Hadoop distributed file system -> Master - Worker(sends heart beat signal)

Storage Replication factor - default 3.

Namenode(Master) - Datanode(worker - sends heart beat every 3 seconds)

Data stored as block (128 MB default)

Namenodes - Metadata - fsimage, editlog
Secondary node - fsimage + editlog -> checkpoint

Namenode - high end system

Datanode - huge storage capacity

HDFS write -

1. Pipelinesetup: clientnode request namenode for datanode ip addresses
2. client node reaches 1st datanode, 1st datanode reaches second and second reaches 3rd
3. client node writes block to 1st, second copies block from 1st and third copies block from 2nd


Mapreduce

Map -> Splitting, Mapping,Sorting & Shuffling
Reduce -> Reducing
Final result


YARN

Data Processing by YARN - Yet Another Resource Negotiater.

Resource Manager & Node Manager

Resource Manager identifies the blocks of data.

Resource Manager requests the Node Manager to process that data

Yarn processing methodologies- Mapreduce, Spark for in memory computing, giraph for graphs
