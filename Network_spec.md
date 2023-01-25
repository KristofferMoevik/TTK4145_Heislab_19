Nettwork specs:

Guarantees about elevators:

What should happen if one of the nodes loses its network connection?
    The other elevators should know if it looses connection. (Heartbeat?). Elevators should be able to run independently if network connection is lost. Try to reconnect. 
    
    How is the order panels connected to the elevators? Over network or not? are there 3 panels? Fikk svar at det er koblet sammen utenom nettet.

What should happen if one of the nodes loses power for a brief moment?
    Orders will be saved in the other elevators continously. Restart elevator. Has to adjust orders the fact that we are missing one elevator.
What should happen if some unforeseen event causes the elevator to never reach its destination, but communication remains intact?
    Set the elevator out of order. Dont give it more orders.

Guarantees about orders:

Do all your nodes need to "agree" on a call for it to be accepted? In that case, how is a faulty node handled?
    The only nodes that needs to agree is the one giving the order and the one executing the order. If the nodes does not agree, because of lost connection. Then the node giving the order needs to execute it him self.
How can you be sure that a remote node "agrees" on an call?
    acceptance message. Answers that it takes the order. 
How do you handle losing packets between the nodes?
    Need accknowledgement, send untill you get acknoknowledgement
Do you share the entire state of the current calls, or just the changes as they occur?
    We only want to share the states and the accepted orders.
For either one: What should happen when an elevator re-joins after having been offline?
    Need to sync orders when the elevator connects.

Skille på nettverk og at strømmen går?? Anta at strømmen går. Alle heisene må utføre alle ordrene.

Topology:

What kind of network topology do you want to implement? Peer to peer? Master slave? Circle? Something else?
    Peer to Peer
In the case of a master-slave configuration: Do you have only one program, or two (a "master" executable and a "slave")?
    NA
How do you handle a master node disconnecting?
Is a slave becoming a master a part of the network module?
In the case of a peer-to-peer configuration:
Who decides the order assignment?
    The elevator recieving the order distributes the order
What happens if someone presses the same button on two panels at once? Is this even a problem?
    Worst case two elevators does the same job.
Technical implementation and module boundary:

Protocols: TCP, UDP, or something else?
If you are using TCP: How do you know who connects to who?
    Everyone connects to everyone. Saved localy what elevator is who
Do you need an initialization phase to set up all the connections?
    
If you are using UDP broadcast: How do you differentiate between messages from different nodes?
If you are using a library or language feature to do the heavy lifting - what is it, and does it satisfy your needs?
Do you want to build the necessary reliability into the module, or handle that at a higher level?
Is detection (and handling) of things like lost messages or lost nodes a part of the network module?
How will you pack and unpack (serialize) data?
Do you use structs, classes, tuples, lists, ...?
JSON, XML, plain strings, or just plain memcpy?
Is serialization a part of the network module?