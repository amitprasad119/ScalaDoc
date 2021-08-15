# Try 

The `Try` represents error handling semantics which could be either  `Success` when no exception caught or `Failure` when caught any.
 It's similar to, but semantically different from the scala.util.Either type.
 There are two instance of `Try[T]` 
   - scala.util.Success   
   - scala.util.Failure
   
Let's see this by an example: 

Try can be used to perform division on a user-defined input, without the need to do explicit exception-handling in all of the places that an exception might occur.

**Example**:
```
def divide: Try[Int] = {
  val dividend = Try(StdIn.readLine("Enter an Int that you'd like to divide:\n").toInt)
  val divisor = Try(StdIn.readLine("Enter an Int that you'd like to divide by:\n").toInt)
  val problem = dividend.flatMap(x => divisor.map(y => x/y))
  
  problem match {
    case Success(v) =>
      println("Result of " + dividend.get + "/"+ divisor.get +" is: " + v)
      Success(v)
    case Failure(e) =>
      println("You must've divided by zero or entered something that's not an Int. Try again!")
      println("Info from the exception: " + e.getMessage)
      divide
  }

    
}
```
**Exercises:** 

- Create a `Try` block and make an exception handling for devide by zero and print both success and failure cases by passing two diffrent arguments one by one. 
- Write the code to validate the age for a person and make the validation if he/she is eligible to vote or not (eligible age is 18 years). 
