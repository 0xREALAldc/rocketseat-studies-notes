`React Fundamentals` 
- it's a JS library to build interfaces that are highly interactive

`Rendering Patterns`
- SPA (single page application)
- SSR (server side rendering)

`SPA (single page application) concept`
- it's a concept introduced around 11'-12' and AngularJS was one of the first ones to use it
- used by *angularJS, Vue, Svelte, Aurelia...*
- here the flow is the browser asks for a page, the backend only get's the data and passes to the frontend in a JSON object, so the frontend can render the information in a page for the user
	- in this way, we have the ability to have *more than one* front end application consuming the data from *ONE* backend

`SSR (server side rendering)` 
- a more older, and the first one, way to develop web sites
- the flow it's the browser asks for a page, the backend built the html/css/js and return to the browser the page fully built

`Bundlers & Compilers`
- `Compilers` 
	- tools to compile code, to convert form a format A to a format B. Usually is compiling a code from a higher version of JS to a lower version that the browser can understand
	- *Babel* is one of the most known compilers for JS 
- `Bundlers` 
	- are tools that we're able to convert all of our files in JS to a single file, so the browser could understand all that we've developed
	- this is because browsers in older versions could'nt understand the structure of having more than one file, that used to import one inside the other
	- *webpack* is one of the most knowns
- Since two years to now (2023) we hade indications that browsers we're going to be able to import scripts natively

`Vite`
- library to develop easier and faster webprojects 
- no need to use webpack
- no need to use babel, it has a internal compiler
- has a awesome performance
- uses EcmaScript modules natively

`Snowpack` 
- very similar to Vite, but Vite has more appeal from the frontend dev community

`Creating a porject with Vite`
- we need to have *nodeJS* installed
- to create a project we use the command  below
	- `npm create vite@latest` 
- *id="root" in the index.html* 
	- it's where it'll be rendered all the html, css and JS for our application and presented to the user
- in the file *main.jsx* we have the *createRoot* creates the root of our page in html in the *root* elemnet cited above. If we look in this file, we are using the same syntax that we use for *HTML tags* but for what is *react components*, like the *<App />* 

`Components` 
- a component in react is *a function that returns HTML*, where we abstract a part of our whole interface in other archive that can be reusable as many times in our application as we need
	- this is why our components have the extension *.jsx* that stands for *JavaScript + XML* 
	- it's a JS file that has HTML
- it's a piece of our interface that we maintain in a separated file that is easier to give maintenance and also is something that's easier to replicate if we want to, like inside a loop or something like this, even being populated with different informations
- *Default Exports vs Named Exports*
	- In the *Default exports* the advantages that are said to be given is that you're able to give a name to the component when you're doing the *import* in another component, and not when you do the *export ...* 
	- In the *Named exports* we don't use the *export default [name of component]* in the end of the file, we put the *export* keyword before the function name and we export by the name of the function. In the file that we want to import, we will use the following syntax `import { MyComponent } from './MyComponent'` 

`Properties` 
- you can understand the *properties* in react kind like the *attributes* that exist in html
- this is the way that we can pass different values to our components, where we can replicate them if needed in our UI but have different content for each of them
- `props` 
	- in every component we have the *props* that is a object that contains every properties that was passed to our component
	- in our project, we are passing two properties that are *author* and *content*, inside our *props* we have them like below
		- `props: { author: "...", content: "..." }` 
	- in *react* when we want to display a value of a variable JS inside the html, we nees to use the *curly braces* around the variable inside the tag 
		- `<p>{ props.content } </p>` 

`Application structure` 
- `Css Modules` 
	- important to mention that in *react* we don't import *css* files to the *index.html*, we do this always in our components
	- *scoped css* when we do the css maintaining the scope of the component, that css will only apply to that specif component 
	- *Vite* has automatic support to *Css Modules*
	- when we use *css modules* we try to only use *classes* to add our styling in our components, not using another types of selectors
	- when we use css in a component, we always use *className* and not *class* 
	- *A IMPORTANT* thing to remember is that when we use *css modules* when we import the css file in our component, we need to *GIVE A NAME* to it, like in th example below
		- `import styles from './Header.module.css' ` 
	- link to reference : https://github.com/css-modules/css-modules




`Tips` 
- *Can I Use?* : website to know if a browser supports a tech or syntax
- *n node manage package* : manager to use with nodeJS. It's easier to change between versions of node using this manager, take a look someday
	- https://github.com/tj/n

`Repository for the project`
- we can find the code for the project in:
	- https://github.com/0xREALAldc/ignite-01-reactjs-fundamentals
