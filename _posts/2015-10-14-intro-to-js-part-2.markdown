---
layout: post
title:  "Intro to JavaScript Part 2"
date:   2015-10-14 9:00:00
---


Functions are repeatable sets of instructions
---

You can think of a `function` like a recipe. If I ask you to bake some cookies for me, I don't have to tell you each ingredient and how to do it. You have a recipe for that.

Your favorite cookie recipe contains a repeatable set of instructions for how to make cookies.

Functions allow you to split your code into smaller reusable parts



Your first function
---

Functions are created using the `function` keyword followed by parentheses and a set of curly braces.

	function() {}

---

Unfortunately, while that *is* a function, it doesn't do anything. Not very useful.

Let's make a function that logs a story.

	function() {
		console.log("Once upon a time there was a wise king.");
		console.log("The king ruled his kingdom in kindness.");
		console.log("Everyone was happy.");
	}

---

OK, so now you have a function. But how do you use it?

To use a function you need to assign it to a variable. Then you can **call** the function by typing the name followed by parentheses.

	var myStory = function() {
		console.log("Once upon a time there was a wise king.");
		console.log("The king ruled his kingdom in kindness.");
		console.log("Everyone was happy.");
	};

---

Notice the semicolons. Each line inside the function needs to end with a semicolon as well as the function itself (after the closing curly brace).

	myStory();
	// → Once upon a time there was a wise king.
	// → The king ruled his kingdom in kindness.
	// → Everyone was happy.



Function parameters
---

The real power of functions comes from being able to do different things base on the input. For instance, we could turn our simple, boring story into a Mad Libs style story.

First, we need to give our function the words we want to use in the story. You give inputs to your function by putting them between the perenthesis and separating them with commas.

	myStory("wise", "ruled", "kingdom", "happy");

---

Next, we need to use those inputs within our function.

Each input to a function is called a `parameter`. You simple give each parameter a name when declaring your function then you can use that parameter within your function just like a variable.

	var myStory = function(adj, verb, noun, adj2) {
		console.log("Once upon a time there was a wise king.");
		console.log("The king ruled his kingdom in kindness.");
		console.log("Everyone was happy.");
	};
	myStory("wise", "ruled", "kingdom", "happy");

Notice the order you pass parameters to a function determines the name they have inside the function. The parameters also have to have unique names within the function.

---

Now we just need to use the parameters in our logging to modify our story.

	var myStory = function(adj, verb, noun, adj2) {
		console.log("Once upon a time there was a", adj, "king.");
		console.log("The king", verb, "his", noun, "in kindness.");
		console.log("Everyone was", adj2, ".");
	};
	myStory("wise", "ruled", "kingdom", "happy");
	// → Once upon a time there was a wise king.
	// → The king ruled his kingdom in kindness.
	// → Everyone was happy.

---

If we just change the parameters, we change the story.

	myStory("baby", "rode", "turtle", "annoyed");
	// → Once upon a time there was a baby king.
	// → The king rode his turtle in kindness.
	// → Everyone was annoyed.

---

Great job! Given what we just learned, you may have noticed that `console.log()` is a function. You've been using functions the whole time and didn't even know it. :)



Returning values
---

Functions are great for performing complex operations on data you pass in, but you also need a way to get data back out of a function. Remember in algebra class you had mathematical functions like y = x + 4? You put in a value for x and you get back your value for y. We can do the same thing with JS.

In JS you tell functions to give you something back using the `return` keyword followed by the value you want to return.

	var addFour = function(x) {
		return x + 4;
	};
	addFour(6);
	// → 10

	addFour(213);
	// → 217

Note: As soon as the interpreter sees the `return` keyword, it will stop running any code after that. You should therefore only return something from a function after you have done everything else you need to.



Scope
---

`Scope` refers to how your code can access other parts of your code.

	var favoriteNumber = 3;
	var cubePlus = function(x) {
		var secondFavoriteNumber = 7;
		return x * x * x + secondFavoriteNumber;
	};
	cubePlus(favoriteNumber);
	// → 34

	console.log(favoriteNumber);
	// → 3

	console.log(secondFavoriteNumber);
	// → Error: secondFavoriteNumber is not defined

	console.log(x);
	// → Error: x is not defined

