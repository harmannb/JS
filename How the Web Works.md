# How the Web Works 

* Important Definitions 
	* **Protocol** - The Internet is built on protocols which strictly define how information is sent and recieved on the web. 
	* **HTTP** - Hyper Text Transfer Protocol is well-defined client-server protocol which allows the client to get data from the server or data on the server. 
	* **IP Address** - The Internet Protocol (IP) is the protocol that governs how data is sent accross a network from one computer to another. 
	* **DNS** - Domain Name System is a server that takes a domain like *https://www.rithimschool.com* as input and returns an IP address as output. This is necessary for the web because computers can only make connections to ip addresses. 
	* **Idempotent** - refers to an operation that can be repeated many times on a set of data and the state of set of data will not change. This concept is applicable to the HTTP spec since operations like a GET request should be idempotent but a POST request is not.    