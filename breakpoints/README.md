# ![[tktk Module Name] - tktk Microlesson Name](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to set a breakpoint to examine the current state using sample code.

## Introduction: Breakpoints (10 min)

The second topic we'll be covering today is the **breakpoint**. In general terms, a breakpoint is a position in the code at which you want to halt execution.

> **Knowledge Check**: Why would we want to do this?

Adding a breakpoint allows you to:
- Trace execution of the code step by step.
- Inspect the value of all variables in scope.

That second point can make debugging your code much faster. Instead of adding a lot of `print` statements to monitor your variables, you can just stop your code in place.

> **Knowledge Check**: Why are breakpoints cleaner for debugging than `print` statements?

## Demo: Breakpoints (10 min)

Let's continue with the array example from the previous demo. Enabling breakpoints in IntelliJ is simple. Go ahead and click the margin next to Line 13 where we access Index 0 in the array.

Next, you need to run the program in debugging mode. Instead of pressing the "Run" icon like normal, you need to press the "Debug" button.

The program should run, but a new window will pop up on the bottom and you should see your code change slightly.

The console now shows us the values of the variables, as well as any errors that might show up. Also, in the actual code, it shows us what the values of the variables are.

Let's add one more breakpoint in `main` where we call the `printSomethingArray()` method. If we initialize the array with a few values and rerun the program, we should see these values change and the error should go away.

> **Knowledge Check**: How can you use breakpoints and a stack trace together?


## Conclusion (5 min)

Learning to debug well is a crucial skill, and what we covered today is a great way to start. You can apply it to almost any programming language you might learn in the future.