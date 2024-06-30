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
