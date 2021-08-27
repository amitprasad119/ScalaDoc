## Installation

**Step 1:**  Make sure you have the Java 8 JDK (also known as **1.8**)
  - Run javac -version on the command line and make sure you see javac 1.8.___
  - If you don’t have version `1.8` or higher, [install the JDK!](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html)  
  
**Step 2:** Next, download and install [IntelliJ Community Edition!](https://www.jetbrains.com/idea/download/#section=mac)

**Step 3:** Then, after starting up IntelliJ, you can download and install the Scala plugin by following the instructions on [how to install IntelliJ plugins!](https://www.jetbrains.com/help/idea/managing-plugins.html) (search for “Scala” in the plugins menu.)

When we create the project, we’ll install the latest version of Scala. Note: If you want to open an existing Scala project, you can click **Open** when you start IntelliJ.

## Test the installation By sample Project
**1.** Open up IntelliJ and click **File => New => Project**  
**2.** On the left panel, select Scala. On the right panel, select IDEA.  
**3.** Name the project **HelloWorld**  
**4.** Assuming this is your first time creating a Scala project with IntelliJ, you’ll need to install a Scala SDK. To the right of the Scala SDK field, click the Create button.   
**5.** Select the highest version number (e.g. 2.13.6) and click Download. This might take a few minutes but subsequent projects can use the same SDK.  
**6.** Once the SDK is created and you’re back to the “New Project” window click Finish.  

### Create Hello World 
 **Step 1.** On the Project pane on the left, right-click src and select New => Scala class.   
 If you don’t see Scala class, right-click on HelloWorld and click on Add Framework Support…, select Scala and proceed.  
 If you see Error: library is not specified, you can either click download button, or select the library path manually.  
 If you only see Scala Worksheet try expanding the src folder and its main subfolder, and right-click on the scala folder.    
 **Step 2.** Name the class Hello and change the Kind to object.  
 
 Change the code in the class to the following:  
 ```
 object Hello extends App {
  println("Hello, World!")
}
```

**Step 3:** Run it 

 - Right click on Hello in your code and select Run ‘Hello’.
 - Congratulation! You are done with installation success!






