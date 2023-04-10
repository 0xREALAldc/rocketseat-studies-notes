`Styled Components` 
- it's a way for us to style our applications in react using a concept known as *css in js* .
- *css in js* is basically us writting our css in the javascript syntax
- to begin using it, we need to install it
	- `npm i styled-components` 
	- since we're using typescript, we also need to install the types for the *styled components*. We're going to install this package only as a development dependency because in *production* our code is 100% compiled in JS
		- `npm i @types/styled-components` 
- So why we're going to use *Styled components* ?
	- we're going to use it to make it simpler to style our components using JS
	- when we need to apply many styles to a component or even give it a style that is conditioned to a variable, it's easier to us to apply this styling. When you think of one property that changes the styling it seems that all the trouble to use *styled components* isn't worth the work, but when we have more properties that can change styling it will make our job easier
	- one thing to notice is that always when we use *interpolation (${})* in a styled component, react will run it as a function and pass all the *props* that the styled component have in it so we can use these values
- Configuring themes
	- we can create a folder inside *src* with the name *styles/themes* and inside we create a file *default.ts* that will be the default theme for the application
	- to use we'll need to import the *ThemeProvider* from *styled-components* and wrap around the components that we want to apply our theme
	-  to access the colors that we declared in the *default.ts* file inside one of our *styled components* we can access it using *props.theme.* and the name of the property declared inside the file of the theme choosen at the moment 
- Types of Themes
	- when we use Typescript we have the possibility of defining our own themes in our project
	- we can name it *@types* but you can use whatever you think it's better
		- inside we will declare our files with the extension *.d.ts* this meaning that inside this file we're only going to have code defining types for typescript
		- and the *theme variable* that we had defined in the *default.ts* had some properties in herself, being *primary and secondary* both string. If we want to put this *typing* into a variable, we can use a function of typescript called *typeof*
			- we define a *type variable* and then use this function to assign the type 
				- `type ThemeType = typeof defaultTheme;` 
			- so we can use this typing in our project, we need to *declare* a module that we'll override something or we'll replace the typing, in our case as we will have imported the *styled-components* and we'll use the *declare module styled-components* we will only override a type that is the *DefaultTheme*
- Global styles
	-  inside the folder *styles* we'll create a file named *global.ts*
	- and inside we'll be importing a function from *styled-components* called *createGlobalStyle*
		- and inside we use the same syntax that we did for a styled-component `export const GlobalStyle = createGlobalStyle` and inside we put all the styling that we want to apply to every html component from our application
	- to apply this global style to our application, we can import it anywhere in our application but we'll put inside the *App.ts* and it's important that it stays inside the *ThemeProvider* so we still have access to the variables from the theme

`ESLint - ECMAScript Linting` 
- it's something that verifies that our code is following some code patterns defined by the creators of the project
	- like default spaces in the beginning of the line
	- use or not of the `;` that is not mandatory in JS
- to use it we can install with the command below
	- `npm i eslint -D` as a developer depencency 
	- we will also install another package that is a configuration created by the folks at Rocketseat with some patterns for writting code. 
		- `npm i @rocketseat/eslint-config -D` 
		- after we will need to create a file called `.eslintrc.json` and inside we will write the code below to use the installed package. We use the name of the packaged with the `/react` in the end because this file has configuration for other languages too, and we want to use only the one for react
			```json
			{
				"extends": "@rocketseat/eslint-config/react"
			}
			```
		- to check for errors we can use the following code, and it will show us what we have wrong in our files. We use the command *npx eslint* then the folder *src* and after the extensions *--ext .ts, .tsx* 
			- `npx eslint src --ext .ts, .tsx` 
		- to fix everything, we can run the same command from above but with the flag *--fix* in the end
			- `npx eslint src --ext .ts, .tsx --fix` 
	- If you want you can create your own configuration too, you just need to run the command below and go answering the questions that are shown and in the end Eslint will generate a config file for you
		- `npx eslint --init`  

`React Router DOM` 
- can be used in *web* or *react native* for mobile
- to use this package we will install the package with the following command
		- `npm i react-router-dom` 
- then to structure our project we will create a folder named *pages* inside *src* 
- to organize better our project, we will create a file to have all our routes called *Router.tsx* 
- components like *ThemeProvider* or *BrowserRouter* are components that doesn't provide us nothing in the UI but are components that provide us with contexts that are used by our visual components