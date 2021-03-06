# jPost-it Plugin jQuery

![](http://img15.hostingpics.net/pics/503718jPostit.png "jPost-it Plugin jQuery")

### Simple, usefull and easy to set up

Sticky notes have always been convenient. jPost-it allows you to __create floating sticky notes into a div and synchronizes them with a database using ajax__. You only have to complete the file which receive requests in order to save the datas.
jPost-its are __editable__, __draggable__, __resizable__ and they have __4 colors__ (yellow, green, purple and blue) that you can simply change anytime. All these actions will be considered as an update so you will be able to save these informations.

## Set Up

1. Include jQuery & jQuery-ui:

	```html
	<script src="../dist/jquery/jquery.min.js"></script>
	<script src="../dist/jquery-ui/jquery-ui.min.js"></script>
	```

2. Include plugin's code and CSS file:

	```html
	<script src="../dist/jquery.jPost-it.js"></script>
	<link rel="stylesheet" href="../dist/style.jPost-it.css">
	```

## Usage

1. Define the container. The following lines are the files which will receive your request ajax when a jPost-it will be created, updated or deleted :

	```javascript
	$("#container").jPostIt({
		"url" : {
			"create": "./createInDatabase.php",
			"update": "./updateInDatabase.php",
			"delete": "./deleteInDatabase.php"
		}
	});
	```
	You can also choose the same file for these 3 actions. Indeed, the ajax request will receive the content, the color, the top position, the left position, the width, the id (if it is an update or delete) and the action. With the action, you will be able to handle the request in a different way on a same file.

2. Define the element which will create your jPost-its (like a button for example) :

	```javascript
	$('#yourElement').click(function() {
		$("#container").jPostIt("create");
	});
	```

## Full options usage

You can choose the default position, color (between yellow, green, purple and blue) and content. Of course, these informations are simply editable.

```javascript
	$('#yourElement').click(function() {
		$("#container").jPostIt("create", {
			"content": "your custom content",
			"color": "green",
			"top": 200,
			"left": 500
		});
	});
```

You also have the posibility to add a custom dialog box to confirm your choice when you want to delete a jPost-it.

```javascript
	$("#container").jPostIt({
		"url" : {
			"create": "./createInDatabase.php",
			"update": "./updateInDatabase.php",
			"delete": "./deleteInDatabase.php"
		},
		// Dialog box options
		"confirm" : {
			"visible" : true,
			"content" : "your custom question"
		}
	});
```

## Event

When a jPost-it is created, updated or deleted, it creates an event. You have the power to execute instructions when one of these action is done.

```javascript
	// On create
	$("#board").on("jPostItcreated", function(event, datas) {
		// some logic
	});
	// On update
	$("#board").on("jPostItupdated", function(event, datas) {
		// some logic
	});
	// On delete
	$("#board").on("jPostItdeleted", function(event, datas) {
		// some logic
	});
```
The event have data which contains the id, color, width, content, top position and left position of the jPost-it.

> Created by [Jonathan Fievet](https://github.com/jonathanfievet).
Based on the concept of [Laura Mead](https://github.com/shmeadyy) : [board.html](https://gist.github.com/shmeadyy/7324662)
