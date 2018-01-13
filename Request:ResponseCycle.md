# Request/Response Cycle

* Http Request and Response - at a high level, the HTTP involoves a computer making a request for some information at a URL. The web server (another computer) somewhere on the internet handles that request and then sends back the appropriate data to the requesting computer. 
	1. **DNS Lookup** - First, the browser uses a system called domian name server which translates human readable URLs like `https://www.rithmschool.com` into an IP address (e.g. 104.27.190.189). Once the browser has an IP addres, it can make a connection to the server. IP addresses aren't easy to remember like URLs, which they're typically abstracted away from humans. 
	2. **HTTP GET Request** - Using the IP address, the browser makes a HTTP GET request to the server. The GET request conatins the path. 
	3. **Server Receieves Request** - The server recieves the GET request and generates the appropriate HTML page. 
	4. **HTML Response** - The HTML page is sent back to the requesting computer (the browser) via a HTTP response message. The response contains a status code in this case 200, and a response body. The body of the HTTP response is the HTML text that will be displayed in the browser. 
	5. **Browser Creates DOM** - the broswer will read the body of the HTTP response. The browser reads the response body from top to bottom. 
	6. **GET Requests for Images/Scripts/CSS** - While the browser is creating the DOM, it may encounter tags like , `<script src="main.js">` is a reference other files. In order to use the resource, the browser must make an additional GET requests. 