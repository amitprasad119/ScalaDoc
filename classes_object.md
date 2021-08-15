# Classes	

## Defining a Class 				


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

### Constructors 
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

### Default and Keyword Parameters

All Scala methods and constructors support keyword parameters and default parameter values.
When we call a method or constructor, we can use parameter names as keywords to specify the parameters in
an arbitrary order:

This comes in doubly useful when used in combintion with default parameter values, defined like this:
 `new Person(lastName = "Last", firstName = "First")` 
 `// res: Person = Person(First,Last)`
 
### The apply method

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

## Abstract Class 
Abstract classes are more indicated for refining what an object is. For instance, we can have an abstract class Animal and now say that Cow is a subclass of Animal. One important limitation is that classes can only inherit from a single abstract class at most.

Abstract classes are defined with the abstract modifier preceding the class keyword. Moreover, abstract classes can contain fully defined methods and abstract methods as well:
```
abstract class Animal {

  def heartBeat(): Int = {
    42
  }

  // this is an abstract method that should 
  // be overridden by subclasses
  def eat(): String // returns the sound made while eating
}
```
## Case Class 
 Case classes are an excetionally useful shorthand for defining a class, a companion object, and a lot of sensible defaults in one go. They are ideal for creating lightweight data-holding classes with the minimum of hassle.
Case classes are created simply by prepending a class defintion with the keyword case:

```
case class Person(firstName: String, lastName: String){
def name = firstName + " " + lastName
}
```
Whenever we declare a case class, Scala automatically generates a class and companion object:

```
val amit = new Person("Amit", "Prasad") // we have a class 
// amit: Person = Person(Amit,Prasad)
Person // and a companion object too 
// res: Person.type = Person
```

### Features of a case class
 -  A field for each constructor argument—we don’t even need to write val in our constructor definition, although there’s no harm in doing so.
 ` amit.firstName
// res: String = Amit`
 -  A default toString method that prints a sensible constructor-like representation of the class(nomore@ signs and cryptic hex numbers):
 ` amit
// res: Person = Person("Amit","Prasad")`
 - Sensible equals,and hashCod emethods that operateon the field values in the object. 
 This makes it easy to use case classes with collections like Lists, Sets and Maps. It also means we can compare
objects on the basis of their contents rather than their reference identity:

`new Person("Noel", "Welsh").equals(new Person("Noel", "Welsh"))
// res: Boolean = true`

`new Person("Noel", "Welsh") == new Person("Noel", "Welsh") 
// res: Boolean = true`

-  A copy method that creates a new object with the same field values as the current one:
` amit.copy()
// res: Person = Person(Amit,Prasad)`

Note:  that the copy method creates and returns a new object of the class rather than returning the current one:
### Features of a case class companion object

The companion object contains an apply method with the same arguments as the class constructor. Scala programmers tend to prefer the apply method over the constructor for the brevity of omiting new, which makes constructors much easier to read inside expressions:
```
Person("Amit", "Prasad") == Person("Jay", "Kumar") // res: Boolean = false
Person("Amit", "Prasad") == Person("Amit", "Prasad") // res: Boolean = true
```
## Case objects
A final note. If you find yourself defining a case class with no constructor arguments you can instead a define a case object. A case object is defined just like a case class and has the same default methods as a case class.
```
case object Citizen {
def firstName = "John"
def lastName = "Doe"
def name = firstName + " " + lastName
}
```
The differences between a case object and a regular singleton object are:
• The case object keyword defines a class and an object,and makes the object an instance(actually the only instance) of the class:

```
 class Citizen { /* ... */ }
object Citizen extends Citizen { /* ... */ }
```
 With a case object we still get all of the functionality defined for case classes above
## Object 

An object is a class that has exactly one instance.
Most often, you need an object to hold methods and values/variables that shall be available without having to first instantiate an instance of some class.
As a top-level value, an object is a singleton.

## Defining a singleton object

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

## Companion Objects

Sometimes we want to create a method that logically belongs to a class but is independent of any particular object. In Java we would use a static method for this, but Scala has a simpler solution that we’ve seen already: singleton objects.
One common use case is auxiliary constructors. Although Scala does have syntax that lets us define mutiple constructors for a class, Scala programmers almost always prefer to implement additional constructors as apply methods on an object with the same name as the class. 
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

**Exercises:**
- Create a class to calculate the simple intrest using a method call *calculateSimpleIntrest* having two parameters **principle** , **rate** for one year. 
- Create a class where constructors takes a parameter as number and calculate the cube in **calculateCube** 
- Create a case class and override **apply** method to print a custom message 
- Create a single object with HelloWorld 
 
