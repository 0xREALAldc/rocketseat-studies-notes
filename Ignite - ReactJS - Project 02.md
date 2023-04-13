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
- components like *ThemeProvider* or *BrowserRouter* are components that doesn't provide us nothing in the UI but are components that provide us with contexts that are used by our visual components (context providers)

`Routes Layout`
- we create a new folder called *layouts* inside the *src* folder
- we will use the component *Outlet* that comes directly from the *react router DOM*, and he's kind like a blank space where we can put some content in that space 
- so how this will work to put our *Header* in each of our pages? 
	- we will go in our *Routes.tsx* file and then add another *Route* tag, but this one will be around all the routes that we want to put our *Header* in. 
	- what happens is that using this structure, when we go in our *localhost:3333/* or *localhost:3333/history* we will have our *Home* component displayed to the user and also in the place of the component *Outlet* that we also have in the *DefaultLayout*, will be shown the component that cames in the route that the user is accessing in that moment. Cool isn't? 

- `NavLink` 
	- used as the *link 'a'* tag for the react router DOM
	- we use to be able to navigate to other components
	- when we're in one of the pages, react automatically set a *active* class in the tag, that we can use in our CSS to display something to show the user that we are currently in that page, if we use a icon as in this project we can change it's color like below 
		```css
		&.active {
			color: ${(props) => props.theme['green-500']};
		}
		```

`Styled components` 
- a cool thing that we can do is cascading styling in *styled components*, that is when we're inside a component we can style some tag that will be inside that component, as a *form* a *span* or whatever you want
```css
export const HeaderContainer = styled.header`

	display: flex;
	align-items: center; 
	justify-content: space-between;

	nav {
		display: flex;
		gap: 0.8rem;
		
		a {
			width: 4.8rem;
			height: 4.8rem;
			
			display: flex;
			justify-content: center;
			align-items: center;
			
			color: ${(props) => props.theme['gray-100']};

			border-top: 3px solid transparent;
			border-bottom: 3px solid transparent;
			
			&:hover {
				border-bottom: 3px solid ${(props) => props.theme['green-500']};
			}
			
			&.active {
				color: ${(props) => props.theme['green-500']};
			}
	}

}
`
```

- another cool feature that styled components has it's the possibility to create a *custom component* that can be used locally by other components that share a bunch of the same styling, as the example below
```css
	const BaseInput = styled.input`
		background: transparent;
	`
	
	export const TaskInput = styled(BaseInput)``
	export const MinutesAmountInput = styled(BaseInput)``
```
- there are some cool tricks of css on this project, in case of need for reference later
	- the *styles* for the *Home* and *History* pages have some really cool things
	- in the *History* styles we created a element inside a span that's really cool and that receive a property to change it's color
		- we just need to create a interface to describe the properties that this styled component will be able to receive and then pass to the styled component using the generic syntax `export const Status = styled.span<StatusProps>` 


`Controllet and Uncontrolled forms` 
- *Uncontrolled*
	- we only get the value from the input when we need it, like in a form we would get the values from the inputs only when the user do the *submit*
	- but we loose the good flow that we have with the *controllet components*, but we win in the performance side
	- 
- *Controlled* 
	- this is when we keep the state of what the user is doing every moment inside a state variable on our component, in real time
	- what are the benefits of using this type of controll?
		- we have easy access to the values that the user has inputed to us
		- we can easily reflect to the user changes in our interface based on these inputs
		- is very fluid 
	- what are the bad side ?
		- every time we change a state, we make react render the component of the state that has changed
- When we use one of them instead of the other?
	- controlled > simple forms with only a few inputs, like a login page, a register page
	- uncontrolled > dashboards that have MANY inputs that are something that you don't need to keep a control of every type that the person gives 

`React Hook Form` 
- it's a package that is able to work with our forms in both ways *controlled* and *uncontrolled* 
- we need to install it with the command below
	- `npm i react-hook-form` 
- *hooks* are functions that add some functionality to a component, this is why they all begin with the prefix *use* 
- *useForm* will return for us a object that we can destructuring to get only the variables and methods that we will use
	- when we're using this *useForm* it's like we are creating a form in our application
	- `register` is the method from the object that *useForm* returns that will add the fields that we will have in this new form
		- the syntax to use this function is as follow `{...register("name_of_input")}`
			- as a second parameter in this call, we can pass a object for configurations, and in our project for example we will use to pass a variable to configure the type of one input, called *valueAsNumber: true*, so this field can be a number 
				- syntax `{...register("name_of_input", { valueAsNumber: true })}`
		- it returns methods that are used to handle inputs in JS, as *onChange*, *onBlur*, *onFocus*...
		- because of this return of methods that the function has, we use the syntax as above with the spread operator (`...register("name")`) to pass all the methods to the input, it would be like we pass each of them by hand to the field
	- `handleSubmit` is a method that we will use in the *onSubmit* of our form and as parameter of this function, we will pass one function that we create to handle the submit of the form
		- then our function will be able to receive a parameter called *data* that has the values of all the form fields
	- `watch` is a method that we can use to, as the name say, *watch* the value of a field
- path: https://react-hook-form.com/
