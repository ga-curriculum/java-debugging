<h1>
  <span class="headline">Java Debugging</span>
  <span class="subhead">Breakpoints</span>
</h1>

**Learning objective:** By the end of this lesson, you'll be able to debug a Java program by pausing your program execution using breakpoints and then observing variables and runtime behavior using step-by-step debugging.

## Breakpoints

A breakpoint is a marker that we set in our code to pause the program's execution at a specific line. Breakpoints help us to:

1. Examine the state of the program at a particular point.
2. Verify the flow of execution.
3. Check the values of variables.

## Demo: Debugging using breakpoints in IntelliJ IDEA Community Edition IDE

Here are the IntelliJ IDEA Community Edition IDE's debugging UI elements.

![An image of IntelliJ IDEA UI highlighting debugging UI elements](./assets/IntelliJDebuggingOptions.png)

1. Debug icon
2. Breakpoint (red dot)
3. Debug panel
4. Debug execution navigation options

These are the sequence of steps you need to follow to debug using breakpoints.

### Step 1: Setting a breakpoint

- Open your Java project in IntelliJ.
- Locate the line of code where you want to pause execution.
- Click in the gutter area (the left margin next to the line numbers). A red dot will appear, indicating a breakpoint is set.

### Step 2: Starting the debugger

- Click the Debug icon (a green bug icon) in the top-right corner.
- IntelliJ will compile and run your program in debug mode, stopping at the first active breakpoint.

### Step 3: Navigating the debugging controls

Once the program pauses at a breakpoint, use the navigation buttons in the Debug panel (at the bottom of the IDE) to control execution:

- **Resume Program**: Continues execution until the next breakpoint.
- **Step Over**: Executes the current line and moves to the next line in the same method.
- **Step Into**: Steps into the method call to debug its code.
- **Step Out**: Steps out of the current method and returns to the caller.
- **Stop**: Stops the debugging session.

## Debugging features in IntelliJ IDEA Community Edition IDE

### Watching variables

- We can hover over a variable to see its current value.
- Alternatively, we can check the Variables tab in the Debug tool window to view all active variables and their values.

### Modifying variables

- We can right-click a variable in the Variables tab and select 'Set Value' to modify its value during debugging.

### Evaluating expressions

- We can Highlight any expression or variable, then right-click and choose Evaluate Expression. We can use this feature to test expressions or perform calculations on the fly.

### Adding conditional breakpoints

- We can right-click a breakpoint to add a condition (for example, x > 5) to make the breakpoint active only when the condition is true.

<div class="activity solo-exercise">
  <h2 class="title">Practice debugging</h2>
  <span class="minutes">15 min</span>
</div>

Use this sample program to complete the following tasks listed below. Feel free to try some of your own experiments too!

``` java
import java.util.ArrayList;

public class DebuggingExample {
    public static void main(String[] args) {
        ArrayList<Integer> numbers = new ArrayList<>();
        for (int i = 1; i <= 10; i++) {
            numbers.add(i);
        }

        int sum = calculateSum(numbers);
        System.out.println("The sum of numbers is: " + sum);
    }

    public static int calculateSum(ArrayList<Integer> numbers) {
        int sum = 0;
        for (int num : numbers) {
            sum += num;
        }
        return sum;
    }
}
```

### Task 1: Set breakpoints

- Place a breakpoint on the `numbers.add(i)` line inside the `for` loop.
- Place another breakpoint on the `sum += num` line in the `calculateSum` method.

### Task 2: Start debugging

- Click the Debug icon.

### Task 3: Observe the execution flow

- The program will pause at the first breakpoint `(numbers.add(i))`.
- Hover over `numbers` in the **Debug** panel to see the current state of the list.

### Task 4: Step through the code

- Click the **Step Over** icon to see how the `for` loop adds elements to the list.
- When execution reaches the `calculateSum` method, click the **Step Into** icon to debug its logic.

### Task 5: Evaluate variables

- At the `sum += num` line, hover over `sum` and `num` in the Debug panel to see their values.
- Use the Evaluate Expression feature (<kbd>Alt</kbd> + <kbd>F8</kbd> or <kbd>Option</kbd> + <kbd>F8</kbd> on macOS) to test sum + num.

### Task 6: Resume and complete execution

- Click the Resume Program icon to allow the program to complete execution.
