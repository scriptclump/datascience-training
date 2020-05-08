# Hadoop Distribution File System:
NameNode: MetaData of the file
DataNode: Content of the actual file

## HDFS Replication
Replication the important files more datanodes. by default the replication factor is 3. Same Datanode can't have the duplicate files.

## HDFS Design & Limitation:
It's good only if you are using for hugh data. Data latency will be there. It is not good for smaller files. Hdfs will work with normal hard disks.

## HDFS Files Reading & Writting:
Client->NameNode->Temp entry on NameNode->Write on NameNode if is acting as DataNode->Write on the closet DataNode->return to client->Replication of data starts->client to NameNode->NameNode confirms with DataNode

## HDFS Backup & failover
NameNode stores at Disk & RAM. Disk content two files (Ondemand)Namespace image & Edit logs.
To make the namenode resilient, HDFS keep two namenodes main & standby. Zookeeper helps to switch from one to another.
In HDFS Federation, we have multiple namenodes containing parts of metadata.
Mount table is not a service. It is a file kept along with and referred from the HDFS configuration file. The client reads mount table to find out which folders belong to which namenode.

## Ambari
A dashbaord where you can see the list of NameNode, DataNode, CPU cores & other information in detail.

## Hue
Hue is required to upload the files on HDFS. HDFS file permission is same as Unix file permission. Home directory starts with /user/

## Copy the file from local to HDFS using console
hadoop fs -copyFromLocal FILEPATH or
hadoop fs -put FILEPATH
hadoop fs -cat FILEPATH

## Where are the blocks
hdfs fsck -block -location -rack -files FILEPATH

## Change the replication factor of file
hadoop fs -setrep 1 FILEPATH 
hadoop fs -setrep -w 1 FILEPATH (Wait till the process)
hadoop fs -setrep -w -R 1 FILEPATH (Recursive)
