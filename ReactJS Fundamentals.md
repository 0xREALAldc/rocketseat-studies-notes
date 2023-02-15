- a JS library that the objective is to facilitate the creation of interfaces
- we call it a *library* because he is not a *opiniated language*, meaning that he doesn't have a structure of folders, many rules as frameworks usually have
- we have a big liberty to create our interfaces almost in any way that we want
- we can create UI for *web* and *mobile* with react (native compiled for IOs and Android) and there's also for desktop

`Creating a project` 
- `create react app` 
	- it's a way that we can use
	- it's a boilerplate for a new project, comes with a sample for your project

- `vite` 
	- it's also a boilerplate to a new project
	- we're going to use *vite* because today he has a better performance when compared to *create react app* 
	- and it brings in your new project only a base, really what's needed to start a project
	- to create the app we use the command below
		- `npm create vite@latest name_of_app --template react` 
			- the *--template* is because vite has support for creating projects for other frameworks, like *svelte*, *vue*...
	- react is based in UI's that are constructed using many components 

`JSX` 
- in the syntax that *react* used that allow us to create interfaces using *JS* and returning a *HTML*
- so we're going to have functions in JS that will return content in html that's going to be rendered to the user
- also *jsx* allows us to use the components that we create in a simple way, very similar to the *html tags* that we use when developing a web page
	- as an example, in the *main.jsx* we import the *App* component and we use it as *<App />* inside the area that the html is rendered
- *Fragment* 
	- when building our components with *JSX* we need to always return *ONLY ONE* element in our *return* in the function within the component file, so if we're going to have more than one element in HTML inside our component, we need to wrap them with a *fragment* that would be
		- `<> .....elements here... </> ` 
	- it's a blank tag, just to hold all the elements
	- we can also use a *DIV* to hold the HTML elements, we just cannot return two HTML elements
		- `<div> ....elements here </div>`
`Using CSS`
- *global file* 
	- we define styling that will be applicable in the all the files of our project
	- to work in our project, we just need to do a import inside the *main.jsx*
		- `import './styles/global.css'` 
	- when we're using HTML in *react*, if we want to apply a styling to a component using *class attribute* we then need to use the *className attribute* 
- *Each component with style*
	- 

`Folder structure`
- *package.json* and *package-lock.json* : responsible for the dependencies of our project both in *production* and *development* mode, also we have the scripts that we can use declared inside
- *.gitignore* : is where we set what files and folders are not supposed to be sent to a github repository
- *node_modules* : is where we have downloaded all the packages that hold the dependencies that our project has
- *vite.config.js* : is a config file for vite, we're not going to touch it
- *src*
	- *main.jsx* : responsible for initializing our application
	- *App.jsx* : is where we have the first component declared 
	- *App.css* : is the styling for the *App.jsx* component
	- *index.html* : file where is rendered the content from our whole project
	- *pages*
		- we can create the folder inside *src* to better organize our project 
		- then put the *app.tsx* file inside, and we can rename for *home.tsx* 
		- it's a good structuring tecnique to create folders to *each* component that will hold the *.jsx* file and also the *.css* styling file
			- then we can also use the the naming standard of using *index.jsx* 
			- where we do the import of our component, we can still use only the path to the folder where it holds our *index.jsx* and will work fine, because as default when not defined the name of the file imported, it'll get the file named *index.jsx* 
	- *styles*
		- *global.css* : global styles that will be applicable in the whole project
		- inside each folder of each component, we can have a *styles.css* that'll be the styling applied only to that component

`Using external fonts in react`
- we'll go to the fonts.google.com and select the font that we want and the respective families 
- after we get the *link* that google fonts provide to us and we're going to past in the *head* tag inside the *index.html* file of our project
- after also we can go to our *global.css* and set the font for the whole project

`Components`
- react is based in componentization, that meaning, we build many individual components that united together make our application whole
- to keep the strutcture of the project organized, we will create a folder named *components* that will hold inside the folders of all the individual components that we're going to build

`Properties in components` 
- to use properties in our components we have a standard to use that is first we set a name to the property and after a *=* sign we pass the value
	- EG. `<Card id={56} />` : number we use *{ number }* 
	- EG. `<Card name="Matthew" />` : strings we use the quotation marks *"string here"*  
