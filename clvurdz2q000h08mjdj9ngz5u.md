---
title: "Learning MVC with Node&Expressjs"
seoTitle: "MVC with Node & Express"
seoDescription: "Learn about MVC architecture with Node & Express, understanding Model, View, Controller, and Routes for building efficient applications
Ashutosh7i"
datePublished: Mon May 06 2024 09:28:05 GMT+0000 (Coordinated Universal Time)
cuid: clvurdz2q000h08mjdj9ngz5u
slug: learning-mvc-with-nodeexpressjs
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1714987564937/17245c9a-4f3c-448c-aada-5ae08c4de19b.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1714987635593/116cf963-1cfa-44df-8297-c146d256f6d8.png
tags: mvc, javascript, apis, mern

---

Started learning MVC with Node&Express, this blog contains all the work i done. A kind of backup.

# What is MVC?

MVC stands for Model View Controller. MVC is a Application designing Architecture used to standardize an application for production level, by using MVC your application becomes more easy to develop with a team. MVC is a industry standard and a Best Practice.  
MVC is a backend tech and used in "server side rendered" apps.

![](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/routes/mvc_express.png align="left")

## Model

Model handles the database part of an application, its main task is to interact with a database/storage and read/write data to it, a model is accessible only by the Controller.

The model determines how a database is structured, defining a section of the application that interacts with the database. This is where we will define the db functions, query(s) and properties of a user that will be store in our database.

## View

View handles the presentation part of an application, its main task it to create presentation for the user using the data provided by the controller, it uses a template engine for this process.

**What is a template engine?**

A ***template engine*** enables you to use static template files in your application. At runtime, the template engine replaces variables in a template file with actual values, and transforms the template into an HTML file sent to the client. This approach makes it easier to design an HTML page.

as i said earlier MVC is a backend tech and to make webpage interactive we dont use js, so we use a template engine, there are many template engines, in express there are [Pug](https://pugjs.org/api/getting-started.html), [Mus](https://pugjs.org/api/getting-started.html)[tache](https://www.npmjs.com/package/mustache), [EJS](https://www.npmjs.com/package/mustache), [Jade](https://expressjs.com/en/starter/generator.html). I personally use and recommend ejs.

The view is where end users interact within the application. Simply put, this is where all the HTML template files go.

## Controller

The controller interacts with the model and serves the response and functionality to the view. When an end user makes a request, it’s sent to the controller which interacts with the database.

You can think of the controller as a waiter in a restaurant that handles customers’ orders, which in this case is the view. The waiter then goes to the kitchen, which is the model/database, and gets food to serve the customers, which is the controller handling the request.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714976625450/ec102cad-17f1-46c4-9d24-ec720f68eeb8.png align="center")

## Routes

Even though R is not in word MVC but Routes play a big role in a MVC application.  
Routes contain routes for different endpoints of an application or api.

# How exactly it works?

The flow is described in the index.js/app.js file of an app, it is the entry point for any MVC application.

Firstly the request is handles by the routes, routes is a file that handles all request sent to the server, Then the routes pass the request to the appropriate controller.

Contoller then uses its internal logic(s) to process the request,it interacts with the model.

Model is uses to fetch and send back information to the database,and then to controller.

Controller then processed the information sent by model and sends it to views.

Views create a presentation for that information and sends the updated presentation (HTML) back to the controller,

And at last, the controller shows the information back to the user.

This is the working flow of a MVC application.

*Overwhelming? yes it is, but once you code it, it is very easy✨*

# Implementation in Express&Node.

Code structure-

```plaintext
- Controllers/
    - index.js
- Models/
    - mainModel.js
- Routes/
    - index.js
- Views/
    - homepage.ejs
    - users.ejs
    - register.ejs
- package-lock.json
- package.json
- server.js  
```

server.js-

```javascript
//standard express setup
const express = require('express')
const app = express()
const port = 3000

//main router to handle requests
const mainRouter = require("./Routes/mainRouter")
//bodyParser to parse the form body
const bodyParser = require('body-parser');

//setting EJS view engine
app.set("view engine", "ejs");
const path = require("path");

//setting views directory
app.set("views", path.resolve("./Views"))

//json middleware for Json body parsing
app.use(express.json())

//parsing the form body
app.use(bodyParser.urlencoded({ extended: true }));

//sending all requests to the router
app.use("/", mainRouter)

app.listen(port, () => console.log(`Server started on port ${port}`))
```

Router/index.js-

```javascript
//importing express and express router
const express = require('express')
const router = express.Router();

//importing controller functions for handling
const {
    //any function exported from controller
    handleGetRequest,
    handlePostRequest,
    handleGetAllUsers,
    handleRegisterNewUser
} = require("../Controllers/mainController")


//routing to specific controller functions
router.get("/", handleGetRequest)               //to show homepage
router.post("/", handlePostRequest)             //user registration using form and POST
router.get("/users", handleGetAllUsers)         //show all registered uses
router.get("/register", handleRegisterNewUser)  //registration form 

//exporting router
module.exports = router;
```

Controller/index.js-

```javascript
//importing database
const userModel = require("../Models/mainModel")

//import any package used
const moment = require("moment")
let date = moment().format("DD MM YYYY, hh:mm:ss a");

//handles get request on /; redirects to homepage on views
async function handleGetRequest(req, res) {
    return res.render("homepage")
}

async function handlePostRequest(req, res) {
    //Fill the form on views/register or
    //send a post request on / with a json body
    /*
    {
    "username" : "ashutosh7i",
    "fullname" : "Aashutosh soni"
    }
    */
    //parsing the data from response
    let username = req.body.username;
    let fullName = req.body.fullName;

    //saving the response in the database
    await userModel.create({
        username: username,
        fullName: fullName,
        registered: date
    })

    res.send(`user ${fullName} with username ${username} added✅ on ${date}`)
}

//shows page users on /users endpoint, 
async function handleGetAllUsers(req, res) {
    const results = await userModel.find();
    console.log(results)

    //page page to render along with json data to render
    res.render("users", { results })
}

//handle the /register route, redirect to register page of views
async function handleRegisterNewUser(req, res) {
    res.render("register")
}

module.exports = { handleGetRequest, handlePostRequest, handleGetAllUsers, handleRegisterNewUser }
```

