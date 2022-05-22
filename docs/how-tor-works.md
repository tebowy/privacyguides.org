---
title: "How does Tor work?"
icon: 'pg/tor'
---

Tor is a network designed for using the internet with as much privacy as possible. If used properly, the network enables private and anonymous browsing and communications. Tor is both free to use and decentralized. Below, we will explain how it works.

## Path Building

Tor works by routing your traffic through a network comprised of thousands of voluntarily run servers called nodes (or relays).

Every time you connect to Tor, it will choose three nodes to build a path to the internet—this path is called a circuit. Each of these nodes has its own function:

  - **The Entry Node**: often called the guard node, this is the first node your computer connects to. The entry node sees your IP address, but does not see what you are connecting to. Unlike the other nodes, the Tor client will randomly select an entry node, and stick with it for 2 to 3 months to protect you from certain attacks.
  - **The Middle Node**: The second node to which your Tor client connects. This node can see which node traffic came from (the entry node) and which it goes to next. It does not, however, see your IP address, or the domain you are connecting to. This node is randomly picked from all Tor nodes for each circuit.
  - **The Exit Node**: This is where your traffic leaves the Tor network and is forwarded to your desired destination. The exit node does not know your IP (who you are) but it knows what you are connecting to. The exit node will, like the middle node, be chosen at random from the Tor nodes (if it runs with an exit flag).

```mermaid

```

The Encryption Tor will encrypt each packet three times, with each key in turn from the exit, middle and entry node in that order. Once Tor has built a circuit, browsing is done as follows:

1. When the packet arrives at the entry node the first layer of encryption is removed. In this encrypted packet it will find another encrypted packet with the middle node’s address. The entry node will then forward that to the middle node.

2. When the middle node receives the packet from the entry node, it too will remove a layer of encryption with its key, and find an encrypted packet with the exit nodes address. The middle node will then forward the packet to exit node.

3. When the exit node receives its packet, it will remove the last layer of encryption with its key. The exit node will see the destination address and forward the packet to that address.

Here is an alternative visualization of the process. Note how each node removes its own layer of encryption, and when the destination website returns data, the same process happens entirely in reverse. For example, the exit node does not know who you are, but it does know which node it came from, and so it adds its own layer of encryption and sends it back.

```mermaid

```

So what do we learn from this? Well we learn that Tor allows us to connect to a website without any single party knowing the entire path. The entry node knows who you are, but not where you are going; the middle node doesn’t know who you are OR where you are going; and the exit node knows where you are going, but not who you are. Because the exit node makes the connection, the destination website will never know who you are (the IP address of the originating device).
