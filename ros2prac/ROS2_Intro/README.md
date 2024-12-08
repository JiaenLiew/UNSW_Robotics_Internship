# <ins>Summary notes on ROS 2 Introduction from husarion:</ins>
## <ins>**Topics and Nodes**</ins>

A Node is a process or executeable that performs a specific task such as handling devices or computing algorithms. A Node can also subscribe and/or publish messages to and from topics.

A Topic is a communication channel used to exchange information between nodes. Topics also have a defined message type and a unique name, this is to ensure that nodes know where and what type of information they are publishing and subscribing to.

This model of communication between the Nodes using the Topics is known as the publisher-subscriber communication model, and this form of communication is asynchronous. The publishers and subscribers do not wait for each other to be ready to send or receive messages. There are pros and cons associated to this model of communication such as:

<ins>**Pros**</ins>:
1. The Nodes are independent of each other and thus if one fails it does not block other Nodes from publishing or subscribing data even if they are directly related.
2. Data can be queued such that if a Node is too busy with current information it can process queued up information in the order that it is received.

<ins>**Cons**</ins>:
1. With decoupled timing in messages due to queued up data of different times in multiple Nodes it can be hard to debug.
2. Since messages are expected into the queue in order by each Node, this can cause issues due to poor latency as messages may arrive out of order.

A physical way to visualise this is through thinking Nodes as the parts of the robot such as sensors and actuators and topics as the wires that carry information between them.

## <ins>**Services**</ins>

Another model of communication Ros has is a client-server or a request-response model through services. This model is a synchronous two-way communication between nodes meaning that it would only send data to other nodes when specifically called. Just like a Topic the service has its own defined message type which defines the structure of the request and response. A Node can either provide a service (Service Server) by defining its logic and sharing it with other Nodes (Service Clients) through the service.

<ins>**Pros**</ins>:
1. Services are good for providing immediate responses to one time interactions such as toggling behaviours as its model is both synchronous and deterministic
2. Simpler and more lightweight and thus is much easier to implement for isolated tasks.

<ins>**Cons**</ins>:
1. Delays can occur if the server is slow as information will only occur when a client asks and thus the client would need to wait for a response from the server.
2. Requests can only be processed one at a time bouncing messages between the client and the server as there is no queue like that in the Topic model to slowly process data over time.

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
2. Publisher count (Helps to verify that intended nodes are publishing the data)
3. Subscriber count (Helps to confirm whether nodes are receiving data from the topic)