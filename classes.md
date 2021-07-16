# Classes	

# Defining a Class 				


A class is a template for creating objects that have similar methods and fields. In Scala a class also defines a type, and objects created from a class all share the same type: 		

 ```
class Person {
    val firstName = "Amit"
    val lastName = "Prasad"
    def name = firstName + " " + lastName
} 
 ```
Like an object declaration, a class declaration binds a name (in this case Person) and is not an expression. However, unlike an object name, we cannot use a class name in an expression. A class is not a value, and there is a different namespace in which classes live.
​​		
We can create a new Person object using the new operator. Objects are values and we access their methods and fields in the usual way:	

```
val personObj = new Person
// noel: Person = Person@3235186a					
personObj.firstName 
​​// res: String = Amit

```

## Constructors 
As it stands our Person class is rather useless: we can create as many new objects as we want but they all have the same firstName and lastName. What if we want to give each person a different name?
					
The solution is to introduce a constructor, which allows us to pass parameters to new objects as we create them: 
```
class Person(first: String, last: String) {
val firstName = first
val lastName = last
def name = firstName + " " + lastName
}
val personObj = new Person("Amit", "Prasad")
// personObj: Person = Person@3ed12df7
personObj.name
// res: String = Amit Prasad
```

The constructor parameters first and last can only be used within the body of the class. We must declare a field or method using val or def to access data from outside the object.
Constructor arguments and fields are often redundant. Fortunately, Scala provides us a useful short-hand way of declaring both in one go. We can prefix constructor parameters with the val keyword to have Scala define fields for them automatically:

```
class Person(val firstName: String, val lastName: String) { 
def name = firstName + " " + lastName
}
new Person("Amit", "Prasad").firstName // res: String = Amit
```
`val` fields are immutable—they are initialized once after which we cannot change their values. Scala also pro- vides the var keyword for defining mutable fields.

# Default and Keyword Parameters

All Scala methods and constructors support keyword parameters and default parameter values.
When we call a method or constructor, we can use parameter names as keywords to specify the parameters in
an arbitrary order:

This comes in doubly useful when used in combina􏰀on with default parameter values, defined like this:
 `new Person(lastName = "Last", firstName = "First")` 
 `// res: Person = Person(First,Last)`
 
# The apply method

For now we are going to look at just one of Scala’s features supporting functional programming—function application syntax.
In Scala, by convention, an object can be “called” like a function if it has a method called apply. Naming a method apply affords us a special shortened call syntax: foo.apply(args) becomes foo(args).
For example, let’s rename the add method in Adder to apply: 

```
class Adder(amount: Int) {
def apply(in: Int): Int = in + amount
}
val add3 = new Adder(3)
// add3: Adder = Adder@1d4f0fb4
add3(2) // shorthand for add3.apply(2) // res: Int = 5

```
# Object 

An object is a class that has exactly one instance.
Most often, you need an object to hold methods and values/variables that shall be available without having to first instantiate an instance of some class.
As a top-level value, an object is a singleton.

# Defining a singleton object

An object is a value. The definition of an object looks like a class, but uses the keyword object:
`object Person`

Here’s an example of an object with a method:

```
package logging

object Logger {
  def info(message: String): Unit = println(s"INFO: $message")
}
```

The method info can be imported from anywhere in the program. Creating utility methods like this is a common use case for singleton objects.

# Companion Objects

Sometimes we want to create a method that logically belongs to a class but is independent of any particular object. In Java we would use a static method for this, but Scala has a simpler solution that we’ve seen already: singleton objects.
One common use case is auxiliary constructors. Although Scala does have syntax that lets us define mul􏰀ple constructors for a class, Scala programmers almost always prefer to implement additional constructors as apply methods on an object with the same name as the class. 
We refer to the object as the companion object of the class. For example:

```
class Timestamp(val seconds: Long)
object Timestamp {
def apply(hours: Int, minutes: Int, seconds: Int): Timestamp =
    new Timestamp(hours*60*60 + minutes*60 + seconds)
}
Timestamp(1, 1, 1).seconds
// res: Long = 3661
```

 
