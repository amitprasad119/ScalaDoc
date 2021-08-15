# Scala Type Hierarchy

Scala contains huge predefine types of hierarchy 

In Scala, there are no primitive types. All basic types are also classes and they are part of the class hierarchy. Scala type hierarchy divided into two categories which are `AnyRef` and `AnyVal`

![Scala Type Hierarchy](https://docs.scala-lang.org/resources/images/tour/unified-types-diagram.svg)

`Any` is the supertype of all types, also called the top type. It defines certain universal methods such as `equals`, `hashCode`, and `toString`. Any has two direct subclasses: `AnyVal` and `AnyRef`.

`AnyVal` represents value types. There are nine predefined value types and they are non-nullable: `Double`, `Float`, `Long`, `Int`, `Short`, `Byte`, `Char`, `Unit`, and `Boolean`. 
`Unit` is a value type which carries no meaningful information. There is exactly one instance of `Unit` which can be declared literally like so: (). All functions must return something so sometimes Unit is a useful return type.

`AnyRef` represents reference types. All non-value types are defined as reference types. Every user-defined type in Scala is a subtype of `AnyRef`. If Scala is used in the context of a Java runtime environment, `AnyRef` corresponds to `java.lang.Object`

Here is an example that demonstrates that strings, integers, characters, boolean values, and functions are all of type Any just like every other object:

```
val list: List[Any] = List(
  "a string",
  732,  // an integer
  'c',  // a character
  true, // a boolean value
  () => "an anonymous function returning a string"
)
list.foreach(element => println(element))
```

It defines a value list of type `List[Any]`. The list is initialized with elements of various types, but each is an instance of scala.Any, so you can add them to the list.

# Nothing and Null

There are two special types at the bottom of the hierarchy. Nothing is the type of throw expressions, and Null is the type of the value null. These special types are subtypes of everything else, which helps us assign types to throw and null while keeping other types in our code sane. The following code illustrates this:
```
def badness = throw new Exception("Error") // badness: Nothing
null
// res: Null = null
val bar = if(true) 123 else badness // bar: Int = 123
val baz = if(false) "it worked" else null // baz: String = null

```

Although the types of badness and res are `Nothing` and `Null` respectively, the types of bar and baz are still sensible. This is because Int is the least common supertype of Int and Nothing, and String is the least common supertype of `String` and `Null`.

**Exercises:**

- Create a list of type `AnyVal`
- Create a variable of type `Unit`  


