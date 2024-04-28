# ![[tktk Module Name] - tktk Microlesson Name](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to analyze stack traces to identify common errors.

## Opening (5 min)

Even the best programmers make mistakes when writing code, and a large amount of development time is often spent fixing errors in code, also known as **bugs**. The process of fixing bugs is called **debugging**. Many tools and techniques can be used for debugging, but today, we'll be concentrating on **reading a stack trace** and **using breakpoints**.

## Introduction: Stack Trace (10 min)

Making mistakes is a natural part of programming, so it's absolutely critical to be able to debug your code. The first thing we'll be looking at is the **stack trace**. You've probably seen a stack trace in the past few days without realizing it.

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

```
Exception in thread "main" java.lang.NullPointerException
	at Main.printSomething(Main.java:11)
	at Main.main(Main.java:7)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:497)
	at com.intellij.rt.execution.application.AppMain.main(AppMain.java:144)
```

While this might seem intimidating, you only need to focus on a few key parts. The first is the top line, which tells you what the error actually was. In this case, we had a `NullPointerException`, meaning we tried to call a method on a variable that was null.

Next, concentrate on the lines that contain your file name (in this case, `Main.java`). This is called the stack trace: It shows the path of execution for your program. Because the errors in the code are in the files we wrote, those are the lines we'll focus on. The higher up in the stack trace, the more recent the execution.

The number after the colon next to the file name is the line number where the error occurred. In our example, the error was in `Main.java` on Line 11.

> **Knowledge Check**: What does the second line of the stack trace after the `printSomething` call mean?

## Demo: Stack Trace (5 min)

Let's take a look at another example. Can you find the error?

```java
public class Main {

    public static void main(String[] args) {
        int[] arr = {};

        printSomethingArray(arr);
    }

    public static void printSomethingArray(int[] arr) {
        System.out.println(arr[0]);
    }
}
```

If we run this code, we get the following error:

```
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: 0
	at Main.printSomethingArray(Main.java:13)
	at Main.main(Main.java:9)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:497)
	at com.intellij.rt.execution.application.AppMain.main(AppMain.java:144)
```

> **Knowledge Check**: Who can explain what's going on here?

The two errors we just saw, `NullPointerException` and `ArrayIndexOutOfBoundsException`, are common, so they're something you'll probably see in your stack traces.

> **Knowledge Check**: How could we avoid the `ArrayIndexOutOfBoundsException`?