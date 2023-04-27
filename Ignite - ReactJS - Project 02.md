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
	- `reset` is a function that we can use to reset all the fields of our form after we have done what we should after the submit
		- it's important to remember that this function will reset the fields to the value that we have difined in the *defaultValues* for each field
- path: https://react-hook-form.com/

`Validation for forms`
- as default, *react hook form* doesn't comes with validation for forms
- it gives emphasis in doing the work of handling the forms and fields but uses another packages that are very good for validation integrated with itself
- there are many packages for validation as *yup, joi, zod* that we can choose to use
- we're going to use *zod* becasue it has a better integration with TS, but only because of this. In general, they all do the same things
- to install *zod* we use the command `npm i zod` 
- to integrate the *zod* with *react hook form* we need another package that is called *@hookform/resolvers* 
	- install it with `npm i @hookform/resolvers`
	- and we need to import *zodResolver* from *'@hookform/resolvers/zod'* 
	- then in the line where we use the *useForm* we need to pass a object with configurations, to tell that we're going to use the *zodResolver* to integrate *zod* to our form. 
		- also, in our *zodResolver* we need to tell what is the schema that we're going to use to validate the fields of the form, as we show below in the example 
	```ts
	const {register, handleSubmit, watch } = useForm({
		resolver: zodResolver()
	})
	```
- to check the errors that the validation will show to us, we need to get the variable *formState* from the *useForm* and inside it will have the value *errors* that will have all the errors that our validation can throw
	- `console.log(formState.errors)` - we can console log in any place of our component to see it in our console in the browser
- in the *useForm* we can also pass default values in the property *defaultValues* to assign what are the initial values of the fields that we will have in the forms

- `interface` use this definition when we're defining the structure of a object
- `type` use this definition when we're creating a type from other reference, from other variable or something like this
- `typeof` use always when we want to reference a JS variable for something in typescript

- in our project, instead of we writing a interface to define the structure of our object that is all the fields in the form we can use *zod* to infer the type from the validation schema that we have defined earlier for *zod*
	- below I'll leave the example of how we can create a *type* just be infering from the validation schema using *zod* 
		```ts
		type NewCycleFormData = zod.infer<typeof newCycleFormValidationSchema>
		```

`useEffect` 
- it takes two parameters, the first one a *function* that is going to be called and the second is what *variable* is going to watch over to execute the function
- if we need to change a state and right after use this new value, we can use a *useEffect* to monitor the value of this state variable and in the use effect, when the variable is changed right after it will call the *useEffect* function and THERE we will have the updated value for this state. 
	- this is different from if we tried to get the value of this state right after we called his *set...* function, because it would still have the old value, but with the use of *useEffect* we can get access to the new value
- a good advantage of *useEffect* is that we can tell the component WICH variable is needed to watch over to do something
- every *useEffect* is ALWAYS executed in the first time that the component is rendered on screen
	- if we don't want our hook to be called in the first time that the component is rendered we can use a *if* condition to see if the variable that we're supposed to watch over was changed as we wanted
- BEWARE of this, it's uncommon, VERY uncommon to use a *useEffect* to update a state
	- if we're needing to use a  *useEffect* to update a state variable, we need to look better to this code because we probably are doing something wrong 
- ALWAYS that we use a external variable inside a *useEffect* we need to include this variable in the dependency array
- INSIDE a *useEffect* we always have a *return* that is a function, known as *clean up function*. This is cited in the react useEffect documentation, and describes that all that we do *inside* our useEffect is the *setup function* while the function that ran in the return is called the *cleanup function*. 
	- in the first render of the component, useEffect will be ran but will only run the *setup function*
	- this *cleanup function* will run only in a second or whatever number of re-render of your component and also when the component is removed from the DOM react will run the *cleanup function* from the useEffect

`Prop Drilling in React`
- it's a common problem that is when we have many props only for communication between components
- when we have only *one* or *two* props that a component needs to be passed to him to fully work, it's okay that we pass it as props, the problem starts when we need too much props
- we can resolve this problem using *Context API*

