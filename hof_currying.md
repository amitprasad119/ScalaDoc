# Higher order function (HOFs)
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


