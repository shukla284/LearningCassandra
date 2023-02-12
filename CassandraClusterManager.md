# Cassandra Cluster Manager

Cassandra is distributed and decentralized kind of database whose full potential can be unveield through the distributed environment. This means that having something like cluster to test out the things when we are making any educated guesses about the functionality of the system is quite more helpful to be more deterministic of the behaivour of the database. 

So to cater that very thing, for testing and developing on cassandra on the developer system is provided CCM tool.This is quite helpful when we are working on the learning basis. CCM is quite handy, easy to use. While the setup might be an issue. 

## Installation of CCM 

- With latest python version at the current time CCM might be failing on Ubuntu. We can simply follow the instructions on the [official repository](https://github.com/riptano/ccm) for this purpose. To describe in brief cloning the repo and simply running the setup file to install the essesntials works. 
- An important thing to note is that output might be not as expected with the current python version 3.10, there were some errors due to some list in python, list index out of range. Important thing to note is that we might need to have some different version for that purpose. Describing the process which worked for my Ubuntu system. Please check for more information on the tools before using in case that is fine to work with. 
- The goal was to create a python version on the same local console without disturbing the existing python version since we already did some mappings for the current python to work correctly within the system. 
- For this pupose, I came across [this answer](https://stackoverflow.com/questions/59549829/how-do-i-downgrade-my-version-of-python-from-3-7-5-to-3-6-5-on-ubuntu) on stack overflow. Where one such python tool is introduced and described. 
- Simply have this tool according to the instructions provided. And go to the correct directory which we want to work with, and change the local python for that folder to the version 2.7. Run the command for create again now the things should work fine. One thing that might create problem is the ports. 
- As we already know the cassandra needs 3 ports for running correctly. Please ensure these ports are free CCM might throw error for the required port if not found free. 
- Use command for example if 9042 is not free and we are getting some exceptions due to this, ```lsof -t -i:9042``` and if there is an output then it would be the <process_id> of the process which is currently occupying that port. if this is not intended and we are not intentionally running something on this port prior to CCM then simply kill that process using ```kill -9 <process_id>```, here the <process_id> is the result of the above command. 
- Now simply try to run the things, it should be fine to run with. Plese note that CCM is not atomic kind of command, that its different parts may fail and there might be the case that cluster nodes are initialized or created but are not going up, this might be issue when we are trying to run command for correctness. 
- Another thing which might create issue is JAVA_HOME environment variable whose value might not be set in the bash, which could create issue while runing the cluster, CCM requires at least for running, so specify that using the bash file by adding these lines to ```~/.bashrc``` file 
~~~shell
export JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64"
export PATH=$PATH:$JAVA_HOME/bin
~~~

- Please turn the current cluster down using ```ccm remove``` which will stop the cluster nodes. 
- If everything goes fine in the above step then this should result into ccm clusters working correctly, checking this through ```ccm status``` should show all of nodes up, this might take some time though to start the nodes. 
- One of the ways to run the above using minconda is described in this ```article```.

## CCM Important commands
- ```ccm list``` for listing the currently running clusters. 
- ```ccm status``` for checking the currently running nodes and what are the status of those. 
- ```ccm stop``` For stopping all of the nodes. 
- ```ccm <node_id> show``` for showing the information for each of the node. 
- ```ccm remove``` for removing all of the nodes from cluster and deleting all of the data related to it. 

