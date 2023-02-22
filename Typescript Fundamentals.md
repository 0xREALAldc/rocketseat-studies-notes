`What is Typescript?`
- created by Microsoft with the objective to bring a super set of types for JS
- is also called as a programming language
- without defining types in JS, some errors can pass by without we noticing them, as passing the content of a variable in the wrong type, forget a parameter of a function, mistakes that we'll problably only find while executing the application
- with typescript this type of errors will not occur, we will notice them while still in development
- interesting is that *WE DON'T NEED* to use types for everything, but since you're using typescript it would be better to do so
- in the end, everything will be compiled down to JS

`Why use Typescript`
- `Quokka.js` 
	- is a extension that wil run the JS in the VSCode, so we don't need to run it in a web page or somewhere else
```javascript
function sum(a, b) {
	return a + b
}
console.log(sum(1,2))     // = 3
console.log(sum('1',2))   // = 12
console.log(sum('1','2')) // = 12
```
	- the error above only happens because we don't have the *type* for *a* and *b* defined, so when we have a parameter that is a *string* JS will automatically understant that we want to concatenate the two values

- we are able to find bugs using typescript before running our code becasue typescript is a static checker of code
	- it checkes before run time 
		- the type expected of a variable value
		- the parameters that are expected in a function
		- the types of the parameters expected in a function to be passed right

- there are some tricks that we can do using TS, like the one below where we can define a *default value* to something that is passed as parameter, in this case *user* 
```typescript
function showTicket(user: string | null, ticket: number) {
	console.log(`Hi ${user ?? 'Default User'}. Your ticket number is ${ticket}`)
}
```
	- this in JS would have a more complicated validation to be written, like is shown below
```javascript
function showTicket(user, ticket) { 
	console.log(`Hi ${user !== null && user !== void 0 ? user : 'Default User'}. Your ticket number is ${ticket}`); 
}
```

`Explicit type` 
- is when we declare the type of a variable, like if I tell a *variable: string* it'll only accept strings

`Any type` 
- in typescript, the default type of a variable is *any* when we don't excplicitly describe the variable type
- this type will literally accept any type of content

`Type inference`
- we can declare explicitly the type of a variable 
	- `let user: string = "0xREALaldc";` 
- but *type inference* is something that exists in typescript, and this is when we just declare a variable and assign a value to it but we don't define the type. Typescript will infer that the variable is the same type of that value
	- `let user = "0xREALaldc";` 
- both the above cases, if you hover with the mouse pointer above the *user* variable, it'll tell you that the variable type is *string* 
- after it will also validate the values assigned to that variable, and in this way it'll only accept the values of the same type of the first attribution 

`Primitive types`
- the basic types that are available for us to use, like
	- boolean
	- string
	- number
		- THIS one is for *whole numbers* or *numbers with decimals* 

`Arrays` 
- we declare them using the below syntax
	- `let numbers: number[]` : this one only accepts *numbers*
	- `let numbers: string[]` : this one only accepts *strings* 
- we can also declare in this other way
	- `let users: Array<string>` 

`Functions` 
- when we have a function that has no *return value* we give the type *void*
	- `function showMessage(messsage: string): void` 
	- if we declare the function and don't use the *return* keyword inside, it's *inferred* that the function is *void*. If you hover on the function name, it'll show it in the information message
		- `function showMessage(message: string)` 
- IF WE don't explicitly declare the *return type* to a function it'll be *INFERRED* that the type of the value assigned to the *return* keyword is the type of the function return
	- we can declare a function like the example below and hover over the name of the function, it'll show in the information message that the *return type* for the function is *number*
		- `function showMessage(message: string) { return 10; }

`Union` 
- is a operator that will allow us to tell that a *variable* or *parameter* can accept more than one type values
	- `function printUserId(id: number | string) { ... }` in this function, the variable *id* can be a *number* or a *string*

`Generics` 
- is used to allow us to have the type of a variable more flexible, similar to the *union operator*, but generics have a difference that it'll define the type in **run time** *BUT* after the *FIRST* time that was assigned a value to that variable, it'll only *accept other values in the SAME TYPE* 
	- to create *generics* there are some conventions to the name, like below
	- `S` > usually used for *state*
	- `T` > usually used for *type*
	- `K` > usually used for *key*
	- `V` > usually used for *values*
	- `E` > usually used for *element*
```typescript
function useState<T>() {
	let state: T

	function get() {
		return state
	}

	function set(newValue: T) {
		state = newValue
	}

	return { get, set }
}

let newState = useState<string>() // we set the type in the creation between '<>'
newState.get()
newState.set("hello")
newState.set(10)
```
