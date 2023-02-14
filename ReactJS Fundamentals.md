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


