# Tail Recursion 

Functions which call themselves as their last action are called tail-recursive. The Scala compiler detects tail recursion and replaces it with a jump back to the beginning of the function, after updating the function parameters with the new values ... as long as the last thing you do is calling yourself, it’s automatically tail-recursive (i.e., optimized).

You may be concerned that recursive calls will consume excessive stack space. Scala can apply an optimisation, called tail recursion, to many recursive functions to stop them consuming stack space.
A tail call is a method call where the caller immediately returns the value. So this is a tail call


`def method1: Int = 1`
`def tailCall: Int = method1`


because tailCall immediately returns the result of calling `method1` while

```
 def notATailCall: Int = method1 + 2
 ```
because `notATailCall` does not immediatley return—it adds an number to the result of the call.

We use the annotation to indicate the scala compiler that method should be treated as tail recursion is `@tailrec`

### How it works : 
```
def tailrecSum(n:Int, runningTotal:Int = 0): Int =   {
    if (n == 0) {
        return runningTotal
    } else {
        return tailrecSum(n - 1, runningTotal + n)
    }
}
```

Here's the sequence of events that would occur if you called `tailrecSum(5)`, (which would effectively be `tailrecSum(5, 0)`, because of the default second argument).

```
tailrecSum(5, 0)
tailrecSum(4, 5)
tailrecSum(3, 9)
tailrecSum(2, 12)
tailrecSum(1, 14)
tailrecSum(0, 15)
15
```

In the tail-recursive case, with each evaluation of the recursive call, the runningTotal is updated.

