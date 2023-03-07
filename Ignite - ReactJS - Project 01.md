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
	- link to reference : https://github.com/css-modules/css-modules
	- important to mention that in *react* we don't import *css* files to the *index.html*, we do this always in our components
	- *scoped css* when we do the css maintaining the scope of the component, that css will only apply to that specif component 
	- *Vite* has automatic support to *Css Modules*
	- when we use *css modules* we try to only use *classes* to add our styling in our components, not using another types of selectors
	- when we use css in a component, we always use *className* and not *class* 
	- *A IMPORTANT* thing to remember is that when we use *css modules* when we import the css file in our component, we need to *GIVE A NAME* to it, like in th example below
		- `import styles from './Header.module.css' ` 
		- then when we want to use in a component filling the *className* we will need to use the syntax that we use when we want to use a JS var. So in our component the *className* will be filled as the example below, using curly brackets
			- EG: `strong className={styles.header}>Ignite Feed</strong>` 
		- if we take a closer look inspecting the element in our browser, we'll se that the name of the *class* in the css that is applied to him it's kinda weird, it'll be a mixture of the name that we choosed for the class, as the example above that we choose *header* with a random hex concatenated. 
			- Css Modules does this to ensure that not one class that we use in one component change the css style in other component, if in this second component we use the same *name* for the class, as it would be if in component 2 we had in the css a class named *header* again
	- `global.css` 
		- will be our global css styling sheet, with some default styles that we want to be applied in the whole project 

`css variables`
- we can declare our custom css variables for colors that we want to make default for our project, as the example below.
	- to use them after declaring, we will use the following syntax 
		- `background: var(--gray-300)` 
```css
:root {
	--white: #ffffff;
	--gray-100: #e1e1e6;
	--gray-300: #c4c4cc;
	--green-500: #00875f;
}
```

`A note about using metric units on css - REM` 
- when we use *1rem* means that we're using ONE metric unit relative to the default font size for html, that is 16px
- this means the size of font will be relative to the device, and allows to if people have theis devices configured to increase/decrease the font size to still do this in your website.
- it's a good practice to use this relative metric units in every aspect of our application, like for buttons or spacing, because in this way our appplication will grow or shrink as a whole in all elements if the user have some custom configuration in his device

`Importing images in react components` 
- just as we did with the Css files, we also need to give it a name when we import images to our components, like the example below
	- `import igniteLogo from '../assets/ignite-logo.svg'` 

`Icons with Phosphor Icons`
- to use this library in our project we first need to install it with the command below
	- `npm i phosphor-react` 
- then to use it we will first do the import like is shown below
	- `import { [name of the Icon] } from 'phosphor-react'` 
- then to use the Icon, we just use the name as if it was a tag for a element, if we had got the Icon *PencilLine*, we would use it as below
	- EG: `<PencilLine />` 

`Flow to create a UI for a component`
- we can follow this flow, it's not meant to be the best, but I thought it's a cool way to think how the structure should be
	1. Create the html structure that will be needed to show all the content that you want, using static information *(HTML)*
	2. After you have the structure, we go in and do the style (css) for the elements *(CSS)*
	3. Then we will go over the functional part of the component, to create all the interactions that the user can have with our application *(INTERACTIONS)*

`Override outline of elements`
- the elements, if you *focus* them in the html or use *tab* key, you will notice that they'll have a outline that is a white mixture with something else
- we can override this to let our application have a better UI using a color from our default colors in the *global.css* with the code below
```css
:focus {
	outline: transparent; /* here we hide that ugly outline */
	box-shadow: 0 0 0 2px var(--green-500); /* here we add our color for the outline */
}
```

`Hidding and showing elements`
- we will be using the tecnique showed below to hide and display the button for publishing the comment. It's a way that we can do this to be displayed according to what the user is doing
```css
/* Here we'll use this footer to apply the properties to hide the button and don't occupy the space, in the button it hides him but still takes the space in screen */
.commentForm footer {
	visibility: hidden;
	max-height: 0;
}

/* here we are telling css that when we have 'focus' in a element inside the 'form', the 'footer' will be displayed */
.commentForm:focus-within footer {
	visibility: visible;
	max-height: none;
}
```

