---
title: "Wiki History Book"
tags: [graph, d3js, javascript]
---

As per a request of [Professor Dr. Peter Gloor][gloor] of the [Massachusetts Institute of Technology, MIT][mit], [Center for Collective Intelligence][cci] I've worked out three different versions of a graph representation on the connections among famous people of  [English Wikipedia][en-wikipedia]. Each person was represented by a node. More people referred to a person, thicker got its node.

The main requirement was that the representation was in the browser. The three different versions were:

* an java applet, dynamic applicatoin on the client side
* an static SVG, rendered on the server side
* an mix between the first two versions, calculations on the server and rendering on the client with [d3js][d3js]

The most interesting was the third version with [d3js][d3js]. However the issue was the number of edges among nodes that rose exponentially and got closer to the present. There were too many edges for the javascript to handle in the browser. The solution was that we suppressed a certain number of edges in order to be able to run the script.

![Dynamic Version of the Wiki History Book](/images/blog/2014-07-09-wiki-history-book-dynamic.png)

You see the [wiki history book here][wikihistorybook] and the [source code is here][wikihistorybook-source].

[gloor]: http://cci.mit.edu/pgloor/
[mit]: http://www.mit.edu/
[cci]: http://cci.mit.edu
[en-wikipedia]: http://en.Wikipedia.org
[d3js]: http://d3js.org/
[wikihistorybook]: http://ol19ns18004.fhnw.ch:8080/wikihistorybook/
[wikihistorybook-source]: https://github.com/kubera/wikihistorybook
