---
layout: post
title:  "Intro to JavaScript Part 1"
date:   2015-10-07 9:00:00
---


JavaScript is a scripting language
---

A programming language is just like a human language in that it consists of words and characters that can be interpreted by the computer to mean something. The `code` you write is a set of instructions to the computer in a language it understands.

A `scripting` language is one that the computer doesn't undestand by itself. It relies on a seprate interpreter to translate the code into language it does understand. In the case of JavaScript, your web browser is the interpreter, converting JavaScript to instructions your computer *can* inderstand.



Strings are sets of characters
---

In JS (JavaScript), a `string` is represented as a line of text with quotes.

	"John Doe"
	// → John Doe

---

You can use either double or single quotes as long as you start and end with the same type.

	'John Doe'
	// → John Doe

---

You can access certain properties on objects (strings are a type of object).

	"John Doe".length
	// → 8



Numbers are numbers
---

In JS, a `number` is just a number.

	42
	// → 42

---

You can add, subtract, multiply and divide

	2 + 3
	// → 5

	2 - 3
	// → -1

	2 * 3
	// → 6

	2 / 3
	// → 0.666666666667

---

Parenthesis affect order of operations like in algebra class

	42 / 7 - 5
	// → 1

	42 / (7 - 5)
	// → 21

---

`+` `-` `*` `/` are all `operators`.

Operators do something with the values on both sides of them. (In this case, they perform mathematical operations on them).



Booleans are ether true or false
---

In JS a `boolean` is a value that is either true or false.

	true
	// → true

	false
	// → false



Errors help you fix bugs
---

Unlike spoken languages, computer languages are unforgiving of errors. If you don't use the right words and grammar (`syntax`), the computer can't understand your instructions. If that is the case you will get an error telling you what is wrong.

	jump

	Error: jump is not defined



Comments make your code better
---

Use `comments` to add explanations and descriptions to your code for other humans to read. Start a line with `//` and the whole line is ignored by the JS interpreter.

	// This is a comment
	// this is another comment



Alert, confirm, and prompt
---

You can interact with the user with some built-in commands your browser supports.

For each of these commands, you need to give the command a message to display to the user. You do that with parenthesis and the message (string) you want displayed inside the parenthesis.

`alert` gives the use information and an OK button

	alert("You are learning to code!");

---

`confirm` asks the user to confirm or cancel something

	confirm("You are about to learn more!");
	// → true

---

`prompt` asks the user to type a response

	prompt("What is your name?");
	// → 'John Doe'



Console.log
---

The interpreter doesn't print out everything it does. If we want to know what it's thinking, we have to ask it to tell us.

`console.log()` is a command to the browser to log whatever is inside the parenthesis to the console.

	console.log(3 * 4);
	// → 12

	console.log("My name is John");
	// → My name is John

---

You can even log more than one thing at a time by separating each thing you want to log with commas inside the parenthesis.

	console.log("I am", 35 * 12, "months old");
	// → I am 420 months old



Comparisons
---

Comparisons use additional `operators` beyond the mathematical ones we already talked about.

A comparison always results in a `boolean`.

Here the most common operators you will use to compare two values:

Greater than `>`

	console.log(8 > 4);
	// → true

---

Less than `<`

	console.log(8 < 4);
	// → false

---

Greater than or equal to `>=`

	console.log(8 >= 4);
	// → true

---

Less than or equal to `<=`

	console.log(8 <= 4);
	// → false

---

Equal to `===`

	console.log(8 === 4);
	// → false

---

Not equal to `!==`

	console.log(8 !== 4);
	// → true

---

> Note, you may see `==` and `!=` used around the web when comparing things in JS. These operators will work in most cases but have slightly different behaviors when comparing some other data types we haven't covered yet. It's good to get in the habbit of using `===` and `!==` unless you really know what you're doing.



Decisions (If this then that)
---

Now that we know about comparisons, we can use them to ask yes and no questions.

You do this with an `if` statement.

	if (237*91 > 10000) {
		console.log("237 x 91 is greater than 10,000");
	}
	// → 237 x 91 is greater than 10,000

An `if` statement is made up of the `if` keyword, a condition in parenthesis, and a pair of curly praces. If the answer to the condition is yes (true) then the code inside the curly braces will run.

---

In addition to doing something when the condition is true, you can tell the computer to do something if it is false.

You do this with the `else` keyword.

	if ("John Doe".length > 10) {
		console.log("You have a long name!");
	}
	else {
		console.log("You have a short name!");
	}
	// → You have a short name!

The `else` keyword is followed by a set of curly braces that contain the code you want run if the condition is false.



Variables store things
---

A `variable` is a way to store something under a name.

You can think of a variable like a bucket. You can have an empty variable (like an empty bucket) and you can change the value of a variable (like putting something new in the bucket).

To create, or `declare` a new variable you use the `var` keyword followed by the name of the variable you are creating.

	var myVariable;

---

To set the value of your variable, use the assignment operator `=`.

	myVariable = 42;

---

You can both declare a new variable and assign a value to it at the same time.

	var afterBirthday = true;

---

Once a variable has been declared, you can change its value any time.

	var myAge = 35;

	if (afterBirthday) {
		myAge = 35 + 1;
	}

---

To use a variable, just type its name.

	console.log("May age is", myAge);
	// → My age is 36

	console.log("May wife's age is", myAge - 4);
	// → My wife's age is 32

---

<hr class="visible" />

Exercise 1
---

1\. Ask the user for their name and store the result in a variable

	// create a variable
	var userName;

	// use "prompt" to ask the user for their name
	// and assign it to your variable
	userName = prompt("What is your name?");

	// if their name is longer than 16 characters
	if (userName.length > 16) {
		console.log("You have a long name");
	}
	else {
		console.log("You don't have a long name");
	}

<div class="code-cover"></div>

2\. Log "You have a long name" if their name has more than 16 characters

3\. Otherwise, log "You don't have a long name"

---

<hr class="visible" />

Exercise 2
---

Let's make a simple game:

1\. Ask the user for their age and store the result in a variable

	// create a variable for the user's age
	var userAge;

	// use prompt to ask the user for their age and assign it to "userAge"
	userAge = prompt("How old are you?");

	// if they are younger than 8...
	if (userAge < 8) {
		alert("Sorry, you are too young to play. :(");
	}
	// if they are 8 or older, play the game
	else {
		// set up the story
		console.log("You are at a carnival and a clown asks you to race.");

		// are they ready?
		if (confirm("Are you ready to race the clown?")) {
			// they win
			console.log("You take off and the clown eats your dust.");
		}
		else {
			// they lose
			console.log("The clown squirts water in your eyes and runs away.");
		}

		// game over
		alert("Game over. Thanks for playing!");
	}

<div class="code-cover"></div>

2\. If the user is younger than 8, alert them that they are too young to play and don't do anything else.

3\. Otherwise, log "You are at a carnival and a clown asks you to race."

4\. Confirm that the user is ready to race.

5\. If the user is ready, log "You take off and the clown eats your dust."

6 \. Otherwise, log "The clown squirts water in your eyes and runs away."

7 \. Tell the user the game is over with an alert.



