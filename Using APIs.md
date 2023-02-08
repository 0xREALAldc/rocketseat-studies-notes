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

- `Beggining a project with NodeJS`
	- *npm init -y* : this command creates a file called *package.json* that's the beggining of a project using node
- `Express` 
	- it's a framework that we'lll use to help us when creating our *API*
	- he already has all the *http methods* and also *middlewares* that we will see later 
	- `npm i express` : command to install into the project
