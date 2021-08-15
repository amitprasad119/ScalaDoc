# ScalaTest 
ScalaTest is a library to test and write a robust code with targetted feature and write the granular level of test cases to make the code aligned with our features. 
There are multiple libraries and testing methodologies for Scala, but in this section, we’ll demonstrate one popular option from the ScalaTest framework called `AnyFunSuite`.

ScalaTest's Framework supports using ScalaTest from `sbt`.
 Add this to your project file:
```
libraryDependencies += "org.scalactic" %% "scalactic" % "3.2.9"
libraryDependencies += "org.scalatest" %% "scalatest" % "3.2.9" % "test"
```
>Note: The dependency on `Scalactic`, ScalaTest's sister library focused on quality through types, is recommended but not required.

Let's create a class to calculate the cube of a passed number:

```
object CubeCalculator extends App {
def cube(n: Int) = {
    n * n * n
}
```
Now let's test the above code via `AnyFunSuite` 

```
 import org.scalatest.funsuite.AnyFunSuite

  class CubeCalculatorTest extends AnyFunSuite {
      test("CubeCalculator.cube") {
          assert(CubeCalculator.cube(3) === 27)
      }
  }
  ```
Above code will always test the logic of our written code with expected match. Under the test we can pass the readable format message for clear understanding of the logic or what is being tested against the same run. 

### Adding another test case
```
 import org.scalatest.funsuite.AnyFunSuite
    
   class CubeCalculatorTest extends AnyFunSuite {
       test("CubeCalculator.cube 3 should be 27") {
           assert(CubeCalculator.cube(3) === 27)
       }

       test("CubeCalculator.cube 0 should be 0") {
           assert(CubeCalculator.cube(0) === 0)
       }
   }
```

To test the cube of zero, we have added anotther assertion and likewise we can add the more test cases to the extended logic of our actual codes.

> To Execute the test cases we can run the below commands 
  
  `> cd <project-folder>` 
   
   `> sbt test`
   
**Exercises:** 
- Create a class to calculate add,substract,multiplication,divide and write the testcases for to test all the logics, also each method should accepts two aruguments 
e.g `def add(num1:Int, num2:Int) = num1 + num2`

- Explore the option of `AnyFlatSpec` and try to write the test cases for above created class.
  For AnyFlatSpec you can follow this link to know more:  [AnyFlatSpec](https://www.scalatest.org/scaladoc/3.2.9/org/scalatest/flatspec/AnyFlatSpec.html)
