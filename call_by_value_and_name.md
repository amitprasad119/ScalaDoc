#   Call by value & Call by name
Function call in scala are traditionally same as any other languages except it has two ways to achive in terms of evaluation of function parameters.
There are two ways of calling a functions in scala: 
- call by value 
- call by name 

### call by value 
Function arguments are considered call by-value by default in Scala. Let’s define a function, test, which takes an argument as call by-value:
 **example:**
`def sqr(a: Int) = a * a`

In general, applications of parameterized functions are evaluated similarly as operators. First, it evaluates all the function arguments, from left to right. Then it replaces the function application by the function’s right-hand side, and, at the same time, it replaces the formal parameters of the function by the actual arguments. The call by-value strategy has the advantage that it evaluates every function argument only once.

### call by name 
To make an argument called by-name, we simply prepend `=>` to its type.

Let’s define a function, test, which takes an argument as call by-name:

`def sqr(a: => Int) = a * a`

Call by-name evaluation is similar to call by-value, but it has the advantage that a function argument won’t be evaluated until the corresponding value is used inside the function body.

Both strategies are reduced to the final value as long as:

The reduced expression consists of pure functions
Both evaluations terminate

Let's see the example for both how it gets evaluated in both ways: 

```
def mockMethod() = {
  println("calling mockMethod")
  1
}
```

Now we are going to define two function that accept Int arguments that are exactly the same except that one takes the argument in a `call-by-value style (x: Int)` and the other in a `call-by-name style (x: => Int)`.

```
def callByValue(x: Int) = {
  println("x1=" + x)
  println("x2=" + x)
}
```

```
def callByName(x: => Int) = {
  println("x1=" + x)
  println("x2=" + x)
}
```
Now let's call both the functions and see what would be the real side effects. 
```
scala> callByValue(mockMethod())
calling mockMethod
x1=1
x2=1

scala> callByName(mockMethod())
calling mockMethod
x1=1
calling mockMethod
x2=1

```
So you can see that in the `call-by-value` version, the side-effect of the passed-in function call `(mockMethod())` only happened once. However, in the call-by-name version, the side-effect happened twice.

**Exercises:**
- Create a class to calculate the simple intrest using a method call *calculateSimpleIntrest* having two parameters **principle** , **rate** for one year. 
- Create a class where constructors takes a parameter as number and calculate the cube in **calculateCube** 
- Create a case class and override **apply** method to print a custom message 
- Create a single object with HelloWorld 
