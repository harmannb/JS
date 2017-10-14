## Intermediate Javascript I 

* Debugging Javascript
	* Common JavaScript Errors
		* ReferenceError - occurs when we try to access a variable that does not exist in scope. 
		* TypeError - occurs when you make incorrect use of certain types in javascript. 
		* RangeError - occurs when we have a function that calls itself (also known as a recursive function). If we have too many functions that have been called (before they are returned) we run out of memmory and cause a RangeError. 
* Catching and Throwing Errors in Javascript
	*  Try / Catch Statement 
		* We place code inside of the try block (a block is defined as code inside of a {}) and if an error is thrown, the code moves to the catch block. 
	* In our try/catch statements, we can add one more special keyword called finally. Inside of the finally block, code will execute regardless of an error being thrown. 
	
	``` 
	try {
	    // let's randomly try to throw an error
	    if(Math.random() >= .5){
	        // The following code will throw:
	        // Uncaught TypeError: undefined is not a function(…)
	        undefined();
	    }
	    console.log("Whew, we made it");
	} catch(e){
	   console.log("We didn't make it. The error message is", e.message);
	} finally {
	   console.log("No matter what we will see this statement");
	}
	```
* Nested Objects
	* Accessing and Setting values in nested objects 
	
	
	```
	var programmingLanguages = {
	    java: {
	        yearCreated: 1995,
	        creator: "James Gosling"
	    },
	    javaScript: {
	        yearCreated: 1995,
	        creator: "Brendan Eich"
	    }
	}

	function addProgrammingLanguage(nameOfLanguage, yearLanguageCreated, creatorOfLanguage){
	    // how can we access the programming languages object?
	    // We can't use dot notation, because we don't know the name of
	    // the key until the function is called.
	    // Instead we use bracket notation where the key is the
	    // nameOfLanguage that is being passed to the function.
	    programmingLanguages[nameOfLanguage] = {
	        // Creating the object which will be the value of the
	        // key.  We can directly assign the yearLanguageCreated
	        // and creatorOfLanguage to the appropriate keys here.
	        yearCreated: yearLanguageCreated,
	        creator: creatorOfLanguage
	    }
	}
	
	// Usage example: Adding a key of ruby to the programming language object,
	// with the value of 1995 for the key "yearCreated" and the value
	// "Yukihiro Matsumoto" for creatorOfLanguage
	addProgrammingLanguage("ruby", 1995, "Yukihiro Matsumoto");
```




