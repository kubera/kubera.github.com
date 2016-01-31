---
title: "Wiki History Book"
tags: [graph, d3js]
---

I had to work out three different versions of an graph representation of the connections between famous people on the [English Wikipedia][en-wikipedia]. A person was represented as a node. As more other persons referred to this person as fatter the node became.

The main requirement was that the representation was in the browser. The three different versions were:

* an java applet, dynamic applicatoin on the client side
* an static SVG, rendered on the server side
* an mix between the first two versions, calculations on the server and rendering on the client with [d3js][d3js]

The most interesting was the third version with [d3js][d3js] but the problem was the number of edges between nodes exponentially rise getting closer to the present. There were to many edges for the javascript to handle in the browser. The solution was that we suppressed a certain number of edges to be still able to run the script.

![Dynamic Version of the Wiki History Book](/images/blog/wiki-history-book-dynamic.png)

You see the [wiki history book here][wikihistorybook] and the [source code is here][wikihistorybook-source].

[en-wikipedia]: http://en.Wikipedia.org
[d3js]: http://d3js.org/
[wikihistorybook]: http://ol19ns18004.fhnw.ch:8080/wikihistorybook/
[wikihistorybook-source]: https://github.com/kubera/wikihistorybook
