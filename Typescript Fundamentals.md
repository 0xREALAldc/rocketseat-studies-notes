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
- and you can alternate between the two types without a problem, meaning, send a *number* as parameter and after send a *string* as parameter

`Generics` 
- is used to allow us to have the type of a variable more flexible, similar to the *union operator*, but generics have a difference that it'll define the type in **run time** *BUT* after the *FIRST* time that was assigned a value to that variable, it'll only *accept other values in the SAME TYPE* 
	- to create *generics* there are some conventions to the name, like below
	- `S` > usually used for *state*
	- `T` > usually used for *type*
	- `K` > usually used for *key*
	- `V` > usually used for *values*
	- `E` > usually used for *element*
- we will just assign a *placeholder* for the type using the letters cited above, and then when we create the object, the line `let newState = useState<string>()` we declare the type that we want, in this case was *string* 
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
- *IF WE WANT STILL* to be able to accept two different types, like when we use the *union* above, we can use the following syntax using the *extends*.
	- `function useState<T extends number | string>() {..`  
	- *BUT IN THIS CASE* it would make the object only accept *string* or *number* as type, but *STILL* after you create the object choosing one of the types, you would only be allowed to assign values of that type to the variable.
- *WE ALSO CAN SET A DEFAULT* type when the user does not define one while creating the object, like this line below where we declare the default value as *number* using the *...= number* syntax
	- `function useState<T extends number | string = number>() {..` 

`Creating Type's` 
- we can define our own types when using typescript, using the syntax below that we're defining a *type* that can be a *string* or *number* or *undefined* and then we can use when declaring variables
	- `type IdType = string | number | undefined;` 
	- using in a variable declaration `let userId: IdType;` 

`Creating types for Objects using Types` 
- just like above when we created a type for a variable, we have a example below of the syntax for creating a *type for an object*
```typescript
type Point = {
	x: number;
	y: number;
}

function printCoord(points: Point) {
	console.log(`The x axis is: ${points.x}`)
	console.log(`The y axis is: ${points.y}`)
}
```

`Optional` 
- when a property in a type is *optional*, not *required*
- we just need to add a *question mark ?* before a property in a type, just like the example below where *isAdmin* is optional
```typescript
type User = {
	name: string;
	email: string;
	age: number;
	isAdmin?: boolean;
}
```

`Type Assertions` 
- it's when typescript can't understand by itself which type somthing is, and then you 'say' for it what type it is, kind of like a conversion
- it's very used when consuming API's
- we got a example below where we *assert* that the *userResponse* is type of *UserResponse* using the syntax of the value of the variable *as TYPE* 
	- when we give a *type* to an API response, we don't need to describe every property that comes in the API response, we can only define in our type the ones that we're going to use
```typescript
type UserResponse = {
	id: number;
	name: string;
	avatar: string;
}
// we simulate that the variable below is the return of a API that typescript won't know the structure or type of 
let userResponse = {/*content here*/} as UserResponse
```

`Intersections of types` 
- it's when we combine two types in one variable declaration like the example below where we declar the types *User* and *Char* and then we declare the type *PlayerInfo* where we declare that this new type is a combination of the first two that we've created just by using the syntax `type & type` 
- when we declare a variable with the type *PlayerInfo* it'll have the properties from both of the types declared before
- also we have added other example where we use a type that was defined and add another one that is not defined before, using the `type PlayerInfo = User & {...type here...} ` 
```typescript
type User = {
	id: number;
	name: string;
}

type Char = {
	nickname: string;
	level: number;
}

//now we declare the type PlayerInfo that is the combination of the first two
type PlayerInfo = User & Char;

OR WE CAN DO THE WAY BELOW ALSO
type PlayerInfo = User & {
	race: string;
	age: number
}
```

`Interface` 
- is another way to declare and create types
- the declaration varies a little from the type 
- we also can declare *properties* that are *optional*
- we can also create *TWO OR MORE* interfaces and declare a *NEW* interface that is the combination of the other interfaces like the example below using the syntax `interface Account extends User, Payment {}`, where different from when declaring with *type* where we use the *&* here we use *extends* 
```typescript 
interface User {
	id: number;
	name: string;
	canGiveMoney?: boolean;
}

interface Payment {
	method: string
}

interface Account extends User, Payment {}
```

`
`What's the difference between TYPE and INTERFACE`
- the objective for both is the same, helping us to create *types*
- there's a little difference when declaring a third *interface or type* using *types* or *interfaces* that we're declared before
- *type* is more recommended to be used because it's more simple, it's easier to use with primitive types, more flexible
- *interface* it's more used for development of libraries, when we use more classes

`tsconfig` 
- it's a configuration file where we can put all the rules that the typescript will have to abide in our application

`Converting a JS project in a TS project`
- first we need to install the *typescript* package
	- `npm install typescript --save-dev` 
- after we need to create the file *tsconfig.json* that will have the rules for the typescript in our application and we do the configuration according to the framework that we used to create the project, *vite, create react app, ....* 
- after this, we'll go inside our *components* folder to add *type* for our components 
	- first thing we need to do is rename the file from *.jsx* to *.tsx*
	- we create the type that we need for each component according to the properties that are used inside that component
	- probably we also get an error because we're missing the *types* of the language that we're using, in the case of this project is *@types/react* that is needed because now we are using typescript
		- `npm install --save-dev @types/react` 
- we will do the same that we did above in the *components* folder but now for the *pages*
	- we can also create types inside a file and use `export type NameType...` to use in other files 
	- below we're going to have an example of how we give a *type* to a state that's an object. We then can initialize the object using only the `{}` but we will tell the type after, that is `User` 
	```typescript
		type User = {
			name: string;
			id: number;
		}
		
		const [user, setUser] = useState<User>({} as User);
```
	- below we're going to have a example of how we give a *type* to a *state* that's an array. In the example below the *CardProps* is our type, and we add an *[]* after to show typescript that's an array of that type
```typescript
		const [students, setStudents] = useState<CardProps[]>([])
```

