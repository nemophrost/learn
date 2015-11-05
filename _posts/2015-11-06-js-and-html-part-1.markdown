---
layout: post
title:  "JavaScript and HTML Part 1"
date:   2015-11-06 9:00:00
---

[Lesson Codepen](http://codepen.io/anon/pen/GpXYqy?editors=001){:target="_blank"}

What makes a webpage?
---

A typical web page consists of three main parts:

* HTML
* CSS
* JavaScript

**HTML** (HyperText Markup Language) is the code that defines the structure and content of the page. For instance:

	<!-- HTML example -->
	<form>
		<label>Email</label>
		<input type="email">
		<label>Phone number</label>
		<input type="number">
	</form>

This code adds a form with some labels and input boxes to the page. Structure is provided by nesting the labels and input inside the form as well as by the order of the elements. Content is added by the text (labels) and inputs themselves.

---

**CSS** (Cascading Style Sheets) is a language for describing the presentation of an HTML document. Things like colors, fonts, borders, backgrounds, margins and transparency are defined by css.

	/* CSS Example */
	form {
		border: red solid 1px;
		background: yellow;
		color: black;
		padding: 20px;
	}


---

**JavaScript** is a programming language used to make web pages dynamic.

	// You have seen this kind of code already
	alert("Hello World!");

---

> Note the different ways comments are written in each language



The Document Object Model (DOM)
---

"The Document Object Model (DOM) is a cross-platform and language-independent convention for representing and interacting with objects in HTML, XHTML, and XML documents" - [Wikipedia](https://en.wikipedia.org/wiki/Document_Object_Model)

What?

The DOM is what you use in JavaScript to interact with the actual elements on a webpage.

To understand the DOM, we need to jump back into JavaScript and learn a little more about something called Objects.



Objects
---

In our previous lessons we discussed several data types in JS such as `string`, `number`, and `boolean`. We have also created `functions` which are their own data type. So lets talk about another data types in JS, called an `object`.

In real life, a car is an **object**.

A car has **properties** like *color* and *weight*.

All cars have the same **properties**, but the property values are different for each car. (ie. dashboard GPS could be represented with a `boolean` value)

Objects in JS allow you to store multiple values in one variable. So, instead of creating lots of variables to represent a car, you can create a single `object` that stores all the information about that car.

	// separate variables :(
	var carMake = "Fjord";
	var carModel = "Muztang";
	var carColor = "cherry red";
	var carStyle = "convertible";
	var carDoors = 2;

---

To define an object, we use the familiar curly braces and for each property we want, we write the name of the property followed by a colon and the value for the property.

	// one variable :)
	var car = {
		make: "Fjord",
		model: "Muztang",
		color: "cherry red",
		style: "convertible",
		doors: 2
	};

> Note, each property must be separated by a comma, but be careful not to add a comma after the last property

---

To access a property of an object, simple use **dot notation** with parenthesis (the same as calling a function).

	car.start();
	car.accelerate(); like we have done for getting the length of a string (`myName.length`).

---

	console.log(car.style)
	// → convertible

---

You can also `assign` new properties to an object and change values with **dot notation** with parenthesis (the same as calling a function).

	car.start();
	car.accelerate();.

---

	// change property
	car.style = "coupe";

	// add new property
	car.maxSpeed = 164;

---



Objects are great
---

Objects are great because they can contain a bunch of values that you can pass around in your code without having to use longs lists of variables. For example:

	// separate variables :(
	var carMake = "Fjord";
	var carModel = "Muztang";
	var carColor = "cherry red";
	var carStyle = "convertible";
	var carDoors = 2;

	var carDescription = function(make, model, color, style, doors) {
		console.log(color, style, make, model);
	};

	carDescription(carMake, carModel, carColor, carStyle, carDoors);
	// → cherry red convertible Fjord Muztang

---

Compare that to:
	
	// object :)
	var car = {
		make: "Fjord",
		model: "Muztang",
		color: "cherry red",
		style: "convertible",
		doors: 2
	};

	var carDescription = function(car) {
		console.log(car.color, car.style, car.make, car.model);
	};

	carDescription(car);
	// → cherry red convertible Fjord Muztang

---

The benefits of using objects becomes more apparent when you have more than one:

	// my car
	var myCarMake = "Fjord";
	var myCarModel = "Muztang";
	var myCarColor = "cherry red";
	var myCarStyle = "convertible";
	var myCarDoors = 2;

	// my wife's car
	var myWifesCarMake = "Shevee";
	var myWifesCarModel = "Camarlo";
	var myWifesCarColor = "yellow";
	var myWifesCarStyle = "coupe";
	var myWifesCarDoors = 2;

	// my neighbor's car
	var myNeighborsCarMake = "Yotoya";
	// ... you get the picture

---

As you can see, using separate variables to represent a collection of related data quickly becomes a mess at a larger scale. Imagine you need to work with hundreds or thousands of cars. There is no way you can deal with separate variables for each property of each car.




Methods
---

Each property of an object can be of any data type. When an object has a property that is a `function`, it is called a **method**.

For instance, our car object might have **methods** of **start** and **accelerate**.

	var car = {
		make: "Fjord",
		model: "Muztang",
		color: "cherry red",
		type: "convertible",
		doors: 2,
		start: function() {
			// do whatever we need to do when starting the car
			console.log("The car has started.");
		},
		accelerate: function() {
			// adjust the car's speed based on what type it is and how far down the gas pedal is
			console.log("The car goes faster.");
		}
	};

Methods are defined the exact same way as the other properties, except that the values are functions.

---

To call a method on an object we use **dot notation** with parenthesis (the same as calling a function).

	car.start();
	// → The car has started.

	car.accelerate();
	// → The car goes faster.

---



Back to the DOM
---

Now the we understant objects, we can continue our discussion of the DOM. When a web page is displayed by your browser, it converts all the HTML code in the page to a bunch of JavaScript objects representing each element on the page.

This is the DOM.

You can access the DOM using the global variable `document`. The document variable is created by the browser and is accessible anywhere in your code.

	// we can log the title of the html page with document.title
	console.log(document.title);
	// → JavaScript and HTML Part 1

---

Each element on the page is represented by a DOM `node`.

	<!-- Sample HTML -->
	<form>
		<label>Email</label>
		<input type="email" id="userEmail">
		<label>Phone number</label>
		<input type="text" id="userPhone">
	</form>

---

One way to access a specific element is using its `id` attribute.

	// JS
	var emailInput = document.getElementById("userEmail");

---

Once you have assigned a DOM node to a variable, you can get and set properties on it.

	// set the value of the email input with JavaScript
	emailInput.value = "myemail@example.com";



User interaction
---

Let's look at how to do something in JavaScript when a user clicks on a button.

	<!-- Sample HTML -->
	<button id="myButton">Click me</button>

---

First, we get the DOM node for the button and assign it to a variable.

	var btn = document.getElementById("myButton");

---

Next, lets create a function we want to be called when the button is clicked.

	var onButtonClick = function() {
		alert("You just clicked the button");
	};

---

Finally, we call the method `addEventListener()` on the button node.

	btn.addEventListener("click", onButtonClick, false);

Let's break down what's going on here:

`addEventListener` is a build-in method on the button DOM node. We are calling it with three parameters.

* The first parameter specifies what `event` we want to listen to. An `event` is something that happens in time, like a click, a page load, page scrolling, text input changing, etc.
* The second parameter specifies the function we want to be called when the specified event happens to the button. (In this case when it is clicked).
* The third parameter is a boolean value with a [complicated explanation](http://www.quirksmode.org/js/events_order.html). Just use `false` for now.

---

Your code will then get called each time the user clicks on the button.

If you no longer want your code to run when the button is clicked, you can remove the event listener with `removeEventListener()`.

	btn.removeEventListener("click", onButtonClick, false);



More user interaction
---

Let's also go through how to do something when a user changes the text in an input.

	<!-- Sample HTML -->
	<input type="email" id="userEmail">

---

Get the DOM node for the input and assign it to a variable.

	var emailInput = document.getElementById("userEmail");

---

Create the change handler.

	var onInputChange = function(event) {
		// event.target is the same as emailInput
		// (event.target === emailInput)
		console.log("new value", event.target.value);
	};

> Notice that here we are expecting a parameter to be passed to the change handler function.
> 
> This parameter will be an event object, passed by the browser. All events have a `target` property which is a reference to the DOM node the event happened on. So in this case, event.target will refer to the input just the same as `emailInput`.

---

Add the change handler with `addEventListener()`.

	emailInput.addEventListener("change", onInputChange, false);

---



<hr class="visible" />


Exercise
---

Let's make a helper function for binding event listeners to an element.

<div><a class="code-link"><i class="fa fa-link"></i></a></div>

	var bind = function(nodeId, eventName, handler) {
		var node = document.getElementById(nodeId);

		// If there is no node with the specified ID, node will
		// be a special value: null (acts a lot like the boolean false)
		// This if statement will only execute if node is not null
		if (node) {
			node.addEventListener(eventName, handler, false);
		}
	};

	// alert when a user clicks a button
	bind("myBtn", "click", function() {
		alert("You clicked a button");
	});

<div class="code-cover"></div>

Create a function that takes the following parameters:

* nodeId (The DOM node ID)
* eventName (The name of the event you want to listen for)
* handler (The function you want to use as the handler)

Write the code inside that will get the DOM node by ID and add a listener for the specified event.
