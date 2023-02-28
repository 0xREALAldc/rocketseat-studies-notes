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
- a component in react is *a funtion that returns HTML* 
	- this is why our components have the extension *.jsx* that stands for *JavaScript + XML* 
	- it's a JS file that has HTML
- it's a piece of our interface that we maintain in a separated file that is easier to give maintenance and also is something that's easier to replicate if we want to, like inside a loop or something like this, even being populated with different informations
- 






`Tips` 
- *Can I Use?* : website to know if a browser supports a tech or syntax
- *n node manage package* : manager to use with nodeJS. It's easier to change between versions of node using this manager, take a look someday
	- https://github.com/tj/n

`Repository for the project`
- we can find the code for the project in:
	- https://github.com/0xREALAldc/ignite-01-reactjs-fundamentals
