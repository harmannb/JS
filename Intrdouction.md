## Introduction

* ECMAScript vs Javascript
	* 	ECMAscript is a standard. Javascirpt is an implementation of that standard. The standard dictates certain features and sets of functionality, but there can be different implementations that follow the standard. 
* null vs undefined
	* *undefined* means a variable has been declared but has not been assigned a value
	* *null* is an assignment value and can be assigned to a variable as a repersentation of value. 
	* undefined is a type itself (undefined) while null is an object
	* One way to consider the notion of "undefined: in JavaScript is as a "higher level" null value
* == vs ===
	* Both operators check whether the two things being compared have the same values, but there's one important difference. == allows for coercion of the values, while === does not
* Ternary Operators
	* In general, a ternary operator has the form: 

		`expression ? pathIfTrue : pathIfFalse `
		
		equivalent to
			
		`if (expression) {
		    	pathIfTrue
		} else {
				pathIfFalse
		}`

* The splice method: Removing/Adding or both with splice
	* The splice menthod accepts at least two arguments. The first argument is starting index, indicating where values will be removed or added. The second parmameter is the number of values to remove. Optionally, you can pass in an unlimited number of additional arguements; these correspond to values you'd like to add to the array. 
* Array Methods
	* **Concat**
		* Concat joins two arrays together. In fact, you can pass multiple arrays into concat and it will still return a single array yo you. 
		* You don't even need to pass an array into concat! Any comma-seperated list of values can be concatentated with the orginal array. 

			```
			var moreOpeningWords = 
			openingWords.concat("dark","and","stormy","night");
			moreOpeningWords; // ["It", "was", "a", "dark", "and", "stormy", "night"]
			```
	* **lastIndexOf**
		* lastIndexOf works just like indexOf, but searching from the end of the array rather than the beginning
	* **Reference vs Value**
		* Javascript is *always* pass by value, but when a variable refers to an object(including arrays), the "value" is a reference to the object
		* Changing the value of a variable never chnages the underlying primitive or obejct, it just points the variable to a new primitive or object 
		* However, changing a *property* of an object referenced by a variable does chnage the underlying object 