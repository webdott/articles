## Making Http Requests Using the fetch API


![fetch API.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1590329210851/4V6lwNjd8.jpeg)

This article guide explains what Fetch API means, and the modern approach to making asynchronous request from API networks to your web page using the `fetch()` method.
This article would aim to cover the following:

1. What is Fetch API.

2. Why Fetch API.

3. AJAX.

4. Example guides on using Fetch API.

5. Async…Await.

---

** What is Fetch API?**

The Fetch API is known as a standard modern API that uses promises as its building block. Therefore, in order to have a good understanding of this concept, it is recommended to have a good understanding of Promises and Callbacks.
This standard replaced the  [XMLHttpRequest (XHR)](https://flaviocopes.com/xhr/)  which used to be the means of making these network requests by developers. The difference between these two, is that Fetch API is promised-based.

Promises, introduced in ECMAScript2015 (ES6), are a powerful way to deal with asynchronous code without too many Callbacks. This solved the problem of the high level nesting created by Callbacks and also controlling what to do with data in asynchronous operations, while your app is still running.

Performing all these asynchronous operations with JavaScript does not mean JavaScript itself is asynchronous. As a matter of fact,  [JavaScript is synchronous by default, and single-threaded with Callback mechanisms.](https://stackoverflow.com/questions/2035645/when-is-javascript-synchronous) 

With that being said, the Fetch API has been effective for making asynchronous network requests to different API’s using the `fetch()` method, which returns a 
`Promise` {either resolved or rejected}. On your console, it would look something like — `promise{}` .

The `Response` is resolved from the `Request` to find out whether it is successful or not. When successful, it is **fulfilled**, and **rejected** if otherwise. In between this process exists another state of `Promises` which is **pending**. This as the name implies, means that the `Response` is still being resolved.

In order to resolve, we need the `.then()` handler to wait for the server’s response, and enable us to access the promise’s content. More light will be shed on this as we progress.

---

**Why Fetch API.**

Although there are other various ways to make HTTP requests, the good thing about the Fetch API is that it is supported by most major browsers except the Internet Explorer (IE). It is also fully supported by the JavaScript Ecosystem coupled with being part of the MDN Mozilla Docs.

Below is an image showing the browser support for the `fetch()` function from  [caniuse.com](https://caniuse.com/) .

![browser support for the fetch() function from caniuse.com.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1590329895442/VI1xgtFXY.png)

Hopefully, in years to come, the Fetch API would be fully supported across all browsers.

---

**AJAX**

[Asynchronous JavaScript and XML](https://en.wikipedia.org/wiki/Ajax_(programming) (AJAX) are group of web technologies that enable web applications to transfer and receive data from servers in the background without interrupting the activity or behavior of the existing page, by running the process in the background (asynchronously).

AJAX is now commonly executed on web pages using the `fetch()` method, thereby allowing parts or portions of websites to be updated dynamically (loading content to the screen without refreshing the whole page).

---

**EXAMPLE GUIDES ON USING Fetch API.**

Using the `fetch()` method can be quite easy. All you have to do is to use the keyword coupled with the resource URL you are accessing, inside the parenthesis.



> **Note:** All functions used here, would be arrow functions.

> The API used in this case is the  [‘PokéAPI’](https://pokeapi.co/) , a cool API for Pokemon stuff.

So for the sake of this example we would be fetching a species object from the PokéAPI:

``` javascript

fetch('https://pokeapi.co/api/v2/pokemon/1/')

```

As mentioned before, this code would return a Promise that would contain a bunch of stuff looking like this:

![promise.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1590331148392/MPNxMZVj6.png)

As seen here, the fetch method is available in the window scope. We need to make this data we received useful, as in most cases, we would see the need to. This is where `.then()` handler comes in.

When manipulating the resource, we make use of just a single `.then()` handler. To access the data as in this case however, we need two `.then()` handlers.

Lets see how that would look like:


```javascript

fetch ('https://pokeapi.co/api/v2/pokemon/1/') 
   .then(response => response.json() 
   .then(data => console.log(data))

``` 
 

What the first `.then()` does, is converting the response to a `json` format, while the second allows us to access the data so we have something like this:

![fetch data.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1590331301588/izD5RGawO.png)

You might as well want to access just a specific object in the data. Remember I said we wanted to extract the `species` object. To do this, you just need to include the name of the object in the last `.then()` handler:


```  javascript

.then(data => console.log(data.species)) 
//To access the species object

```

**Handling Errors**

It is important to handle errors when using the `fetch()` method(since it returns a promise). Therefore, to handle errors in execution of our request, we could use the common `catch` method of the `promise`:

``` javascript 

fetch ('https://pokeapi.co/api/v2/pokemon/1/')
 .then(response => {….})
 .catch(err => console.log(err)) 
//This would intercept errors if any

```

---

**Async…Await**

The `async...await` syntax came around with the ES8 and reduced the syntax complexity that were attached to promises. Async functions are a combination of promises and generators (giving them higher level of abstraction over promises).

Another major advantage of this syntax, is the fact that it allows easier debugging since it makes the compiler see the code as synchronous, whereas it is actually asynchronous and non-blocking behind the scenes.

Using the `.then()` syntax is nice, but the `async...await` syntax provides a more concise way of processing requests and also makes the code more readable in my opinion.

So converting the code we wrote in the example above, using the `async...await` syntax, we have:

``` javascript

const fetchPokemonSpecie = async() => {
 const response = await fetch('https://pokeapi.co/api/v2/pokemon/1/');
 const data = await response.json();
 console.log(data.species)
}
fetchPokemonSpecie()

```

Easy to read right?! It sure felt easier to write too. The use of `await` allows us to wait for each `Promise` to be `resolved` before moving on to the next. First, we wait for the `fetch` request to be over before passing its value to the `response` variable.

Then we get the `json` format of this response and pass it to the `data` variable, before logging the value of the `species` object of the `data`, on the console.

---

**Handling Errors in Async…Await**

This basically follows the same method we use with the `.then()` syntax except we use the `try…catch` block in this case instead of just `catch`.

``` javascript 

const fetchPokemonSpecie = async() => { 
   try {
     const response = await fetch('https://pokeapi.co/api/v2/pokemon/1/');
     const data = await response.json();
     console.log(data.species) 
   } catch (err) {
     console.log(err)
   }
fetchPokemonSpecie()

```

We use this error handling method when handling network failures. The code in the `catch` block would only run when a network error occurs.

Looking at the `Promise` gotten after running the `fetch()` method, we have a `Response` object with an `ok` property. We could also handle an error by using an if statement declaring that if this `ok` property is `true`, it lies in the 200 range and should execute the code; otherwise, throw an error.

``` javascript 

const fetchPokemonSpecie = async() => {
   const response = await fetch('https://pokeapi.co/api/v2/pokemon/1/'); 
   if (response.ok) {
      const data = await response.json();
      console.log(data.species) 
   } else {
      throw Error(response.statusText)
   }
}
fetchPokemonSpecie()

```
---

**Conclusion**

After seeing this article, I hope you now have a basic understanding of what the fetch API looks like, how to retrieve data using the `fetch()` method, and the problem it solves. Handling errors is also an important aspect. You can create Request objects to control the request methods and headers.

Personally, I think one can understand this concept without really having any strong coding or programming background. Now, go play around with this and start using it to make your AJAX requests.

---

If you liked this article, please do well to clap and follow. I would like to write more technical articles in the nearest future.