`The TWO MOMENTS where in react we create a component`
- the fist one that is the easiest one to see when to to this is when something is repeating in our UI across more components or pages, and usually has the same *visual* and same *behavior* or *functionalities* 
- the second one is when we're able to get something *OUT* of a bigger component without that bigger component stop working, where in this way we leave the *BIGGER* component more clean and with a clearer function, easier to give maintenance 
	- EG: a screen where we have a listing of users and in the top of the page we have a  button to make upload of users using a .xls document. 
		- so in the button we'll identify when the user clicks, we'll make the upload of the document to pass it to our backend to register all the users...so we can clearly see all the functions that the button has, and that all it does has nothing that influence in the listing of the users. 
			- So here it's the case where even if we don't use again this button somewhere else, we can put it in a component because this will not change the flow for the *listing component* 

`DEFAULT values for props` 
- we can do this in two ways, in our component we do 
```jsx
	// if different than 'false' or 'undefined', it's true
	const hasBorder = props.hasBorder != false; 
	<img
		className={hasBorder ? styles.avatarWithBorder : styles.avatar}
		src={props.src}
	/>
```
- or the second way, we can use the *destructuring concept* and define a *default* value for the property
```jsx
export function Avatar({ hasBorder = true, src }) {...
```
`Responsiveness` 
- a good trick to have our site be responsive, in this layout where we're using *grid-template* is using the code from below, where we use the *@media (max-width: 768px)* to identify that the user is in a *mobile browser* and apply a rule to it, where in our case we change the template to have *only one* column and in this way, the sidebar goes to the top of the page with the posts below her, leaving a nicer look to our user
```css
@media (max-width: 768px) {
	.wrapper {
		grid-template-columns: 1fr; /* 1fr -> uses the whole space*/
	}
}
```


`Iteration` 
- the method *forEach* iterates throught an array, but it has as default *NO RETURN*. So if we try to use him to render react components, we'll end up with a empty screen
- NOW we have another function to iterate throught arrays and this one *DOES HAVE RETURN* and it's called *.map* 

`Intl` 
- is a namespace for ECMAScript Internationalization API that provides us with string comparison, number formatting, date and time formatting. 
- will help us to format dates, time, numbers and so on when we need based in the language from where the person is accessing the application
- we can look into the documentation for more information
	- https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat
- we'll show a example of use below
```javascript
	const publishedDateFormatted = new Intl.DateTimeFormat('pt-BR', {
		day: '2-digit',
		month: 'long',
		hour: '2-digit',
		minute: '2-digit'
	}).format(myDate)
```


`date-fns`
- as a second option to a date formatter, we have *date-fns* 
- if we choose to use it, we can install it using `npm i date-fns` 
- we can see the documentation for more infos 
	- https://date-fns.org/docs/Getting-Started
- we'll have an example below, and with *date-fns* it's simpler to format a date to the way we want it. As we see it, we can convert the type of the date based in a *locale* that is the location of the user 
```javascript 
// we need to import from 'date-fns'
import { format } from 'date-fns'
// import ptBR from 'date-fns/locale/pt-BR'

const publishedDateFormatted = format(
	publishedAt, "d 'of' LLLL 'at' h:mm"/*, { locale: ptBR, }*/)
```


`useState` 
- is the possibility to store data in a variable that react will *REACT* to changes and refresh the UI automatically for us
- it's variables that we want the component to keep an eye on the changes


`Tips` 
- *Can I Use?* : website to know if a browser supports a tech or syntax
- *n node manage package* : manager to use with nodeJS. It's easier to change between versions of node using this manager, take a look someday
	- https://github.com/tj/n
- *INSPECT IN CHROME*
	- if you inspect a element using *grid* to align items, in chrome we have a option that is displayed in the sidebar *Styles* of the *Elements* when inspecting a html component that if we click the button (it's like a ...) beside the style *display: grid* we can try it our the different styles and see the changes in real time in our browser, without needing to add in our code 


- *TIP FOR USING REM metric units* - how to easily convert them
	- as 1rem get's the default font value for html that is 16px, we can add a tag *html {}* where we set the *font-size* to 62.5%. 
	- when we set to this value, 62.5% from 16px it's 10, bringing the REM metric unit to something closer to what we are more used to use in our daily life
	- in this way 1rem it's 10px, as 0.1rem it's 1px
	- it get's way easier to convert them, like it's showed in some examples below
		- EG: 
			- 48px it's the same as 4.8rem
			- 61px it's the same as 6.1rem
			- 1248px it's the same as 124.8rem

- *TIP for multiple cursors in VSCode*
	- if you need to change something in VSCode and don't have the ability to use the *Command+D* option to do multi-line changes, we can just hold the key *Option* and click in all the lines that you want to edit simultaneously 

`Repository for the project`
- we can find the code for the project in:
	- https://github.com/0xREALAldc/ignite-01-reactjs-fundamentals