- in our *index.jsx* of our component, he always has a *property* named **props** that is retrieved in the declaration as below
	```javascript
	export function Card(props) {...}
	```
	- we can use the *props* variable to get the *properties* that we have passed, using the name that we declared, as above would be `props.name` and `props.id` 
		- in the *html tag* that we will use the value, we inform the value inside brackets `<strong> {props.name} </strong>` 
		- we can also *destructure* the props variable, as below to already use the variables that we're passed by only their names
		```javascript
		export function Card({ name, id }) {...}
	```
`State`
- the difference between a *state* and a *common variable* is that a common variable is not able to show in the UI real time changes that it happens to her, as opposed to a state, that is capable of doing this 
- everytime that a state variable is changed it automatically refreshed it's value in the UI
- to use, we need to import *React* and *{ useState }* from the package *'react'*  
- the pattern to declare a state is like we'll show in the example below. 
- a state has *two elements*, first a *variable* where the value of the state will be written and a *function* to refresh this state variable value
	- the function has a pattern for the name, that is to use the prefix *set* then finish with the same name that was given to the variable, as we can see in the example below
	- also, in the *... useState()* we can set a default start value for the state, being whatever we want like in this example, could be a name of a student *...useState('Matthew')* 
```javascript
import React, { useState} from 'react'
...
const [studentName, setStudentName] = useState()
```

`Immutability`
- is the principle that the *states* in react abide
- means that the content of something must not be *changed*, but *replaced*
	- costs less processing to just replace something then go and change
- this is why we have a *function* to refresh the value of the state
- when we want to change a value of a state, but keeping what had inside the state like in an *array*, we can, we just need to use a different way to assign the value in the state
	- `setStudents([newStudent])` : this is the usual way to set a value for a state
	- `setStudents(prevState => [...prevState, newStudent])` : the *prevState* is a propriety that you can give whatever name you want, but it's kind of a standard to give this name to it. This *prevState* will hold the value that the state had before, and using in this way you'll be able to keep what you had and store one more value to the state
		- the *...* before *prevState* means that we will get the content within *prevState* to add to the new array. If we don't use in this way, it'll add a array to the array

`key prop in loops`
- one thing to keep an eye is when we make a *loop* or a *map* of an array to display a component in a dynamic manner, we need to give to each of them a *key* 
- if we don't do this, the browser will give us a warning telling about this
- we need to do this so that the performance of the listing be better, and to help *react* when it's running it's validations in the *DOM*

`Hooks`
- the *useState* that we've just used is a hook
- usually the hooks have the pattern of starting with the prefix *use..* and the name of the hook (useState, useEffect..)
- are functions that allow us to turn on and connect the states and life cycles of react from totally functional components
- why hooks exist? 
	- they were created to facilitate the development of react in a functional manner, being, using *functions* and no *classes*
	- to allow a more flexible development of components managing the life cycle of our application

`UseEffect`
- to begin with, we need to import from the package `import React, { useEffect } from 'react'`
- the initial declaration of a *useEffect* is `useEffect(() => {}, [])` 
	- first we have a arrow function pointing to the body `() => {}`
	- and after we have an array of dependencies `[]` 
		- here we list the *states* that our *useEffect* depends
	- a userEffect is executed automatically right after our UI is rendered
	- when we create a *useEffect* and leave the `[]` blank, it'll be executed only one time after the UI is rendered
		- if we put a state in the `[]`, everytime that state is modified, the *useEffect* will be executed
		- we can have more than one state that the useEffect is dependent on 
	- we *CANNOT* make a *useEffect* as **asynchronous**, if we needed to do something that is async we would need to declare a function that is *async* inside the *useEffect* and call it right after declaring
	```javascript
	// when need to use async in a useEffect
	
	useEffect(() => {
	  // we need to declare the function, we can declare inside of outside of the    useEffect
	  asynct function doSomething() {
	  ...
	  //using AWAIT in here for something 
	  }
	
	  // then we call it after declaring the function
	  doSomething()
	})
	```

```javascript 
// Syntax of a useEffect 

useEffect(() => { 
  //everything in here are the actions that we want to be executed
  console.log('use effect was called')
}, [])
```


