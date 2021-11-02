
# Hoisting

## Example 1
```javascript
getName()
console.log(x)
var x = 7;
function getName(){
    console.log("Hello World")
}
```

This will give the output:

```
Hello World
undefined
```
### Why
In the first phase

- Line 3: A variable x is created in the Memory with the value undefined.
- Line 4: A function named getName is created in the Memory component. 

In the second phase

- Line 1: getName is executed, Hello world is printed.
- Line 2: Variable x is printed. It is not initialized with a value yet, so we get the value undefined as output.

## Example 2
```javascript
var x = 7

function getName(){
    console.log("Hello World")
}
getName()
console.log(x)
```
This will give the output:

```
Hello World
7
```
### Why
In the first phase

- Line 1: A variable x is created in the Memory with the value undefined.
- Line 4: A function named getName is created in the Memory component. 

In the second phase

- Line 1: Variable x is initialized with the value 7, which replaces undefined.
- Line 4: getName is executed, Hello world is printed.
- Line 5: Variable x is printed. It is initialized with the value 7 now, so we get 7 as output.


## Example 3
```javascript
getName()
console.log(x)

function getName(){
    console.log("Hello World")
}
```
Will give us the output
```
Hello World
hoisting.js:2 Uncaught ReferenceError: x is not defined
    at hoisting.js:2
```
### Why

In the first phase

- Line 1: A function named getName is created in the Memory component. 

In the second phase
- Line 1: getName is executed, Hello world is printed.
- Line 2: Variable x is printed. But it was not created in the first phase, so we get an error.

## Example 4

```javascript
console.log(getName)
var getName = () => {
    console.log("Hello World")
}

console.log(getName)
```

```
Output:
undefined
Hello World
```
### Why

In the first phase

- Line 2: An arrow function with the name getName is created. It stores the function as a variable. Hence, the value stored initially is undefined.

In the second phase
- Line 1: getName is executed. Since it's not initialized, we get undefined value.
- Line 4: getName is printed. It is initialized now, hence, we get Hello World


## WHAT'S HAPPENING

Before the execution of a javascript program, memory as allocated to all the variables and functions in execution context.
Variables and functions are allocated memory in 2 phases.

In the first phase, variables are allocated the value undefined and function name are allocated the value which is the entire code
In the second phase, variables are assigned their real values.

## SO, WHAT IS HOISTING 

Accessing variables and functions before initializing without any error. The variables and functions are already created in the memory, hence we don't encounter errors.
