<h1>
  <span class="headline">Java Debugging</span>
  <span class="subhead">Stack Trace</span>
</h1>

**Learning objective:** By the end of this lesson, you'll be able to perform debugging tasks on exceptions/runtime errors by interpreting a Java program's stack trace.

## An introduction to stack trace

A stack trace is a detailed report of the program's execution at a specific point in time. In Java, a stack trace is automatically generated when an exception is thrown. It shows:

- The exception type.
- The exception message.
- The call stack - The sequence of method calls, from the most recent to the oldest, leading to the exception.

## Stack trace demo

Take the following example. Can you spot the problem?

```java
public class Main {

    public static void main(String[] args) {
        printSomething(null);
    }

    public static void printSomething(String s) {
        System.out.println(s.length());
    }
}
```

If we run this code, we get the following error in the console:

```plaintext
Exception in thread "main" java.lang.NullPointerException
    at Main.printSomething(Main.java:11)
    at Main.main(Main.java:7)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:497)
    at com.intellij.rt.execution.application.AppMain.main(AppMain.java:144)
```

While this might seem intimidating, we only need to focus on a few key parts. 
1. The first is the top line, which tells us what the error actually was. This is the **exception message**. In this case, we got a `NullPointerException`, which is our **exception type**. In other words, our code tried to call a method on a variable that was null.

2. Next, concentrate on the lines that contain our file name (in this case, `Main.java`). This is called the **call stack trace**. It shows the path of execution for your program. Because the errors in the code are in the files we wrote, those are the lines we'll focus on. The higher up in the stack trace, the more recent the execution.

3. In the top most line of our call stack is the call to `printSomething()` method. That's the last method call that happened in at line number 11 in our `Main.java` file. No method calls happened beyond that. We can be certain that the error is in one of the statements of this method. Below that we see that our `main` method was called at line number 7. That's where our program execution started. All the lines below that are a sequential summary of how our JVM (Java Virtual Machine) started the execution of our program.

From the call stack tracing activity, we can determine how far our program ran without exception, and narrow down the location and reason for the exception. 
