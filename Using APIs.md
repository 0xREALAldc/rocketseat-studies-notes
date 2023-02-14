- `What the hell is a API (Application Programming Interface) `
	- a intermediary that allows two applications to interact with each other
	- are an accessible way to extract and share data within and across organizations
	- it's a way for us to get data from other sources beyond our database
	- can be a path to send data from one application to another, like a payment gateway to run a payment

- `JSON (JavaScript  Object Notation)` 
	- commonly used in web development to exchange data
	- can be used in any language
	- it's composed by a structure of *key - value* 
	- we can store strings, numbers, arrays, objects
	- the *key* **CANNOT** have spaces, so if is more than one word, we separate with *underscore _* 

- `Main HTTP methods used when working with an API`
	- *GET* request to the API to send data to us
	- *POST* we use when we wanna send data to the API, data that can be saved or only used in that call for something
	- *DELETE* the API receives a identifier of a record that must be removed
	- *PUT* we send data to the API that we want update in one or many records
	- *PATCH* we send data to the API that we want to update, but this one is reserved to use to update only *ONE* record

- `Insomnia` 
	- it's a client that let us test RESTful applications, because using only the browser we can't do other calls beyond *GET* 
	- it's where we'll be testing our *API's* 

- `Begining a project with NodeJS`
	- *npm init -y* : this command creates a file called *package.json* that's the beggining of a project using node
- `Express` 
	- it's a framework that we'lll use to help us when creating our *API*
	- he already has all the *http methods* and also *middlewares* that we will see later 
	- *Middleware* : it's like a bridge between the requisitions, so when we call a *path* from the API our call will first go through the *middleware* and then do whatever it's supposed to
	- `npm i express` : command to install into the project
	- `index.js` : will be a main file where we will tell node how to create our application
	- *to run a nodeJS project*: we use the command `node index.js` 
		- we can also use `node .` and this has a dependency that in the *package.json* the *main* property is set with the name of the file that hold our application
	- `app.listen('port_number')` : we set the port that our application will run
	- `app.route` : we use to declare the routes that our application will have
		- we then specify the *path* to the route and the method that will use
			- `app.route('/').get( (req, res) => res.send("Welcome to Home Page") )`
			- `app.route('/register').post( (req, res) => console.log(req.body) )`
				- using *post* and sending a body in *JSON* we'll have to say to our application that we will use *JSON*, so we do like below
					- `app.use(express.json())` : this line will tell our application to know that we're going to be using *JSON* files
			- `app.route('/register').put( (req, res) )`
	- `sending parameters in routes` : we have three ways to send parameters in routes, the *body params, route params and query params*
		- *body params*: 
			- the informations sent to the *API* will not be showed anywhere in the URL
			- they'll be sent inside the *body*
			- a *body* can be only sent in the *PUT, PATCH* and *POST* http methods
		- *route params*: 
			- the param will be visible in the *url* 
			- we will declare like `/:id` and in the application we'll get the value from `req.params.NAME_OF_ROUTE_PARAM`, in this case, `req.params.id` 
		- *query params*: 
			- the params will also be sent in the *url*
			- each one is defined by the syntax *?name=VALUE* 
				- eg: `?search=how+to+find+love` 
			- we can send more than *ONE* query param in the url, we just need to separate them using the *&* 
				- eg: `?search=how+to+find+love&city=london` 
			- in our application, to get each of the params sent we can use *req.query.variable_name_used* 
				- eg: `req.query.search`
				- or if it's more than one as above, `const { search, city } = req.query;` 

`working with github api` 
- we're just going to update the project to get the information of a user in github and display the picture of the user when calling the `/` path

`Using fetch in the FrontEnd` 
- `Fetch` 
	- it's a JS interface that allows us to do http calls from the frontend
	- we're going to use a node api that is *OUR* and running locally to make calls from our front end page using *fetch* 
		- project with the API: 
			- https://github.com/jakeliny/node-api-discover
	- is promise based
	- *POST* : 
		- we can use POST with fetch to send data
		- in the call using *fetch* to do a POST, we need to specify the *method* as being a POST, because the default is *GET* and also the *headers*
	- *PUT* 
		- it's just like a POST call, we just need to pass the ID of the user because the API requires and use *PUT* in the method
	- *DELETE* 
		- it's just like the others, we need to pass the *method, headers* not a *body* because we only need to know the *id* of the record that's going to be deleted
```javascript
function addUser(newUser) {
  fetch(url, {
    method: 'POST',
    body: JSON.stringify(newUser), 
    headers: {
      'Content-type': 'application/json; charset=UTF-8'
    }
  })
  .then(response => response.json())
  .then(data => alertApi.textContent = data)
  .catch(error => console.error(error))
}
```

`Using Axios in the FrontEnd`
- we're going to need to import in the `index.html` the script that is the path for a *cdn* for *axios* that enables us to use in our *main.js*
- the use is basically almost equal to the one that we made with fetch
- one thing that changes is that when using *POST* and *PUT* we pass the data a little bit different, we don't need to set *method, body, headers* we only pass the object as a second parameter after the *URL* 
