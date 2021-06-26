# P2P-HAC Heartbeat
A multithreaded implementation of a P2P heartbeat protocol using UDP and a custom packet design

Is executed with a text file containing all of the hosts as a command line argument (current configured for a total of 4 peers)

    -java p2pDriver hosts.txt
    
Adds all of the IPs in the hosts.txt into an array that contains peers. A heartbeat is sent to all peers in the network every 5-10 seconds containing information about which peers are currently running and which peers have gone offline. 

Upon receiving data that a peer has gone offline, all other peers will automatically update their peerlists to remove the offline machine. Likewise, when the peer comes back online and sends a packet to its peers, all other peers will update their peerlists to reflect the status change.

If a machine has not sent a heartbeat for some time, then that peer is timed out and all other peers assume that the machine has gone down.

