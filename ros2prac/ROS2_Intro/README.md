# <ins>Summary notes on ROS 2 Introduction from husarion:</ins>
## <ins>**Ros2 run**</ins>
**Syntax:** ros2 run <package_name> <node_type> [--ros-args options]

1. **<package_name>:** Name of the ROS2 package containing the node to be executed
2. **<node_type>:** Name of the node's executable
3. **[--ros-args options]:** Optial arguments to pass into the executable

## <ins>**Ros node list**</ins>
**Syntax:** ros2 node list

This command lists all nodes that are currently running in the system.
The command should be run on a different terminal.

## <ins>**Ros node info**</ins>
**Syntax:** ros2 node info <name_of_node>

This command provides information on the node such as:
1. Subscribers
2. Publishers
3. Service Servers
4. Service Clients
5. Action Servers
6. Action Clients

## <ins>**Ros topic list**</ins>
**Syntax:** ros2 topic list

Just like ros node list rost topic list lists out the topics currently registered in the system


## <ins>**Ros topic info**</ins>
**Syntax:** ros2 topic info <name_of_topic>

This command lists out the named topic's info such as:
1. Type (Displays the type of messages the topic publishes and/or subscribes to)
2. Publisher count (helps to verify that intended nodes are publishing the data)
3. Subscriber count (helps to confirm whether nodes are receiving data from the topic)