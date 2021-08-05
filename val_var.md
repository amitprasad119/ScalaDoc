# val and var 
 Scala – a multi-paradigm programming language allows one to declare variables `mutable` or `immutable`. We can create mutable variables via keyword `var` and immutable variables via `val` keyword. Let’s understand each one of these variables in detail.
 
 ## Mutable Variable [var]:
 These are those variables which allow us to change a value throughout its lifetime after the declaration of a variable.
 
 ### Syntax:
      var varName: Data_type = "value" 
Scala has a built-in type inference mechanism which allows the programmer to omit certain type annotations. So, we can omit Data_type from the above.

### Example :

```
class Person {
  var name: String = "Admin"
  var age : Int = 20
}
```

## Immutable Variable [val] : 
 These variables are those variables which do not allow us to change or reassign a value once initialized.
 
 ```
 val Variable_name: Data_type =  "value"
 ```
### Example :

```
class Person {
  val name: String = "Admin"
  val age : Int = 20
}
```


      
