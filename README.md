# Async-Await-Practice
<html>
<head>
<meta charset="UTF-8">
<title>Password Generator</title>
<link rel="stylesheet" href="password.css">
<script src="password.js"></script>
</head>

<body>
<main>
<h1>Generate a strong password</h1>
<label for="num">Number of characters:</label>
<input type="text" id="num"><br>
<label for="password">Password:</label>
<input type="text" id="password" disabled><br>
<label>&nbsp;</label>
<input type="button" id="generate" value="Get Password">
<input type="button" id="clear" value="Clear"><br>
</main>

</body>
</html>

=================CSS===========================

body {
font-family: Arial, Helvetica, sans-serif;
background-color: white;
margin: 0 auto;
width: 500px;
border: 3px solid blue;
padding: 0 2em 1em;
}

h1 {
color: blue;
}

label {
float: left;
width: 11em;
text-align: right;
padding-bottom: .5em;
}
input {
margin-left: 1em;
margin-bottom: .5em;
}

#num {
width: 5em;
}
#password {
width: 18em;
}

==============================JAVA SCRIPT=======================


"use strict";

var $ = function(id) { return document.getElementById(id); };

var getRandomNumber = function(max) {
var random;
if (!isNaN(max)) {
random = Math.random(); //value >= 0.0 and < 1.0
random = Math.floor(random * max); //value is an integer between 0 and max - 1
random = random + 1; //value is an integer between 1 and max
}
return random;
};

var generatePassword = function() {
if(!isNumeric($("num").value)){
alert("Please enter a valid number");
$("num").value = "";
}

var len = $("num").value;
$("password").value =""; // clear previous entry
var chars = '0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz_-+*/@';
var pass = "";
var i =0;
for (i = 0; i < len; i++) {
var index = getRandomNumber(chars.length);
pass = pass+chars[index];
}
$("password").value =pass;
};

var clearFields = function() {
$("num").value = "";
$("password").value = "";
$("num").focus();
};

function isNumeric(n) {
return !isNaN(parseFloat(n)) && isFinite(n);
}

window.onload = function() {
$("generate").onclick = generatePassword;
$("clear").onclick = clearFields;
$("num").focus();
};
