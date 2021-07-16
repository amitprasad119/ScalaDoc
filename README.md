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

This comes in doubly useful when used in combintion with default parameter values, defined like this:
 `new Person(lastName = "Last", firstName = "First")` 
 `// res: Person = Person(First,Last)`
 
