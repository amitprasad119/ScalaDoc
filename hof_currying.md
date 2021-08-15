# Higher order function (HOFs) and Currying

### Higher order functions
A function is Higher Order Function if it contains other functions as a parameter or returns a function as an output i.e, the functions that operate with another functions are known as Higher order Functions.
The key benefits of this feature are : 

- The Higher order functions are possible, as Scala programming language acts towards the functions as first-class values, which implies that analogous to some other values, functions can even be passed as a parameter or can be returned as an output, which is helpful in supplying an adjustable method for writing codes.
- It is beneficial in producing function composition where, functions might be formed from another functions. The function composition is the method of composing where a function shows the utilization of two composed functions.
- It is also constructive in creating lambda functions or anonymous functions. The anonymous functions are the functions which does not has name, though perform like a function.
- It is even utilized in minimizing redundant lines of code from a program.

Let's see this through an example: 

Consider we have a function call `greetings(name: String)` which takes a name parameter and greets the person. 
And another method is to print the message which would take a function as an arguument along with name to greet the person. When we pass the function as a paramter we have to give the param name, passed function argument types and return type separated by `:` and `=>` respectively 
i.e `def mainFun(func:<func accepted argument type> => <func return type>)`

**example:**
```
 def greet(name:String) = "Hello " + name + "!" 
```
Now let's pass greet  function as an argument to message function 
```
def message(greet: String => String , name:String) = println(greet(name))
```
When we call the message function

`message(greet,"Amit")`

**Hello Amit!** would be printed.

### Currying 
A curried function is applied to multiple argument lists, instead of just one. 
Function currying is an interesting concept in Scala. We often associate it with the partially applied functions. Let's try to understand the basics with an example:

```
def plainOldSum(x: Int, y: Int) = x + y
plainOldSum: (x: Int,y: Int)Int
scala> plainOldSum(1, 2)
res4: Int = 3
```

By contrast, in below example shows a similar function that’s curried. Instead of one list of two Int parameters, you apply this function to two lists of one Int parameter each.
```
scala> def curriedSum(x: Int)(y: Int) = x + y
curriedSum: (x: Int)(y: Int)Int
scala> curriedSum(1)(2)
res5: Int = 3
```

What’s happening here is that when you invoke curriedSum, you actu- ally get two traditional function invocations back to back. The first function invocation takes a single Int parameter named x, and returns a function value for the second function. This second function takes the Int parameter y.

**Exercises:**
- Create two methods to calculate Square,Cube then pass these methods to a `sum` function and add both passed function as result 
   i.e `def sum(function1,function2,num) = {}` 
- Calculate the principle intrest in curried function by passing principle amount,rate and years as individual argument. 
  
