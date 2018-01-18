# HTTP and REST 
* HTTP Format - when we issue an HTTP request, we specify the URL we are making a requestto and we can pass additional meta-information to the request by using the headers. 
	 * **Request headers** can include information about: 
	 	* Sending cookies to the server
	 	* Caching information 
	 	* Data types that are ok to be sent (json/html/xml)
	 	* Browswe information (Name/Version)
 	* **Reponse Headers** can include information about: 
 		* Caching information 
 		* The server issuing the response 
 		* Attaching a cookie in the broswer 
 		* The data type being sent (json/html/xml)
	* **Curl Commands** 
		 * -v - for additional information 
		 * -H - for adding request headers
		 * -I - including response headers
		 * -X - for picking an HTTP verb
		 * -d - for passing data in the request
* HTTP Verbs - 
	* Different verbs serve different purposes, and only some of them are idempotent (An idemptent operation is one that will repeatly produce the same result.)
	* **GET** - An idempotent operation that is designed for getting data on the server
	* **POST** - A non idempotent operation that can create data on the server or otherwise modify data. 
	* **PUT** - Technically idempotent, but commonly used for updating data that already exsits on the server. 
	* **PATCH** - Non idempotent and also used for modifying data on the server. 
	* **DELETE** - Deletes data form the server. Not idempotent. 	 	