# Pattern Matching 
Pattern matching is a mechanism for checking a value against a pattern. A successful match can also deconstruct a value into its constituent parts. It can be used in place of a series of `if/else` statements.

### Syntax

```
<value> match {
    case <expression> => <value>
    .
    .
    .
    case _ => <default value>
}
```
Here `_` is treated as wild card where if nothing is matched this block will be executed. 

**Example:** 

```
def matchTest(x: Int): String = x match {
  case 1 => "one"
  case 2 => "two"
  case _ => "other"
}
matchTest(3)  // prints other
matchTest(1)  // prints one
```
The val x above is a random integer between 0 and 10. x becomes the left operand of the match operator and on the right is an expression with four cases.Cases are also called alternatives.

### Matching on case classes

Case classes are especially useful for pattern matching.

```
abstract class Notification

case class Email(sender: String, title: String, body: String) extends Notification

case class SMS(caller: String, message: String) extends Notification

case class VoiceRecording(contactName: String, link: String) extends Notification
```
Notification is an abstract super class which has three concrete Notification types implemented with case classes Email, SMS, and VoiceRecording. Now we can do pattern matching on these case classes:

```
def showNotification(notification: Notification): String = {
  notification match {
    case Email(sender, title, _) =>
      s"You got an email from $sender with title: $title"
    case SMS(number, message) =>
      s"You got an SMS from $number! Message: $message"
    case VoiceRecording(name, link) =>
      s"You received a Voice Recording from $name! Click the link to hear it: $link"
  }
}
val someSms = SMS("12345", "Are you there?")
val someVoiceRecording = VoiceRecording("Tom", "voicerecording.org/id/123")

println(showNotification(someSms))  // prints You got an SMS from 12345! Message: Are you there?

println(showNotification(someVoiceRecording)) 

```

**Exercises:**

- Create a pattern match function which can display a message if age is >= 18 as eligible or else not eligible 
- Create a pattern matching function which can take three paramters , num1, num2 and symobol(+,-,*,/) and perform the operation based on passed symbol and send the result as return type , if sysmbol is not matched from list then return 0. 
- Create a case class of Cricket and Hockey and check player preference are sent as Hockey/Cricket in pattern matching 
- Create a case class and print if a number is even (**Hint** :Use pattern guard condition).  
