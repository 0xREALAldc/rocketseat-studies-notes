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
	- 