`Context API`
- allow us to share informations between *MANY* components at the same time
- we don't need to use props to pass information between components, it's like our informations are global variables that all the components have access, modify and when changed and indiferent from which component has made the change all the components that are relying on this information will be updated
- it's like a way that we can talk to many components in our application at the same time
- inside *Context API* we can put *ANYTHING* that we want, like variables or states or any information that we want
- How do we use it?
	- first we will need to import a function called *createContext* from *react*
		- *createContext* is the method that will be used to create our context, that we need to assign to a variable. Usually the name of this variable will make sense to what information we're going to store inside this variable and usually it's the first name followed be the suffix *...Context* 
			- when calling *createContext* the value inside the parenthesis is the *initial value* for the context.
			- because we use context more when we have MANY values that we want to share between components, we usually store a object as the initial value for *createContext* then inside the object we will describe all the values that we're going to have in this context, as properties
			```ts
			const CyclesContext = createContext({
				activeCyle: 1,
				// other properties will follow
			})
			```
	- THEN to use the context in the components, we will need to import another function from react called *useContext* 
		- then inside the component that we want to use the context, we call as below the method passing the context that we've created before as parameter 
		- from this call we can destruct the return and get the properties from the context that we need to use in that component
		```ts
		const { activeCycle } = useContext(CyclesContext)
		```
		- but there's one *caveat* in this. If the variable that we've created as above is of a primitive type, the value that we've assigned to her will always be the same, we cannot change it.
		- to change a value from a variable on a context, we need to use *state*. And this state *HAS* to be created in the component that is the *PARENT* of the other components that need to access this *state* 
	- THEN to give the children components access to the context, we need to use a component that comes from the context that we've created, in this example *CyclesContext* that's called *CyclesContext.Provider*. We put this component wrapping aroung all the components that we want to allow the access to this context 
		- this component has a property called *value* that is where we specify the informations that will be shared to the children components
		- here also we usually use a object to send all the informations that we want to send, as our newly created *state* 
		- usually we try to put in a *context* stuff that will not change if we change a library for another or something like it 
	- When we're using forms and a part of it is not in the main component where we have defined the *useForm* from *react-hook-form* we can use a *context* that react hook form gives us to pass the properties from the parent component to the child component. 
		- In our case, our *NewCycleForm* needed to use the *register* function to register the fields of our form, so we used the *FormProvider* around the component *NewCycleForm* and more above, we assigned the *useForm* to a variable before destructuring the methods that we would use in the parent component, and then in the *FormProvider* we passed using the *spread operator* all the properties of *useForm* as below
			```ts
			const newCycleForm = useForm<NewCycleFormData>({...})
			...
			<FormProvider {...newCycleForm} >
				<NewCycleForm />
			</FormProvider>
			```
		- And in the *NewCycleForm* we will use the function *useFormContext* to get the variables and functions that we need from the context. This *useFormContext* only works in a component that is wrapped around with a *FormProvider* in the parent component
			```ts
			const { register } = useFormContext()
			```
	- NOTE TO REMEMBER : we usually use more *props* in react, *context* is not the main way we pass things from component to component. We have to remember that we only use *context* when we see that we will have MANY variables, functions and stuff that we will need to share between the components, but always the first way to do things is using *props* 


`Context between Routes` 
- we have shared the context between the components used inside the page *Home*, but in our application we also have the page *History* that needs to have access to the *cycles* variable to create the history of all the cycles 
- what we can do is create a new folder called *contexts* to hold only our contexts
	- inside we will create the *CylcesContext.tsx* and here we will put all the code that's used only for the context and what was not exported to the context, we will export 
	- in this way, we will be able to go in out *App.tsx* and use our *CyclesContext* wrapped around the *Routes* component, and in this way we will give access to the context to all the other pages of our application

`TIP` 
- to use a *ternary condition* that only has the THEN option, we can use two *&* to make JS understand this. In the case below JS only will run the `<Status statusCode="Green"/>` if the condition is true, in this case different than *undefined* 
	- EG: `{ cycle.finishedDate && <Status statusCode="Green"/>}` 

`Reducer (useReducer)` 
- we use just like the *useState* to store a information and change it later
- we use reducers to store more complex information and mostly for the ones that when we need to change something, it's harder 
	- when we see that the changes that we make in a *state* they rely on the old state and the changes are done with more code, calculation and stuff
	- we can use a reducer to have a function, just like in our project we have the function *interruptCycle*, abstracted inside the reducer to be easier to use in more than one place. Using the example of our *interruptCycle* function, today if we want to use this function in other place we would have to copy and paste the code in this second place to have the functionality 