For example, function parameters and variables declared (with the `var` keyword) within functions are only accessible within that function.

You can think of functions as a being like one-way mirrors. The code inside a function can access and see everything outside of it, but code outside of a function cannot see anything inside.

---


<hr class="visible" />


Exercise 1
---

Let's make an interactive story:

1\. Start with the last myStory function found in the **Function parameters** section

<div><a class="code-link"><i class="fa fa-link"></i></a></div>

	var buildAStory = function() {
		// create the four variables from user input
		var adj = prompt("I need an adjective please.");
		var verb = prompt("Past tense verb please.");
		var noun = prompt("Noun please.");
		var adj2 = prompt("One more adjective.");

		// log the story
		console.log("Once upon a time there was a", adj, "king.");
		console.log("The king", verb, "his", noun, "in kindness.");
		console.log("Everyone was", adj2, ".");
	};

	buildAStory();

<div class="code-cover"></div>

2\. Create variables inside the function named the same as the parameters, then remove the parameters

3\. Use `prompt` to ask the user for each type of word you need and assign the user's response to the corresponding variable

---


<hr class="visible" />


Exercise 2
---

Let's make a tip calculator:

1. Create a function and assign it to a variable named **calculateTip**
2. To calculate a tip, we need the total bill and a desired percentage. Add **total** and **tipPercentage** as parameters to your function
3. Return the total times the tip percentage divided by 100 (to convert the percentage to a decimal)
4. Call the function with 50 as the total and 18 as the tip percentage. You should get 9

<div><a class="code-link"><i class="fa fa-link"></i></a></div>

	var calculateTip = function(total, tipPercentage) {
		return total * tipPercentage / 100;
	};

	console.log("18% tip:", calculateTip(50, 18));
	// → 18% tip: 9

<div class="code-cover"></div>


---


Bonus challenge 1:
===

Let's make a default tip percentage. If you don't provide a tip percentage, we want it to default to 18.

1. To check if `tipPercentage` was passed into the function, check `if` it is equal to the keyword `undefined`. Inside your `if` statement, assign `18` to `tipPercentage`. (You can treat the parameters just like variables in that you can change their values inside the function).
2. Call the function with 50 as the total and no tip percentage. You should still get 9

<div><a class="code-link"><i class="fa fa-link"></i></a></div>

	var calculateTip = function(total, tipPercentage) {
		// if tipPercentage was not provided
		if (tipPercentage === undefined) {
			// assign it the default value of 18
			tipPercentage = 18;
		}
		return total * tipPercentage / 100;
	};

	console.log("Default tip (18%):", calculateTip(50));
	// → Default tip (18%): 9

	console.log("20% tip:", calculateTip(50, 20));
	// → 20% tip: 10

<div class="code-cover"></div>


---


Bonus challenge 2:
===

Let's make our function return a sring formatted to look like a dollar amount. (ie. "$3.12")

1. Start by assigning the tip amount to a variable named tip.
2. Numbers in JS have a method (methods are properties that are functions) called `toFixed`. You use it just like `length` on strings, but with parentheses since you are actually calling a function. `Number.toFixed()` accepts a single numeric parameter and returns a string version of the number you call it on rounded to the number of decimal places you pass to it. So `(98.765).toFixed(1)` would give you `"98.8"` (it rounds for you too). I also mentioned briefly that you can use the `+` operator on strings to join or concatenate them. Use `toFixed` and `+` to return the tip with 2 decimal places and a dollar sign in front.
3. Calculate the tip needed for a total bill of $87.16

<div><a class="code-link"><i class="fa fa-link"></i></a></div>

	var calculateTip = function(total, tipPercentage) {
		// if tipPercentage was not provided
		if (tipPercentage === undefined) {
			// assign it the default value of 18
			tipPercentage = 18;
		}
		// asign the tip as a dollar amount to the variable "tip"
		var tip = total * tipPercentage / 100;
		// return the properly formatted tip amount
		return "$" + tip.toFixed(2);
	};

	console.log(calculateTip(87.16));
	// → $15.69

<div class="code-cover"></div>
