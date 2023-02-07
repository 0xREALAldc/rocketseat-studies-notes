- `synchronous` 
	- one task runs each time, the first has to finish so the next can begin
- `asynchronous` 
	- tasks are executed together, one doesn't has to wait the other to finish so it can start

- `callback` 
	- just for knowledge, functions in *JS* accept any type of data as paramater
	- *callback* means  a function passed as parameter that will run after some other things are done

- `setTimeout` 
	- it's a function that uses callback to run a function after some given time

- `https request`
	- in a *https* request we have a example of a callback where we make a request using some HTTP method, in the below example a GET, and the `res => ...` is a callback function, that will run after we get the *response* from the call
	- `https.get(API, res => { console.log(res.statusCode) })`

- `Promise`
	- it's a *promise* that something will happen in the future
	- there's four states for a promise
		- **pending** initial state, when the promise object is instantiated
		- **fulfilled** was accomplished with success
		- **rejected** was rejected or some error occurred
		- **settled** with success or error, the promise was finally finalized
	- it's a *javascript object* with the promise that something will happen
	- it's used in *asynchronous* operations as
		- load a file
		- read data from a API
	- `const promise = new Promise((resolve, reject) => { return resolve() OR return reject() })`
		- after declaring, we have to handle the *resolve* and *reject* responses, and ALSO the *finally* 
			- *resolve* we will work with using the syntax `promise.then(..something...)`
			- *reject* we will work with using the syntax `promise.then(...resolve...).catch(...handle..reject..)`
			- *finally* we will work with using the syntax `promise.then(..resolve..).catch(..reject..).FINALLY(..do..something)` 
				- the FINALLY will run **ALWAYS**, doesn't matter if the result was *resolve* or *reject*, it'll run anyway
				- eg of some chaining of promises, with one *.catch* to watch over them all
				```js 
				fetch("https://api.github.com/users/0xREALaldc")
					.then((response) => response.json()
					.then(data => fetch(data.repos_url))
					.then(repos => repos.json()
					.then(repos => console.log(repos))))
					.catch(err => console.log(err))```

- `axios` 
	- it's a *http client* based in promises
	- when you make a request using axios, it'll generate a *pending promise* 
	- we can nest calls using *axios* to let the code more readable, just like we did before with *fetch*
```js
import axios from 'axios';
axios.get("https://api.github.com/users/0xREALaldc")
  .then(response => axios.get(response.data.repos_url))
  .then(repos => console.log(repos.data))
  .catch(error => console.log(error));
```
- `asynchronous promises execution` 
	- to achieve this, we use the `Promise.all([ here_goes_the_promises ]` 
	- because we have an *array of promises* we will have an *array of responses* 
	- the *catch* in the end will catch any error that happens on any promise in the array
	- all the promises executions will run simultaneously, so it will only enter the *then* clause when *ALL OF THEM* finish their call
```js
Promise.all([
  axios.get('https://api.github.com/users/0xREALaldc'),
  axios.get('https://api.github.com/users/0xREALaldc/repos')
])
.then(responses => {
  console.log(responses[0].data.login)
  console.log(responses[1].data.length)
})
.catch(err => console.log(err.message))
```  

- `Async & Await in JS`
	- is a syntetic sugar (more elegant way) for writting promises 
	- *await* is as the word says, we will wait for the promise execute to get the result from her. 
	- this is a way that let us use a more readable manner to get the *result* and catch *errors* of run the *finally* of a promise. I'll show a example below of the promise *before* and *after* the use of *async/await* 
```js
const myPromise = new Promise(function(resolve, reject) { 
  return resolve('ok') 
  // OR
  return reject('error')
})

//OLD WAY
myPromise
  .then(function(response){
    console.log(response)
  })
  .catch(function(error){
    console.log(error)
  })
  .finally(function() {
    console.log('always run this one ')
  })
//Async/await
async function start() {
  try {
    const result = await myPromise;
    console.log(result);
  } catch (e) {
    console.log(e);
  } finally {
    console.log("always run this one");
  }
}

start();
```
- `async/await with fetch` 
	- another example as how is easier to understand the use of *async/await* in calls, this will be the example from before where we explained what is a *Promise*, the same example but did using *async/await*
	- it gives a more *synchronous* view to the code
	- the *async function ...* also returns a promise and this is how we can use the *.then* and *.catch* or *.finally* in the function call after
```js
async function start() {
  try {
  /*
    const response = await fetch("https://api.github.com/users/0xREALaldc");
    const user = await response.json();
    const reposResponse = await fetch(user.repos_url);
    const repos = await reposResponse.json(); 
    */
//we also can make it more short, as below 
    const user = await fetch('https://api.github.com/users/0xREALaldc').then((r) => r.json());
    const repos = await fetch(user.repos_url).then((r) => r.json());
    console.log(repos);
  } catch (e) {
    console.log(e)
  }
}

start();

// or we can use the .catch in the function call
start().catch(e => console.log(e))
```
- with *axios* we just use the syntax for axios in the requests, all the rest is the same.
```js
  ...
  const user = await axios.get("https://api.github.com/users/0xREALaldc");
  const repos = await axios.get(user.data.repos_url);
  console.log(repos.data);
  ...
```

