# All about promises in JS
This is my new vlog about Promise 
## Getting started with Promise 
```js
let promise = new Promise((res,rej)=>{
    res("Resolved")
})
```
as soon as Promise object will created the call back function that you passed will start executing.
And you can actually set two callback function for resolve and reject.
for eg

```js
promise.then(function(res){
    // do whatever you want
    console.log(res);
})
promise.catch(function(err){
    console.log(err);
})
// OR 
promise.then(function(res){
    // do whatever you want
    console.log(res);
},function(err){
    console.log(err);
})
// OR 
promise.then(function(res){
    console.log(res);
}).catch(function(err){
    console.log(err);
})
```
## Convert Async/Await to Normal Promises

I have heard some people saying **JavaScript** waits for 
the asynchrounus task (await ) to be completed in async function then it goes to next line. But it's not true 
for example 
```js
async function doSomeTask(){
    let data = await axios.get("https://dog.ceo/api/breeds/list/all");
    console.log(data);
    let data2 = await axios.get("https://dog.ceo/api/breeds/list/all");
    console.log(data);
    console.log(data2);
}
```
### Does JavaScript wait for the task to completed ?
No JavaScript is single threaded programming language it waits for none and all the async tasks are performed by web api but the question is then how the above task is being executed in JavaScript ?

So basically behind the scence JavaScript converts the async task to normal promises 

```js
function doSomeTask(){
    axios.get("https://dog.ceo/api/breeds/list/all").
    then(res=>{
        let data = res;
        console.log(data);
        axios.get("https://dog.ceo/api/breeds/list/all")
        .then(res=>{
            let data2 = res;
            console.log(data);
            console.log(data2);
        })
    })
}
```

So this is how JavaScript works behind the scence in async/await function

Thank you
#### Krishna Yadav