- the *useReducer* receives two parameters
	- the first one is a function
		- this function receives two parameters, 
			- *state (the current value of our variable)* 
			- *action (the action the user want to do to alter our variable)* : this we will give the names we want for the functionalities that we want to implement and run
	- the second is the initial value for our variable that is kind of like our *state* 

1. Notes about the code below
	1. the *cycles* is the variable with the value, our "state"
	2. the *dispatch* is kinda like our *setCycles* but the difference is that we will call it passing the name of the functionality that we want to run from our reducer
		1. when we call dispatch the function in our reducer will run and the value passed as a parameter in the *dispatch(parameter)* will be in the *action* variable of our reducer
		2. the usual way we pass values as parameter in the *dispatch* is passing a object and inside we put our values
			1. *type*: we describe what we are sending to be able to distinguish inside the reducer
			2. *payload* : we put the data that we need to send
```ts
const [cycles, dispatch] = useReducer((state: Cycle[], action: any) => {
	
	return state

}, [])
```

`Saving objects inside of a Reducer` 
- we can create a interface of a object with more than one property and pass as the type for the variable (our state inside the reducer) and in there, we can store more than just one value
	- in our project, we removed the state for *activeCycleId* and we are using this variable inside our interface that we created to have a object with the array of *cycles* and this *activeCycleId* variable

`Splitting Action Types`
- first thing we did we got our function that was the *first parameter* in our *useReducer* and splitted in a new file, inside */src/reducers/cycles.ts*
	- this to make it easier to see and understand both this function and the *CyclesContext.tsx* that was growing too much
	- to make it easier our life, we also created a *enum* for our ActionTypes so in this way we don't need to remember how each action is written, we can use our enum across our application

`Splitting the Actions` 
- in the first way we dit the calls with our *dispatch* we would have to remember what to send in the *payload*, but we're going to make it better
- inside the *src/reducers* folder we're going to change the name of the file we created above with the name *cycles.ts*, now we're going to change it to a folder named *cycles* and inside create two files, one called *reducer.ts* with the contents for the function that was inside the *cycles.ts* and another with the name *actions.ts*
	- inside this *actions.ts* we're going to define functions that we will call in the *dispatch* and they will already have the type of WHAT we need to send with it and make our lifes easier
	- I'll leave a example below, where we will be able to see that our action *ADD_NEW_CYCLE* needs in his payload a object with the type of *Cycle* 
```ts
export function addNewCycleAction(newCycle: Cycle) {

	return {
		type: ActionTypes.ADD_NEW_CYCLE,
		payload: {
			newCycle,
		},
	}
}
```

`Using the library Immer` 
- is a library (or package, you choose the naming) that is used to work with immutable variables, something that is very used in react
- it's a library to make it easier for us to make changes in immutable variables making it seem like we're changing the value of a usual JS variable, but behind the scenes, Immer is doing just what we do using a `state.map((cycle) => {...})` but we get a way much simplier to do just that
- to install Immer we use the following command
	- `npm i immer` 
- Below we're going to have a example of how Immer makes our life easier when we need to change a value of a *immutable state* 
```ts
			// USUAL WAY WE CHANGE A VALUE OF A IMMUTABLE STATE 

case ActionTypes.ADD_NEW_CYCLE:
	return {
		...state,
		cycles: [...state.cycles, action.payload.newCycle],
		activeCycleId: action.payload.newCycle.id,
	}
```

```ts
			// NOW USING IMMER
case ActionTypes.ADD_NEW_CYCLE:
	return produce(state, (draft) => {
		draft.cycles.push(action.payload.newCycle)
		draft.activeCycleId = action.payload.newCycle.id
		})
```
- if we take a look at the second piece of code, we see that we are using *.push(..)* in the *cycles* array as if it was a *mutable* variable and in the same time we're using *=* to assign a value to *draft.activeCycleId* too
- this is only possible because Immer after will treat all of this as Immutable variables, doing what we used to do in the first piece of code, but for us it's way easier now to change values 


`TIP` 
- typescript error translator > helps you to understand some typescript errors that are not that clear to us
	- https://ts-error-translator.vercel.app/