Models/mainModel.js -

```javascript
//connect to mongodb
const mongoose = require("mongoose")

//database url with  /databaseName
const url = "mongodb://127.0.0.1:27017/userDatabase";

//connecting to database
try {
    mongoose.connect(url);
    console.log("connected to database");
} catch (error) {
    console.log("database connection failed");
}

//making a Schema
const userSchema = new mongoose.Schema({
    username: {
        type: String,
        required: true,
        unique: true
    },
    fullName: {
        type: String,
        required: true,
    },
    registered: {
        type: String,
    }
},
    { timestamps: true }
)

//making a model
const userModel = mongoose.model('user', userSchema);

//exporting the model
module.exports = userModel;
```

Views/homepage.ejs-

```xml
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>basic MVC app</title>
</head>
<body>
    This is home of application, rendered on / route.
</body>
</html>
```

Views/register.ejs-

```xml
<!--Basic registeration page-->
<!DOCTYPE html>
<html lang='en'>
<head>
<meta charset='UTF-8'>
<meta name='viewport' content='width=device-width, initial-scale=1.0'>
<meta http-equiv='X-UA-Compatible' content='ie=edge'>
<title>Register</title>
<style>
</style>
</head>
<body>
<h1>Register</h1>
<form action="/" method="POST" onsubmit="return validateForm()">
  <label for="username">Username:</label>
  <input type="text" name="username" id="username" required>
  <span id="username-error" class="error-message"></span>
  <br><br>
  <label for="fullName">Full Name:</label>
  <input type="text" name="fullName" id="fullName" required>
  <span id="fullName-error" class="error-message"></span>

<button type="submit">Register</button>
</form>
<script>
  function validateForm() {
    var isValid = true;
    var usernameInput = document.getElementById("username");
    var fullNameInput = document.getElementById("fullName");
    var usernameError = document.getElementById("username-error");
    var fullNameError = document.getElementById("fullName-error");

    // Validate username
    if (usernameInput.value.trim() === "") {
      usernameError.textContent = "Username is required.";
      isValid = false;
    } else {
      usernameError.textContent = "";
    }

    // Validate full name
    if (fullNameInput.value.trim() === "") {
      fullNameError.textContent = "Full name is required.";
      isValid = false;
    } else {
      fullNameError.textContent = "";
    }

    return isValid;
  }
</script>
</body>
</html>
```

Views/users.ejs-

```xml
<!--This page is server rendered-->
<!DOCTYPE html>
<html lang='en'>
<head>
<meta charset='UTF-8'>
<meta name='viewport' content='width=device-width, initial-scale=1.0'>
<meta http-equiv='X-UA-Compatible' content='ie=edge'>
<title>All uses</title>
<link rel='stylesheet' href=''>
<script defer src=''></script>
</head>
<body>
<H1>List of all registered users</H1>
<style>
  table {
    border-collapse: collapse;
    width: 100%;
    font-family: Arial, sans-serif;
    font-size: 14px;
  }
  th, td {
    border: 1px solid #ddd;
    padding: 8px;
    text-align: left;
    vertical-align: middle;
  }
  th {
    background-color: #f2f2f2;
  }
  tr:nth-child(even) {
    background-color: #f9f9f9;
  }
  td:hover {
    background-color: #ddd;
    cursor: pointer;
  }
</style>

<table>
  <thead>
    <tr>
      <th>Username</th>
      <th>Full Name</th>
      <th>Registered On</th>
    </tr>
  </thead>
  <tbody>
    <% results.forEach(function(user) { %>
      <tr>
        <td><%= user.username %></td>
        <td><%= user.fullName %></td>
        <td><%= user.registered %></td>
      </tr>
    <% }); %>
  </tbody>
</table>

</body>
</html>
```

A Standardized MVC Application looks like this- \[ [repo 😂](https://github.com/ashutosh7i/Node-Express-MongoDB-EJS_MVC_Template)\]

* 1. server.js is the entry point, also any middleware included in server.js will be availabe to any file in relation.
        
    2. server.js calls Routes/router, it holds all endpoint, when request sent to any endpoint, sends it to specified controller.
        
    3. Controllers/controller handles the request and renders/redirects to specified pages.
        
    4. Views/view hold all pages to be rendered by controller handlers.
        

## Flow in our Application-

* Server is started from index.js, then index.js tells routes to handle upcoming requests,
    
* Routes handles types of request and tells the respective controller to process the request,
    
* Controller handles the request and uses different models to manipulate the data,
    
* Models works with database(mongodb here) & gives response to controller,
    
* Views (router again here) makes presentation & gives response to controller.
    
* Controller sends the presentation back to user using routes.
    

# Notes-

1. Any middleware required/imported on the main index.js page, will be availble to any page which will have instance to main page. eg- the express.json allows to pass the request body(req.body.anyJsonKeyName). without it we wont be able to parse it, in the controller page, we needed it, but we didnt required it, it worked out of the box. more on that page.
    
2. The app.route(...) chainable handler & the express.Router() class can be chained together, to make chainable request handler and exported simultaneously. as done it routes.
    

### This is what i learnt about MVC in a day, remained confused for a while about MVC before today, but after implementing it today, everything is crystal clear✨

## Hope it helps.😉🚀