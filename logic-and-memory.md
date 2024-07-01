# Logic and Truth

* Computers and Logic
    • Automata: computers automatically run commands based on their state
    • State: stored in memory (RAM)
    • Execution: command are executed by the processor (CPU)
    • I/O devices: keyboards, mice, screens, speakers, and internet interfaces allow interaction

* Von Neumann Architecture
    • Code is translated into machine instructions
    • Instructions are loaded into memory and executed by the CPU
    • Instructions include arithmetic, logic operations, and control flow

* Logic and Truth Tables
    • Syllogistic Logic: originates from Aristotle, involves deriving truth from premises
        - Example: "All humans are mortal. Socrates is a human. Therefore, Socrates is mortal."
    • Booleans: True or False values used in logical expressions

* Logical Operators

• AND (&&): True if both operands are true
```js
A   B   A && B
--------------
0   0      0
0   1      0
1   0      0
1   1      1

```

• OR (||): True if either operand is true
```js
A   B   A || B
--------------
0   0      0
0   1      1
1   0      1
1   1      1

```

• NOT (!): Inverts the boolean value
```js
A   !A
-------
0    1
1    0

```

* Compound Logic

• NAND: Not AND, true unless both operands are true
```js
A   B   A && B   !(A && B)
--------------------------
0   0     0          1
0   1     0          1
1   0     0          1
1   1     1          0

```

• De Morgan's Law: Logical equivalence of expressions
    • Example: `!(A && B)` is equivalent to `!A || !B`
```js
A   B   !A   !B   !A || !B
---------------------------
0   0    1    1       1
0   1    1    0       1
1   0    0    1       1
1   1    0    0       0

```

* XOR (Exclusive OR)

• XOR(^): True if exactly one operand is true
```js
A   B   A ^ B
--------------
0   0      0
0   1      1
1   0      1
1   1      0

```
• Alternative Expression: `(A && !B) || (!A && B)`

* Key Takeaways
    • Truth Tables: visual representation of logical expressions
    • Logical Equivalence: different expressions can produce the same truth values
    • Simplifying Logic: Aim for simple and clear logical expressions


# Simplifying Code Logic

Logical equivalence can be used to simplify and condense your code to make it more readable and maintainable. Here's an example to illustrate this concept.

* Counting to Zero
We will write a function that takes a number and counts from that number to zero, handling various cases including posititive and negative integers, as well as non-integers.

* Example Output:
```js
countToZero(5);
// 5
// 4
// 3
// 2
// 1
// 0

countToZero(-5);
// -5
// -4
// -3
// -2
// -1
// 0

countToZero(5.5);
// 5.5
// 5
// 4
// 3
// 2
// 1
// 0

```

* Key Points to Consider
    1. Positive Non-integer: Print the number, subtract the decimal part, and continue
    2. Negative Non-integer: Print the number, add the negative decimal part, and continue
    3. Positive Integer: Print the number, subtract 1, and continue
    4. Negative Integer: Print the number, add 1, and continue
    5. Zero: Print zero and terminate

* Checking for Integers
To determine if a number is an integer, use the modulo operator:
```js
function isInt(n) {
    return n % 1 === 0;
}
```

* Initial Verbose Solution
```js
function countToZero(n) {
    if (n > 0 && !isInt(n)) {
        console.log(n);
        countToZero(n - n % 1);
    }

    if (n < 0 && !isInt(n)) {
        console.log(n);
        countToZero(n + -(n % 1));
    }

    if (n > 0 && isInt(n)) {
        console.log(n);
        countToZero(n - 1);
    }

    if (n < 0 && isInt(n)) {
        console.log(n);
        countToZero(n + 1);
    }

    if (n === 0) {
        console.log(0);
    }
}
```

* Simplifying the Code
To simplify, we note:
    • All conditions start with `console.log(n)`
    • Modulo operation can be used to determine the decrement for non-integers
    • Decrement for integers should be based on the sign of the number

* Simplified Implementation:
```js
function countToZero(n) {
    // print the number
    console.log(n);

    // base case: end on zero
    if (n === 0) return;

    // decrement the non-integer part for non-integers
    let decrement = n % 1;

    // if number is an integer, decrement by 1 * the sign of n
    if (decrement === 0) {
        decrement = n / Math.abs(n);
    }

    // recurse
    countToZero(n - decrement);
}
```

* Recap
In this example, we learned how to simplify code logic by:
    1. Identifying common operations across conditions
    2. Using mathematical properties (e.g. modulo operation) to reduce redundancy
    3. Refactoring code to make it more concise and readable

Simplifying your code not only makes it easier to read and maintain but also helps in identifying potential errors and improving performance.
