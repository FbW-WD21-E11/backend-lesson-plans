1) What means of storing data on the browser that you know of?

- localStorage
- sessionStorage
- Cookies


2) Does switching work between these two radio buttons?

<input type="radio" name="radio" id="radio1" />
<input type="radio" name="radio" id="radio2" />


3) What are history.pushState and history.popState?

4) What is a closure in JavaScript?

```js
const name = "App";


function runSomething() {

    const a = 123;

}
```

5) What is an event in the browser?

Events are user generated, such as click, change, submit

6) How can we prevent event bubbling?

`event.stopPropagation()`
`event.preventDefault()`

7) How does == and === differ?

1 === "1" // false
1 == "1" // true

8) What is hoisting?

```js

hello();

// function declaration
function hello() {


}

````


```js
// does not apply hoisting
hello(); X

// function assignment
const hello = () => {}

```


9) How can check if an object is an array?

`Array.isArray()`

10) What is the difference between `var`, `const` and `let`?

`const` and `let` are block scoped `{}`
`var` is function scoped

```js

const power = 1313;

try {
    const a = 324;
} catch(e) {
    console.log(a) // this does not work

}

function something() {

    for (var index = 0; index <10; index++) {
        var b = 34;
        console.log(power) // this works

    }

    for (let index = 0; index <10; index++) {

    }

    console.log(b); // this works
}

```
